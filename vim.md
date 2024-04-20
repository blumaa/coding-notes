## VIM

`_` goes to the beginning

`$`goes to the end

`0`goes to the beginning character (0 character)

`d$` move from your cursor to the end

`f(` forward to the character (in this case parenthisis), use `f`+`;`to go to character and repeat it

`F(`back to the character

`t(` until just before the character

`T(`back until the just before character

`,`backward

`;`forward

`dt(`delete up to open parenthesis

Search and replace:

1. Execute a regular search with `/`.
2. Use the keystroke `cgn` on the first result to replace it.
3. Type `n` or `N` to go to the next result.
4. Use `.` to replace the occurrence with the same replacement, or go to the next result if you want to keep it.

What’s this `cgn` keystroke, you may ask? What does it mean? If you read `:help gn`, you’ll see that `gn` is the same as `n`, except that it will start Visual mode and select the occurrence. We just do a change (`c`) on the next (selected) searched occurrence. From there, you can imagine that keystrokes like `cgN` or `dgn` will work as well.

## vim-surround

In Normal mode, on an empty line, I type ysst, followed by the name of my tag (e.g. "div"), then Enter.

In Insert mode I type Ctrl+s, then t, then the name of my tag, then Enter.

These are the default vim-surround keybinds, and they're the same for any other "surround", the only difference is instead of typing ")" or "}" you type "t", then the tag name, then Enter.

Btw when you're typing the tag name, you can add other stuff and it'll work as expected. For example, you can add html attributes and they won't be added to the closing tag. Or you can put a slash "/" at the end, and it'll correctly interpret that as a self-closing tag.

`csw"`- vim-surround, surround current word with quotes

`ysiw"`- vim-surround, surround current word with quotes

`ctl-v` then go down or up, it will select the current character vertically. Then press `$A`to insert at the end and replace everything - https://vimtricks.com/p/edit-multiple-lines-at-once-in-vim/

normal mode H toggles dotfiles

normal mode I toggles gitignore

`ctl z` exit vim with saving terminal

`fg` resume vim with same windows

`zz` center vim at your cursor

`vap` visual cmd around paragraph

`vi{` delete within squirrely

`gv` previous highlight


---

### vim macros

1. `qw` start recording at register of w
2. add something / perform action
3. go to next line
4. press escape
5. `number@w` pastes what is recorded in register of w four times/lines

---

### multi line insert

You can also use ctrl + v to highlight the first character of each line and then do shift + i.

---

### search and replace

```
:vimgrep /word/ `find . -type f`
```

Use vimgrep to find the word. find in this directory of type file and add to quick fix list

- `:copen` - open quick fix list


Go through every instance and check whether to change it - g = global, c = interactive check
```
:cdo %s/word/words/gc
```

