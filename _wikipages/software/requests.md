---
layout: default
title: How Do I...?
permalink: p/requests
category: software
---



### Overview

This is a list of tools that I'd like to have and things that I'd like to know how to do.  I'm looking for suggestions, so [contact me](https://www.brandoncurtis.com/contact) if you have ideas!  My hope is that I will be able to build my own solutions as my programming skills complete.

----

### Request 0001 - workspace to workspace multi-window mover

Hotkey combination to move all of the windows in a given workspace to another workspace.  Works under Unity 7 in Ubuntu 16.04.

### Request 0002 - Unix CLI app for searching contact info

I want to pop open a terminal and quickly grab peoples' contact info. Should support importing data from the CSV produced by Google Contacts.

### Request 0003 - Unix CLI app for searching unicode codepoints

I use Unicode symbol insertion frequently, so I want to pop open a terminal and quickly grab the hex code for a given unicode symbol.

### Request 0004 - Printing Tables with Python

Let's say I have a list/array and I want to print it as a formatted table.

In Bash, I can use C-style string formatting with `printf`:

```bash
a=(1 2 3 4 5 6 7)
printf "%s\t%s\n" ${a[*]}
1	2
3	4
5	6
7	
```

note that `${a[*]}` notation mass-expands the array elements.

This works because `printf` reuses the format string until all arguments are consumed.
I don't need to worry about how many elements are present in a.

In Python, this is NOT the case:

```python
a = [1,2,3,4,5,6,7]
print("{:<4}{:<4}".format(*a))
1   2 
```

note that `*a` notation mass-expands the list elements.

`.format()` does NOT reuse the format string.
`.format()` returns once all of the placeholders have been filled, regardless of how many arguments are passed to it.

So what's the idiomatic way to accomplish this in Python?
I came up with this:

```python
a = [1,2,3,4,5,6,7]
cols = 2
for row in [a[i:i+cols] for i in range(0,len(a),cols)]:
     s = '{:<4}' * min(cols,len(row))
     print(s.format(*row))
1   2   
3   4   
5   6   
7  
```

Am I being dumb here?  Is there a better way?
