---
layout: post
title:  "Regex : Bane of my existence"
date:   2016-10-11 23:27:07 +0000
---


Ok, so along my path of web development, I've stumbled into an annoying little creature known as regex. Barb-tailed, crimsome-eyed and acid spitting. Everything you can imagine. For those of you unfamiliar with this creature, it's basically an expression (regex == regular expression) used for searching and matching patterns in strings.

The cool thing about regex is that it makes string manipulation simple.  It takes the cumbersome job of interating through strings to find a match and groups it into one ~~simple~~ expression. For example, lets say you have a  string "I like apples, tomatoes, and oranges" and would like to return an array of words that starts with a vowel. Normmaly, you can  just write a method that iterates over each word and store the ones beginning with vowels. Somthing along the lines of :

```
string = "I like apples, tomatoes, and oranges"
vowels = 'aeiou'
vowel_words = []
string.split.each{|word|vowel_words << word if vowels.include?(word[0].downcase)}

vowel_words
```
However, with regex, this is made easy by a simple expression of:
```
 "I like apples, tomatoes, and oranges".scan(/\b[aeiou]\w*/i)
```

Simple enough right? Not really, at least not to me initially. When I started out familiarizing myself with regex, it all looked like a clusterf$%k of I-don't-know-whats, and even now I find myself looking apprehensively at the more complex Regex(s).'What's with all the slashes and brackets?' I initially thought. However, I must say, it's not as scary as it looks. Though intimidating at first, regex quickly becomes quite friendly once you take your time with it. The most difficult part would be memorizing what each expression (eg: \b) does, but even that's unecesarry being that there's hundreds of reference sheets floating around the web. Once you know exactly what you want to match, you just have to carefully type out the expression to match your needs.

Let's break down the previous example...for example. First thing's first, regexs are always ( to my knowledge) written between two forward slashes `//` , they're basically the start and end of the expression. The exception to this is when you're including options into the parameters, which are placed after the last forward slash`/`. 

Following that, we'd want to indicate the start of a word, which is exactly what the `\b` does. It also indicates the end of a word if used after an expression. We then enclose the characters we want to begin with into a square bracket `[]` which basically says that any of the character within those brakets. So `\b[aeiou]` is just saying 'look at the beginning of a word for the letters a or e, or i etc.

Next we followed up with `\w` which stands for any word character. In addition to letters, this includes numbers and underscores. Take note on the case of the 'w' because an uppercase 'W' would have the opposit effect: selecting non-word characters. Thus far our expression says search for words that begins with vowels followed by any word character.

Penultimately, we added an asterisk `*` following the word character. The asterisk denotes that the previous statement (word character) may not be present or there could be more than one of them. Thus saying that after the opening vowel, there may or may not be other letters, numbers, or underscores.

Finally. we end our expression with the forward slash `/` signifying the end. However, as I've previously mentioned, an optional character can be placed after the closing slash. Till this point, our expression searches for words beginning with vowels that may or may not be followed by other characters, which is exactly what we want it to do. This, however, omits words that start with uppercase vowels, such as the beggining of a sentence. To include uppercase characters, we add the optional character `i` behind the closing slash. This signifies that the previous expression is not case sensitive, thus would include uppercase characters.

Okay, so the explanation was a bit lengthy for such a small bit of code, but the point is it's not so bad once you take your time. There's plenty of online resources to aide in the quest of mastery, these include  [rubular](http://http://rubular.com/) and [memberpress](http://www.memberpress.com/how-to-become-a-regular-expression-power-user/).  I believe that turning five lines of code into one line is worth the time and effort it takes to get comfortable with regexs. It's just another beast of burden.



