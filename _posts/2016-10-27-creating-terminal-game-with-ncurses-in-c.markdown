---
layout: post
title: "Creating Terminal Game With Ncurses in C"
date: 2016-10-27T19:21:27+07:00
---

Inspired by some terminal game like nsudoku and 2048 terminal. I interested in learning on how to make those kind of game. After doing some research on internet about those game, i found 1 similiarity in those game. They are using libncurses as their rendering functions. Instead of using built in c `printf`.

## Installation
There are several ways to install libcurses. On mac, you may have it installed by default after you install xcode. On ubuntu, you can run

```
sudo apt-get update
sudo apt-get install libncurses5-dev
```

to install them

## Usage
To use the lib you only need to include ncurses header file

```
#include <ncurses.h>
```

and then you are free to use their functions

## Hello World
Here is the sample script to show hello world at certain position on screen

```
#include <ncurses.h>

int main(int argc, char const *argv[])
{
    initscr();
    while(1){
        mvprintw(10, 10, "hello");
        refresh();
    }
    endwin();
    return 0;
}
```

- `initscr()` is used to initialize an empty screen used to render the text
- `mvprintw(int position_y, int position_x, char string_to_show)` is used to print `string_to_show` at position_x and position_y relatives to the screen
- `refresh()` is used to flush changes to screen.
- `endwin()` is used to close the screen we've created using `initscr()`

To compile it run:

```
$ gcc name_of_files -o output -lncurses && ./output
```

## Sample Code with controls

You can find sample code with controls right and left via this repository
[Lapan Astronot Test](https://github.com/bekicot/lapan_astronot_test)

This post is intended to complete besut code challenge 3, create a blog post in my github blog. The code it self is intended for create an astronot game. For my Data Structure project.
The sample code is unfinished, but it should be runable on ubuntu / mac.

