# Hotels
Object orientated programming (OOP) is a style of programming. The Java language has been created to capture and express this style of programming. We need to learn about OOP in order to read and write Java code. There are a set of core concepts and values that you need to know about to start writing Java code like a pro. The main idea behind OOP is that our computer program should model how things are and how things relate to each other in the real world. For example today we are going to build a hotel. Our hotel will have rooms and guests and a location, just like hotels do in the real world.

!(https://www.youtube.com/embed/UrGq7qSvtgI)

## new Hotel
We are going to make a Hotel in Java. Our hotel can start off with a name. In a file called `Hotel.java` add the following basic class.
```java
public class Hotel {
    public String name;

    public Hotel(String name) {
        this.name = name;
    }
}
```
In the code above we are declaring a public class that means other parts of our program can use this class. The class has a property called `name` that is a string. I have added a `constructor` function to my class. The `public Hotel` method will be called when I create a new instance of this class like this.
```java
Hotel grand = new Hotel("The Grand");
```
When you see the `new` keyword you know that you are creating a new instance of a Hotel, we are passing the name of the hotel to the constructor function, so when the hotel is constructed (or instantiated) it can be assigned a name. How will you be able to access the name of the hotel?
```java
grand.name // "The Grand"
```
This object in our code is going to represent our real world hotel. Our hotel has a name, it will also need rooms for our guests.

## OOP Design
When you are thinking about the design of an object orientated program there are some principles of good practice that you should know about.

1. Single responsibility
1. Open for extension closed for modification
1. Build complexity with simplicity
1. Small simple interfaces
1. Backwards compatibility

This is a simplified version of the [SOLID principles](https://www.digitalocean.com/community/conceptual_articles/s-o-l-i-d-the-first-five-principles-of-object-oriented-design).

Our Hotel's single responsibility is to have rooms available. The Room's single responsibility is to hold upto 2 guests. The Guests responsibility is to have a surname. So to practice this we should make a new class from which we can create the rooms for our hotel.

## new Room
A room will have a room number. A room might be a Single, Twin or Double room, those different rooms will have different rates, and we'll want to check and see if the room is available or not. Finally we want to be able to place guests into the room. In a new file called `Room.java` can you create the following class definition.
```java
public class Room {
    public int number;
    public String type = "Double";
    
    public Room(int number) {
        this.number = number;
    }
}
```
Very similar to our `Hotel` class. Can you also create a `Guest.java` with a `Guest` class that we can instantiate with a `String` surname.

We can now make 3 types of object in a program. Finally in a `Main.java` class we can start to create these objects in the OOP style!
```java
public class Main {
    public static void main(String[] flags) {
        Hotel grand = new Hotel("The Grand");
        Guest simmonds = new Guest("Simmonds");
        System.out.println(grand.name);
    }
}
```

## Relating objects
At present our hotel has only a name. We will want to create a hotel and say how many rooms it has. When we instantiate a new hotel it would be good if we could also passing the number of rooms that we like that hotel to have. It will be an integer. Can you update your code when you create a new hotel to also accept an integer that will represent the number of rooms we want a hotel to have.

Now if you think about your data structures, the best data structure to hold a list of rooms it's going to be an array, so we can use the number of rooms that the hotel needs to create an empty array and then we will iterate over it in a for loop and fill that array with rooms.
```java
public class Hotel {
    public String name
    private Room[] rooms;

    public Hotel(String name, int numOfRooms) {
        this.name = name;
        this.rooms = new Room[numOfRooms];
        for(int i = 0; i < numOfRooms; i++) {
            this.rooms[i] = new Room(i + 1); // I'm using the index to be the room number
        }
    }
}
```

## Debugging

We should have a Hotel with rooms, but how can we be sure? At present our code just runs and then exits. To examine more closely what the state of our program is as it runs, and verify that values and variables are being set correctly we need to learn to debug our code.

|Debugging|Admiral Grace Hopper|
|:--------|:------------------:|
_This is an odd term. Back in the early days of computing, computers were large constructions with physical valves and relays - they were bright warm and dusty things - very attractive to moths. The Mark II which was being built and run in Harvard University showed some unusual failing and faults. It got the engineering team curious as to what the problem was, upon closer investigation [Admiral Grace Hopper](https://en.wikipedia.org/wiki/Grace_Hopper) discovered a dead moth was blocking one of the relays. They went looking for other bugs and told the team leads they needed to "debug" the system!_|![Admiral Grace Hopper](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ad/Commodore_Grace_M._Hopper%2C_USN_%28covered%29.jpg/440px-Commodore_Grace_M._Hopper%2C_USN_%28covered%29.jpg)


Let's use the debugger to inspect the objects in our code and verify that we do have a hotel with rooms in it.

First create a breakpoint on the last line of the main method in your `Main.java` file after you declare and assign your Hotel. You can add a `System.out.println(hotel.name)` and add the breakpoint to that line.

_you might need to goto: vscode->settings->features->debug->__Allow Breakpoints Everywhere___

![adding a breakpoint](https://user-images.githubusercontent.com/4499581/148397894-e65070c3-73b0-4ede-a6a2-b6eb5ad3cad4.png)

Can you see the red dot that I added to the left of the line numbers? That is a breakpoint. When we run our program in debug mode the program will stop there are we will be able to inspect our hotel. Try clicking on 'debug' instead of 'run' to start a debugging session.

![annotated debugging screen](https://user-images.githubusercontent.com/4499581/148399443-a471f985-7560-4284-a50a-a09101af0bf7.jpg)

Take a moment to orientate yourself and inspect your hotel object. Our code is paused at the breakpoint, so what comes after the breakpoint has not yet been executed. While we are paused here we can look around in our program, inspect the local variables, and even interact with our code by writing expressions in the 'DEBUG CONSOLE' tab. Pretty amazing, very useful...

You can also see you have a set of controls, like pause/play, step over, step into etc. These control the execution of your program, so you can step over a function, or into it and move through your program step by step, following the path of execution.

## Interfaces and interactions

We have a hotel with rooms for guests. Now we want to be able to place a guest in a room. To do this our objects will interact. Usually when a guest arrives at the hotel they check-in and the hotel assign them their room. So it makes sense for the hotel to take responsibility for placing a guest in a room. At present our hotel has no way for us to check-in a guest. What we need to do is build out the Hotel's interface by adding a method.
```java
public class Hotel {
    public String name;
    private Room[] rooms;

    public Hotel(String name, int numOfRooms) {
        this.name = name;
        this.rooms = new Room[numOfRooms];
        for(int i = 0; i < numOfRooms; i++) {
            this.rooms[i] = new Room();
        }
    }

    public int checkIn(Guest guest) {
        return 0;
    }
}
```
Now our hotel has a name, rooms, and a method that we can call with a guest. Our `checkIn` method needs to do the work of adding the guest into the first empty room it can find. Can you write this method? Think about how you might do that and the code that you might _want_ to write. For example as I iterate over all the rooms taking one room at a time I will want to ask each room,

> Are you empty?

That might look like:
```java
for(Room room : this.rooms) {
    if (room.isEmpty()) {
        //... more code in here
    }
}
```
This is another interface, but this time on the `Room` class. Here we are in the essential point of this workshop which is writing code were classes interact with one another. You will need to update your `Room` class as well at the `Hotel` class to complete the task of adding a guest to a room.

📌 Remember the SOLID principles mentioned earlier? _Small simple interfaces_ in the _SOLID_ principles means **Interface segregation principle** it is the _I_ in SOLID and states.

> A client should never be forced to implement an interface that it doesn’t use, or clients shouldn’t be forced to depend on methods they do not use.

This principles encourages us to keep the public interface of a class as small and concise as possible. We need these interfaces of `checkIn` and `isEmpty` so let's update our classes to have these interfaces.

```java
public class Room {
    public String number = "00";
    private Guest[] beds = {null, null};

    public Room() {
        this.number = this.toString().substring(5,7);
    }
    public boolean isEmpty () {
        // need logic to check room is empty
    }
}
```
Once we've found an empty room, we will need an interface to add the guest, and remove them when they check-out. 
