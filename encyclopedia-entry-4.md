#`margin-bottom` in CSS

*The `margin-bottom` property in CSS sets the bottom margin for an HTML element.*

The CSS margin properties are used to generate space around elements. The margin-bottom property is used for setting the margin for the bottom side of an element.

![bottom-margin](bottommargin.jpg)

## Syntax

Like all the margin properties, the margin-bottom property can take the following values : 

```
margin-bottom: length|percentage|auto|initial|inherit;
```



## Values

### → length

Specifies a fixed width in px, pt, cm, em, etc. 

Default value is 0.

Negative values are allowed.

#### Example : 

```
margin-bottom: 50px;
```

![margin-bottom : length](img/margin_bottom_2.png)
 
### → percentage

Specifies a width in % of the width of the containing element.

Negative Values are allowed.

#### Example : 

```
margin-bottom: 10%;
```

![margin-bottom : percentage](img/margin_bottom_3.png)


### → auto 

The browser calculates a bottom margin.

#### Example : 

```
margin-bottom: auto;
```

![margin-bottom : auto](img/margin_bottom_1.png)


### → initial 

Sets this property to its default value.

#### Example : 

```
margin-bottom: initial;
```

![margin-bottom : initial](img/margin_bottom_4.png)


### → inherit

Specifies that the margin should be inherited from the parent element.

#### Example : 

```
margin-bottom: inherit;
```

![margin-bottom : inherit](img/margin_bottom_5.png)


## Special Notes

**Margin collapse**

Collapsing margins happen when two elements with vertical margins are stacked on top of each other. If one margin is greater than the other, then that margin overrides the other, leaving only one margin.

This does not happen on horizontal margins (left and right), only on vertical margins (top and bottom).

On this example Here we can see that the space between the two elements amount to 50px instead of adding the bottom and top margins of the two stacked element : 

![margin-bottom : collapse](img/margin_bottom_6.png)

## Browser support

*The numbers in the table specify the first browser version that fully supports the property.*

| Chrome    | Internet Explorer        | Firefox   | Safari  | Opera   |
|---        |---                       |---        |---      |---      |
| 1.0       | 6.0                      | 1.0       | 1.0     | 3.5     |
