# picoCTF dont-use-client-side

---

author: sibi361
date: "2023-02-22"
category: Web Exploitation

---

We are given the website https://jupiter.challenges.picoctf.org/problem/29835/ which contains a textbox with a "Verify" button. Submitting random values into this form returns an `alert` saying "Incorrect password".

On viewing the website's source code we can see that on submitting the form, the `verify()` function is called which simply checks different parts of the given string againsts hardcoded sets of some other string, possibly the flag using the [checkpass.substring()](https://developer.mozilla.org/en-US/docs/Web/XPath/Functions/substring) function.

Individually piecing together the smaller strings in the right order of the indexes gets us the flag.

...
End of writeup
