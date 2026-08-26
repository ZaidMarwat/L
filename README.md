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
```

## Install

Bash. Add it to your `.bashrc` (or `.zshrc`):

```bash
git clone https://github.com/ZaidMarwat/L
echo "source $PWD/L/L" >> ~/.bashrc
```

## Use

Prefix anything you want to remember with `L`. It runs for real, its output prints
normally and in real time, and gets captured into `$L`. From then on, `$L` is just an
ordinary shell variable — reference it in any command and your shell expands it natively,
no special handling needed.

- Output is never altered or annotated — what you see is exactly what the command printed.
- Your own aliases work through `L` (`L ll`, `L gs`, ...) the same way they do through
  `sudo` or `time` — it's a real alias under the hood, not a function, specifically so this
  composes instead of shadowing your setup.
- Empty output never overwrites `$L` — the last real value sticks around.
- `$L` is capped at 220 characters, matching the very first version of this trick.
- Exit status passes through untouched, so `L some-check && echo ok` works as expected.

## Why

Explained on [zaidmarwat.com](https://zaidmarwat.com).
