---
layout: post
title:  Creating Object Models in Ionic/Ng 2+
date:   2017-06-04 23:56:15 -0400
---

So if you're anything like me, someone who came from an object oriented programming background using Model-View-Controller pattern, you're probably used to blueprinting models (or objects in JS) via Classes.  For example, in Ruby, we can create a blueprint to a person with to ability to say their name like: 

```
class Person
  def initialize ( name, age)
    self.name = name,
    self.age = age
  end

  def say_name
    puts name
  end
	
	def change_name(new_name)
	  self.name = new_name
	end
	
end
```


This would be the equivalent in javascript:

```
function Person (name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.sayName = function() {
return this.name;

Person.protoype.changeName = function(newName){
  this.name = newName;
	}
	
};
```


Not much of a loss,  however, it does get exceedingly tedious when you want to add properties or methods to the class (prototype) object instead of the instance. So it was really exciting when ES6 included a similar class system.

Since my use of ES6, I've been using the class syntactical sugar religiously whether it be via libraries like Jquery or bigger framework such as Angular or Ionic.  Since my current focus is in the Ionic 2+ framework, I'll explain the straightforward process of implementing object models in your ionic/angular project.

To create an Object model in angular you'd first create the typescript file and define the class, being sure to include a constructor and any properties or functions you want your model to have.  The constructor is run each time you create an instance of the object so it's used to set up object properties such as a person's name.  You must also include an export statement before defining the class to make it accessible to other components of the application. A person data-model would look similar to this:

```
export class Person{
  constructor( public name: string, public age: integer ) {}

  sayName(){
    console.log(this.name)
  }
	
  changeName(name){
    this.name = name;
  }

}
```


After fleshing out your data model, you can import it into any component that you wish to use it in. You can do so by adding the following line at the top of your component:

import { Person } from '../path/to/person-model';

From there, you can easily create instances of the person model by calling new on the Person object and passing in parameter values:

`var toby = new Person('Toby', 20)`

All in all, though this is a basic example it may seem unnecessary as you can just create objects using hashes ( {} ). This is useful for simple needs, however, as projects get more and more complex so does your models, and I imagine a full page of hashes would be unsightly and unmanagable. So it is very useful to get into the habit of blueprinting your objects in a separate file.

