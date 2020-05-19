# viewing man pages in vim

Vim has a "built-in" functionality of displaying man pages. To activate this, add this to your `.vimrc`
```
runtime ftplugin/man.vim
```
This will load a standard plugin shipped with vim. You are now able to view the man page of a command with the vim command `:Man`. For example, if you want to know what the c functin `sbrk` does, type
```
:Man 2 sbrk
```

If the function is already in the buffer, put the cursor on the function and hit `K` (as in `Shift-k`) to view the manual page of it. This only works on functions without hyphens.
