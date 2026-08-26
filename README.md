# L

The first program I wrote. Rebuilt properly.

It saved whatever the last command printed into a variable called `$L`, so I could hand
it straight to the next command instead of retyping it. This is that same idea as a real
variable in your real shell — not a separate program you have to enter and exit.

```
$ source L
$ L curl -s ifconfig.me
203.0.113.42
$ echo my IP is $L
my IP is 203.0.113.42

$ L ls
one.txt
two words.txt
three.txt
$ touch $L                 # zsh splices every item as its own word
$ touch "${L[@]}"          # same thing in bash
```

## Install

Bash. Add it to your `.bashrc` (or `.zshrc`):

```bash
git clone https://github.com/ZaidMarwat/L
echo "source $PWD/L/L" >> ~/.bashrc
```

## Use

Prefix anything you want to remember with `L`. It runs for real, its output prints
normally and in real time, and gets captured into `$L` — a real array, one element per
line of output. From then on, `$L` is just an ordinary shell variable, no special handling
needed to use it — how far "ordinary" gets you depends on the shell:

- **zsh:** bare `$L` splices every element in as its own word, so `touch $L` after `L ls`
  touches every listed file, one argument each — even a filename with spaces in it stays
  one argument, since each array element is a whole line, never re-split.
- **bash:** bare `$L` only gives the first element (that's just how bash arrays work).
  Use `"${L[@]}"` for the same all-elements behavior zsh gives you for free.
- A single-line result behaves the same either way — `echo my IP is $L` works in both.

Other details:

- Output is never altered or annotated — what you see is exactly what the command printed.
- Your own aliases work through `L` (`L ll`, `L gs`, ...) the same way they do through
  `sudo` or `time` — it's a real alias under the hood, not a function, specifically so this
  composes instead of shadowing your setup.
- Empty output never overwrites `$L` — the last real value sticks around.
- No length cap — a line is a line, however long it is.
- Exit status passes through untouched, so `L some-check && echo ok` works as expected.

## Why

Explained on [zaidmarwat.com](https://zaidmarwat.com).
