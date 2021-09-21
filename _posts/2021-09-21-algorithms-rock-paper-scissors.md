---
layout: post
title: "Algorithms: Rock Paper Scissors Game"
author: "Serhii T."
categories: journal
tags: [algorithms,js,game]
image: 
---

Since yesterday I worked on Rock Paper Scissors Game:
- there is no interface;
- you play with computer, so here is the fist function **computerPlay** that makes a random choice for computer:
```
//function will randomly return either ‘Rock’, ‘Paper’ or ‘Scissors’
function computerPlay(){
  let random = Math.floor(Math.random() * 3);
  if( random === 0 ){
    return 'Rock';
  } else if( random === 1 ){
    return 'Paper';
  } else {
    return 'Scissors';
  }
};
```
- trying to divide a task into several small problems first I found all possible combinations in the game:
```
// All possible combinations
// rock vs paper
// rock vs scissors
// paper vs rock
// paper vs scissors
// scissors vs rock
// scissors vs paper
```
- then write a function that plays a single round with all possible combinations mantioned above:
```
function playRound(playerSelection, computerSelection){
  if( playerSelection === 'rock' && computerSelection === 'scissors' ){
    console.log(`You Won Round! ${playerSelection} beats ${computerSelection}`);
    return 1;
  } else if ( playerSelection === 'paper' && computerSelection === 'rock' ){
    console.log(`You Won Round! ${playerSelection} beats ${computerSelection}`);
    return 1;
  } else if ( playerSelection === 'scissors' && computerSelection === 'paper' ){
    console.log(`You Won Round! ${playerSelection} beats ${computerSelection}`);
    return 1;
  } else if ( playerSelection === computerSelection ){
    console.log(`TIE! ${playerSelection} equals ${computerSelection}`);
    return 0;
  } else {
    console.log(`Computer Won Round! ${computerSelection} beats ${playerSelection}`);
    return -1;
  }
};
```
- new function for playing 3 rounds in a row. Use previous functions inside, _while_ loop and variables for keeping score of every player, [prompt function](https://developer.mozilla.org/en-US/docs/Web/API/Window/prompt) to receive input from user:
```
// game function
function game(){
  let playerScore = 0;
  let compScore = 0;
  let i = 0;
 
  while( i < 3 ){
    let playerSelection = prompt("Make your choice: Rock, Paper or Scissors").toLowerCase();
    let computerSelection = computerPlay().toLowerCase();
    let result = playRound(playerSelection, computerSelection);

    if( result === 1 ){
      playerScore++;
    } else if( result === -1 ){
      compScore++;
    }
    i++;
  }
  if( playerScore > compScore ){
  console.log(`You Won Game: Final score is You: ${playerScore} vs Computer: ${compScore}`);
  } else {
    console.log(`Computer Won Game: Final score is You: ${playerScore} vs Computer: ${compScore}`);
  }
};

console.log(game());
```

All code you could find on [GitHub](https://github.com/SergeyTocarchuk/rock-paper-scissors).