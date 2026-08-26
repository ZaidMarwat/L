# L

The first program I wrote. Rebuilt properly.

It saved whatever the last command printed into a variable called `$L`, so I could hand
it straight to the next command instead of retyping it. This is that same idea as a
small, real REPL.

```
$ ./L
L -- type a command. $L holds whatever the last one printed.
exit or Ctrl-D to leave.

L> curl -s ifconfig.me
203.0.113.42
L> echo my IP is $L
$L -> echo my IP is 203.0.113.42
my IP is 203.0.113.42
```

## Install

Bash and Perl. Both ship on macOS and virtually every Linux box.

```bash
git clone https://github.com/ZaidMarwat/L && cd L
./L
```

## Use

Type any real shell command. It runs for real, its output prints normally, and gets
captured into `$L`. Reference `$L` in your next line and it's substituted in before
that line runs.

- Empty output never overwrites `$L` — the last real value sticks around.
- `$L` is capped at 220 characters, matching the very first version of this trick.
- `$L` only expands as a whole word, so `$Lorem` is left alone.
- `exit` or Ctrl-D leaves.

## Why

Explained on [zaidmarwat.com](https://zaidmarwat.com).
