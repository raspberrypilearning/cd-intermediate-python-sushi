## Loading the quizzes

Now that you have that shiny, cool, new quiz you need somewhere to play it! Switch over to the second file.

+  First you’ll need to import some libraries: **guizero** and **json**.

+  Great! Now just setup the app variable again, like the last time!

For this program to work you are going to need multiple **screens**. The screen where you select the quiz, the screen where you see the questions, and the score screen.

+ To create screens with guizero you can use the **Box** element. Create your first Box called **selectQuizScreen**. Again, do this above the line `app.display()`

```python
selectQuizScreen = guizero.Box(app)
```

Now how about adding some elements! A title would be nice. This is exactly the same as on your previous program, except instead of **app** being the master you should pass in **selectQuizScreen**.

+ Add this code give the screen a title.
```python
guizero.Text(selectQuizScreen, text="Play a quiz", size=25)
```

Now, you need a way of showing the user which quizzes are available. How about having a button for each quiz?

+ To do this, you’ll need to know what json files are there. This is actually really easy thanks to the **glob** library. Go ahead and import it.

+ Type in:

```python
quizzes = glob.glob(“*.json”)
```
  By saying **\*.json** you ask glob to scan your current directory(folder) you all files that end with .json. It won’t look in any other folders though.

+ Now you want a button for each file, so you are going to have to loop through the list. For this you can use a **for loop**:
```python
for quiz in quizzes:
    #Indented code
```

Next, you’re going to need to the name of the quiz. You can use the **split** method again for this. 

+ Split the file’s name at ".json", and assign store the first item of the resulting list in a variable:

```python
buttonText = quiz.split(".json")[0]
```

+ Now just tell guizero to create the button

```python
guizero.PushButton(selectQuizScreen, playQuiz, args=[quiz], text=buttonText)
```

--- collapse ---
---
title: What is the 'args' bit?
---

You are now passing an extra thing into the PushButton: `args=`. Anything in here will get sent to the function when the button is clicked. 

You want the quiz that was clicked to be sent, so you say `args=[quiz]`.

--- /collapse ---

+ Since you are passing something to the function, you need to setup the function differently:

```python
def playQuiz(file):
```
  When this function is called, `file` will contain the quiz you want to play. The things that get passed to functions are called **parameters**.

+ Inside the function, open up the quiz file

```python
with open(file, “r”) as file:
```

+ Now from this file, you need to get all the questions. You can use the json library again for this:

```python
quizQuestions = json.loads(file.read())
```
 This tells json to load everything in that file, and put it into the variable **quizQuestions**

Amazing! Now you can choose a quiz and you can get all the questions. 

+ How about you try out the program? Add this line to test it:

```python
print(quizQuestions)
```

**Note:** Testing code is great, but you need to remember to get rid of the extra line when your done. You don’t want a file filled with `print`s!
