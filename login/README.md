# picoCTF login

---

author: sibi361
date: "2023-02-22"
category: Web Exploitation

---

We are given the website https://login.mars.picoctf.net/ which contains a simple username-password login page. On going through it's source code, on `line 3` we can see the link to a javascript file: https://login.mars.picoctf.net/index.js.

On visiting this file we see that the contents are on a single line i.e. [minified](<https://en.wikipedia.org/wiki/Minification_(programming)>), so we use a non-minifier tool like https://deobfuscate.io/ to improve visibility.

On going through the javascript we can see it using these two javascript functions:

- [atob()](https://developer.mozilla.org/en-US/docs/Web/API/atob) (ASCII to base64)
- [btoa()](https://developer.mozilla.org/en-US/docs/Web/API/btoa) (base64 to ASCII)

We also see a long string of alphanumeric characters in a single line if-else block: `cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ`. Since base64 related functions are being used, we try to decode the long string as base64 and that gets us the flag.

`echo cGljb0NURns1M3J2M3JfNTNydjNyXzUzcnYzcl81M3J2M3JfNTNydjNyfQ | base64 -d`

...
End of writeup
