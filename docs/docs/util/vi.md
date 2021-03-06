---
title: VI
---

vi +36 foo.c
:36
SHIFT+g     Goto line number

/string     Search forward for occurrence of string in text
?string     Search backward for occurrence of string in text
n           Search for next instance of string
N           Search for previous instance of string
CTRL+b      Page up
CTRL+f      Page down
G           End of file
g           Begin of file
:set        Nu(mber) show line numbers
:.=         Returns line number of current line at bottom of screen
:=          Returns the total number of lines at bottom of screen
^g          Provides the current line number, along with the total number of lines, in the file at the bottom of the screen

see escape characters
:set list
:set nolist

The UNIX vi editor is a full screen editor and has two modes of operation:
       Command mode commands which cause action to be taken on the file, and
       Insert mode in which entered text is inserted into the file.
   In the command mode, every character typed is a command that does something to the text file being edited; a character typed in the command mode may even cause the vi editor to enter the insert mode. In the insert mode, every character typed is added to the text in the file; pressing the <Esc> (Escape) key turns off the Insert mode.
   While there are a number of vi commands, just a handful of these is usually sufficient for beginning vi users. To assist such users, this Web page contains a sampling of basic vi commands. The most basic and useful commands are marked with an asterisk (* or star) in the tables below. With practice, these commands should become automatic.
   NOTE: Both UNIX and vi are case-sensitive. Be sure not to use a capital letter in place of a lowercase letter; the results will not be what you expect.
   To use vi on a file, type in vi filename. If the file named filename exists, then the first page (or screen) of the file will be displayed; if the file does not exist, then an empty file and screen are created into which you may enter text.
*     vi filename     edit filename starting at line 1
     vi -r filename     recover filename that was being edited when system crashed
To Exit vi
   Usually the new or modified file is saved when you leave vi. However, it is also possible to quit vi without saving the file.
   Note: The cursor moves to bottom of screen whenever a colon (:) is typed. This type of command is completed by hitting the <Return> (or <Enter>) key.
*     :x<Return>     quit vi, writing out modified file to file named in original invocation
     :wq<Return>     quit vi, writing out modified file to file named in original invocation
     :q<Return>     quit (or exit) vi
*     :q!<Return>     quit vi even though latest changes have not been saved for this vi call
Moving the Cursor
   Unlike many of the PC and MacIntosh editors, the mouse does not move the cursor within the vi editor screen (or window). You must use the the key commands listed below. On some UNIX platforms, the arrow keys may be used as well; however, since vi was designed with the Qwerty keyboard (containing no arrow keys) in mind, the arrow keys sometimes produce strange effects in vi and should be avoided.
*    
   If you go back and forth between a PC environment and a UNIX environment, you may find that this dissimilarity in methods for cursor movement is the most frustrating difference between the two.
   In the table below, the symbol ^ before a letter means that the <Ctrl> key should be held down while the letter key is pressed.
*     j or <Return>
 [or down-arrow]     move cursor down one line
*     k [or up-arrow]     move cursor up one line
*     h or <Backspace>
 [or left-arrow]     move cursor left one character
*     l or <Space>
 [or right-arrow]     move cursor right one character
*     0 (zero)     move cursor to start of current line (the one with the cursor)
*     $     move cursor to end of current line
     w     move cursor to beginning of next word
     b     move cursor back to beginning of preceding word
     :0<Return> or 1G     move cursor to first line in file
     :n<Return> or nG     move cursor to line n
     :$<Return> or G     move cursor to last line in file
Screen Manipulation The following commands allow the vi editor screen (or window) to move up or down several lines and to be refreshed.
    ^f     move forward one screen
     ^b     move backward one screen
     ^d     move down (forward) one half screen
     ^u     move up (back) one half screen
     ^l     redraws the screen
     ^r     redraws the screen, removing deleted lines
Adding, Changing, and Deleting Text: Unlike PC editors, you cannot replace or delete text by highlighting it with the mouse. Instead use the commands in the following tables.
Perhaps the most important command is the one that allows you to back up and undo your last action. Unfortunately, this command acts like a toggle, undoing and redoing your most recent action. You cannot go back more than one step.
*     u     UNDO WHATEVER YOU JUST DID; a simple toggle
   The main purpose of an editor is to create, add, or modify text for a file.
