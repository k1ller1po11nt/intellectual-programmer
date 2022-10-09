# intellectual-programmer
Learning programming to be a software enginner for some time and an entrepreneur in the future
common arrays in javascript

var arr = ["a", "b", "c"];
arr.push("d");
console.log(arr);
console.log(arr.pop());
console.log(arr);
var arr2 = ["g", "q"];
console.log(arr.concat(arr2));
console.log(arr2);
console.log(arr);
console.log(arr.join("!"));
console.log(arr.reverse());
console.log(arr);
console.log(arr.shift());
console.log(arr);
console.log(arr.unshift("p"));
console.log(arr);
console.log(arr.slice(1, 2));
console.log(arr.slice(1, 3));
arr.push("i");
arr.push("f");
arr.sort();
console.log(arr);
console.log(arr.splice(2, 2, "Coding Fanboy"));
console.log(arr);

null vs undefined in javascript

var test
console.log(test);
test = null
console.log(test);
console.log(typeof null);
console.log(typeof undefined);
console.log(null === undefined);
console.log(null == undefined);
console.log(null === null);
console.log(null == null);
console.log(!null);
console.log(!!null);
console.log(1 + null);
console.log(1 + undefined);

20 string methods in javascript 

var stringOne = "FreeCodeCamp is the best place to learn"
var stringTwo = "frontend and backend developemnt"
console.log(stringOne.charAt(1));
console.log(stringOne.charCodeAt(1));
console.log(stringOne.concat(stringTwo));
console.log(stringOne.endsWith("learn"));
console.log(stringOne.endsWith("to"));
console.log(String.fromCharCode("114"));
console.log(stringTwo.includes("end"));
console.log(stringTwo.indexOf("end"));
console.log(stringTwo.lastIndexOf("end"));
console.log(stringTwo.match(/end/g));
console.log(stringOne.repeat(3));
console.log(stringTwo.replace(/end/g, "End"));
console.log(stringTwo.search("end"));
console.log(stringTwo.slice(2, 4));
console.log(stringOne.split(" "));
console.log(stringOne.startsWith("Free"));
console.log(stringTwo.substr(2, 4));
console.log(stringTwo.substring(2, 4));
console.log(stringOne.toLowerCase());
console.log(stringOne.toUpperCase());
var stringThree = "     Subscribe now!        "
console.log(stringThree.trim());

proxies in javascript 

var handler = {
  get (target, key) {
    return key in target ? target[key] : 7;
  }
};
var p = new Proxy({}, handler);
p.a = 1;
p.b = undefined;
console.log(p.a, p.b);
console.log('c' in p, p.c);
let validator = {
  set: function(obj, prop, value) {
    if (prop === 'age') {
      if (typeof value !== 'number' || Number.isNaN(value)) {
        console.log('Age must be a number')
      }
      if (value < 0) {
        console.log('Age must be positive number')
      }
    }
    obj[prop] = value;
    return true;
  }
};
let person = new Proxy({}, validator);
person.age = 'young';
console.log(person.age)
person.age = -30;
person.age = 12;
console.log(person.age)

observer design pattern in javascript

var Subject = function() {
 let observers = [];
 return {
  subscribeObserver: function(observer) {
   observers.push(observer);
  },
  unsubscribeObserver: function(observer) {
   var index = observers.indexOf(observer);
   if(index > -1) {
    observers.splice(index, 1);
   }
  },
  notifyObserver: function(observer) {
   var index = observers.indexOf(observer);
   if(index > -1) {
    observers[index].notify(index);
   }
  },
  notifyAllObservers: function() {
   for(var i = 0; i < observers.length; i++){
    observers[i].notify(i);
   };
  }
 };
};
var Observer = function(number) {
 return {
  notify: function() {
   console.log("Observer " + number + " is notified!");
  }
 }
}
var subject = new Subject();
var observer1 = new Observer(1);
var observer2 = new Observer(2);
var observer3 = new Observer(3);
var observer4 = new Observer(4);
subject.subscribeObserver(observer1);
subject.subscribeObserver(observer2);
subject.subscribeObserver(observer3);
subject.subscribeObserver(observer4);
subject.notifyObserver(observer2);
subject.unsubscribeObserver(observer2);
subject.notifyAllObservers();

objects in javascript

var myCar = new Object();
myCar.make = "Bugatti";
myCar.model = "Chiron Pur Sport";
myCar.color = "Copper Orange";
console.log(myCar.make);
console.log(myCar.model);
console.log(myCar.color);
myCar["year"] = 2022;
console.log(myCar["year"]);
myCar["Do I like it?"] = "I love my car!";
console.log(myCar["Do I like it?"]);
function showProps(obj, objName) {
 var result = "";
 for (var i in obj) {
  if (obj.hasOwnProperty(i)) {
   result += objName + "." + i + " = " + obj[i] + "\n";
  }
 }
 return result;
}
console.log(showProps(myCar, "myCar"));
var myHonda = {color: "red,", wheels: 4, engine: {cylinders: 4, size: 2.2}};
function Car(make, model, year) {
 this.make = make;
 this.model = model;
 this.year = year;
}
var mycar = new Car("Chevy", "Malibu", 1993);
var anothercar = new Car("Mazda", "Miata", 1990);
console.log(mycar.model);
mycar.color = "black";
console.log(mycar.color);
var Animal = {
 type: "Invertebrates",
 displayType: function() {
  console.log(this.type);
 }
}
var animal1 = Object.create(Animal);
animal1.displayType();
var fish = Object.create(Animal);
fish.type = "Fishes";
fish.displayType();

switch statements in javascript

let day;
switch (new Date().getDay()) {
 case 0:
  day = "Sunday";
  break;
  case 1:
   day = "Monday";
   break;
   case 2:
    day = "Tuesday";
    break;
    case 3:
     day = "Wednesday";
     break;
     case 4:
      day = "Thursday";
      break;
      case 5:
       day = "Friday";
       break;
       case 6:
        day = "Saturday";
        break;
}
console.log(day);
var Animal = 'Dinosaur';
switch (Animal) {
 case 'Cow':
  case 'Giraffe':
   case 'Dog':
    case 'Pig':
     console.log('This animal will go on Noah\'s Ark.');
     break;
     case 'Spoon':
      console.log('A spoon is not an animal!');
      break;
      case 'Dinosaur':
       default:
        console.log('This animal will not be on the Ark');
}
