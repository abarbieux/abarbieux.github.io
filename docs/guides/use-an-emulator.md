# Use an Emulator
---

## Why use an Emulator?

Use an emulator instead of real kilobot can be a real benefit for your project.

But depending on your case, some  disadvantage could be very disabling.

So, to help you choose whether using an emulator or not, here is a non-exhaustive list of Pros, Neutral and Cons

---

### Pros : fact that are at your advantage.

- You can use the emulator whereever you want.
- You are not dependent of the kilobot's battery.
- You are not limitted by the amount of your kilobots.
- You are not limitted by intengrity probleme of your kilobots.
- Testing on emulator is generally faster than testing on kilobot.
- It is easier to debug the code because you can use  `assert.h`.

---

### Neutral : Pros or Cons depending in your case.

- You will be all the time in a perfect condition to test.

---

### Cons : fact that are at your disadvantage.

- You have to choose your emulator.
- You have to set up your emulator and his config.
- You have to learn the caracteristique of your emulator and how to use it.
- When your project work in your emulator you have to adapte you code for your kilobots.

---

!!! note
    This guide only talks about `Kilombo` and `Argos3`.

    However, you are advised to look for other emulators to find the one that best suits your project.

## What Emulator choose

To choose what emulator you will use, you need to know their caracteristiques to compare them.

To learn their caracteristique, you have to read the documentation of the emulator.

But you also have to test the emulator by yourself to see if it's really what you are need.

Here his an example with [`Kilombo`](https://github.com/JIC-CSB/kilombo) and [`Argos3`](https://github.com/ilpincy/argos3-kilobot):


!!! warning
    The Exemple is based on the `Kilombo` and `Argos3` documentation and my personal experience!

    This exemple isn't exhaustive and can be invalided by an update of one of the emulator!
    
    Pleas read the documentation and test by youself before make your choice!


### `Kilombo`
  * Architecture
    * Single-thread, single process wrapper around kilolib.h
      * Robots must run the same behavior
      * Global variables cannot be used to contain state
  * Models
    * Only model offered is the Kilobot
    * Motion is kinematics with simple overlap resolution
      * Robots cannot push other objects
    * Communication neglects obstructions
    * Message drop has uniform probability
  * Features
    * pause button (pause the simulation)
    * speed button (button to accelerate or descelerate the simulation)
    * possibilities to move the kilobots with the mouse during the simulation


### `ARGoS`
  * Architecture
    * Multi-thread, multi-process architecture
    * Robots can run different behaviors
    * Global variables can be used to contain state
  * Models
    * Models of Kilobot, other robots, boxes, cylinders
      * Motion is full 2D dynamics
      * Robots can push other objects
    * Communication considers obstruction
    * Message drop considers local density
  * Features
    * pause button (pause the simulation)
    * select frame button (button to  move the simulation frame by frame)

As you can see, although these two are made to emule the kilobots, they didn't make it with the same methods!

So, if you have a project with different code  working together, it would be better to use `Argos3` because if his multy threading.

But if you have only one code in all your kilobots and that you want to test them in different layout, `Kilombo` would be better because of his speed and deplacement feature.


What emulator you choose depends of your goal(s)!


---

## How to install an emulator?

Each emulator need a specific instalation.

To know it, read the documentation or the `readme.md / readme.txt`


---



## How to Use an emulator?

Each emulator works with his own rules.

To know them, you can read the documentation but you must above all make a lot of try.




---