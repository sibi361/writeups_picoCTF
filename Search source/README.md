# picoCTF Search source

---

author: sibi361
date: "2023-02-22"
category: Web Exploitation

---

We are given the link: http://saturn.picoctf.net:61941/ which seems to be the a Yoga firm's website. The title tells us to "Search source" so we shall first save the website locally for easy searching using the command: `wget http://saturn.picoctf.net:61941/ --mirror`

Then we use [`grep`](https://en.wikipedia.org/wiki/Grep) with the recursive `-r` flag to search the local copy of the website that we just downloaded using `wget`, for the keyword "pico": `grep -r pico saturn.picoctf.net:61941/*`. And that shows us the flag which is located in the file `saturn.picoctf.net:61941/css/style.css`.

...
End of writeup
