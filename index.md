 <html>
  <head>
    <link href="https://fonts.googleapis.com/css2?family=Krona+One&display=swap" rel="stylesheet">
    <style>
    body{background-color:orange;}
h1{text-align:center;
font-family: 'Krona One', sans-serif;
  color:navy;
  font-size:300%;}
h2{text-align:center;
font-family: 'Krona One', sans-serif;
  color:navy;
  font-size:150%;
margin-top:-20px;}
h4{padding:5px;
font-family: 'Krona One', sans-serif;
  color:navy;
  font-size:130%;
text-align:center;
}
#result{border:5px double navy;
border-radius:20px;
box-shadow:gray 10px 10px;
margin-bottom:20px;
min-height:300px;
max-height:310px;
min-width:300px;
max-width:300px;
background-color:gold;
background-size:cover;}
#result2{min-height:300px;
background-color:gold;
max-height:310px;
min-width:155px;
max-width:180px;
border:5px double navy;
border-radius:20px;
box-shadow:gray 10px 10px;
margin-bottom:20px;
margin-left:10px;
display:flex;
flex-flow:column;
justify-content:center;
padding:5px;}
#result3{min-height:300px;
background-color:gold;
max-height:310px;
min-width:100px;
max-width:160px;
border:5px double navy;
border-radius:20px;
box-shadow:gray 10px 10px;
margin-bottom:20px;
margin-left:10px;
display:flex;
flex-flow:column;
justify-content:center;
padding:5px;}
button{background-color:gold;
  color:navy;
  font-weight:bold;
  width:150px;
  border-radius:20px;
  height:50px;
  border:none;
}
input{
  color:navy;
  font-weight:bold;
  width:200px;
  height:50px;
border:none;
margin-left:0px;
margin-right:10px;
border-radius:10px;}

#resultarea{display:flex;
flex-flow:row wrap;
justify-content:center;}
#inputarea{display:flex;
flex-flow:row wrap;
justify-content:center;}
span{font-family: 'Krona One', sans-serif;
  color:navy;}
#other{background-color:gold;
align-self:center;
width:200px;}
#submit{padding:50x;
  background-color:gold;}
#giveup{background-color:gold;
margin-left:10px;}
::placeholder{color:navy;
opacity:0.7;}
button:hover{box-shadow: gray 5px 5px;}
img{position:absolute;
width:100px;
height:100px;}
#attempt{font-family:sans;
padding:5px;
font-weight:bold;
color:navy;
font-size:15px;
background-color:orange;
margin-bottom:10px;}
h5{color:navy;
font-size:30px;
text-align:center;
padding:5px;
font-weight:bold;
margin-top:-10px;
font-family:sans}
#score{font-family:sans;
padding:5px;
font-weight:bold;
color:navy;
font-size:15px;
background-color:orange;
margin-top:10px;
margin-bottom:10px;}
#streak{font-family:sans;
padding:5px;
font-weight:bold;
color:navy;
font-size:15px;
background-color:orange;
margin-bottom:10px;}
#guessessofar{font-family:sans;
padding:5px;
font-weight:bold;
color:navy;
font-size:15px;
background-color:orange;}
#stats{text-align:center;
font-weight:bold;
color:navy;
font-family: 'Krona One', sans-serif;
  font-size:130%;
}
#guesscounter{font-size:14px;}

