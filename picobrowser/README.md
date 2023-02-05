# picoCTF picobrowser

---

title: "picoCTF - picobrowser"
author: sibi361
date: "2023-02-04"
category: Web Exploitation
...

- By visiting the given url (https://jupiter.challenges.picoctf.org/problem/50522/) we can see a Login button clicking upon which we get the message "You're not picobrowser!" followed by our browser's [User Agent](https://en.wikipedia.org/wiki/User_agent).

- The challenge's description says: "This website can be rendered only by picobrowser". Hence we change our browser's user agent with a browser extension such as [User-Agent Switcher and Manager](https://chrome.google.com/webstore/detail/user-agent-switcher-and-m/bhchdcejhohfmigjafbampogmaanbfkg) after which reloading the webpage gives us the flag.

...
End of writeup
