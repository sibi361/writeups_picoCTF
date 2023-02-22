# picoCTF Local Authority

---

author: sibi361
date: "2023-02-22"
category: Web Exploitation

---

We are given the website http://saturn.picoctf.net:49701/ which seems to contain a simple username-password login page. The hint asks us to figure out the password checking mechanism. So we go to the login form's `action` url: http://saturn.picoctf.net:49701/login.php where we some minimal "SQL Injection" prevention measures as well as another useful link: http://saturn.picoctf.net:49701/secure.js.

This javascript file contains an if-else loop with the username as well as password hardcoded in. Submitting these values in the original login form redirects us to the website http://saturn.picoctf.net:49701/admin.php where we are shown the flag.

In the `login.php` script we can see that once the `checkPassword()` function present in `secure.js` checker returns `True`, the PHP script inserts the string `2196812e91c29df34f5e217cfd639881` into a hidden textbox with the `id` attribute as `adminFormHash` and then submits that form. Since that form's `action` is `admin.php` we are redirected to it.

...
End of writeup
