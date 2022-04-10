# Compile your code
---

There are many ways to compile code for kilobots. This guide presents
two of them.

!!! note
    The following methods have mostly been tested on **MacOS Big Sur**.

    If you experience any problem, please consider visiting [this quick-start wiki](https://diode.group.shef.ac.uk/kilobots/index.php/Getting_Started:_How_to_work_with_kilobots#Compile_your_own_control_software) or [this guide from the official website](https://www.kilobotics.com/documentation#advanceduse) (go to 'advanced use' in the 'documentation' section).

    Both of those websites where used to write this guide.

---

## Compiling your code - the easy way

The [kilobotics website](https://www.kilobotics.com) provides a simple online editor to write code for kilobots.

Once logged in with your Dropbox account, you can access the editor, create new programs and save them.

To compile your program, just click the green `compile` button. A `.hex` file with the same name as your `.c` file should appear in the KiloEdit directory of your dropbox.

!!! warning
    Kilobotics' online editor has aged and is not really maintained anymore. Depending on your operating system, browser or dropbox account and configurations, the editor may not work properly. If this is your case, please use the alternative method presented below.

---

## Compiling your code - the less-easy way

If the kilobotics' online editor doesn't work or doesn't suit your needs, you can still go for the tough method : compiling the code manually. The goal of this tutorial is to get you a simple command-line utility to easily compile your different programs.

!!! warning
    The following method may not work with Windows operating system.  
    We suggest that Windows users use a virtual machine running Linux.

### Step 1 : install AVR compilator

#### For Linux using `apt`

Run the following command in the terminal :
```
sudo apt-get install avr-libc gcc-avr avrdude
```

#### For MacOS using `homebrew`

Run the following command in the terminal :
```
brew tap osx-cross/avr
brew install avr-gcc
```


### Step 2 : download the template code

To get the task simpler, download [this file](https://diode.group.shef.ac.uk/kilobots/images/8/8a/TemplateForCompilingKilobotCode.zip).

It contains a shell script that will take care of library dependencies and allow us to compile code with just one command.


### Step 3 : place your files inside the template directory

Place your files inside the 'TemplateForCompiling' directory. They should now be in the same directory as `compileCode.sh`.

### Step 4 : compile with one command

Open a terminal window and navigate inside the 'TemplateForCompiling' directory with the `cd` command.

Type the following command :

```
./compileCode.sh your-file
```

!!! note
    Replace 'your-file' by the real name of the file you want to compile.

!!! note
    Note how we didn't put the `.c` extension at the end of the file name.


### We are done !

The `.hex` file corresponding to your program should now appear inside the 'TemplateForCompiling/build/' directory.

If anything went wrong, refer to the error message returned by the `compileCode.sh` script. If your code contains syntaxical errors, they will be listed there.

---

## Compiling your code - the windows' hard way

If the kilobotics' online editor doesn't work or doesn't suit your needs and that you are a windows’ user who doesn't want to use a virtual machine, this way is for you. 

The goal of this tutorial is to get you a simplified guide to compile on windows with Eclipse IDE and the WinAVR .


---

### Step 1 : Install WinAVR



- [Download](http://winavr.sourceforge.net/) and install WinAVR. During installation, accept the option to install Programmer’s Notepad.


---

### Step 2 : Build Kilolib



- [Download](https://github.com/acornejo/kilolib) Kilolib and extract the zipped file.


- In your text editor of preference, click `File -> Open`, navigate to the Kilolib directory and open the file `blank.c`. 

- Click `Tools > Make All`.

!!! note
    If all goes well, you should get: `Process Exit Code: 0`. The built files are now found under `/build` in your Kilolib directory. The static library is the file `kilolib.a`.

---

### Step 3 : Install Eclipse and Plugins


- Install Eclipse with c/c++ support, link available [here](http://eclipse.org/downloads/packages/eclipse-ide-cc-developers/lunasr2)

- Install the AVR Eclipse plugin by following the instructions [here](http://avr-eclipse.sourceforge.net/wiki/index.php/Plugin_Download).

 ---


### Step 4 : Create the Project

- Open Eclipse and select a workspace.

- Click `File > New > C Project`.

- In the dialog, give your project a name (here we'll assume it's `Kilobot`) and under `Project Type`, select `AVR Cross Target Application > Empty Project`.

- Click `Next`.

-  Uncheck `Debug` and click `Next`.

- In the next dialog (`AVR Target Hardware Properties`), under `MCU Type` select `ATmega328P`, and set the `MCU Frequency` to `8000000` Hz (8 MHz).

- Click `Finish`.

- Create a new source file in your project by right clicking on the project's name `> New > Source File`.

- Give this new source file a name, e.g. `main.c`. Copy and paste into this file the code from `blank.c` found in the Kilolib directory.

### Step 5 : Set the Header and Library File Paths

- In your Eclipse project, create two new directories and call them `include` and `lib` (to create a new directory, right click on the project name `> New > Folder`). 

- Copy *all* the .h files from the Kilolib directory into the `include` directory in your project. 

- Copy the `kilolib.a` file from `/build` in the Kilolib directory into the new `lib` directory in your project. 

- Rename the kilolib.a file you just copied into the `lib` directory to `libkilolib.a` (i.e. prepend it with "lib").


- Right click on the project name and click `Properties`.  Go to `C/C++ Build -> Settings`. Under `Tool Settings` go to `AVR Compiler -> Directories`. Under `Include Paths (-I)` add a new path. Click `Workspace` and navigate to the `include` directory in your project. Click `OK`.

- Still under `C/C++ Build -> Settings`, go to `AVR C Linker -> Libraries`.

- Under `Libraries Path (-L)` add a new path. Click `Workspace` and navigate to the `lib` directory in your project. Click `OK`.

- Under `Libraries (-l)` add a library and type: `kilolib`.

---

### Step 6 : Build Your Code and Upload it to a Kilobot



- Close the settings - you’re now good to go. Build the project by pressing `Ctrl+B` (or going to `Project -> Build All`). A `Release` directory will be created in your project, and this will contain the object code file (aka "hex file"), `Kilobot.hex`.

- You can now upload the hex file onto your Kilobot robot using the [KiloGUI tool](https://github.com/acornejo/kilogui).


!!! note
    When starting a new project, you might want to rename a copy of your boilerplate project. Apart from renaming the directory, you also need to open each of the files `.cproject` and `.project`, and do a Search and Replace operation from the old (boilerplate) project name to your desired new one.

---

If you want the complete guide or if you have some unexpected results you can click [here](https://github.com/mgauci/kilobot_notes/blob/master/eclipse_winavr_setup/eclipse_winavr_setup.md)
