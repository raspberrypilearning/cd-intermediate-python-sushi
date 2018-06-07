## Getting the user's questions

First, you are going to need a set of questions and answers. So you will need to build a quiz creator. It would look nice if it used a **GUI**. A GUI is a way of controlling programs visually. Most programs like text editors, your browser, etc use a GUI. 

+ You’re going to use the **guizero** library to create your own GUI. To do this you’ll need to import this library:

```python
import guizero
```

This tells python to import the features of the guizero library so you can make a GUI.

+ The first step is to make the actual window:

```python
app = guizero.App(title="Quiz Creator")
```

+ Of course, you need to be able to see this! So tell it to display itself

```python
app.display()
```

+ Now run this script to see your first application.

--- hints ---

--- hint ---

+ Type `python quizCreator.py` in the command line to run the progra,.

--- /hint ---

--- /hints ---
  
The first thing you need is a title. To make this you are going to need a **Text** element.

+ You can create one by typing this line above `app.display()`:

```python
guizero.Text(app, text=”Create a quiz!”, size=25)
```

--- collapse ---
---
title: How does the code work?
---

This gets a new **Text** element from guizero. 

+ Notice that you pass it `app`. This is because `app` is the container element that the **Text** element is being placed inside of. So your Text needs to belong to `app`.

--- /collapse ---

Great! Now to make a quiz you need questions, and questions have three parts: The actual question, the correct answer, and some incorrect answers.

+ First ask the user for the question. For this you will need a **Text** and a **TextBox** element:

```python
guizero.Text(app, text="What is the question?")
newQuestion = guizero.TextBox(app)
```
**Note:** You assign a variable to the TextBox so that you can access its value later

+ Repeat this for the correct answer (call its **TextBox** `correctAnswerInput`) and the incorrect answers (call its **TextBox** `incorrectAnswersInput`).

+ Great! Now you should add a button. For this you will use the **PushButton** element. It needs three things: its master(app), the text, but also a function to call when it is pressed.

  ```python
  guizero.PushButton(app, addQuestion, text="Add question")
  ```

--- collapse ---
---
title: What is a function?
---

Often when you write code, you'll want to define a bunch of lines of code that together make up one 'action'.

You do this by defining a **function** and giving it a name. 

Having code in a function lets you reuse the same bit of code lots of times without having to write it all out each time. All you have to do to run the code inside a function is to **call** the function using its name.

--- /collapse ---

+ Now you just need to add the `addQuestion` function. This needs to go above the button's code. In Python you can create functions using the `def` keyword

```python
def addQuestion():
```

**Note:** One thing to always remember is that all code inside a function needs to be indented

```python
def addQuestion():
    #I’m indented code
#I am not indented code
```

Perfect! Ok so now you need to get all the information. You’re going to be storing it like this:

```JSON
{"question": "What is the Capital of Ireland", "correct_answer": "Dublin", "incorrect_answers": ["Madrid", "Paris", "Kiev"]}
```

+ The first thing you need to do is split up the incorrect answers. At the moment they are all together as one **String**, instead they should be a **List** of strings, as shown above.

```python
otherAnswers = incorrectAnswersInput.value.split(“,”)
```

This will split the text in `incorrectAnswersInput` every time it sees a `,`, and give you back all the separated strings as a list.

--- collapse ---
---
title: Top tip for testing your code!
---

Sometimes I like to make sure my code is working. Try adding the following line and seeing the result

```python
print(otherAnswers)
```

--- /collapse ---

Cool! Now it’s time to collect all the question information. 

+ Create a new variable, called `questionToAdd`, and have it equal the following:

```python
questionToAdd = {“question”: newQuestion.value, “correct_answer”: correctAnswerInput.value, “incorrect_answers”: otherAnswers}
```

--- collapse ---
---
title: What is happening in this code?
---

What you are doing here is creating a **dictionary**. 

This is like an **list** except for every value you set a **key**. 

For example you set the **key** “correct_answer” for the correct answer.

--- /collapse ---

Ok, now you just need to store this somewhere. You are going to store it in another variable. 

+ At the top of your code type, underneath the import, type:

```python
questions = []
```

+ The last thing to do is add your dictionary to the list

```python
questions.append(questionToAdd)
```
