## Part 1  
Commands:-
1. ``echo`` -> Request Output of any provided text
2. ``whoami`` -> list current logged in user.
3. ``ls`` -> list directory
4. ``cd`` -> Change Directory
5. ``pwd`` -> print working directory
6. ``cat`` -> concatenate
7. ``nano`` -> open file in nano text editor
8. ``find`` -> find files in a directory
9. ``grep`` -> search for specific values within a file

Shell Operators
1. ``&`` -> runs commands in background of terminal
2. ``&&`` -> combines multiple commands together in one line.
3. ``>`` -> redirector; direct the output of one command to another command.
4. ``>>`` -> same as redirector except that the output is appended instead of replacing the output of the other command.

## Part 2
Commands:-  
1. ``man`` -> used to open the manual for particular commands and their uses.
2. ``touch`` -> create a file
3. ``mkdir`` -> create a new directory/folder
4. ``cp`` -> copy
5. ``mv`` -> move
6. ``rm`` -> remove
7. ``file`` -> used to find the type of a file
8. ``su`` -> switch user

Comman Directories:-
1. ``/etc`` -> location of system files used by the OS.
2.  ``/var`` -> stores data accessed or written by applications running on the system.
3.  ``/root`` -> home folder for the root user.
4.  ``/tmp`` -> volatile storage storing data only needed to be accessed once or twice.

## Part 3
Text Editor:-
1. ``Nano`` -> best for beginners like me
2. ``Vim`` -> a sign of professional hackerman. much more feature rich but needs effort to use properly.

Utilities:- 
1. ``wget [file download link]`` -> downloads files
2. Secure Copy (SCP) ->  Used to transfer files to and from host via SSH.
examples: ``scp important.txt ubuntu@192.168.1.30:/home/ubuntu/transferred.txt`` from host to another device  
``scp ubuntu@192.168.1.30:/home/ubuntu/documents.txt notes.txt `` another device to host.

Managing Processes:-
1. ``ps [aux]`` -> provides list of running processes [for all users].
2. ``top`` -> real time stats about the processes and refreshes ever 10 seconds or when arrow buttons are used
3. ``kill`` -> used to kill certain processes based on their PID number.
4. ``systemctl [option] [service]`` -> interact with the systemd process/daemon [start/stop/enable/disable] [a specificed service].
5. ``fg`` -> brings a previously backgrounded process back to the foreground.

Kill Signals:-
1. ``SIGTERM`` -> Kill the process, but allow it to do some cleanup tasks beforehand
2. ``SIGKILL`` ->Kill the process - doesn't do any cleanup after the fact
3. ``SIGSTOP`` -> Stop/suspend a process

Automating Commands:-  
``cron`` jobs are processes scheduled to run to set intervals. ``crontabs`` is used to interact with and manage cron jobs and it starts during boot. (crontab stands for time table)  
Use [[https://crontab-generator.org]] to generate crontabs

Package Management:-  
1. ``add-apt-repository`` -> used to add a particular repository. (apt is a package management software)
2. ``apt-update`` -> updates the repositories. (use sudo for system wide update)
3. ``apt remove [software name]`` -> removes the software.