Inserting or Adding Text
   The following commands allow you to insert and add text. Each of these commands puts the vi editor into insert mode; thus, the <Esc> key must be pressed to terminate the entry of text and to put the vi editor back into command mode.
*     i     insert text before cursor, until <Esc> hit
     I     insert text at beginning of current line, until <Esc> hit
*     a     append text after cursor, until <Esc> hit
     A     append text to end of current line, until <Esc> hit
*     o     open and put text in a new line below current line, until <Esc> hit
*     O     open and put text in a new line above current line, until <Esc> hit
Changing Text
   The following commands allow you to modify text.
*     r     replace single character under cursor (no <Esc> needed)
     R     replace characters, starting with current cursor position, until <Esc> hit
     cw     change the current word with new text,
starting with the character under cursor, until <Esc> hit
     cNw     change N words beginning with character under cursor, until <Esc> hit;
 e.g., c5w changes 5 words
     C     change (replace) the characters in the current line, until <Esc> hit
     cc     change (replace) the entire current line, stopping when <Esc> is hit
     Ncc or cNc     change (replace) the next N lines, starting with the current line,
stopping when <Esc> is hit
Deleting Text
   The following commands allow you to delete text.
*     x     delete single character under cursor
     Nx     delete N characters, starting with character under cursor
     dw     delete the single word beginning with character under cursor
     dNw     delete N words beginning with character under cursor;
 e.g., d5w deletes 5 words
     D     delete the remainder of the line, starting with current cursor position
*     dd     delete entire current line
     Ndd or dNd     delete N lines, beginning with the current line;
 e.g., 5dd deletes 5 lines
Cutting and Pasting Text
   The following commands allow you to copy and paste text.
     yy     copy (yank, cut) the current line into the buffer
     Nyy or yNy     copy (yank, cut) the next N lines, including the current line, into the buffer
     p     put (paste) the line(s) in the buffer into the text after the current line
Determining Line Numbers
   Being able to determine the line number of the current line or the total number of lines in the file being edited is sometimes useful.
     :.=     returns line number of current line at bottom of screen
     :=     returns the total number of lines at bottom of screen
     ^g     provides the current line number, along with the total number of lines,
in the file at the bottom of the screen
Saving and Reading Files
These commands permit you to input and output files other than the named file with which you are currently working.
     :r filename<Return>     read file named filename and insert after current line
(the line with cursor)
     :w<Return>     write current contents to file named in original vi call
     :w newfile<Return>     write current contents to a new file named newfile
     :12,35w smallfile<Return>     write the contents of the lines numbered 12 through 35 to a new file named smallfile
     :w! prevfile<Return>     write current contents over a pre-existing file named prevfile

## Basic movement

h l k j  : : : character left, right; line up, down
b w  : : : : word/token left, right
ge e   : : : end of word/token left, right
{ }  : : : : beginning of previous, next paragraph
( )  :beginning of previous, next sentence
0 ^ $ : : :beginning, rst, last character of line
nG ngg   : line n, default the last, rst
n% : : :percentage n of the le (n must be provided)
nj  : : : column n of current line
%match of next brace, bracket, comment, #define
nH nL  : : : line n from start, bottom of window
M   : middle line of window

## Insertion & replace ! insert mode

i a  insert before, after cursor
I A   : : insert at beginning, end of line
gI  : insert text in rst column
o O :open a new line below, above the current line
rc   : replace character under cursor with c
grc   : : like r, but without acting layout
R  : : : : replace characters starting at the cursor
gR   : : : like R, but without acting layout
cm : : : : change text of movement command m
cc or S  : : : : change current line
C  : : : change to the end of line
s   : : : change one character and insert
~   : : : : switch case and advance cursor
g~m  : : : switch case of movement command m
gum gUm: : : lowercase, uppercase text of movement m
<m >m  : shift left, right text of movement m
n<< n>>   shift n lines left, right

## Deletion

