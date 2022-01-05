# Pre-requisites
For details of the software you need to have installed prior to undertaking the SWE Programme, please see [SWE training pre-requisites](/curriculum#pre-reqs)

## Learn you Java

This collection of 3 workshops is designed to get you started with Java before our 5 week bootcamp. You will need to read through and practice using the parts of the language introduced in these online resources:

### Programviz

#### Workshop 1 - Noughts and Crosses
* [Java Introduction](https://www.programiz.com/java-programming/hello-world)
* [Java Flow Control](https://www.programiz.com/java-programming/if-else-statement)
* [Java Arrays](https://www.programiz.com/java-programming/arrays)
#### Workshop 2 - Hotels
* [Java OOP(I)](https://www.programiz.com/java-programming/class-objects)
* [Java OOP(II)](https://www.programiz.com/java-programming/inheritance)
#### Workshop 3 - Supermarkets
* [Java List](https://www.programiz.com/java-programming/collections)
* [Java Queue](https://www.programiz.com/java-programming/queue)
* [Java Map](https://www.programiz.com/java-programming/map)

## Standards of Software Engineering

All the Bootcamp and Module content taught during the Software Engineering Programme is directly aligned with the [standards for the Level 4 Software Developer programme](https://www.instituteforapprenticeships.org/apprenticeship-standards/software-developer-v1-1) as designed by the Institute for Apprenticeships & Technical Education. Refer to this programme regularly to reflect on what you are learning and identify areas for development whilst on the job. The Knowledge, Skills and Behaviours for this standards are also summarised below: 

### Knowledge
* K1: all stages of the software development life-cycle (what each stage contains, including the inputs and outputs)
* K2: roles and responsibilities within the software development lifecycle (who is responsible for what)
* K3: the roles and responsibilities of the project life-cycle within your organisation, and your role
* K4: how best to communicate using the different communication methods and how to adapt appropriately to different audiences
* K5: the similarities and differences between different software development methodologies, such as agile and waterfall.
* K6: how teams work effectively to produce software and how to contribute appropriately
* K7: software design approaches and patterns, to identify reusable solutions to commonly occurring problems
* K8: organisational policies and procedures relating to the tasks being undertaken, and when to follow them. For example the storage and treatment of GDPR sensitive data.
* K9: algorithms, logic and data structures relevant to software development for example:- arrays- stacks- queues- linked lists- trees- graphs- hash tables- sorting algorithms- searching algorithms- critical sections and race conditions
* K10: principles and uses of relational and non-relational databases
* K11: software designs and functional or technical specifications
* K12: software testing frameworks and methodologies

### Skills
* S1: create logical and maintainable code
* S2: develop effective user interfaces
* S3: link code to data sets
* S4: test code and analyse results to correct errors found using unit testing
* S5: conduct a range of test types, such as Integration, System, User Acceptance, Non-Functional, Performance and Security testing.
* S6: identify and create test scenarios
* S7: apply structured techniques to problem solving, debug code and understand the structure of programmes in order to identify and resolve issues
* S8: create simple software designs to effectively communicate understanding of the program
* S9: create analysis artefacts, such as use cases and/or user stories
* S10: build, manage and deploy code into the relevant environment
* S11: apply an appropriate software development approach according to the relevant paradigm (for example object oriented, event driven or procedural)
* S12: follow software designs and functional or technical specifications
* S13: follow testing frameworks and methodologies
* S14: follow company, team or client approaches to continuous integration, version and source control
* S15: communicate software solutions and ideas to technical and non-technical stakeholders
* S16: apply algorithms, logic and data structures
* S17: interpret and implement a given design whist remaining compliant with security and maintainability requirements

### Behaviours
* B1: Works independently and takes responsibility. For example, has a disciplined and responsible approach to risk and stays motivated and committed when facing challenges
* B2: Applies logical thinking. For example, uses clear and valid reasoning when making decisions related to undertaking work instructions
* B3: Maintains a productive, professional and secure working environment
* B4: Works collaboratively with a wide range of people in different roles, internally and externally, with a positive attitude to inclusion & diversity
* B5: Acts with integrity with respect to ethical, legal and regulatory ensuring the protection of personal data, safety and security.
* B6: Shows initiative and takes responsibility for solving problems within their own remit, being resourceful when faced with a problem to solve.
* B7: Communicates effectively in a variety of situations to both a technical and non-technical audience.
* B8: Shows curiosity to the business context in which the solution will be used, displaying an inquisitive approach to solving the problem. This includes the curiosity to explore new opportunities, techniques and the tenacity to improve methods and maximise performance of the solution and creativity in their approach to solutions.
* B9: Committed to continued professional development.

# Frequently Asked Questions

## <a name="pre-reqs">What software do I need to install for the Bootcamp?
* [Node](https://nodejs.org/en/) (version which is recommended for most users)
* [VSCode](https://code.visualstudio.com/)
* [git](https://git-scm.com/)
* [SQLite3](https://www.sqlite.org/download.html)
* [DB Browser for SQLite3 ](https://sqlitebrowser.org/)
* Google Chrome
* You also need access to a GitHub repository

## <a name="createNewProject"></a> How do I create a new Node.js project for my lesson?
  1. Create a new directory to hold the lesson's work - do not use spaces or special characters in directory or filenames.. `cd` into it.
  1. Run `npm init` to create a new `package.json` file. Accept all defaults. The `package. json` file holds metadata relevant to the project such as the project's dependencies.
  1. Add any Node package dependencies you require using `npm install`. For the majority of Bootcamp assignments you will require:
     * `npm install jest`
  1. Modify your `package.json` to allow running of Jest tests and generation of test coverage reports:
  ```json
    "scripts": {
    "test": "jest",
    "test:report": "jest --coverage=true"
  }
  ```

## <a name="runJestTests"></a> How do I run my Jest tests?
To run all your tests use `npm run test` or use `npm run test -t` to run a single test.

## <a name="generateCoverage"></a> How do I create a Jest coverage report?
To create a Jest coverage report run `npm run test:report`.

You should see that Jest generates a 'coverage' report in your project folder under `/coverage/Icov-report/index.html`. Open this in your browser to view coverage by line, branch, function and statement.
