# Vim Navigation and Text Manipulation: Essential Shortcuts for Efficiency

So far we've learned about vim editor's basics, modes, and how to exit and save files. You now know how to create a file, add basic text, manipulate it a bit, and save your work. 

Now it's time to supercharge your vim skills! Learning vim shortcuts will make you significantly more efficient. We'll cover navigation shortcuts, deletion, cutting (yanking), pasting (putting), and text transformation. These commands will transform how you work with text.

**Quick Note:** There are many more powerful shortcuts available than what's covered in this document. Think of this as your foundation - a way to understand what's possible with vim and inspire further exploration. I've included a comprehensive cheat sheet I found at the end for your reference.

**Pro Tip:** Once you master these basics, you can unlock even more power by learning **operators**, **text objects**, and **macros** - which we'll cover in future articles. These concepts will help you combine commands in powerful ways!

## Navigation: Moving Around Like a Pro

Remember, THese navigation commands work in **Normal mode** (press `Esc` to get there). One of vim's greatest strengths is that you can navigate without moving your hands from our normal typing position.

### Basic Movement (The Foundation)
```
h - move left     (think: h is on the left)
j - move down     (think: j points down)
k - move up       (think: k points up) 
l - move right    (think: l is on the right)
```
```
Navigation Map:
    k (up)
    ↑
h ← • → l
    ↓
  j (down)
```

**Memory trick:** The `hjkl` keys are arranged on your keyboard from left to right, just like the directions they represent!

### Line Navigation
```
0 - jump to start of line (beginning of line = 0)
^ - jump to first non-whitespace character
$ - jump to end of line (think: $ is at the end in shell prompts)
```

### Word Movement
```
w - jump forwards to start of next word
W - jump forwards to start of next WORD (ignores punctuation)
b - move backward word by word (think: b = back)
e - move forward to end of current word (think: e = end)
```

**Example:** If your cursor is on the 'H' in "Hello, world! How are you?":
- `w` moves to the comma `,`
- `W` moves to `world!` 
- `e` moves to the 'o' in "Hello"

### Page and Document Navigation
```
Ctrl + f - page down (think: f = forward)
Ctrl + b - page up (think: b = back)
gg - go to first line of document 
G - go to last line of document
{number}gg or {number}G - go to specific line
```

**Example:** To go to line 25, type: `25gg` or `25G`

## Deletion: Removing Text Efficiently

In **Insert mode**, you use Delete and Backspace as normal. But **Normal mode** offers much more powerful deletion options.

### Basic Deletion
```
x - delete character under cursor (think: x marks the spot to delete)
X - delete character before cursor
```

### Advanced Deletion (The Real Power)
```
dd - delete entire line
dw - delete from cursor to start of next word
d$ - delete from cursor to end of line
d0 - delete from cursor to beginning of line
```

**A way to easily remember:** Notice the pattern? `d` (delete) + movement command!
- `d` + `w` = delete word
- `d` + `$` = delete to end of line
- `d` + `d` = delete whole line

**Practical Example:**
```
Original: "The quick brown fox jumps over the lazy dog"
Cursor on 'b' in "brown"

dw → "The quick fox jumps over the lazy dog"
d$ → "The quick "
dd → (entire line deleted)
```

## Cut (Yanking) and Paste (Putting): Moving Text Around

Vim calls copying "yanking" and pasting "putting" - think of it as yanking text out and putting it somewhere else.

### Yanking (Copying)
```
yy - yank (copy) entire line
yw - yank word from cursor position
y$ - yank from cursor to end of line
```

### Putting (Pasting)
```
p - put (paste) after cursor or below current line depending on what you copied or the place you in.
P - put (paste) before cursor or above current line
```

**Practical Example:**
```
Original text:
Line 1: "Hello World"
Line 2: "Goodbye World"

1. Position cursor on Line 1
2. Type: yy (yanks the line)
3. Move to Line 2
4. Type: p (puts the copied line below)

Result:
Line 1: "Hello World"
Line 2: "Goodbye World" 
Line 3: "Hello World"
```

**Pro Pattern:** Notice that yank commands follow the same pattern as delete:
- `y` + movement = yank that text
- `d` + movement = delete that text

## Text Transformation: Changing and Substituting

### Case Changes
```
~ - toggle case of character under cursor
guu - make entire line lowercase
gUU - make entire line UPPERCASE
```

### Search and Replace
To work with below commands you need to press ":" and go to line mode we discuees in modes.
```
:s/old/new/ - replace first occurrence of 'old' with 'new' on current line
:s/old/new/g - replace all occurrences of 'old' with 'new' on current line
:%s/old/new/g - replace all occurrences in entire file
:%s/old/new/gc - replace all with confirmation prompts
```

**Practical Example:**
```
Original: "This cat in the hat sat on the mat"

:%s/the/a/g

Result: "This cat in a hat sat on a mog"
```
<img width="868" height="235" alt="image" src="https://github.com/user-attachments/assets/65f23b05-6c3b-43d6-9615-9b96bc36a76e" />


### Quick Changes
```
r{char} - replace single character under cursor with {char}
cw - change word (deletes word and enters insert mode)
cc - change entire line
c$ - change from cursor to end of line
```

**Example:**
```
Original: "Hello World"
Cursor on 'W' in "World"

r + M → "Hello Morld"
cw + "Universe" → "Hello Universe"
```

## ASCII Quick Reference

```
Quick short note:
┌─────────────────────────────────────┐
│  Navigation     │  Text Objects     │
├─────────────────┼───────────────────┤
│  h j k l        │  w = word         │
│  0 ^ $          │  $ = line end     │
│  gg G           │  0 = line start   │
│  Ctrl+f Ctrl+b  │  gg G = document  │
└─────────────────┴───────────────────┘

Action Commands Pattern:
[action][count][motion]

Examples:
d2w  = delete 2 words
y3j  = yank 3 lines down  
c$   = change to end of line
```

## Summary and Pro Tips

**Key Patterns to Remember:**
1. **Action + Movement = Power**: Most vim commands combine an action (`d`, `y`, `c`) with a movement (`w`, `$`, `j`)
2. **Double letters often mean "whole line"**: `dd`, `yy`, `cc`
3. **Uppercase usually means "stronger version"**: `W` vs `w`, `P` vs `p`

**Practice Tips:**
- Start with `hjkl` navigation - avoid arrow keys to build muscle memory
- Practice the `d` + movement pattern with different combinations
- Use `:help [command]` in vim to learn more about any command

**Next Steps:** 
Once these commands become second nature, you'll be ready to learn about **operators**, **text objects**, and **macros** - which will multiply your efficiency even further!

Remember: vim has a learning curve, but every shortcut you master saves you countless keystrokes in the future. Start with a few commands, use them daily, then gradually add more to your toolkit. [Here](https://vim.rtorr.com/) is a good cheatsheet I found. 
