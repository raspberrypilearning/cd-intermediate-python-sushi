## Setting up Virtual Environments and installing libraries

One of the coolest things about Python is all the libraries available for i. A library is a piece of code that someone has already written. You can then use their code in your own programs. This allows you to do some cool stuff like send tweets or display images!

There are a ton of libraries available for Python, so if you ever want to do something it is always good to look at what libraries are available. They can save you loads of time!

In order for you to install libraries, you are going to use a tool called **pip**. Pip is a **package manager** and allows for you to install and update your libraries.

+ Open the command line on your computer and type in
```bash
pip install virtualenvwrapper
```
Note: To open the command line search for the **command prompt** on Windows or the **Terminal** on Linux or macOS.

+ Great! Once that has downloaded you are going to create a **virtual environment** for your programs to run in.

```bash
mkvirtualenv -p python3 intermediate-sushi
```

--- collapse ---
---
title: What's a virtual environment and why do I need one?
---

Sometimes libraries can get annoying, especially if you have a lot of them!

For example: Say you write a game which needs the **pygame** library (a library which helps you create video games). A few months later you write another game which also uses **pygame**, but it has just been updated. So you update **pygame** and make your new game. But when you go back to your old game, it is now broken!

This is a common situation, and is caused because libraries change from version to version. This means that code that used to work won’t anymore! Instead you should give specific programs specific versions of the libraries.

To do this, create **virtual environments**. This will mean that each of your programs will have their own copy of the library, which will only change when you’re working on that particular program. So none of your programs will ever have the wrong libraries.

The **virtualenvwrapper** tool makes this simple for you to do. 

--- /collapse ---

+ Finally you need to go into that virtual environment. To do this just run:

```bash
workon intermediate-sushi
```
  **Note:** Everytime you want to work on these sushi cards, you’ll need to run this command.

Perfect! Now that you are inside this virtual environment you can install the library that you need. You want the `guizero` library, which will make designing programs a breeze! 

+ To do this just run:

```bash
pip install guizero
```

