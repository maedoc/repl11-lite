### repl11

A small repl-through-pipes utility. You run it

```bash
$ repl11
```

and it creates a few files

```bash
$ ls -a
.   r11		    repl11-5027.log  .repl11-out.fifo  .repl11.swp
..  .README.md.swp  .repl11-in.fifo  repl11
```

including one `r11` which pipes it's stdin to a Python process which evaluates
it and writes result to stdout in comments,

```bash
$ ./r11 <<EOF
print 42
EOF
print 42
# 42
```

which is suitable for filtering when writing your Python code in Vim, e.g.

```vim
map <F9> mtvip<F9>`t
vnoremap <F9> :!./r11<CR>
map <F10> <F9>))
imap <F9> <ESC><F9>a
```

or other similar unixy editors.

Of course you want to stop the repl process when you're done, which
cleans everything up.

```
$ ./r11 quit
$ ls -a
.  ..  README.md  .README.md.swp  repl11  .repl11.swp
```