x X   delete character under, before cursor
dm  delete text of movement command m
dd D  : : : : delete current line, to the end of line
J gJ  : : : join current line with next, without space
:rd -  : : : : delete range r lines
:rdx -  : : : : delete range r lines into register x
Insert mode
^Vc ^Vn  insert char c literally, decimal value n
^A   : : : : insert previously inserted text
^@ : :same as ^A and stop insert ! command mode
^Rx ^R^Rx  insert content of register x, literally
^N ^P  text completion before, after cursor
^W  : : delete word before cursor
^U  : delete all inserted character in current line
^D ^T  : shift left, right one shift width
^Kc1c2 or c1 c2   enter digraph fc1; c2g
^Oc  : : : execute c in temporary command mode
^X^E ^X^Y  : : : : scroll up, down
hesci or ^[  abandon edition ! command mode

## Copying

"x  : : : use register x for next delete, yank, put
:reg -   : show the content of all registers
:reg x -   show the content of registers x
ym  : : yank the text of movement command m
yy or Y  :yank current line into register
p P  : : put register after, before cursor position
]p [p   : like p, P with indent adjusted
gp gP  : : like p, P leaving cursor after new text

## Advanced insertion

g?m : perform rot13 encoding on movement m
n^A n^X   +n, n to number under cursor
gqm  : : format lines of movement m to xed width
:rce w -  : : center lines in range r to width w
:rle i -  : : left align lines in range r with indent i
:rri w -  : right align lines in range r to width w
!mc - : lter lines of movement m through command c
n!!c -   lter n lines through command c
:r!c -  lter range r lines through command c
Visual mode
v V ^V : : start/stop highlighting characters, lines, block
o : : : exchange cursor position with start of highlighting
gv  : : start highlighting on previous visual area
aw as ap  : : select a word, a sentence, a paragraph
ab aB   : select a block ( ), a block { }
Undoing, repeating & registers
u U  : undo last command, restore last changed line
. ^R  : :repeat last changes, redo last undo
n.  : repeat last changes with count replaced by n
qc qC: : : :record, append typed characters in register c
q   stop recording
@c   : : execute the content of register c
@@    : repeat previous @ command
:@c -  : : execute register c as an Ex command
:rg/p/c -  :execute Ex command c on range r
b where pattern p matches

## Complex movement

+ +  line up, down on rst non-blank character
B W   : space-separated word left, right
gE E  : : end of space-separated word left, right
n  : : : down n  1 line on rst non-blank character
g0 gm  : : :beginning, middle of screen line
g^ g$  : : rst, last character of screen line
gk gj  : : : screen line up, down
fc Fc  : next, previous occurence of character c
tc Tc  : : : : before next, previous occurence of c
; ,  : : : : repeat last fFtT, in opposite direction
[[ ]]   start of section backward, forward
[] ][   : end of section backward, forward
[( ])   : : : unclosed (, ) backward, forward
[{ ]}   : : unclosed {, } backward, forward
[m ]m  : : : start of backward, forward Java method
[# ]#:unclosed #if, #else, #endif backward, forward
[* ]*  : start, end of /* */ backward, forward

## Search & substitution

/s - ?s -  : : : : search forward, backward for s
/s/o - ?s?o -  search fwd, bwd for s with o
set o
n or / -   : : : repeat forward last search
N or ? -   : repeat backward last search
# * : : : search backward, forward for word under cursor
g# g*  : : : : same, but also nd partial matches
gd gD : : : local, global denition of symbol under cursor
:rs/f/t/x -   substitute f by t in range r
b x : g|all occurrences, c|conrm changes
:rs x -  : : repeat substitution with new r & x
This will display line numbers along the left side of a window:
:set number
You can also define a mapping to toggle the option, for example:
:nmap <C-N><C-N> :set invnumber<CR>
By pressing Ctrl-N twice in normal mode, Vim toggles between showing and hiding line numbers.
If you have Vim version 7 or greater, you can change the width of the "gutter" column used for numbering:
:set numberwidth=3
You can use the number column for the text of wrapped lines:
:set cpoptions+=n
Finally, you can change the color used for the line numbers. For example:
:highlight LineNr term=bold cterm=NONE ctermfg=DarkGrey ctermbg=NONE gui=NONE guifg=DarkGrey guibg=NONE
