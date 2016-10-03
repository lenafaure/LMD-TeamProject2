#The `<em>` HTML tag

*The HTML tag `<em>` is used to emphasize text, which traditionally means that the text is displayed in italics by the browser.*

It provides semantic meaning about the text it contains, effectively saying, "this text is slightly more important than other text here." Use it to mark up text content of any kind that needs *moderate* emphasis. (See the `<strong>` tag for *strongly* emphasized content).

## Usage

The `<em>` tag surrounds the word/term being emphasised. It is a **phrase tag** : a tag used to indicate that a block of text has structural meaning (other phrase tags include `<strong>`, `<cite>` or `<code>` for example).

Example of `<em>` tag usage: 

```
<p>This is how to <em>emphasize</em> a single word.</p>
```

Will render : 

>This is how to *emphasize* a single word.

Most browsers will display the `<em>` element with the following default values:

```
em { 
    font-style: italic;
}
```

However, it is important to note that the choice of rendering the `<em>` tag with an italic style is not an established rule : `<em>` could be rendered by the browser in any other way (text color, uppercase for example) that would *emphasize* the text it surrounds.

The role of an `<em>`tag is **semantic**, not *visual* : it serve the purpose of inserting a meaning in the HTML code, and to insist on a particular piece of text.

## Example 1

The `<em>` element is used to mark up text content of any kind that needs moderate emphasis :

```
I just <em>had</em> to eat this piece of cake.
```

Will render: 

>I just *had* to eat this piece of cake

→ The person or software reading this line would read it with an emphasis on the words in italic.

## Example 2

This `<em>` elements differentiates itself from the `<i>` element, which merely sets the font to italics. If you only want to make text italic, but not for the purposes of emphasis, use `<i>`.

```
<p>Do you <em>really</em> need to buy a new phone?</p>

<p>I am considering buying the new <i>Harry Potter</i> for my daughter</p>
```

Will render: 

>Do you *really* need to buy a new phone ?

>I am considering buying the new *Harry Potter* for my daughter

→ The fact that they both have the same default style is mere coincidence : there is no semantic meaning of emphasis in the second sentence, merely a visual way of saying that we are speaking of the book *Harry Potter*.


## Special Notes

By default the `<em>` tag is an inline element that can be nested, and each level of nesting increases the degree of emphasis. 


## Browser support

| Chrome    | Internet Explorer        | Firefox   | Safari  | Opera   |
|---        |---                       |---        |---      |---      |
| yes       | yes                      | yes       | yes     | yes     |

---------------
*Léna Faure - 9/30/2016 - Career Path 3: Modern Front-End Developer*
