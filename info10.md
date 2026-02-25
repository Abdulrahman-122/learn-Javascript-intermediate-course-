#  Concurrency + event loop in Js 
  - we can make JS have multi threads at the same time.
  - by using events
  see the  engine of Js
<img width="2400" height="1600" alt="image" src="https://github.com/user-attachments/assets/e9a81777-89f5-438a-8677-3204f0842118" />

you need to understand these things in order to understand how concurrency works in js
	- head
		- a memeory storage used to store variables, objects in unordered manner.
	- call stack
		- it's a place to store the frames of the objects being running like functions,variables.
		-when running a function contain a nested functions
			- the inner functions will run first then the one above it and so on untill we got to the log statments that render the output.
			when you run this function it's appear in the stack as you see;<img width="1200" height="800" alt="image" src="https://github.com/user-attachments/assets/6cca33a2-0101-41c4-b310-4a59f4bb20a9" />

function foo() {
 return function bar() {
   return function baz() {
     return 'I love CodeCademy'
   }
 }
}
console.log(foo()()());

		see picture 2 (stack frames with function)
				- as you see ;
					- we put global() at the bottom of the stack to initiate the environment of Js(lixecal,variable environment)
					- data stored in stack in FILO
-event queue;
				-it's a bunch of the messages that is taken from the API or whatever => these messages are stored in FIFO.
				-these messages wait to be back into the stack.
-event loop;
				-it's an event inside the engine that hold the data that sent to the stack from the event queue.
now let's see how it's working in the code;
console.log("This is the first line of code in app.js.");

function usingsetTimeout() {
    console.log("I'm going to be queued in the Event Loop.");
}
setTimeout(usingsetTimeout, 3000);

console.log("This is the last line of code in app.js.");

here;
1.the first console will log the message
2. setTimeout -> put a 3 seconds  as a time for the function to be run.
3.the third log will log the message after the first log then settimeour.
