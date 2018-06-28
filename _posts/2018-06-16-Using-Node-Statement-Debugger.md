---
layout: post
title: "Using Node Statement Debugger"
date: 2018-06-16 23:03:44
tags:
- hacker
- terminal
- nodejs
---

# My method for debugging code using terminal rather than browser console

Test aren't really effective for arriving or developing a solution, rather they are for more on if you did the right thing. This is why we need a debugger statement.

1. Place a debugger in a function to inspect.
2. Make sure to call the function.
3. In terminal, run `node inspect index.js`
4. Run `cont` to continue debugging function.
5. To inspect some variable floating around the function. Enter *repl* mode by running `repl`.
6. Enter the var name to check its value.
7. We can also run a line of code and check if its working properly or spitting out the valueas expected.
8. To exit, press `ctrl + C`.

Another scenario is testing a for loop.

1. Repeat steps 1 to 5.
2. Since its a *for loop*, it can be executed many times. Leave the repl by `ctrl c`.
3. Continue execution again by entering c.
4. Now its paused again on 2nd iteration of for loop.
5. If you press c again, it will go to 3rd iteration and so on.
6. You can enter repl again and check/audit variables.

When done with debugger, make sure to remove debugger statement and remove function call. We had to call function manually to invoke function and pass in value.

## Cleaner debugger steps

1. Add a `debugger` statement in your function.
2. Call the function manually.
3. At the terminal, run `node inspect index.js`.
4. To continue execution of the file, press `c` then `enter`.
5. To launch a `repl` session, type `repl` then `enter`.
6. To exit the `repl`, press `ctrl c`.

-----

Note that this only works for `.js` files. I'll further explore debugging in terminal with `.vue` files or other type of JavaScript framework files.

  
-----

#### References:

- [The Coding Bootcamp Interview: Algorithms and Data Structure](https://www.udemy.com/coding-interview-bootcamp-algorithms-and-data-structure/)
