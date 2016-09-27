#`String.prototype.replace()`

*The replace() method of the String global Object prototype searches a string for matches with the first parameter (pattern) and replaces
them with the second parameter (replacement).*

```
str.replace(pattern, replacement)
```


## Syntax

The `pattern` parameter can be a string or a RegExp, and the `replacement` parameter can be a string or a function to be called for each match :

```
str.replace(regexp|substr, newSubStr|function[, flags])
```

## Return

String.prototype.replace() returns a new string with some or all matches of a pattern replaced by a replacement.

## Parameters

### → First parameter : either a string or a regular expression:

- **String**: 
To be found literally in the input string. 

- **Regular Expression**: 
To be matched against the input string. 

Be warned : only the *first occurrence* of a string or regular expression is replaced. If you want to replace multiple occurrences, you must use a regular expression with a global `/g` flag. 

### → Second parameter : either a string or a function:

- **String**:
Describes how to replace what has been found.

- **Function**:
Computes a replacement and is given matching information via its parameters.

## Example 1 


## Example 2 


## Example 3 

## Special Notes

1. This method does not change the String object it is called on. It simply returns a new string.

2. Don't forget : to perform a *global* search and replace in the whole string, include the `g` switch in the regular expression or the method will stop at the first occurrence.

