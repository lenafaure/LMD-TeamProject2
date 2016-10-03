#`String.prototype.replace()`

*The replace() method of the String global Object prototype searches a string for matches with the first parameter (searchFor) and replaces
them with the second parameter (replaceString).*

```
string.replace(searchFor, replaceString)
```


## Syntax

The `searchFor` parameter: what word is going to be replaced. This can be a **string** or a **regular expression**.

The `replaceString` parameter : what the word will be replaced with. This can be a **string** or a **function** returning a string.

```
string.replace(regexp|substr, newSubStr|function[, flags])
```

## Return

`String.prototype.replace()` returns a new string with some or all matches of `searchFor` replaced by `replaceString`.

## Parameters

### → First parameter : either a string or a regular expression:

- **String**: 
The most obvious way to do string replacement is by passing two strings to `replace()`: the string to find and the string to replace it with.

```
console.log("mommy".replace("m", "t"));
// → tommy
```

It’s worth mentioning that this approach is case sensitive. Searching for "M" in the above example would not work and the console would still print *"mommy"*. We will see how to counter this behaviour later on.


There is one major caveat if the first parameter is a simple string : only  the first occurence of the `searchFor` is replaced, so :

```
var result = "to_be_determined".replace('_', '-');
console.log(result);
```

will produce “to-be_determined”, which is supposedly not what we were trying to achieve.

To replace all occurrences, you’ll want to use the regex flavored version of `replace()`:


- **Regular Expression**: 
Let's do another replace, except this time, we'll use a a regular expression instead of a string. The only change we need to make is to surround our `searchFor `word with slashes / / instead of quotations " ".

```
console.log("Abracadabra".replace(/a/, "o"));
// → "Abrocadabra"
```

What's going on here ? The character that was replaced was only the second "a" : the first capital "A" was not recognized because our search is case sensitive. Let's add the `i` (ignore) option to make the search case insensitive : 

```
console.log("Abracadabra".replace(/a/i, "o"));
// → "obracadabra"
```

Ok, now the first "A" character has been recognized and replaced. But what we want to do is to replace *all* the "a" characters in the string. Let's add the `g` (global) option this time : 

```
console.log("Abracadabra".replace(/a/ig, "o"));
// → "obrocodobro"
```

Finally ! When a `g` option is added to the regular expression,  *all* matches in the string will be replaced, not just the first.


### → Second parameter : either a string or a function:

- **String**:
Describes how to replace what has been found.

**If replacement is a string**, its content is used verbatim to replace the match. The only exception is the special character dollar sign ($), which has special meaning :

|Pattern:  |Inserts:                            |   
|---       |---                                 | 
| `$$` 	   | $                                  |
| `$&`     | Capture group text                 |                  
| `$number`| The matched text                   |                    
| ``$` ``  | The text preceding the match       |               
| `$’`     | The text following the match       |

Let's have a look at an example to understand how to use the special character as `replaceString` :

The following uses a regex to look for a 4 digit number and replace it with the same number, but with dashes between the digits :

```
var pin = 'Your new PIN code is 4197.';
var newPin = pin.replace(/(\d)(\d)(\d)(\d)/g, '$1-$2-$3-$4');
console.log(newPin);

// "Your new PIN code is 4-1-9-7."
```

`\d` is a special regex element that matches any single digit, so we use 4 of those to find 4 digit numbers in a row. Each one is wrapped in parenthesis (), which we refer to as a *group*, and lets us reference them in the replacement string.

`$1` is replaced with whatever was matched in the first set of parenthesis, `$2` with what’s in the second, and so on. This means that we can play a little with the string and for example if we wanted to reverse the PIN code we would just do : 

```
var pin = 'Your new PIN code is 4197.';
var newPin = pin.replace(/(\d)(\d)(\d)(\d)/g, '$4-$3-$2-$1');
console.log(newPin);

// "Your new PIN code is 7-9-1-4."
```


- **Function**:

**If  replaceString is a function**, it will be called for each match, and the string returned by the function will be used as the replacement text.

```
var a = "The fbi's ten most wanted fugitives.";
var b = "fbi";
var newString = a.replace(b, function replacer(match){
    return match.toUpperCase();
} );
console.log(newString);

