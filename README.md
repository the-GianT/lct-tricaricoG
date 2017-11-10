# lct-tricaricoG
last class today for 2017-11-08, to be added to the main one for pd. 5

## Wednesday, 2017-11-08 Sending mixed signals by Gian "Giant" Tricarico

**Tech News:** [Waymo's Autonomous Cars Cut Out Human Drivers in Road Tests](https://nyti.ms/2hP9QVh)

Signals are a limited way of sending information to a process in the form of an integer value. `kill` is the command line utility to send a signal to a process:

	$ kill <PID>

The default action for `kill` is to send the signal SIGTERM (defined as the integer 15) to PID. You can use a flag to send different a different signal instead:

    $ kill [-<SIGNAL>] <PROCESS>

e.g.