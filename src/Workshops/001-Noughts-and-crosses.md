# Noughts and Crosses

In this workshop, you are going to use all the things you have learned about Java code to write a computer program! Our program is going to accept input from the user, store and update the state, it will print out the state so the user can see it, and finally conclude with a win, lose or draw result. What you have studied so far are the primitives of Java, branching logic, and Arrays. These are like the words and phrases of a spoken language. When we write a computer program we combine all these building blocks and compose a story.

## Before you start
This workshop assumes that you have read through the following sections from [Programviz](https://www.programiz.com/java-programming).
* [Java Introduction](https://www.programiz.com/java-programming/hello-world)
* [Java Flow Control](https://www.programiz.com/java-programming/if-else-statement)
* [Java Arrays](https://www.programiz.com/java-programming/arrays)
We are going to create a Noughts and Crosses or Tic Tac Toe game. It will be a simple version of the game that you can play on the command line. Learning to use the primitives, flow control, and Arrays as building blocks for an actual program we hope will give you great confidence and inspiration to keep building on your knowledge.

----

## Designing a program

There are 3 things to consider when we start to design a program:

* The inputs
* The state & processes
* The outputs

🤔 Let’s think about these 3 things before we start.

* What inputs do we need for a game of tic tac toe?
* What might we need to keep track of in our program?
* What will our program need to output?

### Setup

Create a new Java file in a folder with a name like `TicTacToe.java`. In that file create a class with the same name at the file, and add the `main` method. That `main` method can print out a message to our users. Then run your program to check that everything is set up correctly.
```java
public class TicTacToe {
    public static void main(String[] args) {
        System.out.println("Choose a square between 1-9 to play on");
    }
}
```
## Input
The first thing we need to do for our program to work is to capture input from the user. In Java, there is a module in the core API that will enable us to do that.
```java
import java.util.Scanner;
```
The way to use this class is to create a single instance for the program to use throughout it’s life cycle. This kind of class is called a ‘Singleton’ because there should be just one instance of the class within the program. This instance enables us to stop the program and capture input from the user, before we continue. We should try to do that now and capture numbers between 1 and 9.
```java
import java.util.Scanner;

public class TicTacToe {
    private Scanner scanner = new Scanner(System.in);

    TicTacToe() {
        captureInput();
    }
    void captureInput() {
        int input = scanner.nextInt();
        System.out.printf("You want to play on square %d", input);
    }
    public static void main(String[] args) {
        System.out.println("Choose a square between 1-9 to play on");
        new TicTacToe();
    }
}
```
## State
We have input, now we can think about the state in our program. The state is data that our program creates, reads, updates, and deletes. For us we need to create and maintain the state of the `board` during the life cycle of our program.

### The Board

A tic-tac-toe board has 9 squares that players can place their counters on. An Array is a great data structure that will help us hold those 9 related pieces of data. Can you add this state to our `TicTacToe` class?
```java
private int[] board = {1,2,3,4,5,6,7,8,9};
```
If we have input from the user, and a board to play on, we should be able to set a counter on the board where the user chose to play. Usually, the first player is `X` but we are not going to be able to add `X` into our Array - why is that?

### The Players
Our Array will only hold integers. So we could substitute the value X for integer 10, and player O with integer 0. This is also state that we will need to keep track of - who’s turn it is? When the game starts the player 10 will take the first move so player should equal 10 when the game starts, then we need to update the state after a play so the next player is player 0. Can you figure out where to add the following 2 pieces of code?
```java
private int player = 10;

private void move(int index) {
  board[index] = player
}
```
## Output

In theory, we should now be able to make a play on the tic-tac-toe board. The problem is we can’t see what’s going on. What we need is to print out the board after a move has been made.
```java
private void printBoard() {
    System.out.printf("%d|%d|%d\n", board[0], board[1], board[2]);
    System.out.printf("%d|%d|%d\n", board[3], board[4], board[5]);
    System.out.printf("%d|%d|%d\n", board[6], board[7], board[8]);
}
```
What do you get? I get something like this:
```sh
Choose a square between 1-9 to play on
1
10|2|3
4|5|6
7|8|9
```
This needs some work, but you can see we are on our way. Somewhere we need to swap out the `10` for an `X` and the `0` for a `O` we should do the same for the `int` values that represent empty squares too. Can you use conditional logic to write a function that takes an `int` and returns a `char`? You will have to update your printBoard private method to format `char` i.e. `"%c|%c|%c"`and then call your displayCell method to transform the `int` to a `char` for display purposes.
```java
private char displayCell (int index) {
    if (board[index] == 0) {
        return 'X';
    } else if (board[index] == 10) {
        return 'O';
    } else {
        return (char) Character.forDigit(board[index], 10);
    }
}
```
## First Milestone
![Keep going](https://media.giphy.com/media/RrVzUOXldFe8M/giphy.gif "You got this, keep going!")
This is going to work. We have the basic interaction of our program in place. We can capture user input, update our state and display the state of the tic-tac-toe board back to the user. Ready to build on this? Below is the list of things we need to figure out to play a full game.
1. toggle the players
1. control the flow of the game returning the prompt for the next user input
1. prevent playing over a square that’s been played on
1. check for a win
1. check for a draw
1. display the game over message

### Toggle the players
After a play, we need to toggle the players.

🤔 Can you write a private method that will return the opposite player from the one that is set?

This method needs to be called after updating the board, and before we return the prompt to the user.
```java
private int nextPlayer() {
    return player == 0 ? 10 : 0;
}
```
### Next move
Once the board is updated and the player has been toggled we want to return the prompt to the user for the next player’s input. This can be as simple as calling our `captureInput` method again. Can you update your program so you can place alternate counters (`X` `O`) on the board. I want you to be _able_ to make illegal moves, like play over a square that is already played on.

### Prevent illegal moves

We should validate or check each move before accepting it. That way if the square is not empty, then we’ll return a message to prompt the player to play again. This check method, what kind of type might it return? and how can we control the different outcomes i.e. a legal move vs an illegal move?