// Prints "The FBI's ten most wanted fugitives."
```


## Example 1 : Use `replace()` with a simple string (no regular expression)

Sometimes you just want  to replace a simple chain of characters by another. It is indeed useful to replace a word or a group of words, but is not as frequently used as the regular expressions:

```
var string = "My name is Bond";
var result = string.replace("Bond", "James Bond");

console.log(result);
// Prints "My name is James Bond"
```


## Example 2 : capture informations from a string and reuse them in the replacement string (with regular expression)

As we saw previously, it is possible to use capturing parenthesis to extract informations and reuse them in the output string. Let's say for example that we have a date written in US format : 05/09/2016, and we want to convert it to a day/month/year european format. We can definitely do that with regular expression and `replace()`:

```
var usDate = "05/09/2016";
var euDate = usDate.replace(/(\d{2})\/(\d{2})\/(\d{4})$/, "$2/$1/$3");

console.log(euDate);
// Prints "09/05/2016";
```

Every number is captured within a parenthesis, and to retrieve each parenthesis, we just have to call $1, $2, $3 which correspond to each parenthesis in the order they were declared.

To understand well this example, let's take a little detour and decrypt the special characters we used in this regular expression : 

**The `/^` and `$/` symbols** at the beginning and end of the regular epression represent the beginning and end of the portion of string we are looking for (we are looking for a portion of string that contains two digits, a slash, two digits a slash and four digits).

**The `()` parenthesis** are used to capture the portion of text that the regular expression will extract from the string. Here we have three different portions of text that we want to capture and use, and are refered to as *groups*.

**The `\d{n}` symbol** finds a decimal character (a digit), and the `n`character between accolades indicates how many time the digit character is repeated. In this example, we want to find first a set of two digits, then another set of two digits, and a third set of four digits.

**The `/\` symbols between the parenthesis** represent the slash `/` character that separates the sets of digits we want to find, but since it is part of the characters that a regex uses to perform, we have to escape it with an anti-slash `\`to tell the regular expression to interpret the slash as part of the string.


## Example 3 : use a function for the replacement

Instead of using a chain of characters for replacement, it is possible to use a function to manage the remplacement(s). This allows, for example, to perform operations on captured informations (as we saw in the previous example: $1, $2, $3...).

The parameters of the function have to respect a certain order (even if their names can vary) :

```
function(str, p1, p2, p3 /* ... */, offset, s)
```

Let's review in detail the meaning of each parameter : 

- The `str` parameter

It contains the text portion that has been found by the regular expression.

- The `p*` parameters

They contain the portions captured by the parenthesis.
They represent the captured portions $1, $2, $3 that we saw earlier. If there are only three capturing parenthesis, there will be only three `p` parameters. If there are five capturing parenthesis, there will be five `p`.

- The `offset`parameter

It contains the position of the text portion that has been found

- The `s` parameter

It contains the whole string.

Let's illustrate this with a script that will look for numbers in a string and add one to each number it founds : 

```
var string = "In 2 years I will be 20 years old";

var result = string.replace(/(\d+)/g, function(str, p1) {
    // Convert string to integer
    p1 = parseInt(p1);
    
    // Check if p1 is an integer
    if (!isNaN(p1)) {
        // Add one to the integer
        return p1 + 1;
    }
});

console.log(result);
// Prints "In 3 years I will be 21 years old"
```

Since we added the global `g` option to our regular expression, every digit (`d+` indicates that the number can have an infinite number of digits) in the string will be replaced. 


## Special Notes

1. This method does not change the String object it is called on. It simply returns a new string.

2. Don't forget : to perform a *global* search and replace in the whole string, include the `g` switch in the regular expression or the method will stop at the first occurrence. If the first argument is a string, then only the first occurrence of the substring will be replaced. The only way to replace all instances of a substring is to provide a regular expression with the global flag (`/g`) specified.

3. What if i want to replace a character by the dollar `$` sign ? Simply double `$$` the dollar sign in the replacement string.

4. From example 3, we can see that the `replace()` method searches through all occurences of `searchString`, which actually allows us to iterate through it *without using a loop*. The `replace()` method does it automatically for us.

## Browser support

| Chrome    | Internet Explorer        | Firefox   | Safari  | Opera   |
|---        |---                       |---        |---      |---      |
| yes       | yes                      | yes       | yes     | yes     |

---------------
*Léna Faure - 9/30/2016 - Career Path 3: Modern Front-End Developer*
