---
layout: post
title:  "Angular Lifecycle hooks "
date:   2017-09-10 23:46:20 -0400
---


Directive and component instances have a lifecycle as Angular creates, updates, and destroys them. Developers can tap into key moments in that lifecycle by implementing one or more of the lifecycle hook interfaces in the Angular core library.

Each interface has a single hook method whose name is the interface name prefixed with ng. For example, the OnInit interface has a hook method named ngOnInit() that Angular calls shortly after creating the component.

Hooks:

`ngOnChanges()	`
Respond when Angular (re)sets data-bound input properties. The method receives a SimpleChanges object of current and previous property values.

Called before ngOnInit() and whenever one or more data-bound input properties change.

`ngOnInit()`	
Initialize the directive/component after Angular first displays the data-bound properties and sets the directive/component's input properties.

Called once, after the first ngOnChanges().

`ngDoCheck()	`
Detect and act upon changes that Angular can't or won't detect on its own.

Called during every change detection run, immediately after ngOnChanges() and ngOnInit().

`ngAfterContentInit()`	
Respond after Angular projects external content into the component's view.

Called once after the first ngDoCheck().

A component-only hook.

`ngAfterContentChecked()	`
Respond after Angular checks the content projected into the component.

Called after the ngAfterContentInit() and every subsequent ngDoCheck().

A component-only hook.

`ngAfterViewInit()	`
Respond after Angular initializes the component's views and child views.

Called once after the first ngAfterContentChecked().

A component-only hook.

`ngAfterViewChecked()`	
Respond after Angular checks the component's views and child views.

Called after the ngAfterViewInit and every subsequent ngAfterContentChecked().

A component-only hook.

`ngOnDestroy	`
Cleanup just before Angular destroys the directive/component. Unsubscribe Observables and detach event handlers to avoid memory leaks.

Called just before Angular destroys the directive/component.
