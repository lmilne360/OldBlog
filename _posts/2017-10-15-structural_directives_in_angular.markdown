---
layout: post
title:      "Structural Directives in Angular"
date:       2017-10-16 03:32:03 +0000
permalink:  structural_directives_in_angular
---


One thing we rely on heavily when coding in Angular is components. As the name implies, a component in angular is an isolated piece of code that contributes to the larger whole. An example of a component would be an about me page, which itself contains its own properties and style but is part of the whole site. Components help to keep the codebase organized and modular which makes the development process more streamlined.  Components, in turn, are a specific type of directives. Directives in angular come primarily in three flavors; Components, Structural Directives, and Attribute directives. Components are simply directives with their own view templates. Structural directives are directives that manipulate the layout of the DOM by adding and removes elements. Attribute directives, on the other hand, change the appearance or behavior of a DOM element.  In this post, we'll explore structural directives by creating out own ngIf directive.

To get started, we must for create our simple ngIf directive. This can be done with the angular cli with the command `ng generate directive myNgIf`. You can also create it manually by creating a file following the standard angular naming convention of `feature.type.ts`. In our case, it would be `myngif.directive.ts`. Once the directive is created you should have a standard directive like:
```
import { Directive } from '@angular/core';

@Directive({
  selector: '[myNgIf]'
})
export class MyNgIfDirective {

  constructor() { }

}
```

In order to manipulate the DOM, we'd have to import  `TemplateRef` and ViewContainerRef from angular core as well as the Input decorator to pass values to our directive. `TemplateRef`, as the name suggests, is a reference to the template our directive is attached to. The `ViewContainerRef` is basically a reference to a container within our template in which we will place our content.  Our import statement should look like: 
`import { Directive, Input, TemplateRef, ViewContainerRef } from '@angular/core';
`

Within our constructor, we'd want to inject our `templateRef` and `ViewContainerRef ` so we can use it within our code.

`constructor( private vContainer: ViewcontainerRef, private tRef: TemplateRef) {}`

Lastly, we'd use our input decorator to create a setter based on a passed condition to create or clear the dom template. If that condition is true, we will use our viewContainerRef to create a view based on the element(template) the directive is attached to. If the condition is false, however, we will clear the view of the attached element. It would look like:
```
@Input() set myNgIf(condition: boolean) {
    if (condition) {
      this.viewContainer.createEmbeddedView(this.templateRef);
    } else {
      this.viewContainer.clear();
    }
  }
```

Now we can use our directives like `<div *myNgIf=”condition”>Condition is true</div>`
which will then only display the text within the `div` element if the passed condition is true.
