---
layout: post
title:  "Navigation in Ionic2"
date:   2017-06-12 02:29:19 +0000
---


In most programming languages navigation between pages is handled via routing with URLs . In the Ionic 2 framework, however, navigation is approached differently. It works similar to a stack (think array) in that you push new pages onto the stack to go to that page and you also pop the top page off to go back to a previous page.

To start off with navigation in ionic 2, you'd first have to import the NavController, often this is imported by default in your Ionic 2 application. 

` import { NavController } from 'ionic-angular'; `

Additionally, you have to make a reference to the NavController the constructor of your page so that it can be used.

```
export class FirstPage {
  constructor(public navCtrl: NavController){}
}
```

After this, navigation is accomplished by simply calling a push method on the navigation controller and passing the page you want to navigate to as an argument. Also, note that to navigate to the second page you will need to import that page at the top of the file. 

` this.navCtrl.push(SecondPage); `

 Going back to a previous page in Ionic 2 is brainless. This is because when you push a page via the navigation controller, a 'back' button is automatically added to the navigation bar. When you click that 'back' button, the navigation controller automatically 'pop' the current page out of the stack, taking you back to the previous page. On rare occasions, you may need to manually 'pop' a page off the stack. This is achieved by simply calling the 'pop' method on the navigation controller:
 
` this.navCtrl.pop(); `

This sums up the basics of navigating in the Ionic2 framework
