---
layout: post
title:  Linked Lists in Ruby
date:   2017-05-07 23:51:38 -0400
---


In a recent practice question, I was met with the task of creating a linked list in ruby.  Being that I have encountered similar data structure problems before, I thought it'd be proactive to talk about linked lists for a bit.  The biggest challenge I've encountered pertaining to linked list in ruby is that most of the resources available online are writing code in C, as the data-structure has more necessity in languages with manual memory allocation. Due to this issue, I take it upon myself to shed some light on linked lists for my fellow ruby programmers.

Firstly, a linked list is a data structure that represents a sequence. It is a collection of nodes that each contain data as well as a pointer to the next element in the list.The reason linked lists are such a popular data structure is due to memory management. It allows elements (nodes) to be added at the beginning and end of the list without having to reallocate or reorganize the entire data structure.

In ruby arrays are mostly used in place of linked list. The downside of using an array is that whenever an element of the array is deleted, excluding the last element, every succeeding element as to be reindexed. The same is true for inserting an element at a specific index. The advantage, however, is that accessing specific elements in an array is relatively easy in comparison to a linked list. For example, to access a specific element in a ruby array, one would just have to call that index, whereas in a linked list you would be required to scan every element until you find that specific one.

Despite the disadvantages (and advantages),  Linked Lists are a data structure you are sure to encounter, especially during technical interviews. For that reason, it is important to explore the implementation of a linked list.

In ruby, you'd first want to define a node class, which is similar to the elements that would be placed in an array. In that class, you would want an attribute for the data, as well as a pointer which will lead to the succeeding element. A simple node in ruby would look like this:

```
class Node
  attr_reader :data, :next_node
  
  def initialize(data, next_node = nil)
    @data = data
    @next_node = next_node
  end

end
```

After the creation of a node, you'd then have to create the actual linked list. The list class should also contain a way to add elements to the end of the list (append) as well as a way to add data to the head of the list (prepend). Additionally, you'd perhaps want a way to display the data in the list. A simple linked list would to similar to this:

```
class LinkedList

    def initialize
        @head = nil
    end
    
    def empty?
        @head == nil 
    end
    
    def tail
        last_node.data
    end
    
    def prepend(value)
      if empty?
       @head = Node.new(value, nil)
      else
          new_node = Node.new(value, @head)
          @head = new_node
      end
    end
        

    def append(value)
        if empty?
            @head = Node.new(value, nil)
        else
           last_node.next_node = Node.new(value, nil)
        end
    end

        
    def last_node
     current_node = @head
      while current_node.next_node
        current_node = current_node.next_node
      end
     current_node
    end
    
    def content
        current_node = @head
        while current_node !=nil
            print "#{current_node.data}->"
            current_node = current_node.next_node
        end
    end
 
end
```

It may seem like there's a lot going on in the Linked List class, but it's rather straightforward. First I initialized the class with a head variable, which would represent the first node in the list, and proceeded to define a method that checks if the list is empty, just to keep the code DRY (don't repeat yourself). The following methods are then used to add nodes to the end of the list or at the beginning.  The last_node method is there to return the last element(node) in the list, who's data can be displayed via the tail element, or the content method can be used to display the whole list.

Overall, linked lists can be confusing to those not use to the data structure, as I myself was initially confused, but in time the flow would be less intimidating. Also, this post applies to singly linked lists, as there are also doubly and triply linked lists which are even more complex.  Although linked lists may not be helpful as a ruby developer, as ruby has very efficient memory allocation algorithms that make arrays preferred, getting familiar with this data structure is a must for computer programmers. So go ahead, play around with linked lists for a bit until you're comfortable and from there move one to double linked lists.  Enjoy!