@media only screen and (max-width: 900px) {
  img{position:relative;}
}
#currentguess{color:navy;
font-family:sans;
font-weight:bold;
margin:7px;
background-color:white;
padding:10px;}
    
    </style>
 </head>
  <body onload="generate();">
    <a  href="https://codepen.io/MoHus1"><img alt="Mohamed Initials Logo"src="https://assets.codepen.io/4633895/internal/avatars/users/default.png"></a>
    <h1>Guess The Number</h1>
    <h2>Between 0 and 1000</h2>
   <h5 id="nomoreattempts"></h5>
    <div id="resultarea">
    <section id="result"></section>
      <section id="result2">
        <h4 id="status"></h4>
      </section>
 <section id="result3">
        <p id="stats">Game Stats:</p>
        <div id="attempt">Attempts:<span id="attemptcounter"></span></div>
        <div id="guessessofar">Your Guesses:<span id="guesscounter"></span></div>
         <div id="score">Wins:<span id="scorecounter"></span></div>
        <div id="streak">Win Streak:<span id="streakcounter"></span></div>
      </section>
       </div>  <div id="inputarea"> 
      <input type="number" placeholder="Your Guess Here..." id="guess">
    <button onclick="check()" id="submit">Submit Guess</button>
    <button onclick="reveal()" id="giveup"> Give Up?</button>
    <button onclick="generate()" id="other"> Try Another Number</button>
    </div>
    <script>
    var result1 =  document.querySelector("#result");
var result2 =  document.querySelector("#result2");
var result3 =  document.querySelector("#result3");
var guesscounter = document.querySelector("#guesscounter");
var streakcounter = document.querySelector("#streakcounter");
var streak=0;
streakcounter.innerHTML=" "+streak;
var scorecounter = document.querySelector("#scorecounter");
var score=0;
scorecounter.innerHTML=" "+score;
var resultimage = document.querySelector("#result");
var input = document.getElementById("guess");

input.addEventListener("keyup", function(event) {
    if (event.keyCode === 13) {
        event.preventDefault();
 document.getElementById("submit").click();}});

function generate(){computerchoice =Math.floor((Math.random() * 1000 + 0));
  attempts=0;
  attemptalert=document.querySelector("#nomoreattempts");
  attemptalert.style.display="block";
  numberofattempts= document.querySelector("#attemptcounter");
  numberofattempts.innerHTML=" " + attempts+"/15";
    h4=document.querySelector("#status");
    h4.innerHTML="Try To Guess The Whole Number Between 0 And 1000.";
  h4.style.fontSize="21px";
  var guesscounter = document.querySelector("#guesscounter");
  guesscounter.innerHTML=" ";
  var newgamebutton = document.querySelector("#other");
  newgamebutton.style.display = "none";
  var inputarea = document.querySelector("#guess");
  inputarea.style.display = "inline";
   var submitbutton = document.querySelector("#submit");
  submitbutton.style.display = "inline";
  var giveupbutton = document.querySelector("#giveup");
  giveupbutton.style.display = "inline";
  attemptalert=document.querySelector("#nomoreattempts");
    attemptalert.innerHTML="You Have A Maximum Of 15 Attempts ";
  attemptalert.style.backgroundColor="orange";
  attemptalert.style.color="navy";
 var statusimage=document.querySelector("#result");
  statusimage.style.backgroundImage="url('https://cdn.pixabay.com/photo/2016/05/28/05/40/question-mark-1421017_960_720.png')";
 result1.style.marginTop="-10px";
    result2.style.marginTop="-10px";
    result3.style.marginTop="-10px";
  }
