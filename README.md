# lct-tricaricoG
last class today for 2017-11-08, to be added to the main one for pd. 5

Wednesday, 2017-11-08 Sending mixed signals by Gian "Giant" Tricarico
====================================================================

**Tech News:** [Waymo's Autonomous Cars Cut Out Human Drivers in Road Tests](https://nyti.ms/2hP9QVh)

Signals are a limited way of sending information to a process in the form of an
integer value. `kill` is the command line utility to send a signal to a process:

	$ kill <PID>

The default action for `kill` is to send the signal SIGTERM (defined as the
integer 15) to PID. You can use flags to send different signals instead:

    $ kill [-<SIGNAL>] <PROCESS>

You can type the signal in the form of its name or its number.

e.g.

	$ kill -2 <PROCESS>

or

	$ kill -SIGINT <PROCESS>

Refer to the man page using `$ man 7 signal` to see a list of all the signals
(It will probably be a different man page actually, unless you're using the same
operating system as I am).

Signal handling in c programs <signal.h>
----------------------------------------

You can use `kill` in your code as well:

    kill(<PID>, <SIGNAL>)

-Returns 0 on success

-Returns -1 and sets errno on failure

### sighandler

To intercept signals in a c program you must create a signal handling function.
Convention is to use the following header:

```C
static void sighandler(int signo)
```

The function must be static and void, and it must take a single int parameter
(in C, `static` means that the function can only be called from within the file
in which it is defined, so if you include the file into another file, this
sighandler will not be used by the other file).

e.g.

```C
static void sighandler(int signo)
{
  if (signo == SIGINT) {
    printf("I've been interrupted, how rude!");
  }
}
```

This overrides the default action for that signal, meaning that it does not
exit the process anymore unless you specify as such by calling the exit
function within the if statement, e.g. `exit(1)`, which exits the program and
makes it return 1 rather than 0.

If you want to set the action for multiple signals, use additional if statements
within the same signal handling funtion rather than creating multiple functions.

Also, in order for the sighandler to take effect, you must call the signal()
function in your main method for each signal you want to intercept. The first
argument is the signal, and the second is your signal handling
function.

e.g.

```C
signal(SIGINT, sighandler);
signal(SIGUSR1, sighandler);
```