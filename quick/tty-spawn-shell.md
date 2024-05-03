# TTY Spawn Shell

Often during pen tests you may obtain a shell without having tty, yet wish to interact further with the system. Here are some commands which will allow you to spawn a tty shell. Obviously some of this will depend on the system environment and installed packages.

### Fully Interactive TTY

**Step 1:**

```bash
python -c 'import pty; pty.spawn("/bin/bash")'
```

```bash
python3 -c 'import pty; pty.spawn("/bin/bash")'
```

Which uses Python to spawn a better-featured bash shell. At this point, our shell will look a bit prettier, but we still won’t be able to use tab autocomplete or the arrow keys.

**Step 2:**

```bash
export TERM=xterm
```

This will give us access to term commands such as `clear`.

**Step 3:**

Finally (and most importantly) we will background the shell using: <mark style="color:orange;">`CTRL + Z`</mark>

Back in our own terminal we use:

```bash
stty raw -echo; fg
```

This does two things: first, it turns off our own terminal echo which gives us access to tab autocompletes, the arrow keys, and Ctrl + C to kill processes.

```bash
stty rows 38 columns 116
```

### OS system spawn shell

```bash
echo os.system("/bin/bash")
```

### Bash spawn shell

```bash
/bin/sh -i
```

### Perl spawn shell

```bash
perl —e 'exec "/bin/sh";'
```

### Ruby spawn shell

```bash
ruby: exec "/bin/sh"
```

### Lua spawn shell

```bash
lua: os.execute("/bin/sh")
```

### IRB spawn shell

```bash
exec "/bin/sh"
```

### VI spawn shell - 1

```bash
:!bash
```

### VI spawn shell - 2

```bash
:set shell=/bin/bash:shell
```

### Nmap spawn shell

```bash
!sh
```
