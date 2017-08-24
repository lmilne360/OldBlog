---
layout: post
title:  "Angular Reactive Forms"
date:   2017-08-20 23:56:03 -0400
---


Angular provides two ways to work with forms: template-driven forms and reactive forms, the latter also sometimes called model-driven forms. With template-driven forms, the default way to work with forms in Angular, template directives are used to build an internal representation of the form. With reactive forms, by contrast, you build your own representation of a form in the component class.

### Setting Up the form

Before setting up the form, we must first import the forms and reactive forms module to our app module so it can be accessed by our components.

`import { FormsModule, ReactiveFormsModule } from '@angular/forms';`

```
@NgModule({
  // Other properties removed to keep this short
  imports: [
    BrowserModule,
    FormsModule,
    HttpModule,
    ReactiveFormsModule  // Add this!
  ],
})
```
After this, we can either go to our components template and begin defining the HTML for our form, or we can go into the component and build the code for the forms. For this purpose, we'll start at the component level first.

