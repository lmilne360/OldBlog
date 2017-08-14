---
layout: post
title:  "Coding Challenge #1"
date:   2017-08-13 23:54:07 -0400
---


So since I've been playing around with a fiew challenges on the web. I decided to break down one of the really fun ones i've dealth with.

The Challenge:  Write, in the C# language,  a function that takes a string of alphabetic characters, strips out any spaces, reverses the string and then return the string after manipulating it as follows:
Each character in the string is changed to the character in the alphabet that's the number of places ahead of it equal to the character's position in the string, where the first character is in position 1 and z wraps around to a. 

Disclaimer: As this is an already long post, I am not going to dwell on the syntax of the C# language. Google is your friend.

### Step 1: Mr Mime
The first step I decided to tackle in this was getting the user's input from a console and removing all the whitespace. As this was a pretty straightforward task, it was not too coding intensive. To get the user's input, I first declared a variable to store the data in.

`string word;` 

 I then assigned that variable to a `Console.ReadLine()` function which, as the name implies, reads a line (input) returned from the console.  For brevity sake, I combined the declaration and assignment of the input variable so it ended up looking like:

`string word = Console.ReadLine()`

Now that I got my user input, next is to remove all the white spaces. I accomplished this by using the `String.Replace()` and passing in the target and replacement value as its parameters. Since the goal is to replace empty spaces with nothing it came out as:

`word = word.Replace(" ", "")`

I basically reassigned the `word` variable to its previous self after replacing all the white spaces. So that's it; the first step of the challenge is now complete.

### Step2: Lucario
For the second part of the challenge, reversing the string, I decided to write a separate method for this functionality. This method would take a string as a parameter and return the string in reverse order.

`public static string ReverseString(string str){}`

Within the function, my first step was to take the string passed and convert it into an array of all the letters for easy iteration. This is accomplished via a neat `String.ToCharArray()` which returns an array of each character in a string. 

`char[] lettersArr = str.ToCharArray();`

Since this method will be returning the string in reverse, I decided to declare an empty string variable for the reversed string.

` string reverse = ""; `

The following step is to iterate through the `letters array` and add each character to the `reverse` variable, starting from the last character and ending at the first. To do this I used a standard for loop with the index started at the last index of the array and decrement until the first.

```
for (int i = lettersArr.length - 1; i > -1; i--)
{
reverse += lettersArr[i];
}
```
This adds each letter of the array, from end to start, to the `reversed` variable. The final part of this method is to return that reversed value. `return reverse`.  Because this method has a return value, I am then able to go back into the main method and store this value into a variable by calling the method and passing it the string argument.
```
/** main method
string reversed = ReserveString(word); 
```
Now, in the main method, we have a `word` variable, which is the parsed user input, and a `reversed` variable which is the word variable passed through a method and returned in a reversed state. The last part of the challenge is to take that reserved string and replace each character with a character in the alphabet positioned `n` letters away from it with `n` being that letter's index in the string. Confusing, I know.

### Step3: Slowpoke
so the first part is similar to the previous section in which we created a new function that returns a string. In this example, we'll call it `TransformString`. Similar to the previous section, we'll  convert the string being passed into an array and store it in an array as well as declare an empty string variable in which we'd store the replaced characters. Additionally, we'll create an array of alphabet characters for later parsing. For simplicity sake, we'll only be using downcase letters.

```
/** TransformString method
char[] alphabet =  "abcdefghijklmnopqrstuvwxyz".ToCharArray();

char[] lettersArr = str.ToCharArray(); 
string transformed = "";
```

The next step is to create a loop with the goal of looping through each of the strings letters, finding its position in the alphabet, and return an alphabet letter at its index value away.

The loop:
`for (int i = 0; i < lettersArr.Length; i++){};`

Within that loop, we'll declare a `position` variable whose value is the current letters' ( index of the loop ) index in the `alphabet` variable.  Finding the index of an item in an array is as simple as using the `Array.IndexOf()` method and passing it two arguments with the first being the array you're parsing and the second being the item whose position you're seeking. This ends up looking like:

```
/** for loop
var position = Array.IndexOf(alphabet, lettersArr[i]);
```

Now that we have the current letters' position in the alphabet( note we're still within the for loop), we can then find the letter in the `alphabet` that is `i` letters away from this position, `i` being the current index.  Note: we also want to make sure that the index we're looking for is within the bounds of the alphabet, so if we're trying to find a 27th letter (26th index) we should just start back at the first letter (index 0).  To do so we can use an ` if else` statement to validate the index, then store the letter at that index.

```
/** for loop
if ( (position + i + 1) < alphabet.Length)
{
  transformed += alphabet[position + (i +1)]
}
else
{
   transformed += alphabet[0];
}
```
Remember, `position` is the current letters' (lettersArr[i]) index in the `alphabet` variable and `i` is the current index.  The letter we are replacing each letter with is `n` letters away from its position in the alphabet, with `n` being its index (`i`)  in the string. Note** Because we are looking for the letters index value away, we must add 1 to the index being that array indexes start at 0. If we're looking for n letters away for the first letter, we'd be looking for 0 letters away, which would be the same letter. Hence the need to add one (first = 1, second = 2 etc). Now that we replaced every letter in the string with another letter and stored it as a new string, all that's left is to end the `for` loop and return the `transformed` string variable within the parent function.

Now that the last part is finished, all that's left is to display the product. To do so, we once again return to the main method.  In there, we can pass the `reversed` variable as an argument to our `transform` method, which would transform the string so to speak.  We can then place this value in a `Console.WriteLine();` function to display the data to the user.

```
/** Main method
Console.WriteLine(TransformString(reversed));
```

That sums up the basic implementation of this challenge, with the use of encapsulation to make each aspect of the code easier to manage. If you want to see the full code in action, you can view it [here](https://dotnetfiddle.net/vjZTvY)

