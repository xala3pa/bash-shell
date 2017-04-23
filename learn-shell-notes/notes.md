# Learn Shell notes

The first line of the shell script file begins with a "sha-bang" (#!), for example using Bash:
  
  **#!/bin/bash**
  
You can fins out the currently active shell by executing:
  
  **ps | grep $$**

## Variables

1. Shell variables are created once they are assigned a value.
2. Is case sensitive.

    num_km=100

    name=Alvaro

To reference a variable: (A backslash "\" is used to escape special character)

  1. $name
  2. ${name} -> avoid ambiguity

A backslash "\" is used to escape special character using `` (known as back-ticks) or with $() 

FILELIST= \`ls\`

FileWithTimeStamp=/tmp/my-dir/file_$(/bin/date +%Y-%m-%d).txt

## Passing Arguments to the Script

To pass arguments is just writing them as space-delimited list following the script.

$1 -> first argument in the command line

$2 -> second argument in the command line

...

$0 -> references to the current script

$# -> holds the number of arguments passed to the script

$@ -> holds a space delimited string of all arguments passed to the script
