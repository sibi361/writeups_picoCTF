# picoCTF cass

---

author: sibi361
date: "2023-02-22"
category: Web Exploitation

---

We are given the link https://caas.mars.picoctf.net/ where we are asked to make a request to the url https://caas.mars.picoctf.net/cowsay/{message12345}. On visiting that url directly, we see that the website is a web version of the [cowsay](https://en.wikipedia.org/wiki/Cowsay) program.

< {message12345} >

         \   ^__^
         \  (oo)\_______
            (__)\       )\/\
                ||----w |
                ||     ||

---

We have been additionally given the `index.js` file which proably runs the sever, Upon going through it we come to know that the server is running on [Express JS](https://en.wikipedia.org/wiki/Express.js). On `line 8` we see that the `cowsay` program program is being invoked with the syntax `cowsay {message}`, where the message is NOT parameterized. Hence this server will print as well as execute any commands given to it without any safety checks. We can use this fact along with [Command Substitution](https://en.wikipedia.org/wiki/Command_substitution) to get [Remote Code Execution](https://en.wikipedia.org/wiki/Remote_code_execution) on the web server.

We start by listing the files in the web server's folder: `curl https://caas.mars.picoctf.net/cowsay/\$\(ls\)`

Doing so tells us that there is a file named `falg.txt`, so we try to view it by using `cat`: `curl https://caas.mars.picoctf.net/cowsay/\$\(cat%20falg.txt\)` and that gets us the flag. `%20` is the [URL-Encoded](https://en.wikipedia.org/wiki/URL_encoding) version of a `space` character, since using a normal `space` might cause errors in the terminal, we use this method.

...
End of writeup
