#`String.prototype.replace()`

*The replace() method of the String global Object prototype searches a string for matches with the first parameter (searchFor) and replaces
them with the second parameter (replaceString).*

```
string.replace(searchFor, replaceString)
```


## Syntax

The `searchFor` parameter: what word is going to be replaced. This can be a **string** or a **regular expression**.

The `replaceString`parameter : what the word will be replaced with. This can be a **string** or a **function** returning a string.

```
string.replace(regexp|substr, newSubStr|function[, flags])
```

## Return

String.prototype.replace() returns a new string with some or all matches of a pattern replaced by a replacement.

## Parameters

### → First parameter : either a string or a regular expression:

- **String**: 
The most obvious way to do string replacement is by passing two strings to `replace()`, the string to find and the string to replace it with.

```
console.log("mommy".replace("m", "t"));
// → tommy
```

It’s worth mentioning that this approach is case sensitive. Searching for "M" in the above example would not work and the console would still print *"mommy"*.



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

What's going on here ? The character that was replaced was only the second "a" : the first capital "A" was not recognized because our search is case sensitive. Let's add the `i` option to make the search case insensitive : 

```
console.log("Abracadabra".replace(/a/i, "o"));
// → "obracadabra"
```

Ok, now the first "A" character has been recognized and replaced. But what we want to do is to replace *all* the "a" charachters in the string. Let's add the `g` option this time : 

```
console.log("Abracadabra".replace(/a/ig, "o"));
// → "obrocodobro"
```

Finally ! When a `g` option is added to the regular expression,  *all* matches in the string will be replaced, not just the first.


### → Second parameter : either a string or a function:

- **String**:
Describes how to replace what has been found.

**If replacement is a string**, its content is used verbatim to replace the match. The only exception is the special character dollar sign ($), which has special meaning :

$$ 		    $
$&		    The matched text
$number	  Capture group text
``$` `` 	The text preceding the match
$’		    The text following the match

Let's have a look at an example to understand how to use the special charachter as `replaceString` :

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

## Example 1 


## Example 2 


## Example 3 

## Special Notes

1. This method does not change the String object it is called on. It simply returns a new string.

2. Don't forget : to perform a *global* search and replace in the whole string, include the `g` switch in the regular expression or the method will stop at the first occurrence. If the first argument is a string, then only the first occurrence of the substring will be replaced. The only way to replace all instances of a substring is to provide a regular expression with the global flag specified,

