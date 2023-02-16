# picoCTF vault-door-4

---

author: sibi361
date: "2023-02-16"
category: Reverse Engineering

---

We are given a `java` file named `VaultDoor4.java`. The hint asks us to research on ASCII codes and representing numbers in different bases such as octal and hexadecimal. The `checkPassword()` function this time includes something like an array, `myBytes` which has 32 items. The last 8 of them seem to be proper ASCII characters. Therefore we need to convert the first 24 of them into characters. Thus for obtaining the flag, we write the following `python` script.

```
# myBytes (maybe) array
original_codes = ["106", "85", "53", "116", "95", "52", "95", "98",
"0x55", "0x6e", "0x43", "0x68", "0x5f", "0x30", "0x66", "0x5f",
"0142", "0131", "0164", "063", "0163", "0137", "070", "0146",
'4', 'a', '6', 'c', 'b', 'f', '3', 'b']
new_codes = []


counter = 0

# base change done to integer using the following syntax
# <integer> = int(<original_item_as_string>, <original_items_base>)

# for decimals
while counter < 8:
	new_codes += [int(original_codes[counter], 10)]
	counter += 1

# for hexadecimal numbers
while counter < 16:
	new_codes += [int(original_codes[counter], 16)]
	counter += 1

# for octal numbers
while counter < 24:
	new_codes += [int(original_codes[counter], 8)]
	counter += 1

# no conversion required for the normal ascii characters
while counter < 32:
	new_codes += [original_codes[counter]]
	counter += 1


print("picoCTF{", end = '')

counter = 0
while counter < 24:
    # converting ascii codes to ascii text using the chr() function
	print(chr(int(new_codes[counter])), end = '')
	counter += 1

while counter < 32:
	print(new_codes[counter], end = '')
	counter += 1

print("}\n")
```

...
End of writeup
