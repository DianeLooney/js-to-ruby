# Reading a New Codebase
Taken from a talk which I have lost the link to

## First steps
* Clone the repo
* Build the project
* Run the test suite
* Run the project

You can't expect to read every file. Instead you need to understand patterns.

## Methodologies
* grep
* where is this button
* follow input events
* what do the tests do?
* refactor
* read main
* runtime investigation
* add code
* read a class
* rubber duck

### grep / where is this button
Find a UI element, find the line that renders that element. What events does the button raise? Look for a string in the UI, where does the string come from?

### follow input events
When something is clicked, what happens?

### what do the tests do?
The tests likely touch on a tore of core funcitonality. Read the test. It will likely have just enough working to get by. It will also probably mock flows that you will work on in the future.

### refactoring
You are touching other people's code. Don't expect refactors to be pushed back. Treat it as an exercise to learn, not an exercise to improve. Take notes

### read main
Just read line by line down main. Follow the abstractions where you need to in order to understand the flow, skip them otherwise.

### runtime investigation
Event-based? Probably better to enable lots of logging.
Request handling? Probably okay to block a single thread for testing

### add code
Add logs, add tests, add assertions, add a microfeature, then trash it all.

### read a class
Same as read main, but read a class. Learn how it is used, and then its one less mystery.

### rubber duck
Self-evident
