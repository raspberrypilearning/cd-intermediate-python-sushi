## Showing the score

You’re on the last step now. You have created a program to make quizzes, you can select the quiz you want to play and you can show the question and the answers. Now the only thing left to do is to keep score.

+ Firstly create a new variable `score` near the top of your code. Set `score` to `0`.

+ Inside the `selectedCorrectAnswer` function you are going to need to access the score variable, to increase it. This should be done before the `showNewQuestion` function is called. Type:
```python
global score
```

  **Remember:** Since `score` is a **global** variable it can be accessed anywhere, but we need to **tell** python to use it.

+ Then just increase the score by one:
```python
score += 1
```

+ Perfect! Now you just need somewhere to display this score. Go ahead and create a new screen called **scoreScreen**. Remember to hide it!

+ Right! Now add a title and also a **PushButton**. Give the button a text of “Finished!” and a function `resetProgram`.

+ Once all the questions have been answered you should show this screen. Go back to the `showNewQuestion` function and add an `if` statement at the very beginning to test whether the current index (the amount of questions you have already asked) is equal to the total amount of questions.
```python
if(index == len(quizQuestions["questions"])):
```

+ If so hide the playQuizScreen and show the scoreScreen!

+ One more thing: you need to setup a **Text element** for the score. Do this inside your `if` statment. Since you are combining a number with a string, you’ll need to use the `str()` function around the `score` variable.
```python
“Score: ” + str(score)
```

+ Surround the previous code in that function in an `else` statement

+ Now for some final touches, you need to create the **resetProgram** function.

+ First reset the score value. Remember to access it you have to type:
```python
global score
```

+ Next hide the scoreScreen and show the selectQuizScreen!
