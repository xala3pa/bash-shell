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

## Arrays

An array is initialized by assign space-delimited values enclosed in ()

  an_array=(golang groovylang java)

All values in an array -> ${arrayname[@]}

The total number of elements in the array is referenced by ${#arrayname[@]}

The array elements can be accessed with their numeric index. The index of the first element is 0.

## Basic Operators

Simple arithmetics on variables can be done using the arithmetic expression: $((expression))

## Basic String Operations

### String Length

  ${#STRING}

### Index

Find the numerical position in $STRING of any single character in $SUBSTRING that matches. Note that the 'expr' command is used in this case.

  expr index "$STRING" "$SUBSTRING"

### Substring Extraction

Extract substring of length $LEN from $STRING starting after position $POS. Note that first position is 0.

  ${STRING:$POS:$LEN}

If :$LEN is omitted, extract substring from $POS to end of line

### Substring Replacement

Replace first occurrence of substring with replacement (replace be for eat on the string)

  ${STRING[@]/be/eat}

Replace all occurrences of substring

  ${STRING[@]//be/eat}

Delete all occurrences of substring (replace with empty string)

  ${STRING[@]// not/}

Replace occurrence of substring if at the beginning of $STRING

  ${STRING[@]/#to be/eat now}

Replace occurrence of substring if at the end of $STRING

   ${STRING[@]/%be/eat}

Replace occurrence of substring with shell command output

  ${STRING[@]/%be/be on $(date +%Y-%m-%d)}    # to be or not to be on 2012-06-14
