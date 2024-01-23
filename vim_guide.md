----------------------------------------------------------------------<br>
***NOTE***: *Caret symbol* `^` *refers to* `<Ctrl>` *key, while* `<^>`<br>
*refers to actual* **Caret key** (`<shift-6>` *US keyboards) in*<br>
*this document.*<br>
<br>

***NOTE***: *In RARE cases a Vim key can conflict with one of your*<br>
*terminal's shortcut key(s) (likely involving* `<Ctrl>` *key). This*<br>
*doesn't happen often BUT do check terminal shortcuts before* <br>
*going insane :)*<br>
----------------------------------------------------------------------<br>

<br>

# Vim has 4 modes:
# `normal`, `insert`, `visual`, *&* `command`

<br>

1. [Normal](#Normal mode)
2. [Insert](#Insert mode)
3. [Visual](#Visual mode)
4. [Command](#Command mode)

---------------------------------------------------------------------

<br>

<a id="Normal mode"></a>

# Normal mode

`normal` mode is for moving around, copying, pasting, & deleting. In<br>
a way, `normal` mode *(takes up 50% of this document!)* is the most<br>
important since you enter all other modes *from* `normal` mode most of<br>
the time, hence, the name *normal*.<br>

<br>

* Entering **Insert mode** from **Normal mode**
  * `i`              --- insert before cursor
  * `I`              --- insert before line
  * `a`              --- append after cursor
  * `A`              --- append after line
  * `o`              --- open new  line under current
  * `O`              --- open new  line above current

<br>

* Entering **Visual mode** from **Normal mode**
  * `v`              --- `visual` mode at cursor
  * `V`              --- `visual` mode at line
  * `^v`             --- `visual` block mode

<br>

* `ESC` | `^{`     --- entering `normal` mode 
* `^c`             --- entering `normal` mode
  * *There are some differences between `ESC` & `^c` in some cases*
     * *Example: `ESC` is used for multi-line edit in `visual block`* 

<br>

* `ZQ`             --- quit vim without saving (`:q!`)
* `ZZ`             --- save any changes & quit vim (`:wq`)

<br>

#### Basic navigation/motions
* `h`              --- move left
* `j`              --- move down
* `k`              --- move up
* `l`              --- move right

<br>

#### Common `normal` mode functions
* `p`              --- put/paste after position
  * `2p`             --- puts/pastes twice after position
* `P`              --- put/paste before position
  * `3P`             --- puts/pastes twice before position
* `~`              --- change case
* `J`              --- join lines
* `nJ`             --- join next *n* lines
* `r`              --- replace one char
* `R`              --- replace many chars
  * `Esc` | `^c`   --- exit *REPLACE* (like `insert`) to `normal` mode
* Indentation
  * `>`              --- shift selection right (indent) by shiftwidth
  * `<`              --- shift selection left (un-indent) by shiftwidth
  * `>>`             --- shift right (indent) by shiftwidth
  * `<<`             --- shift left (un-indent) by shiftwidth
  * `==`             --- auto-indent
     * `=ap`          --- auto-indent paragraph (contiguous code+line)
     * `=7d`          --- auto-indent from current line to next 7 lines

<br>

### Where to? Navigation/motions
* `+`              --- to the first non-white space of next line
* `-`              --- to the first non-white space of previous line
* `_` | `<^>`      --- to first non-white space in current line
  * *The `<^>` refers to actual Caret key (`<shift-6>` US keyboards)*
* `$`              --- to end of line
* `0`              --- to beginning of line (position 0)
* `<n>|`           --- to column **n** in current line
* `f<char>`        --- to first instance of *char*
* `F<char>`        --- to first instance of *char* back
* `t<char>`        --- up to first instance of *char*
* `T<char>`        --- up to first instance of *char* back
* `(`              --- back a sentence 
* `)`              --- forward a sentence 
* `{`              --- back paragraph (contiguous text + empty line)
* `}`              --- forward paragraph (contiguous text + empty line)
* `%`              --- toggles between matching brackets
* A good approach is to utilize `visual mode` with motions
  * `v` to enter `visual` mode & toggle (){}<>[] with `%` -- USEFUL!
  * `V` to enter `visual` line mode & use `h,j,k,l` for selection 
  * `V` to enter `visual` line mode & use count + `h,j,k,l` 
  * `v` to enter `visual` mode & use `t` to highlight to a *char* 
  * *Many useful options for combining `visual` mode & motions*
* Navigate words & WORDS
  * `w`              --- to next instance of start of word
  * `W`              --- to next instance of start of delimited word
  * `b`              --- to previous instance of start of word
  * `B`              --- to previous instance of start of delimited word
  * `e`              --- to next instance of end of word
  * `E`              --- to next instance of end of delimited word
   
<br>

* Marks
  * `m<char>`        --- sets mark at cursor in **char**
     * `a`-`z`          --- possible marks
  * `m<CHAR>`        --- sets mark at cursor in **CHAR** (uppercase)
     * `A`-`Z`          --- possible marks
     * upper case marks are across files
  * `` `<mark>``     --- jump to the **mark**
  * `'<mark>`        --- jump to start of line with the **mark**

<br>

* `''`             --- jump to last jump
* `` `[``          --- jump to last changed text
  * Applies until the buffer/file is written/saved
* `'[`             --- jump to start of line of last changed text
  * Applies until the buffer/file is written/saved
* `gv`             --- go to & re-select last `visual mode` selection

<br>

* `^u`             --- up 1/2 page
* `^b`             --- up 1 page
* `^d`             --- down 1/2 page
* `^f`             --- down 1 page
* `H`              --- top of screen 
* `M`              --- middle of screen 
* `L`              --- bottom of screen 
* `zb`             --- align current line top of screen (scroll up)
* `zt`             --- align current line top of screen (scroll down)
* `zz`             --- center screen on cursor
* `G`              --- to last line 
* `gg`             --- to 1st line
  * `ngg`            --- to line *n*
  * `nG`             --- to line *n*

<br>

* `^o`             --- previous position (between files as well) 
* `^i`             --- position forward (between files as well)
* `^<^>`          --- previous file/buffer
  * *The `<^>` refers to actual Caret key (`<shift-6>` US keyboards)*
* `gf`             --- open buffer/file under cursor (must be in path)
* Navigate & work with windows
  * `^w v`         --- vertically split (`vsplit`|`vs`) current buffer
  * `^w s`         --- horizontally split (`split`|`sp`) current buffer
  * `^w T`         --- move window to a new tab
  * `^ww`          --- move to last window 
  * `^wr`|`^wR`    --- rotate windows
  * `^wc`          --- close window 
  * `^wo`          --- close other windows
  * `^w hjkl`      --- move cursor between window splits
  * `^w HJKL`      --- move window to left, bottom, top, or right 
  * *Window split size options*
     * `^w +-<>`      --- change size of split
     * `^w =`         --- set equal hight & width for all
* `gt`             --- next tab
* `gT`             --- next tab reverse

<br>

### Yank/copy
* `Y`              --- yank/copy
* `yy`             --- yank a line
  * `nyy`            --- yank *n* lines (*n* includes current line)
  * `ynj` | `nyj`    --- yank current line plus *n* lines below
  * `ynk` | `nyk`    --- yank current line plus *n* lines above
  * `yngg` | `nygg`  --- yank to line number *n* 
  * `ynG`  | `nyG`   --- yank to line number *n* 
* `yw`             --- yank a word
  * `ynw`            --- yank *n* words
  * `ynb`            --- yank *n* words back
* ``y`<mark>``       --- yank from current line to `<mark>`

<br>

* `yf<char>`       --- find *char* & yank to it (inclusive)
  * `yF<char>`       --- backward find *char* & yank to it
* `yt<char>`       --- find *char* & yank up to it
  * `yT<char>`       --- backward find *char* & yank up to it

<br>

* `y/<string>`       --- yank to first instance of *string*
* `yn/<string>`      --- yank to *nth* instance of *string*

<br>

### Deletion
* `x`              --- delete char under cursor
* `X`              --- delete char left of cursor
* `D`              --- delete rest of line
* `dd`             --- delete current  line
  * `ndd`            --- delete *n* lines (*n* includes current line)
  * `dnj` | `ndj`    --- delete current line plus *n* lines below
  * `dnk` | `ndk`    --- delete current line plus *n* lines above
  * `dngg` | `ndgg`  --- delete to line number *n* 
  * `dnG`  | `ndG`   --- delete to line number *n* 
* `dw`             --- delete rest of word
  * `dnw`            --- delete *n* words
  * `dnb`            --- delete *n* words back
* ``d`<mark>``       --- delete from current line to `<mark>`

<br>

* `df<char>`       --- find *char* & delete to it (inclusive)
  * `dF<char>`       --- backward find *char* & delete to it
* `dt<char>`       --- find *char* & delete up to it
  * `dT<char>`       --- backward find *char* & delete up to it

<br>

* `d/<string>`       --- delete to first instance of *string*
* `dn/<string>`      --- delete to *nth* instance of *string*

<br>

### Change (delete + enter insert mode) 
* `C`              --- change rest of line
* `cc`             --- change line
* `S`              --- change line
* `s`              --- change *char* under the cursor

<br>

* `cf<char>`       --- find *char* & change to all to it (inclusive)
  * `cF<char>`       --- backward find *char* & change to all to it
* `ct<char>`       --- find *char* & change up to it
  * `cT<char>`       --- backward find *char* & change up to it

<br>

* `cw`             --- change rest of the word
  * `cnw`            --- change to the *nth* word
  * `cnb`            --- change *nth* word back

<br>

* `c/<string>`       --- change to first instance of *string*
* `cn/<string>`      --- change to *nth* instance of *string*

<br>

### Working with Boundaries
Actions are applied *text objects* in Vim and *text objects* are<br>
defined by boundaries. In fact all examples above have boundaries.<br>
Example: `yy` is `yank/copy` with boundary of 1 line (current line)

<br>

* **Attributes** give more explicit text boundaries
  * Popular **attributes**
     * `f` find *(several examples in sections above...)*
     * `t` find up to *(several examples in sections above...)*
     * `i` inner
     * `a` all
  * `i` is the *inner* attribute =  with in boundaries of text-object 
  * `a` is the *all* attribute = text-object + boundary

* *Attributes* are used with **operators**
  * Popular **operators**
     * `y` yank 
     * `d` delete 
     * `c` change
     * `>` shift 
     * `v` visual 
     * ...etc..

* *Attributes* apply *operators* to **text-objects**
  * **Text-objects**
     * word `w`, WORD `W`
     * sentence `s`
     * blocks: `(` or `)`, `{` or `}`, `[` or `]`, `<` or `>`
     * strings: `"`, `'`
     * tag `t` (i.e XML or HTML tags)

<br>

* **Operators** determine boundaries through **attributes** & work<br>
  on **text-objects**

* Basic boiler plate

  > `<operator> <attribute> <text-object>`<br>

  > *NOTE: Some times the order of `<operator>` & `<attribute>`*<br>
  > *can be reversed to `<attribute> <operator> <text-object>`*<br>
  > *but you can (should) just stick to standard layout until you*<br>
  > *develop enough comfort with vim*<br>

* `i` (*inner*)  & `a` (*all*) are the most used/useful boundaries!
  * ***NOTE*** *for both* `i` *&* `a`: *If the cursor is not on the*<br>
    *text object then the next (relevant) text object selected*

#### Inner attribute 
* The **inner** `i` applies *operators* to text *with in* boundaries<br>
  of an object but *NOT* to the boundaries that define the text object<br>

* `<operator> i  ]` --- "inner block of ]": operate on block 
  * `ci[`           --- change text with in []
  * `vi]`           --- select text within [] in visual mode
* `<operator>  i  w` --- "inner word": operate on word
  * `viw`           --- select word under cursor in visual mode
  * `diw`           --- delete word under cursor
  * `yiw`           --- yank word under cursor
* `<operator>  i  W` --- "inner WORD": operate on delimited WORD 
  * `ciW`           --- change delimited WORD under cursor
* `<operator>  i  s` --- "inner sentence": operate on sentence 
  * `yis`           --- yank sentence under cursor
* `<operator>  i  {` --- "inner block of {": operate on block 
  * `ci}`           --- change text with in {}
* `<operator>  i  >` --- "inner block of >": operate on block 
  * `di<`           --- delete text inside <>
* `<operator>  i  (` --- "inner block of (": operate on block 
  * `yi)`           --- yank text inside ()
* `<operator>  i  "` --- "inner quote": operate on quote
  * `yi"`           --- yank text between quotes 
  * `ci"`           --- change text between the quotes
* `<operator>  i  '` --- "inner quote": operate on quote
  * `yi'`           --- yank the text between single quotes 
  * `di"`           --- delete the text between quotes 
* `<operator>  i  t` --- "inner tag": operate on tag
  * `dit`           --- delete text within the tag
  * `vit`           --- select text within tag in visual mode
* `<operator>  i  p` --- "inner paragraph": operate on contiguous text
  * `=ip`           --- auto-indent contiguous text right
  * `>ip`           --- shift contiguous text right
  
<br>

#### All attribute 
* The **all** `a` attribute, like **inner** `i`, applies operator to<br>
  text in the object *BUT* it *ALSO* applies to the boundary<br>
  that defines the text object: `a` = **object + boundary**

* Below are a few examples of `a` (**all**) applications, for more<br>
  examples see **Inner attribute** in section above & just swap `i`<br>
  with `a` in the examples to switch applications from **inner** to<br>
  **all** -- results will include text boundaries that `i` ignores<br>

* `<operator>  a  ]` --- "all block of ]": operate on block 
  * `ca[`           --- change text **&** enclosing []
* `<operator>  a  '` --- "all single quote": operate on single quote
  * `ya'`           --- yank text **&** the enclosing single quotes 
* `<operator>  a  "` --- "all quote": operate on quote
  * `di"`           --- delete text **&** enclosing quotes
* `<operator>  a  ]` --- "all block of ]": operate on block 
  * `va[`           --- select text **&** enclosing [] in visual mode
* `<operator>  a  (` --- "all block of (": operate on block 
  * `ya)`           --- yank text **&** enclosing ()
* `<operator>  a  p` --- "all paragraph": contiguous text + line
  * `=ap`          --- auto-indent contiguous text **&** line (para)
  * `>ap`          --- shift contiguous text **&** line (para) right
  * `vap`          --- select contiguous text **&** line in visual mode

<br>

### Search
* `*`              --- cycle through other instances of word forward
* `#`              --- cycle through other instances of word backward
* `n`              --- jump to next instance in search
* `N`              --- jump to previous instance in search
* `g*`             --- matches that are not a whole word
  * *use `n`/`N` to cycle as `g*` cycle leads to search pattern change*
* `/string`        --- search for string 
  * `?string`      --- search (backward) for string
* `/string\c`      --- search for string (ignore case)
  * `?string\c`      --- search (backward) for string (ignore case)

<br>

* `f<char>`        --- find **char** in line
  * `F<char>`        --- backward find **char** in line
* `t<char>`        --- find up-to **char** in line
  * `T<char>`        --- backward find up-to **char** in line
* `,`              --- jump to next instance in **char** in line
* `;`              --- jump to previous instance in **char** in line

<br>

### Registers
* `"<reg>`         --- invokes specified register **reg** 
* Registers can be combined with delete, copy & paste 
  * In fact, `d`, `y`, & `p` use the unnamed register `"` by default
     * `""`             --- invokes unnamed/default register `"` 
  * `"ayy`           ---  copies line to register 'a'
  * `"wp`            ---  pastes from register 'w'
  * `"ddd`           ---  deletes & copies line to register 'd'
  * `"2p`            ---  pastes from register '2'

<br>

* There are doezns of registers *(see* `:help registers` *for details)*
  * `""`             --- default/unnamed register
  * `"a`-`"z`        --- "normal" registers
  * `"A`-`"Z`        --- these append to existing register content 
  * `"0`             --- contains last yanked line
  * `"1`-`"9`        --- stacked registers of last 9 line(s) deletions 
     * each reg on stack can have multiple lines from a line(s) `d`
  * `"-`             --- contains last deleted string from a line
  * `"/`             --- contains last search pattern
  * `".`             --- last insert text register
  * `"%`             --- contains name of current file
  * `":`             --- contains most recent executed command
  * `"_`             --- black hole register - shreds whatever goes in 
     * `_4dd`            --- the 4 deleted lines aren't in any register
  * `"#`             --- alternative buffer register
  * `"=`             --- expression register
  * `"+`             --- main system clipboard register
     * `"*`             --- alternative system clipboard register
     * `"~`             --- alternative system clipboard register

<br>

### Folding
* `zf<area>`       --- folds specified **area**
  * `zf7j`           --- folds to 7 lines down from current
  * `zf42k`          --- folds to 42 lines up from current
  * `zfi{`           --- folds lines encapsulated by specified `{}`
  * `zfa{`           --- folds lines encapsulated by specified `{}`
* `zo`             --- opens a fold
* `zc`             --- refolds an opened fold
* `zR`             --- opens all folds
* `zM`             --- closes all folds

<br>

---------------------------------------------------------------------

<br>

<a id="Insert mode"></a>

# Insert mode

`insert` mode is straight forward, its where you type. In `insert`<br>
mode you can backspace, delete, & move around with arrow keys,<br>
like you normally would in regular editors. Of course, this wouldn't<br>
be Vim if there weren't a lot more options with `insert` mode -- some<br>
of the most critical and/or popular ones are in this section.<br>

<br>

* Entering **Normal mode** from **Insert mode** (*exit* `insert` mode)
* `ESC` | `^{`     --- entering `normal` mode 
* `^c`             --- entering `normal` mode
  * *There are some differences between `ESC` & `^c` in some cases*
     * *Example: `ESC` is used for multi-line edit in `visual block`* 

<br>

* Entering **Insert mode**
  * `i`              --- insert before cursor
  * `I`              --- insert before line
  * `a`              --- append after cursor
  * `A`              --- append after line
  * `o`              --- open new  line under current
  * `O`              --- open new  line above current

<br>

* `^r <register>`  --- inserts contents from specified register
  * `^r q`           --- insert contents from resister `q`
  * `^r a`           --- insert contents from resister `a`

<br>

* There are doezns of registers *(see* `:help registers` *for details)*
  * `""`             --- default/unnamed register
  * `"a`-`"z`        --- "normal" registers
  * `"A`-`"Z`        --- these append to existing register content 
  * `"0`             --- contains last yanked line
  * `"1`-`"9`        --- stacked registers of last 9 line(s) deletions 
     * each reg on stack can have multiple lines from a line(s) `d`
  * `"-`             --- contains last deleted string from a line
  * `"/`             --- contains last search pattern
  * `".`             --- last insert text register
  * `"%`             --- contains name of current file
  * `":`             --- contains most recent executed command
  * `"_`             --- black hole register - shreds whatever goes in 
     * `_4dd`            --- the 4 deleted lines aren't in any register
  * `"#`             --- alternative buffer register
  * `"=`             --- expression register
  * `"+`             --- main system clipboard register
     * `"*`             --- alternative system clipboard register
     * `"~`             --- alternative system clipboard register

<br>

* `^r= <expr>`     --- inserts the evaluation from specified expression
  * `^r= sqrt(49)` --- inserts **7.0**
  * `^r= 6+9)`     --- inserts **15**

<br>

### Completion
* `^n` | `^p`      --- word completion
* `^x^l`           --- line completion
* `^x^f`           --- filename completion
* `^x^k`           --- dictionary
* `^x^s`           --- spelling
* `^x^t`           --- thesaurus

<br>

* `^x`             --- *context aware mode* - very useful to learn/use
  * line completion is an example of `^x` mode
     * `^x^l`         --- line completion
  * word completion also comes from `^x` mode
     * `^x^n`         --- word completion
     * `^x^n`         --- word completion

<br>

* Completion menu navigation (hold `Ctrl` until confirm/cancel)
  * `n`              --- next
  * `p`              --- previous
  * `y`              --- confirm
  * `n`              --- cancel

<br>

### Deletion
* `^w`             --- delete word before cursor
* `^u`             --- delete line before cursor

<br>

### Indentation
* `^t`             --- increase line indent by shiftwidth
* `^d`             --- decrease line indent by shiftwidth

<br>

---------------------------------------------------------------------

<br>

<a id="Visual mode"></a>

# Visual mode

`visual` mode is essentially text selection. Being that it is Vim,<br>
the selection comes with many useful options/tools. `visual` mode<br>
is entered from `normal` mode & you always exit to `normal` mode<br>
when any operations are completed on a selection (or if you simply<br>
exit the `visual` mode.)

<br>

* Entering **Visual mode** (always from **Normal mode**)
  * `v`              --- `visual` mode at cursor
  * `V`              --- `visual` mode at line (AKA `visual` line mode)
  * `^v`             --- `visual` block mode
     * Use `h` `j` `k` `l` to set area of block
     * *Can use other motions to set area of block*
         * `^v $`           --- RHS of `visual` block to end of lines
* `gv`             --- go to & re-select last `visual mode` selection

<br>

* Exiting **Visual mode**
  * `ESC` | `^{`     --- entering `normal` mode 
  * `^c`             --- entering `normal` mode
     * *Some differences between `ESC` & `^c` in some cases*
         * *`ESC` is used for multi-line edit in `visual block`*<br>
           *(See below)*
<br>

* **Multi-line edit *from* `visual` block mode:**
  * Multi-line edits are possible using `visual block` mode
  * From block enter `insert` mode with `I` or `A` ( or `c`,`s` ...)
     * `ESC` enters `normal` mode, applying changes to selection
     * `^C` enters `normal` mode, applying changes ONLY to line
  * Useful:
     * In `visual` block mode hit `$` (end of text line), hit `A`
         * EASY multi-line append! 
  
<br>

* `o`              --- toggles between beginning & end of selection
* `O`              --- like `o` but moves horizontal in `visual` block

<br>

* Selections can be:
  * `y`            --- yanked/copied
  * `d`            --- deleted
  * `c` | `s`      --- changed (delete + enter `insert` mode)
  * `~`            --- change case
  * ...etc...
* Once an operation is done on a selection Vim enters `normal` mode.

<br>

---------------------------------------------------------------------

<br>

<a id="Command mode"></a>

# Command mode

`command` mode, ironically, is the simplest to understand. You simply<br>
type out the commands & hit `Enter`, that's it. What makes `command`<br>
mode daunting is the sheer number of commands available to you! There<br>
is no need to memorize every or even most of the commands or even go<br>
out of you way to learn any -- just learn as you need them & that's<br>
more than enough. In this sections we have some essential ones &<br>
they should be MORE than enough to start (actually, even to continue!)<br>

<br>

* Entering **Command mode**
  * `:`              --- entering `command` mode
     * `^d`             --- shows available options
     * `<tab>`          --- cycles through options

<br>

* `:reg`         --- shows contents of different *registers*
  * First column shows *type* of content in the corresponding register
     * `c`            – characterwise text
     * `l`            – linewise text
     * `b`            – blockwise text
  * Second column shows the *name* of the register
  * Third column shows the actual content of the register
     * **NOTE**: *End-of-line is marked by* **^J**
* `:reg "<reg>`  --- shows contents of specified register **reg**
  * *typically also shows contents of the unnamed/default register `""`*

<br>

* `:q!`          --- quit/close without saving
* `:wq`          --- write/save any changes & quit/close
* `:w`           --- write/save any changes to file
* `:w <newFile>` --- write current buffer to *newFile*
* `:w! <fileName>`  --- write current buffer to *fileName*
  * This *OVERWRITES* the *fileName* with current buffer/file

<br>

* `:e <file>`    --- opens *file* buffer/file
* `:badd <file>` --- opens *file* buffer without switching to it
* `:vs <file>`   --- opens *file* buffer/file in window (vertical)
* `:sp <file>`   --- opens *file* buffer/file in window (horizontal)
* `:vs`          --- split current buffer/file vertically
* `:sp`          --- split current buffer/file horizontally

<br>

* Multiple files can be opened in vim
  * You can edit any opened file/buffer, in any tab or window(split)
* `:bn`          --- go to next buffer/file
* `:bN`          --- go to previous  buffer/file
* `:bd`          --- close buffer
  * *Buffers are not lost when switched out unless explicitly closed*<br>
    *OR unless you fully quit Vim (all tabs & windows)*

<br>

* `:tabnew`      --- open a new tab with an empty buffer/file
* `:tabn`        --- next tab
* `:tabp`        --- previous tab
* `:tabc`        --- close tab
* `:tabs`        --- shows the contents (windows) of all tab pages

<br>

* `:r <file>`    --- reads *file* & inserts it *after* current line 

<br>

* `:set nu`        --- enables line numbers
  * `:set nonu`      --- disables line numbers
* `:set hls`       --- enables search highlighting
  * `:set nohls`     --- disables search highlighting
* `:set rnu`       --- enables *RELATIVE* line numbers
  * `:set nornu`     --- disables *RELATIVE* line numbers

<br>

* Some other important/useful options, that should really be placed<br>
  in a `.vimrc` configuration file, but you can set these setting<br>
  manually in `command` mode<br>
  * `:set showcmd`               --- shows state/cmd inputs-*IMPORTANT*
  * `:set showmode`              --- shows the current mode-*IMPORTANT*
  * `:syntax on`                 --- enables syntax detection
  * `:filetype plugin indent on` --- file detection & indentation
  * `:set colorcolumn=n`         --- sets a color column at n
  * `:set ruler`                 --- shows cursor place in file/buffer

* There are many options for tabulation -- again, these should really<br>
  be placed in configuration `.vimrc` file, but but you can set these<br>
  setting manually in `command` mode<br>
  * `:set expandtap` --- inserts spaces for tab
  * `:set ts=n`      --- `tabstop` *is tab size*, `n` is value
  * `:set sw=n`      --- `shiftwidth` *is indentation*, `n` is value
  * to get spaces for tab --- `sts` = `sw` & expandtab is set
     * *You don't need to set `sts` (softtabstop), BUT, if you*<br>
       *set `sts` then it MUST = `sw` (if you want spaces)*
  * `:set autoindent` --- enables auto indentation
  * `:set smartindent` --- will try to follow syntax of code 

* **NOTE**: *You don't need to be an advanced user to utilize a .vimrc*<br>
  *file. Just place the setting/commands in the file (one per line) &*<br>
  *Vim will execute them all every time Vim starts -- its that simple!*<br>
  *For linux users the .vimrc file should be in the home directory, for*<br>
  *windows & Mac see `:help vimrc`*

<br>

* `:help command_name` | `:h command_name`
  * Gives documentation of commands & options specified
     * REALLY the best way to learn more Vim functionality 
     * In fact, it is the organic way to learn as you use Vim
         * *better than memorizing things you'll forget anyway*
     * Its practical: learn about what you need or want to use
         * *How ALL learning should be!*
  * Don't be intimidated by documentation here -- it's to help YOU
     * Just skim to the answer you want (can search with /)
     * Look at additional info around answer (if interesting)

<br>

### Basic find & replace
* Boilerplate for finding & replacing first occurrence in line

   > `:s/find/replace/`

* Boilerplate for finding & replacing every occurrence in line

   > `:s/find/replace/g`

  * Use `\c` to `find` for *ignore case* 

     > `:s/find\c/replace/g`

  * The *ignore case* is preferable over *ignore flag* (below) as<br>
    it works well with hls (as you type the command)<br>

     > `:set hls --- to enable search highlighting`

  * Add `i` flag to ignore case for `find`

     > `:s/find/replace/gi`
   
* With `visual block` mode, the above find-and-replace<br>
  commands can be applied to selected lines

   > `:'<,'>s/find/replace/g`

  * Add `\c` to `find` for *ignore case* 

     > `:'<,'>s/find\c/replace/g`

* Boilerplate for finding & replacing every occurrence in file
                  
   > `:%s/find/replace/g`

  * Add `\c` to `find` for *ignore case* 

     > `:%s/find\c/replace/g`

* You can find-replace with confirmation by adding `c` flag -- this<br>
  is *VERY* handy!
* Boilerplate replacing every occurrence in file *WITH* confirmation

   > `:%s/find/replace/gc`

* **NOTE:** *Its a good idea to have hls (search highlighting) on* with<br>
  *find-replace or even just regular searching (`:set hls`) -- much*<br>
  *better for work flow (& sanity). You can always turn hls off*<br>
  *with `:set nohls`*<br>

<br>

### File explorer (netrw)
* Vim has a built-in file explorer called *netrw*
  * You can launch it in terminal by opening a directory in vim
     * `vim DIR`        --- launches `DIR` in  *netrw*
  * You can launch it within Vim with
     * `:Exp`         --- opens *netrw*
         * `:Exp DIR`    --- opens *netrw* in specified `DIR`
     * `:Hex`         --- opens *netrw* (horizontal split)
         * `:Hex DIR`    --- opens *netrw* split in specified `DIR`
     * `:Vex`         --- opens *netrw* (vertical split)
         * `:Vex DIR`    --- opens *netrw* split in specified `DIR`
     * `:Tex`         --- opens *netrw* in a new tab
         * `:Tex DIR`    --- opens a *netrw* tab in specified `DIR`

  * The *best* way to use *netrw* is to toggle it with `:Lex`
     * `:Lex`          --- opens current path in a window of *netrw*
     * `:Lex`          --- *also* **closes** the *netrw* window
     * `:Lex DIR`      --- opens specified `DIR` in *netrw*
     * It becomes better for work flow when you map<br>
       a key(s) to `:Lex`
         * *Now, same key(s) can toggle Lex* **open** *and* **close**!

  * The window can be resized (like any window)
     * `:vertical resize n` --- resizes window to size n
  * `^w w`           --- switch to/from a netrw window (like any window)

* Basic navigation
  * `h`              --- move left move
  * `j`              --- move down
  * `k`              --- move up
  * `l`              --- move right
  * `Enter`          --- enter a directory or open file
* `%`              --- create file 
* `d`              --- create directory 
* `R`              --- rename file or directory
* `r`              --- reverse file/directory list
* `D`              --- delete file or directory

<br>

### Customization & mappings commands (Advanced)
You don't need to have advanced knowledge of Vim to utilize a<br>
`.vimrc` file. In fact, you should have a `.vimrc` file, even if it is<br>
empty, with in the first few days of using vim -- this way you can<br>
start placing in it the configurations & commands that you find<br>
yourself typing in most frequently. Once you have used Vim for a<br>
bit you can configure it to your needs/liking -- you can set themes,<br>
tab size/type, ruler, column, etc...<br>

**NOTE**: *You shouldn't overwhelm yourself & try to learn all tools &*<br>
*options of Vim -- but once you have had enough experience & are*<br>
*comfortable with what you have already learned (& are using it)*<br>
*then you can learn a bit more (and repeat this learning cycle.)*<br>

One of the things you should DEFINITELY utilize as soon as you are<br>
comfortable to is the mapping/remapping of commands<br>

* This enables you to execute commands from other modes without<br>
  having to go into command mode & typing out commands
* This also allows for combining and/or remapping of existing<br>
  commands to your convenience 
  * For example: we can remap `<Ctrl-d>` so that it not only<br>
    moves down 1/2 a page but also centers it. *How?* We know<br>
    that `<Ctrl-d>` scrolls down 1/2 a page *and* we know that<br>
    `zz` centers the page to the line with the cursor, so we<br> 
    just need to combine the two commands AND remap them<br>
    to `<Crtl-d>` like this:

      > `nnoremap <C-d> <C-d>zz`

     Now, `<Ctrl-d>` scrolls down while centered! :)

     *Remap for centered scroll* **up** (`<Ctrl-u>`):

      > `nnoremap <C-u> <C-u>zz`


* Commands can be mapped to key(s) in `normal` mode by `<cr>`<br>
  `<cr>`, also known us carriage-return, is `Enter` 

   > `map/remap key(s) :command<cr>`

  The specified key(s) executes command from `normal` mode 

* Combine different commands & map them to key(s) `<cr>`

   > `map/remap key(s) :cmd1<cr>:cmd2<cr>:cmd3<cr>`

  This combines 3 commands to a key(s) in `normal` mode 

<br>

* **NOTE:** *ALWAYS use non-recursive remapping* 
  * *Do a bit of research into mappings -- they are not hard at all*<br>
    *but there can be subtleties...*

<br>

* You can also write functions & map their execution to keys!
  * Again, this is not hard & just requires experience -- let<br>
    your learning be organic & learn something new when you<br>
    *need* or *want* to use it!!
  * Here is a  simple function for toggling highlight search on/off<br>
    & it is mapped to the `<F2>` key:

     > `map <F2> :call ToggleHLS() <cr>`

    *The actual function*:


                  function ToggleHLS()
                      if (&hls == 1)
                          set nohls
                      else
                          set hls
                      endif
                  endfunction

  * **NOTE**: *Function names should start with a capital letter* <br>


----------------------------------------------------------------------

* *The HTML version of Vim Help docs*<br>

   >  <https://vimhelp.org/>

* *This Japan based (English language) Vim help doc is easy on*<br>
  *the eyes with an intuitive light-theme color pallets*<br>

   > <https://vim-jp.org/vimdoc-en/>

<br>

***FINAL NOTE***: *The Vim help docs are invaluable but some may find it*<br>
*easier to get a quick answer from a simple search-engine search, while*<br>
*others may prefer a short video to quickly solve their issue -- so use*<br>
*whatever works for you! Just keep in mind that official documentation*<br>
*has little substitute if one wants proficiency at some tool. A good*<br>
*habit to develop is to take the answer/solution you get from anywhere*<br>
*& compare it to official docs while looking for more details &*<br>
*reasonable tangents in the docs -- this helps you fully understand what*<br>
*you are implementing and opens you up to more/better options!*<br>
