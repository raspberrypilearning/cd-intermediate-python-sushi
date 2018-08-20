## Displaying the questions

You’re now going to create your second screen. 

+ Down near the bottom create a new Box called **playQuizScreen**

+ At the start this screen should be hidden so you can write:

```python
playQuizScreen.hide()
```

+ You should also add a title. Do you remember how to do this? Look at the code for the first screen if you don’t!

On this screen you are going to be adding and deleting elements every time a question is shown.

+ To make this easy, create another **Box** called questionBox:

```python
questionBox = guizero.Box(playQuizScreen)
```

Perfect! Now that you have your new screen you’re going to need to show it when the user selects a quiz.

+ Go back to the `playQuiz` function and add in

```python
selectQuizScreen.hide()
playQuizScreen.show()
```

+ Go ahead and test out the program now. See can you select a quiz and change the screen. You’ll notice that there are no questions! That’s what you are going to do next.

+ Create a new function `showNewQuestion`. This needs two **parameters**: the list of questions and the index (position) of the current question.

```python
def showNewQuestion(quizQuestions, index):
```

+ Now call this function from the `playQuiz` function.

```python
showNewQuestion(quizQuestions, 0)
```

In this you first want to clear out the **questionBox** you made earlier. This requires a few things
  * First: You need to access the **questionBox** variable. This variable was created outside of a function and so is a **global** variable. This means it can be accessed anywhere. To tell python to use it type:
  ```python
  global questionBox
  ```
  * Next you need you need to remove the old questionBox
  ```python
  questionBox.destroy()
  ```
  * Finally you need to create a new empty one
  ```python
  questionBox = guizero.Box(playQuizScreen)
  ```

+ Next you want to get the current quiz question. Remember when you created the json data you gave it the key “questions”? Well to access that data you use that key again, along with the index of the question.
```python
currentQuestion = quizQuestions[“questions”][index]
```

Now you need to ask the player the question. 

+ Create a Text element with the text set to the question.

```python
guizero.Text(questionBox, text=currentQuestion[“question”])
```

Perfect! You just need buttons now for all the answers. However, first you should think of which order they should be in. It would be cool if the order changed every time!

To do this you will need an list containing all the answers. You already have a list of the incorrect answers, so you can just add the correct answer to this.

+ Using the `append` method you can add the correct answer to the list.

```python
currentQuestion["incorrect_answers"].append(currentQuestion["correct_answer"])
```

+ Finally you want to randomize the order that the answers are in. To do this you’ll need to import the `random` library. Then you can use `shuffle` to well **shuffle** the list!

```python
random.shuffle(currentQuestion["incorrect_answers"])
```

Ok, I know, a lot has been covered, but you’re nearly there. 

+ The last thing to do is add all these buttons. You’re going to use a **for loop** again.

```python
for answer in currentQuestion["incorrect_answers"]:
```

For this you are going to need to know if it's an incorrect answer you are adding or a correct answer. 

+ You can do this really simply by using **conditional expressions**
```python
functionToCall = selectedCorrectAnswer if answer == currentQuestion["correct_answer"] else showNewQuestion
```

  **Note:** You can say it at loud to understand it. The function to call **is** selectedCorrectAnswer **if** answer **is** the correct answer **else** the function **is** showNewQuestion

+ Now you need to create these buttons. Their arguments will be the quizQuestions and the new index

```python
guizero.PushButton(questionBox, functionToCall, args=[quizQuestions, index + 1], text=answer)
```

+ Lastly (hooray!) you need to define the `selectedCorrectAnswer` function. Just have it call the `showNewQuestion` function for now.

```python
def selectedCorrectAnswer(quizQuestions, index):
      showNewQuestion(quizQuestions, index)
```
