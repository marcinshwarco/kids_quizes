# Quizzes for kids
This is a child friendly quiz that allowed children to guess multiple times before submitting the correct answer. 
The quiz is designed to minimise child's frustration, so children can keep guessing until their answer is correct. 


The JavaScript quiz engine is included in every quizpage and the questions/clues for a particular quiz are stored in a separate js. files as arrays


#Quiz engine with comments below
//variable setup
var questionIndex = 0; // var questionIndex is used to track question number and to select items from questions array
var col = document.getElementById('col'); // gets the html element 
var col2 = document.getElementById('col2'); //   gets the html element 
var score = 0; // keeps track of the quiz score
var totQuestions = questions.lenght; // holds the length value of the questions array
var mainQuestion = document.getElementById('mainQuestion'); // gets the html element 
var secondQuestion = document.getElementById('secondQuestion'); // gets the html element 
var thirdQuestion = document.getElementById('thirdQuestion'); // gets the html element 
var opt1 = document.getElementById('opt1'); // gets the html element
var opt2 = document.getElementById('opt2'); // gets the html element
var opt3 = document.getElementById('opt3'); // gets the html element
var opt4 = document.getElementById('opt4'); // gets the html element
var tick = document.getElementById('tick'); // gets the html element
var cross = document.getElementById('cross'); // gets the html element
var displayAnswer= document.getElementById('displayAnswer'); // gets the html element
var answer; // var answer is use to store the value of selected answer
var checker = false; // checker is used to check if the answer is selected

//Function below is executed when one of the options is selected. 

function myFunction(event, questionIndex) {
var question_Number = questionIndex +1; // var question_Number is used to set the current question number
document.getElementById('question_number').innerHTML = 'Question ' + question_Number +' /6'; //Displays current question number to the user
var qMain = questions[questionIndex][0]; // selects the first clue from questions array
mainQuestion.textContent = qMain; // sets the first clue as text in <h2> with id "mainQuestion" 
var qSecond = questions[questionIndex][1]; // selects the second clue from questions array
secondQuestion.textContent = qSecond; // sets the second clue as text in <h2> with id "secondQuestion" 
var qThird = questions[questionIndex][2]; // selects the third clue from questions array
thirdQuestion.textContent = qThird; // sets the third clue as text in <h2> with id "thirdQuestion" 
opt1.innerHTML = questions[questionIndex][3]; // sets button's innerHTML to the value of an item in questions array
 opt2.innerHTML = questions[questionIndex][4]; // sets button's innerHTML to the value of an item in questions array
 opt3.innerHTML = questions[questionIndex][5]; // sets button's innerHTML to the value of an item in questions array
 opt4.innerHTML = questions[questionIndex][6]; // sets button's innerHTML to the value of an item in questions array
var x = event.target; // setsthe event target
  if (x == opt1 || x == opt2 || x == opt3 || x == opt4){
  checker = true; // if answer selected - checker value changes to true
  answer = x.innerHTML; // var answer takes the value of button's innerHTML
  displayAnswer.innerHTML = 'What am I? ' + x.innerHTML; // selected answer is displayed on the website
  }
  
  
  if ( answer == x.innerHTML && answer == questions[questionIndex][7]) {var audio = $("#firstsoundclip")[0]; 
      audio.play();  tick.style.visibility="visible"; cross.style.visibility="hidden";} else if (answer == x.innerHTML && answer!== questions[questionIndex][7]){var audio = $("#secondsoundclip")[0];
      audio.play();  cross.style.visibility="visible"; tick.style.visibility="hidden";} // the 'if else' statement is used to play a sound when the answer is selected
  }
  
  //Function below is executed when "next question" button is clicked.
var buttonNext =document.getElementById('buttonNext').addEventListener('click', function nextQuestion(){
    tick.style.visibility="hidden"; // hides the green tick
	cross.style.visibility="hidden"; // hides the red cross
    displayAnswer.innerHTML = 'What am I? '; // brings displayAnswer.innerHTML back to its original value
   if(checker == false) {alert('Please select your answer'); return;} // if checker value equals to false, the prompt message will remind user to select the answer
  if (answer == questions[questionIndex][7]) {score+=1; questionIndex++;} // if selected answer is correct the score and questionIndex increase by 1
     else {questionIndex++;}  // if selected answer is incorrect onle the questionIndex increases by 1
  if (questionIndex == questions.length -1) {
    document.getElementById('buttonNext').innerHTML ="Finish";} //When the last question is displayed, the text on the 'next' button changes to 'finish'
if (questionIndex == questions.length) {col.style.display ='none'; col2.style.display ='block'; document.getElementById('result').innerHTML = 'You answered: ' + score + ' out of ' +questionIndex + ' question(s) correctly.';}
	checker = false; //at the end of the quiz the score and congratulation message are displayed to the user
myFunction(event, questionIndex); // myFunction is called

});
myFunction(event, questionIndex); // myFunction is called

