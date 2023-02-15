# picoCTF Surfing_the_Waves

---

author: sibi361
date: "2023-02-15"
category: Forensics

---

We're given a `WAV` file `main.wav` which we are unable to play in [VLC](https://en.wikipedia.org/wiki/VLC).

The first hint says `Music is cool, but what other kinds of waves are there?`. On seeing "waves" we start [Audacity](<https://en.wikipedia.org/wiki/Audacity_(audio_editor)>) and open the file. Now we are able to listen to the audio which seems to be repeating some sound multiple times.

The second hint asks us to look closely so we amplify the entire track but we don't see anything new. So let's try to read the file with `python`.

---

We write the following `python` code to print the contents of the file:

```
# https://stackoverflow.com/questions/2060628/reading-wav-files-in-python

from scipy.io import wavfile
samplerate, data = wavfile.read('main.wav')

print(len(data)) # returns 2736

# get the unique ones (that proabably form the first of the repeating audio units)
uniques = []
for i in data:
	if i not in uniques:
		uniques += [i]

print(len(uniques)) # returns 157

print(uniques)
```

The contents of the file seem to be 4 digit numbers which surely aren't ascii codes:

```
[2000, 2500, ..., 6008, 6004]
```

### PENDING

...
End of writeup
