ubuntu@ip-172-31-0-235:~$ touch notes.txt
ubuntu@ip-172-31-0-235:~$ echo "this is line 1"> notes.txt
ubuntu@ip-172-31-0-235:~$ echo "this is line 2 ">> notes.txt
ubuntu@ip-172-31-0-235:~$ echo "this is line 3"|tee -a notes.txt
this is line 3
ubuntu@ip-172-31-0-235:~$ cat notes.txt
this is line 1
this is line 2 
this is line 3
ubuntu@ip-172-31-0-235:~$ head -n 2 notes.txt
this is line 1
this is line 2 
ubuntu@ip-172-31-0-235:~$ tail -n 2 notes.txt
this is line 2 
this is line 3



very simple exercise for day 6

created a new file named notes.txt using touch command
then, added text to the file using echo and also, used tee to write as well as view the output simultaneously
then using cat, head and tail saw the contents of the file
