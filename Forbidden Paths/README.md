# picoCTF Forbidden Paths

---

author: sibi361
date: "2023-02-24"
category: Web Exploitation

---

We are given the link http://saturn.picoctf.net:55827 where we are presented with an "Web eReader" website which has a single input form. On giving filenames to the form we can read the files present on the server.

The challenge description tells us that the flag is located in the root directory in the file `flag.txt` whereas the web server's working directory is `/usr/share/nginx/html`. It also says that absolute paths are blocked, which is why submitting `/flag.txt` into the form redirects us to `read.php` with the message `Not Authorized`

In order to bypass this restriction we use [relative paths](<https://en.wikipedia.org/wiki/Path_(computing)#Absolute_and_relative_paths>) to get to the root directory and then reach the flag file: `../../../../flag.txt`.

...
End of writeup
