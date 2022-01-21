# Next Steps

There are a few software projects that you could now try.

* Fizz Buzz
* Rock paper scissors
* Fruit machine
* Connect 4
* Battleships
* 21 Card game
* Score a tennis match
* Score 10 pin bowling

## Fizz Buzz

loop through numbers one to 100 in a full loop.
Then if a number is divisible by three you should replace the number with the word FIZZ. If a number is divisible by five you should replace the number with the word BUZZ. If a number is divisible by three and five you should replace that number with the word FIZZBUZZ.

## Rock Paper Scissors

You choose one of the following [Rock, Paper, Scissors]. Then your Java program also chooses. Then match your choices together.

Rock beats Scissors
Paper beats Rock
Scissors beat Paper

Rock lose against Paper
Paper lose against Scissors
Scissors lose against Rock

Print out a winning statement, can you keep track of your score against the Java runtime?

|Fruit Machine||
|:------------|:--|
![fruit machine](https://bloximages.chicago2.vip.townnews.com/muskogeephoenix.com/content/tncms/assets/v3/editorial/7/6a/76a44978-cf9e-11e5-a407-4799c0585b77/56baa120abb56.image.jpg)|Create a Fruit machine with credit. Enable a player to pay for a roll of the fruits! 3 of the same fruit should pay out. Different fruits pay out different amounts. Think about data structures you might use for this. You can pick at items randomly using the `Random` class [see here]().

```java
import java.util.Random;

Random random = new Random();
int randomItemFromArray = array[random.nextInt(array.length)];
```
_If you are going to be getting a random element multiple times, you want to make sure your random number generator is initialized only once._


|Connect 4||
|:--|:--|
Connect Four is a popular two-player connection game in which the players first choose a color and then take turns dropping one colored disc from the top into a seven-column, six-row vertically suspended grid. The pieces fall straight down, occupying the lowest available space within the column. The goal of the Connect Four game is to be the first player to form a horizontal, vertical, or diagonal line of four of one’s own discs.|![connect 4 game](https://images.nexusapp.co/assets/2f/7d/3b/313877873.jpg)

|Battleships||
|:--|:--|
![battleships](https://i.etsystatic.com/26706693/r/il/412c37/3387083205/il_1588xN.3387083205_kqe7.jpg)|This is harder. 2 players. Each player has a grid of their own ships at sea (hard code this to start with). You can take shots at the other players grid and you might hit a ship, you might miss and hit water, if all the squares a ship occupies are hit, then the ship sinks. Think about the way we made tic-tac-toe and adapt that command line game to become battle ships.

|21 Card Game||
|:-----------|:--|
In the 21 card game, most cards have their face value. A 10 is worth 10 points, and a 2 is worth 2 points, and so on. The king, queen, and jack are worth 10 points each. However, the ace is generally considered the most valuable card.<br/><br/>The ace is worth either 11 points or 1 point. It’s up to the player how they use this card, making it one of the most valuable cards in the game. That’s all you need to know about how the cards work.<ul><li>The player and the dealer receive two cards from a shuffled deck.</li><li>After the first two cards are dealt to dealer and player, the player is asked if they'd like another card (called 'hitting'), or if they are happy with the cards they have already (called 'staying'). The object is to make the sum of your card values as close to 21, without going over. If we make 21 exactly, we have blackjack, which can't be beat. If we go over 21, we 'bust' and we lose the round. The player is allowed to stop hitting at any point.</li><li>Once our hand is finished, the dealer tries to do the same. The dealer must keep hitting until they get to 17. If they get above 17 without busting, they can stay.</li><ul>|![adding up cards](https://en.bonus-poker.pro/data/uploads/how-to-play-21-card-game.png)

## Tennis

### How does tennis scoring work?
Tennis matches work in three phases: A game, a set and a match. 

A game is played until a player scores four points, of which a player can earn in a number of different ways (more on that below). 

A set is collection of games, played until a player wins six games (or more). 

A match is played to a best-of-three or five sets. Usually, championship matches are played to five sets. We can play for 3 sets.

|player|set 1|set 2|set 3|
|-----:|:---:|:---:|:---:|
|Kournikova|6|5|6|
|Bouchard|4|7|1|

Kournikova wins the match because she won 2 of 3 sets. Bouchard won only set 2, she beat Kournikova by 2 games.

You'd want to think about writing a program to help keep track of the scores.

```java
new Match(Player player1, Player player2);
```
Then some kind of input from the terminal?

```sh
Set 1, Game 1 who is the winner?
$player2
```
And you could display the score board in the terminal.

```sh
|player    |set 1|set 2|set 3|
|----------|-----|-----|-----|
|Kournikova|  6  |  5  |  6  |
|Bouchard  |  4  |  7  |  1  |
Kournikova wins game set and match
```

|10 pin bowling||
|:-------------|:---|
A game consists of ten frames, which start with a full rack of ten pins. In each frame, you have two deliveries of your ball, in which to knock down as many of the ten pins as you can.<br/><br/>If you knock down all the pins on your first ball, it is called a strike. The score doesn't get added on straight away because for a strike, you get the values of your next two balls as a bonus. For example, if you score a strike in the first frame, then an 7 and 1 in the second frame, you would score 18 (10+7+1) for the first frame, and 8 for the second frame, making a total of 26 after two frames.<br/><br/>If you knock down some of the pins on the first ball, and knocked down the remainder of the pins in the second ball, it is known as a spare. Again, the score doesn't get added on straight away because for a spare, you get the values of your next ball as a bonus. For example, you if score a spare in the first frame, say an 6 and a 4, then got an 8 and a 1 in the second frame, you would score 18 (6+4+8) for the first frame, and 9 for the second frame, making a total of 27 after two frames.<br/><br/>When it comes to the final frame, it is slightly different. In the final frame, you get bonus balls if you strike or spare, to a maximum of three deliveries. If you strike in the first delivery you have the opportunity to strike in the remaining two and have three deliveries in total. If you scored strikes in each of your final three deliveries, the score for the final frame would be 30 (10+10+10). If you spare the final frame, you get the third delivery as a bonus. So, a spare, 9 and 1, followed by a strike would equal 20 (9+1+10).|![Jesus](https://camo.githubusercontent.com/3ba42df7f6abfee37ffc96b5566a0490396f8c201ded3626fd2e71cc3cde6d3e/687474703a2f2f7777772e6a756c69656e736c6976652e636f6d2f696d616765732f6c6f742f363238342f36323834315f302e6a7067)
