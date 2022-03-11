# Package your code into a .jar file

## Jar

A Java Archive file or .jar file is like a .zip file that contains code you want to convenently share among projects. You have likely already been using other people's .jar files in your Java projects. Now its time to make your own.

### 1. Package

The first thing to do is think ahead a bit about name collisions. For example I have a class in my project called Menu, if my code is used in someone elses project, they might also have a class called Menu. So Java developers organise their code into packages and try to avoid name collisions by reversing their domain name and creating folders that corrispond to the domain name. i.e. `https://home.barclays.com` would translate into a project folder structure like the one below.

```sh
├── README.md
├── bin
│   └── com
│       └── barclays
│           └── App.class
├── lib
│   └── sqlite-jdbc-3.36.0.3.jar
└── src
    └── com
        └── barclays
            └── DB.java
            └── Restaurant.java
            └── Menu.java
```
Now we have that stucture we will need to add `package` declarations to the top of each class (DB, Restaurant and Menu) so Java can organise our code when it is compiled and be able to access the `.class` files when our project is finally in a .jar archive. Add the following line as the first line in the `DB.java`, `Restaurant.java` & `Menu.java` files.
```java
package com.barclays;
import // etc rest of your
```

### Manifest

Our .jar file will need a manifest that helps the JVM read the java classes out of our .jar file. There are different setting you can include in the `manifest.txt` file we just need the location of a `main` method. In my project the `DB.java` class has a `main` method.

```txt
Main-Class: com.barclays.DB

```
!IMPORTANT the last line of the file needs to be a blank empty line, so make sure your manifest file has a blank line at the end. Place this in the `./bin` folder as below.

```sh
├── README.md
├── bin
│   └── com
│       └── barclays
│           └── App.class
│   └── manifest.txt
├── lib
│   └── sqlite-jdbc-3.36.0.3.jar
└── src
    └── com
        └── barclays
            └── DB.java
            └── Restaurant.java
            └── Menu.java
```

### Compile

VSCode is auto compiling your code whenever you make a change. If you needed to compile by hand you would run a command like this.

```sh
javac -d ./bin ./src/**/*.java
```
`javac` is the java compiler command.
`-d` is the 'directory' flag and is followed by the location where the compiled java code will be written.
`./src/**/*.java` this is the location of the source files the code you have been writing the `*` mean look in all folders and find all the files with the `.java` extention.

### Jar

Now we are set up to actually create our .jar file and share our code with other developers. I find this easier to run from within the `./bin` folder so `cd` into the `./bin` folder.

```sh
jar -cvmf manifest.txt ../restaurants.jar ./**/*.class
```
`jar` this is the Java Archive program.
`-c` this means 'Create the archive`
`-v` this is the 'verbose' flag and means you get printed output on standard output telling you what is going on
`-m` tells the jar program to include the manifest information from the given manifest file
`-f` this means what follows is the name and location of where to create the archive file

Now you have a .jar file you can place it into the lib folder of other projects and import the classes. We have not added sqlite into our .jar file. Best to keep those peer dependencies out of your code. The way jUnit4 uses Hamcrest as a peer dependency. When you want to use your Restaurant jar file - include sqlite in the project also.
