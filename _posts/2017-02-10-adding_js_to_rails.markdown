---
layout: post
title:  "Adding JS to Rails"
date:   2017-02-10 01:23:41 +0000
---


So, after completing my rails project, which was rather fun, I was tasked with adding some javascript to really improve the user experience. Considering that I was already a good way through the javascript course whilst doing the rails project, the material was fresh and allowed me to hastily work on this aspect.

My initial thought was about what parts did I want to convert to javascript. The structure of my project made it quite a task since the layout was heavily dependent on partials writing to the pages. In time, I concluded that my comments section was a good place to start. To 'scriptify' my comments, I used javascipt to add an submit event on the comment form and prevent the form from submitting the normal way. I then used jquery to serialize the data in the form, and submited a post request to the route the form initially was going to send the data to. it ended up looking like this:
```
  $(document).on("submit", '#new_comment', function(e) {
        e.preventDefault();
        var values = $(this).serialize();
        var posting = $.post("/comments.js", values);
    });
```
Fom there, I set the comment controller to respond to `js` formatted data by sending the data to my javascript create page. This page in turn rendered my original comment partial to style the data and then appended(added) this data to the comments section of the page.
```
$('#comments').append("<%= j render @comment %>");
```

After I finished up comments form. I decided that it would by smooth to be able to hide the comments. this would be usefull if the lists of comments became too long. To do this I added a click function to the comments section, and upon clicking the word 'Comments', all comments display would be set to none thus is doesn't take up space on the page. To make this a bit more sleek, i added a toggle function that slowly fades the comments before changing the display.  My click event ended up following this format:
```
function toggleComments() {
  $(document).on("click",'#comments-toggle', function(e){
    e.preventDefault();
    $("#comments").fadeToggle("slow");
  });
}
```

Finalizing the comments section, i decided to change my focus to the index page Specifically, the link listings.  Inspired by the heart at the bottom of each `Learn.co` page, I decided to implement a favorite system in addition to my already implemented ability to like a posting. This process was rather difficult, as it involved both Jquery and CSS. To start it off, I added a 'favorite' button to each posting. I then used jquery to add a click event to that button. In this event, jquery would then add the class `fave` to the posting. Realizing that I wanted the ability to remove an item from my favorites, i made the class addition a toggle function, so that when I click the button again `fave` would be removed from the class;

`item.toggleClass('fave')`

Afterwards, I then had to find a way to show users their favorites. For this I used a css selector to target all divs with the class fave and then add a red heart  at the end of it. This way, if a posting has the class `fave` it will show a red heart. My css looked like:

`div.fave:after {
  content: ' \2665';
  color: red;
}`
 
 Lastly, I wanted to implement a way for users to filter the index page and only show items that they've favored. To do so, I added a button to my header that, once clicked, uses jquery to target every posting that does not contain the class `fave` and toggle their display to none. This allows only the favorite items to be shown on the index page, the exact effect I was going for. 
 
 `$('.fave-btn').click(function(event){
          event.preventDefault();
          $('.link').filter(':not(.fave)').toggle();
        })`
	
	These effects made my application a lot more reponsive, and using jquery allowed me to do it without ever having to refresh the page. Overall it was a fun process and I'm hoping to add even more functionality in time.
