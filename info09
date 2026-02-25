# what does hoisting means?
  -it's a way JS use to  move the variables,functions to the top of their scope.
    - Find variables,function names-> move them to their execution before executing code.
    - it's the postpone of handling the initialization untill the code is executed
    -  it's also happened inside nested functions .
    ex; 
    console.log(add(1,2)); 
// prints 3

function add(a,b) {
    return a + b
}

  from here; hoisting -> works by drag the method below to the top of the scope in order to execute the log operations 

ex; hoisting on variables (var;
console.log(myVarVariable);
var myVarVariable = 1;
but today as we use ES6; let,const is preferable
ex;
console.log(myLetVariable); 
// triggers a ReferenceError
let myLetVariable = 1;
ex;be sure when using an arrow function -> you should assign it to a variable name first then run it either below or above the executations.
thisWontRun(); 
let thisWontRun = a => console.log(a);

// thisWillRun() gets initialized after function call below
let thisWillRun = b => console.log(b);
// thisWillRun() gets hoisted at the function call
thisWillRun(); 

as you see JS will use hoisting in order to raise the function to the global scope to run it;
foo();
 
let foo = function() {
console.log("I love Codecademy!");
};

to sum up;
Hoisting => is the engine that JS uses to raise the variables to the the global scope in order to run the logs of variables,functions

