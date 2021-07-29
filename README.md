The sysadmin prompt
===================

You have your favourite shell (which is of course fish) throughly configured
and customised.  But despite all your terraforms and ansibles and sshfses, your
job as a sysadmin requires you to ssh-hop between a large number of servers and
VMs to herd dæmons.  And often you're in some service-specific account in the
middle of nowhere with nothing but the default prompt of your distro.

The sysadmin prompt is designed to be a zero-configuration drop-in file that
will run anywhere¹ and give some information which is useful to have on every
line.  Extra information is provided when available, and won't generate errors
when not.  Just source the script at the end of `.bashrc` and you're set.  You
can also call

    source sysadmin_prompt.bash install

and it will append a line on `.bashrc` for you.

Prompt features
===============

![Screenshot](screenshot.png "alacritty, victor mono italic, gruvbox colours")

 - Automatically chosen but deterministic colours for user- and hostnames,
   making changes in environment more noticeable;
 - user@hostname always present, with root shells always in red (including
   root aliases like BSD `toor`);
 - Whether the shell runs over ssh (detection works even under sudo);
 - Basic virtual machine detection;
 - Exit status of last command;
 - Time elapsed for last command (seconds resolution, not counting time at
   prompt);
 - How many jobs are hanging in background of this shell;
 - Whole rest of line for current path;
 - Including, if the standard git prompt bash function is found, git
   information;
 - A newline for clarity;
 - A continuation character and the standard shell prompt character, always in
   the same screen position, and highlighted for root sheels.

TODO
====
Light background mode.

Notes
=====

[1] "anywhere": currently this is only tested on recent-ish Linux+bash combos
(ca. 2017 onwards), and works best with at least a few POSIX tools around.
No GNU dependencies.  Pull requests for portability will be accepted, including
for older bash versions, but this project isn't meant for POSIX sh or zsh or
other shells (if you can run better shells, by which I mean fish, it's probably
a host you can configure freely, right?).  Contributors please take care with
performance hits on the prompt_command function.
