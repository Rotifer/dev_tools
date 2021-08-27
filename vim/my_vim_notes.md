## Chapter 3 : Vim Essentials 

### Essential Navigation Command

h, j, k, l => left, down, up, right

CTRL-f page down
CTRL-b page up
w right by one word
W same as w but ignore punctuation
b back one word
B back one word but ignore punctuation
z+enter move up one screen but keep cursor stationary
0 (zero) beginning of a line
^ (caret) first character on a line
$ end of line
Two ways to jump to a specific line
1. gg
2. G


10gg or 10G go to line 10
These commands without a preceding number
gg go to beginning of file
G go to end of file
Can also use *line mode* with : and follow it with numer to go to a specific line
:10 + <ENTER> go to line 10
g-CTRL-g get more details 

### Deleting text and thinking in Vim

x - delete single character at cursor position
X - delete single character to left of cursor
dw - delete word

There is a pattern: **operator - motion**
dl - same as x
dh - same X
dj - deletes line and one below it
dk - deletes line and one above it
dO - delete to beginning of line
d$ - delete to end of line
D - shortcut for d$
dd - delete current line
3dd - delete 3 lines starting at cursor line

Pattern: **count-operator-motion**
5dw - delete five words
dw is same as 1dw
d3w = 3dw
. (dot) - repeats previous command

The exclamation mark has three purposes:
1. force an action (e.g. :q!)
2. toggle a setting
3. execute an external command

## Chapter 4 - Deleting, yanking, pulling

### Cut, copy and paste

d and x cut rather than delete
dd - cut the line and place its contents in the unnamed register
p - text is **put** 
ddp - swap lines
xp - swap two characters
d$ - cut rest of line from cursor position
y -(yank) copies
cut, copy, paste => delete, yank, put
yw - copy word
y$ - copy rest of line
2yw - copy two words
yy - copy a line yyp - copy and paste a line
4yy - copy 4 lines
u - undo last change
CTRL-r re-do last command

### Registers
Numbered or named - name and number preceded by double quote (")
Unnamed register double double quote ("")
d,c,s,x,y all these commands put text into ""
To see the register - :reg
Black hole register "_
"2P - paste what is in register 2
26 named registers
"ayy - yanks entire line into register named a
"Ayy - Append yanked line to register named a

For numbered registers - 0 holds yank and 1 holds delete or change

## Chapter 6 - Inserting, changing, repeating, deleting and joining

i - go to INSERT mode
I (uppercase) - same as ^i
a - appeand after the cursor position
A - append to the end of the line
o - begin a new line below the cursor and enter INSERT mode
O - begin a new line **above** the cursor and enter INSERT mode
80i # ESC - Create 80 # characters on the line
5o$$ ESC - Insert five new lines beginning with $$ (Note it's a lowercase letter o)
REPLACE Mode
R - replace mode
r - replace mode for a single character
c command - Change mode
cw - change word
c$ - replace from current cursor position to the end of the line
C - same as cw (analagous to D)
cc - change an entire line of text
3cc - change 3 lines
~ (tilde) - switches case
g~w - swaps case for word
n 
g~$ - changes all line
gUw - change all letters in word to uppercase
guw - change all letters in word to lowercase
Joining lines
J - join two lines (keeps spaceP
gJ join two lines without spaces
sJ - join 3 lines

### Searching, finding and replacing - Part 1

fb - Search forward in the current line for the character "b"
fA - find the next A
Fz - search **backwards** on the current line for the character "z"
; (semicolon) - advance to next search result
, (comma) - reverse the search direction
ti (til command) - move to character at position before next character "i"
2fz - go to second z
dtw - delete everything up to the next character "w"

#### Multiline searching

/word - go to next occurrence of the characters "word"
:set is - setting for incremental searching
:set hls - highlighted searching
?is ENTER - reverse search
* (asterisk) - keep searching for the word under the cursor
\# (pound sign, ignore the backslash, it's there to escape the markdown pound) - backwards word search
d/this - delete everything from current cursor position up to "this"

### Searching, finding and replacing - Part 2

:s/old/new/[flags] - substitute command
:[range]s/old/new/[flags] - range-based substitution
:1,5s/for/FOR/g - replace occurrences of "for" with "FOR" on the next 5 lines
:.,s/net/org/ - replace all occurences of "net" with "org" from the current line to EOF
:%/net/org/g - global search and replace in file
:s|old|new|g - can change the / to another character, e.g. pipe symbol, to avoid escaping
cW - change word including puntuation (as distinct from cw)
80iasterisk ESC - Add 80 asterisks to line
5o# - Create five new lines beginning with #
 
### Text objects and macros

dw - delete word
daw - delete a word (check difference between daw and dw)
diw - delete inner word (leave punctuation)
ciw - change inner word
ciW
das - delete a sentence
dis - delete a an inner sentence - leave white space and punctuation

A paragraph is delineated by blank lines
dap - delete a paragraph
dip delete inner paragraph, blank lines remain
ci[ - change everything within [] Can also be written as ci]
da[ - delete everything with []
da< delete within angle brackets
di< within angle brackets. Check da< versus di&lt
cit - change tag contents
cat - change all tag
dit - delete inside tag
aB & iB - block
ca{change everything in braces incuding the braces themselves
ci{ - change within braces
ci" - change everything within inner quotes
ci' - change everything with single quotes

#### Macros
qa - record a macro to register a
q - stop macro recording
@a - play back macro in register a
@@ - replay most recent macro
0 (zero) - first key stroke in macro is a good idea to set it at the start of a line
j - final command so macro moves to next line at end
qb - record macro to reg b
qb0iTIP: ESCjq - Record macro to reg b Macro says: go to start of line, enter INSERT mode, add text "TIP: " 
to start of line, press ESC to get back to normal mode, mode to next line and quite
5@b - apply macro recorded above to next 5 lines.
qC (capital C) - append to macro in register c

## Additional Notes

:%s/\s\+$// -  trim the white space characters off the end of each line
"*y - * use the yank command to copy selection to clipboard 


