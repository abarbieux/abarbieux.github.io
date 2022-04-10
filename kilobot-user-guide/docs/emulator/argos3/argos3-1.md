# Game of life

[*source code of this tutorial*](../resources/sources/Live.c)

---

## Context

The Game of Life is a cellular automaton devised by John Horton Conway. It is a simple game where we can choose the initial state of each "cell" in the grid board ( living or dead) and see how they evolve.

The rule are simple, if a living cell is too isolated  then it dies the next turn. If it is  surrounded by 2 or 3 neighbors then it remains alive, but what if it is surrounded by more it dies to the next turn.

A cell can also become a live cell if a dead cell is surrounded by three living cells then it becomes alive in the next turn.

---

## Goal

The goal of this project was to recreate the Game of Life with the kilobots but without the grid limitation.

---

## Working

The kilobots are place in a large area. They begins with the state "dead" or "living". The majority of the time they send a message with their statut. Next, after a certain number of seconds they update their statut following the rules of the Game of life.

---

## Schema

---

## What you will learn

* Basic template for a kilobot program
* How to make the kilobot flash color with `set_color()`
* How to make the kilobot move with `set_motors()`

---



---

## We are done !

You can now admire your kilobot burn the tarmac ! Well, it might not be that impressive. The kilobots were probably not designed as racing machines. But fair enough, it at least made you learn the basics of programming for kilobots !

---
