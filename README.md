# Color-Game-Code.Org
Practice and Lesson in Code.Org
var randButtonId;
var currentPlayer = 1;
var p1Score = 0;
var p2Score = 0;
setBoard();
function setBoard() {
  var R = randomNumber(0, 235);
  var G = randomNumber(0, 235);
  var B = randomNumber(0, 235);
  var color = rgb(R, G, B);
  setProperty("button1", "background-color", color);
  setProperty("button2", "background-color", color);
  setProperty("button3", "background-color", color);
  setProperty("button4", "background-color", color);
  var R = R+20;
  var G = G+20;
  var B = B+20;
  var diffColor = rgb(R, G, B);
  setProperty("button3", "background-color", diffColor);
  var diffColor = rgb(250, 175, 20);
  randButtonId = "button"+randomNumber(1,4);   // create a random button Id
  setProperty(randButtonId, "background-color", diffColor);  
  console.log(randButtonId);
  console.log("correct one is:" + randButtonId);// set its color to diffColor
}
function checkCorrect(buttonId){
    console.log("Checking: "+buttonId);
    if (buttonId == randButtonId) {
      console.log("right");
      updateScoreBy(1);
    } else {
      console.log("wrong");
      updateScoreBy(-3)();
    }
    switchPlayer();
}
onEvent("button1", "click", function(){
    checkCorrect("button1");
});
onEvent("button2", "click", function(){
    checkCorrect("button2");
});
onEvent("button3", "click", function(){
    checkCorrect("button3");
});
onEvent("button4", "click", function(){
    checkCorrect("button4");
});
function switchPlayer(){
    if(currentPlayer==1){
        currentPlayer=2;
        hideElement("player1_highlight");
        showElement("player2_highlight");
    } else {
        currentPlayer=1;
        hideElement("player2_highlight");
        showElement("player1_highlight");
    }
    console.log("current player is: "+currentPlayer);
}
function updateScoreBy(amt){
    if(currentPlayer == 1){
        p1Score = p1Score + amt;
    } else {
        p2Score = p2Score + amt;
    }
    console.log("P1 score: " + p1Score);
    console.log("P2 score: " + p2Score);
}
