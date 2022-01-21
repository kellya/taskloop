Introduction
============

I use [Taskwarrior](http://taskwarrior.org/) to manage my tasks.  I also use the Getting Things Done (GTD) system to organize my tasks.  This means it is very common for me to think of a project as a set of many tasks. In order to do that with the standard `task` binary, I would have to continually type out `task add project:myproject` before I get to actually typing out the task.  So I wanted a system where I could just get the project name, and loop through adding tasks to that project until I finished.  I initially wrote this as a simple bash script.

While my bash script (see program listing in :ref:`appendix`) basically accomplished what I wanted, it didn't really do much else and wasn't going to allow me to change things very easily.  I decided that I wanted to rewrite it in Python.
