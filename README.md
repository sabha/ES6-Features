# ES6 Features
### let
```sh
/*-----------------------------------------------------------------------------
  ------------      let keyword & Diff btwn LET vs VAR              -----------
  -----------------------------------------------------------------------------*/
//Using var 
var A = "Global";
if(true){
	var A = "Block";
	console.log(A); //Block
}
console.log(A); //Block 

//Using Let
let B = "Global";
if(true){
	let B = "Block";
	console.log(B); //Block
}
console.log(B); //Global

//"let" take care of block level scope apart from Function & Global Scope in Javascript 
```
### const
```sh
/*-----------------------------------------------------------------------------
-------------                       const keyword                 -------------
-------------------------------------------------------------------------------*/
const PI 	 = 3.14;
console.log(PI);
// PI = "Trying to Change PI"; //Uncaught TypeError: Assignment to constant variable.
// var PI 	= "4.5"; //Uncaught SyntaxError: Identifier 'PI' has already been declared
// const PI = "4.5"; //Uncaught SyntaxError: Identifier 'PI' has already been declared

```
### Arrow SYNTAX
```sh
/*-----------------------------------------------------------------------------
------------                          Arrow SYNTAX                  -----------
-------------------------------------------------------------------------------*/

// 1
//This way of defining a function is equalant to below Arrow Syntax
var func1 = function(a){
	console.log(a)
}
func1(78);

//Arrow Syntax
var func3 = (a)=>console.log(a);
func3(78);
var func2 = (a)=>{console.log(a)}
func2(78);


// 2
var array = [2,45,87,22,90];
//Usual way
var arrayofEvens = array.filter(function(item){return item%2 == 0;})
console.log(arrayofEvens); //[2, 22, 90]
//Arrow Syntax
var arrayofEvens = array.filter((item) => {return item%2 == 0;})
console.log(arrayofEvens); //[2, 22, 90]


// 3
//IFFE
(function(array){ console.log(array); })([1,2,3]);
//arrow systax
((array) => console.log(array) )([1,2,3]);
((array) => {console.log(array)} )([1,2,3]);
```
### Class
```sh
/*-----------------------------------------------------------------------------
------------                          ES6                              --------
------------           class , extends & super Keywords                --------
-------------------------------------------------------------------------------*/
//Class definition 
class Person {
	constructor(name){
 		this.name = name;
	} 
	sayName(){
		console.log("My Name is "+this.name+" ES6 . .");
	}
}

var person1 = new Person("Arun");
person1.sayName();

//Inheritance - still internally it is PROTOTYPAL Inheritance
class Employee extends Person{
	constructor(){
		super();
	}
}

var employee1 = new Employee("Krishna");
employee1.sayName();
```
### ES5 Class
```sh
/*-----------------------------------------------------------------------------
------------                          ES5                              --------
------------           class , extends & super Keywords                --------
-------------------------------------------------------------------------------*/
function PersonClass(name){
	this.name = name;
}
PersonClass.prototype.sayName = function(){
	console.log("My Name is "+this.name+" ES5 . .");
}

var person = new PersonClass("Raj");
person.sayName();

//EMployeeClass extends PersonClass
function EmployeeClass(name , designation){
	//Calling Parent COnstructor === super()
	PersonClass.call(this , name);
	this.designation = designation;
}
//EmployeeClass.prototype = new PersonClass();
// Inherit from the parent class
EmployeeClass.prototype = Object.create(PersonClass.prototype);
EmployeeClass.prototype.constructor = PersonClass;

var employee = new EmployeeClass("Vijay","C.E.O");
employee.sayName();
```
### new Keyword

"new" keyword in this statement 'var person2 = new Person("Anandh");' does 3 things in Javascript
- It allocates memory for the instance person2.
- It then calls the method Person.call(person2,"Arun");
- assign person2.__proto__ = Person.prototype
