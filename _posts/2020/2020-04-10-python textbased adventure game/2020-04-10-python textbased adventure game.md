---
title: "Python Project No.2: Text-based Adventure Game"
tags: [python]
---

This idea immediately brought to my attention because I'm a fan of [Zork](https://en.m.wikipedia.org/wiki/Zork). For those of you don't know, Zork it's one of the earliest interactive fiction computer games, and it's text-based.

This is only the beginning of the game. The source code is in [here](https://raw.githubusercontent.com/hasturhu/hasturhu.github.io/master/_posts/2020-04-10-python%20textbased%20adventure%20game/game01.py).

## Input/Output
I'm using Python3 so no need to struggle with `input()` and `raw_input()` as the latter doesn't exist in Python3 anymore.

For output, `print()` is good enough to catch everything I need.

```python
print("\nYou are in front of an old white house.")
response = input("Would you like to step in?(yes/no)\n")
```

## If Statements
Ah, the magic statement in every language.

Note that Python's `If` result cannot be empty. If there's no action, put `pass` in the statement instead.

```python
if response == "yes":
    print("\nThere's a wooden door in front of you. It's locked from inside.")
elif response == "no":
    print("\nGoodbye.")
    quit()
else:
    pass
```

## Loops
I used `while` loops here. The logic is that the loop will continue until the input matches certain conditions.

```python
yes_no = ["yes", "no"]

while response not in yes_no:
    response = input("\nYou are in front of an old white house. Would you like to step in?(yes/no)\n")
    if response == "yes":
        print("\nThere's a wooden door in front of you. It's locked from inside.")
    elif response == "no":
        print("\nGoodbye.")
        quit()
    else:
        print("\nI didn't understand that.\n")
```

## Dedent

### Print Multiple Lines without Indent

Here comes the little challenge. Enclosed with triple quotes is the way to print multiple lines, however, it will also display indent like below.

>You find yourself standing in a kitchen. There's some food on a table.
>  On the corner, you can see a brass lantern and a knife on the counter.
>  A hallway is in the west of the kitchen.

To avoid the extra indent, use `textwrap.dedent` to remove unnecessary indent.

```python
from textwrap import dedent

  desc = dedent("""
  You find yourself standing in a kitchen. There's some food on a table.
  In the corner, you can see a brass lantern and a knife on the counter.
  A hallway is in the west of the kitchen.
  """)
  print(desc)
```
Output:
>You find yourself standing in a kitchen. There's some food on a table.
>In the corner, you can see a brass lantern and a knife on the counter.
>A hallway is in the west of the kitchen.
