# picoCTF logon

---

title: "picoCTF - logon"
author: sibi361
date: "2023-02-04"
category: Web Exploitation
...

- By visiting the given url (https://jupiter.challenges.picoctf.org/problem/15796/) we are shown a basic login webpage requiring a username and password.

- Pressing "Sign In" without entering anything in the fields takes us to (https://jupiter.challenges.picoctf.org/problem/15796/flag).

- Upon inspecting the browser cookies we find an "admin" cookie set to "False".

- Changing it's value to "True" using a browser extension such as [Cookie-Editor](https://chrome.google.com/webstore/detail/cookie-editor/hlkenndednhfkekhgcdicdfddnkalmdm) and then reloading the webpage gives us the flag.

...
End of writeup