function check(){
    var guess=document.querySelector("#guess").value;
if ((attempts>13)&&(guess!==computerchoice)){
  streak=0;
    streakcounter.innerHTML=" "+streak;  attemptalert=document.querySelector("#nomoreattempts");
    attemptalert.innerHTML="You Ran Out Of Attempts. The Number Was " + computerchoice+". Try Another Number.";
    attemptalert.style.backgroundColor="red";
  attemptalert.style.color="white";
  var newgamebutton = document.querySelector("#other");
  newgamebutton.style.display = "block";
 var inputarea = document.querySelector("#guess");
  inputarea.style.display = "none";
 var submitbutton = document.querySelector("#submit");
  submitbutton.style.display = "none";
 var giveupbutton = document.querySelector("#giveup");
  giveupbutton.style.display = "none";}
  if(guess==""){
        h4.innerHTML='Type A Guess In The Box Below';}
else{ if(computerchoice==guess){
  attemptalert.style.display="none";
  result1.style.marginTop="75px";
    result2.style.marginTop="75px";
    result3.style.marginTop="75px";
            h4.innerHTML='Well Done. You Correctly Guessed That The Number Was '+computerchoice+'. Try Another Number.' ;
  document.querySelector("#scorecounter");
          var guesscounter = document.querySelector("#guesscounter");
  guesscounter.innerHTML+=" "+guess;
score++;
streak++;
scorecounter.innerHTML=" "+score;
streakcounter.innerHTML=" "+streak;
           var inputarea = document.querySelector("#guess");
  inputarea.style.display = "none";
     var statusimage=document.querySelector("#result");
  statusimage.style.backgroundImage="url('https://www.publicdomainpictures.net/pictures/80000/velka/winners-trophy-clip-art.jpg')";
 var submitbutton = document.querySelector("#submit");
  submitbutton.style.display = "none";
 var giveupbutton = document.querySelector("#giveup");
  giveupbutton.style.display = "none";
          var newgamebutton = document.querySelector("#other");
  newgamebutton.style.display = "block";}
  else if((guess<computerchoice)&&(guess>=0)){
            h4.innerHTML="Too Low...Guess Higher";
           attempts+=1;
          numberofattempts.innerHTML=" " + attempts + "/15";
          var statusimage=document.querySelector("#result");
  statusimage.style.backgroundImage="url('https://cdn.pixabay.com/photo/2020/04/12/19/05/yellow-5035413_960_720.png')";
         var guesscounter = document.querySelector("#guesscounter");
  guesscounter.innerHTML+=" "+guess+","; }
   else if((guess>computerchoice)&&(guess<=1000)){
            h4.innerHTML="Too High...Guess Lower!";
          attempts+=1;
          numberofattempts.innerHTML=" " + attempts+"/15";
          var statusimage=document.querySelector("#result");
  statusimage.style.backgroundImage="url('https://cdn.pixabay.com/photo/2019/05/27/23/45/plane-4234024_960_720.png')";
          var guesscounter = document.querySelector("#guesscounter");
  guesscounter.innerHTML+=" "+guess+","; }}}
function reveal(){ if (attempts==0){
    streak=0;
    streakcounter.innerHTML=" "+streak;
    h4.innerHTML="Did You Give Up? You Did Not Make Any Attempt To Guess The Number. Anyway, The Number Was " + computerchoice+". Try Another Number.";
    h4.style.fontSize="16px"
  var statusimage=document.querySelector("#result");
  statusimage.style.backgroundImage="url('https://cdn.pixabay.com/photo/2017/08/15/12/58/emoticon-2643814_960_720.jpg')";
  var newgamebutton = document.querySelector("#other");
  newgamebutton.style.display = "block";
 var inputarea = document.querySelector("#guess");
  inputarea.style.display = "none";
 var submitbutton = document.querySelector("#submit");
  submitbutton.style.display = "none";
 var giveupbutton = document.querySelector("#giveup");
  giveupbutton.style.display = "none";}
else if(attempts>0){ 
    h4.innerHTML="Did You Give Up? You Onlu Used "+  attempts+ " Of Your Attempts. Anyway, The Number Was " + computerchoice+" Try Another Number.";
    h4.style.fontSize="16px";
  var statusimage=document.querySelector("#result");
  statusimage.style.backgroundImage="url('https://cdn.pixabay.com/photo/2017/08/15/12/58/emoticon-2643814_960_720.jpg')";
  var newgamebutton = document.querySelector("#other");
  newgamebutton.style.display = "block";
 var inputarea = document.querySelector("#guess");
  inputarea.style.display = "none";
  var submitbutton = document.querySelector("#submit");
  submitbutton.style.display = "none";
  var giveupbutton = document.querySelector("#giveup");
  giveupbutton.style.display = "none";}}

    </script>
    </body>
</html>
  