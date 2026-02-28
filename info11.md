#Memory management in JS;
  - JS do allocate , processes(delete,update,...) instead of writing syntax for that it's automatically handle all of these unlike c++,c.
  - Types of memory that are used inside JS??
    - The heap
    - the stack
   
    - What is the stack??
      - it's a location into os that uses to store static code like variables values(string,numbers,boolean)...
      - it doesn't store any dynamic code like ; arrays,functions because their values are changed as we use stack to store fixed sizes instead of the arrays.. stack knows it through a reference
      - this reference refer to them while these dynamic values are stored into the Heap .
     
    - What is the Heap?
      - used to store dynamic memory allocations at run time => like arrays,objects.
      - these dynamic things that stored into the heap are accessed through the stack using a references to it.
      - ex const cat = {
    name: "Jupiter"
}

const pets = ["Jupiter", "Moshi", "Hercules"]
here ; cat is stored in the  head  while perioriy name is stored in the stack , pets as variable is stored into the stack but it's value are stored into the heap.

what is the memory life cycle?
  - Allocated memory; values in memroy are declared
  - memory in use -> values in memroy are read and rewritten.
  - Releasing memory -> values are no longer in use.

# How memory allocation is done in Js?
  - first-> if the you define a class like this;
 class Instrument {
2    constructor(name, type, instrumentOrigin) {
3        this.name = name;
4        this.type = type;
5        this.instrumentOrigin = instrumentOrigin;
6    }
7}
8
9let mbira = new Instrument("Mbira", "Lamellophone", "Zimbabwe");
instrument constructor at first stored in stack as frame
then when the definition of class is done
the constructor + class is stored into heap + any object that made by the class is stored into the heap.

# how calling functions is done in memory???
  - when you call a function it's stored into heap but it's referenc to the stack equal to a frame
  - if the function frame it's block of code contain another internal functions => so it will make another frame on the top of it this is how function is executed inside stack.
  - once the function is executed -> the stack will deallocated the area inside it that were be using for the function .

ex;
let str = "Hi";
let str2 = str;
  two strings are stored inside the stack as their values are fixed data.
  even if they refer to the same things but they are different in the location .
ex;
let aaliyah = {
    name: "Aaliyah"
}

function nameObjectModification(obj, name) {
    obj.name = name;
    return obj;
}

let sarah = nameObjectModification(aaliyah, "Sarah");

console.log(aaliyah); // { name: 'Sarah' }
console.log(sarah); // { name: 'Sarah' }

the aaliyah object is stored inside the heap
also the function  is stored into heap
when sarah variable is executed it will reference the function inside the stack and pass to it the string.
now the referece will change the value of the name inside heap to that  new string.

# How releasing  memory is done in  JS?
  - we have two algorithms to release a memory;
  1.  Reference counting
      - which means => it's a count for the variables and function definition once that count get to 0 -> the value that represent it is garbage collected.
      - ex;
 let obj = new Object(); // reference count of one
let obj2 = obj; // reference count of two
obj2 = "string"; // obj has a reference count of one again
  - as you noticed -> you assign an object to the variable called obj->it's reference count is 1
  - then you assign the obje to a variable(reference) indicate to that object => reference count =2
  - obj2 -> you change the reference obj2 from obj to another string => reference count =1 again

- ex;
let monument = {
   name: "Eiffel Tower"
};
monument = "Golden Gate Bridge";
monument object has reference count =1
then reassigned it by another string so it's reference count still 1 and the old value is now regarded as garbage => the system will remove it.
2. mark and sweep algorithm
  how it's working:
    - mark => is a boolean that traverse over the reachable variables of the program but that one unreachable will goes to the garbage collection
# What happens when your process runs out of memory?
