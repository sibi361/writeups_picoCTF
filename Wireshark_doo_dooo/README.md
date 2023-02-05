# picoCTF Wireshark doo dooo do doo...

---

title: "Wireshark doo dooo do doo..."
author: sibi361
date: "2023-02-05"
category: Forensics
...

The given shark1.pcapng packets stream is opened with [Wireshark](https://en.wikipedia.org/wiki/Wireshark). Then we start searching for the flag, which should be in the format:

```
picoCTF{FLAG}
```

Using the [filter](https://www.wireshark.org/docs/man-pages/wireshark-filter.html):

```
tcp.payload contains "picoCTF"
```

We are unable to find anything. So we switch to other possibilities of the string "picoCTF".

Upon searching for the [ROT13](https://en.wikipedia.org/wiki/ROT13) version:

```
tcp.payload contains "cvpbPGS"
```

A single packet with the frame number "827" shows up, upon inspecting which we find the flag in a section named "Line-based text data".

...
End of writeup
