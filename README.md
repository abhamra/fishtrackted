A fishy version of [distrackted](https://github.com/PeterFidelman/distracked/tree/master) by Peter Fidelman with the intentional design quirk of storing all the stacks in a single `~/.fishtrackted` file, instead of using a directory and a file for each stack. Used to learn a bit of `awk` and `sed`, mostly.

```
$ ./ft help
--- Fishtrackted ---
usage: ./ft [subcmd]

all:    display erythang
cat:    display contents of current stack
edit:   open all stacks in editor for bulk mod
head:   display top of current stack
heads:  display tops of all stacks
help:   print this message
ls:     list all stacks
pop:    remove top of stack
push:   add to top of stack
rm:     remove a given stack
switch: switch to diff stack, or create if doesn't exist
```

As with `dt`, `ft` starts with an empty stack. You can list all your stacks with `ls` or list the contents of the current stack with `cat`.
```
$ ./ft ls
Creating $YOUR_HOME/.fishtrackted for your stacks!
stacks:
---
1: main

$ ./ft cat
(*) == main == {
}
```

Add things to the stack with `push` and `pop` them once you're done!
```
$ ./ft push Write fishtrackted README
$ ./ft push Finish fishtrackted blog post
$ ./ft cat
(*) == main == {
- Finish fishtrackted blog post
- Write fishtrackted README
}

$ ./ft pop
$ ./ft cat
(*) == main == {
- Write fishtrackted README
}
```

The task below the stack's name is the head of the stack, and the items go down in order from there.

Use `./ft` or `./ft head` to see the head of the currently selected stack.
```
$ ./ft
main - Write fishtrackted README
```

If you need to context-switch, you can make a new stack with `./ft switch <new-stack>`. Use `./ft all` to see all stacks and elements!
```
$ ./ft switch second stack
Creating stack 'second stack'
$ ./ft all
== main == {
- Write fishtrackted README
}
(*) == second stack == {
}
```

You can then push and pop as usual. Use `./ft heads` to see the head of every stack!
```
$ ./ft push Graduate!
== main == {
- Write fishtrackted README
}
(*) == second stack == {
- Graduate!
}

$ ./ft heads
heads of all stacks:
---
main - Write fishtrackted README
second - Graduate!
```

Use `./ft rm <stack>` to delete a stack of your choice:
```
$ ./ft rm second stack
$ ./ft all
(*) == main == {
- Write fishtrackted README
}
```

If you want to edit all your stacks at once, simply use `./ft edit` to open the `~/.fishtrackted` file with your `$EDITOR`.

Enjoy!
