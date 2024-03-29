---
title: "Squid Game: The probability of Glass Bridge"
tags: [data, python]
toc: True
author:
  - Rick Xie
  - Aster Hu
---

> **SPOILER ALERT: this post contains spoilers up to Episode 7.**

I read an interesting article recently about Squid Game, in which the author uses Monte Carlo simulation to calculate the possible outcomes of Glass Bridge<sup id="simulation">[[1]](#reference)</sup>. So I thought it would be interesting to compare the mathematical probability vs. the simulation result.

**TL;DR**: jump to [mathematical probability table](#python-implementation) and [computer simulation chart](#compare-with-simulation).
## Assumption

Knowing that the probability is theory-based, there are few assumptions for the calculation.

1. Unlike the show, we ignore the time limit factor
2. The player remembers the choice of their previous player and can get to the right glass based on that
3. Everyone acts in the best interest of the team; the player won't block the bridge
4. The number of steps is greater than or equal to the number of players

## A simple example

#### The settings

Suppose there are only 3 steps and 3 players. In each step, a player guess which glass (of multiple glasses to choose) is the correct one. In the show, the probability of any player guessing a correct glass in each step is $\frac{1}{2}$. To better illustrate different probability later, I generalize the probability using $p$ here.

Each player <u>starts their game</u> facing different steps. "*The player starts their game facing $x$ steps*" means the previous player just dies, and the player has $x$ steps to choose. For example, in our simple game with 3 steps and 3 players, player 1 _starts the game_ by facing 3 steps. Player 2 could start the game by facing 2, 1, or 0 steps, depending on where player 1 makes a wrong choice and dies.

#### Player 1

Player 1 starts the game by facing 3 steps (denoted as $F_1^3$), so the probability that Player 1 survives (denoted as $S_1$) is simply:

$$P(S_1) = P(S_1|F_1^3) = p^3$$

#### Player 2

For player 2, there are multiple mutually exclusive events, depending on the result of Player 1:

1. (*The worst scenario*) If Player 1 makes 0 correct guesses (they die at the 1st step unfortunately), Player 2 knows the correct choice of the 1st step and starts the game by facing the remaining 2 steps (denoted as $F_2^2$);
1. If Player 1 makes 1 correct guess followed by 1 incorrect guess, Player 2 knows the correct choice of the 1st and 2nd step and faces 1 step (denoted as $F_2^1$);
1. If Player 1 makes 2 correct guesses, Player 2 knows the correct choice of the 1st to 3rd step and faces 0 steps (denoted as $F_2^0$);
1. If Player 1 survives (makes all 3 correct guesses), Player 2 also survives the game. The probability of player 2 survives **and** player 1 survives, is equal to the probability that Player 1 survives, or $P(S_1)$.

**By law of total probability, the sum of the probability of these events are the probability that Player 2 survives**:

$$P(S_2)=\underbrace{P(S_2|F_2^2)P(F_2^2)+P(S_2|F_2^1)P(F_2^1)+P(S_2|F_2^0)P(F_2^0)}_\text{Probability of Player 2 being the first survivor}+P(S_1)$$

The sum of the first three components happen to be the probability of player 2 being the first survivor in the game.

The probability that Player 2 survives conditional on when Player 2 starts the game by facing $k$ steps(i.e. $P(S_2\|F_2^k)$) is easily calculated and similar to Player 1. That is, $P(S_2\|F_2^k) = p^k$. The probability of Player 2 facing $k$ steps (i.e. $P(F_2^k)$) can be derived from Player 1. For instance, Player 2 can only start the game by facing 0 steps when Player 1 dies exactly at the 3rd step. Therefore, $P(F_2^0) = p^2(1-p)$.

#### Player 3

Similarly, the event that Player 3 survives can be decomposed too. The trick here is to decompose Player 3's survival such that it only depends on Player 2:

1. (*The worst scenario*) Player 3 will face 1 step ($F_3^1$), if Player 2 faces 2 steps and makes 0 correct guesses;
1. Player 3 will face 0 steps ($F_3^0$) when:
   1. Player 2 faces 2 steps and makes 1 correct guess only (that is, the first guess is correct and second is incorrect);
   1. Player 2 faces 1 step and 0 correct guesses;
1. If Player 2 survives (no matter how many steps Player 2 faces), Player 3 also survives. This is equal to the probability that Player 2 survives, $P(S_2)$.

**The sum of above probability is the chances that Player 3 survives:**

$$P(S_3)=\underbrace{P(S_3|F_3^1)P(F_3^1)+P(S_3|F_3^0)P(F_3^0)}_\text{Probability of Player 3 being the first survivor}+P(S_2)$$

where the 1st scenario when Player 3 facing 1 step ($F_3^1$) happens only when Player 2 faces 2 steps ($F_2^2$), **and** makes the wrong choice (with probability $1-p$). Therefore the probability is:

$$P(F_3^1) =  P(F_2^2) \times (1-p)$$

Similarly, the probability for the 2nd scenario can be broken down accordingly.

$$P(F_3^0) =  P(F_2^2) \times p(1-p) + P(F_2^1) \times (1-p)$$

## Generalization

By extending the example above, we can generalize the game to $n$ steps and $m$ players where $m \leq n$. The survival probability of player $k$ ($1 < k \leq m$) is:

$$P(S_k) = \sum_{i = 0}^{n-(k-1)}P(S_k|F_k^i)P(F_k^i) + P(S_{k-1})$$

and

$$ P(F_k^i) = \sum_{j=i+1}^{n-(k-2)}P(F_{k-1}^{j})\times p^{(j-i-1)}(1-p) $$

## Python implementation

To get the survival probability of each player, I use Python to calculate the result based on above generation. In the show, it has 16 players and 18 glasses, so I substitute the same value into players $m$ and steps $n$.

```python
import numpy as np

m = 16   # m player
n = 18   # n steps
p = 0.5 # probability of correct guess for each step; default is 50%

# Initiation
P1 = np.zeros((m, n+1))
P2 = np.zeros((m, n+1))

# P1[s,t] is the probability that player s+1 faces n-t steps
# P2[s,t] is the probability that player s+1 survives if they face n-t steps
# Note that python starts index from 0
P1[0,0] = 1
for i in range(1, m):
    for j in range(1, n+1):
        for k in range(0, j):
            P1[i, j] += P1[i-1, k]* p**(j-k-1)*(1-p)

for i in range(0, n+1):
    P2[:,i] = p**(n-i)

P2 = np.triu(P2)

# P3[t] is the probability of player t+1 being the first survivor
P3 = (P1*P2).sum(axis=1)

# P_sur[t] is player t+1's cumulative survival probability in the game
P_survival = P3.cumsum()
```
<br>
**The survival probability `P3` and `P_survival` is shown as the table below.**

<table class="display">
<colgroup>
<col width="20%" />
<col width="40%" />
</colgroup>
  {% for row in site.data.survival %}
    {% if forloop.first %}
    <tr>
      {% for pair in row %}
        <th>{{ pair[0] }}</th>
      {% endfor %}
    </tr>
    {% endif %}
    {% tablerow pair in row %}
      {{ pair[1] }}
    {% endtablerow %}
{% endfor %}
</table>
<center><i>Mathematical survival probability of Glass Bridge</i></center>

As we can see, starting from player 13, they can pretty much chill out because they have over 95% chance to survive. In the mean time, player 10 has the highest chance to become the first one to cross the bridge.

Obviously, it is an optimistic estimate due to our [assumption](#assumption).

## Compare with simulation

When we compare the mathematical probability with computer simulation, the result is quite similar. The chart below is the survival probability after running 1 million Monte Carlo simulations in R.

![p](survivor_sim.png)
*Computer simulation: survival probability of Glass Bridge*

So yes, it's a game based on pure luck and math. What lesson did we learn from it? Well, I guess it would be: *being in the middle is not always the safest choice*.

Of course, as a risk-averse person, I hope no one has to face the same choice.

> Special thanks to my partner and SO, Rick, for his tremendous contributions to the mathematical calculation in this post

## Reference

<sup>[[1]](#simulation)</sup>Helveston (2021, Oct. 19). jhelvy.com: Simulating the Squid Game bridge scene in R. Retrieved from [https://www.jhelvy.com/posts/2021-10-19-monte-carlo-bridge-game/](https://www.jhelvy.com/posts/2021-10-19-monte-carlo-bridge-game/)