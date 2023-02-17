# picoCTF vault-door-6

---

author: sibi361
date: "2023-02-17"
category: Reverse Engineering

---

We are given a `java` file named `VaultDoor6.java`. The hint asks us to read about [XOR encryption](https://en.wikipedia.org/wiki/XOR_cipher).

"XOR" is a kind of [binary operation](https://en.wikipedia.org/wiki/Truth_table#Binary_operations) which stands for "Exclusive OR". In simple terms, it returns true only if the inputs don't match: (1,0) & (0,1). In the remaining two cases (0,0) and (1,1), it returns false.

To encrypt a piece of `Plaintext`, something called a `Key` is required. And the string that is obtained after encryption is called the `Ciphertext`. Performing XOR with the inputs being `Plaintext` and `Key` gives the `Ciphertext `.

> `Plaintext` ^ `Key` = `Ciphertext`

---

Now because of XOR's nature, merely re-applying the XOR function with the key will remove the cipher:

> `Ciphertext` ^ `Key` = `Plaintext`

So we write a new `java` program, `xor_reverse.java` to use the contents of the `myBytes` array within the `checkPassword()` function as the Ciphertext with the key being `0x55` and that gives us the flag.

```
import java.util.*;

class xor_reverse {
    public static void main(String args[]) {
        System.out.print("\npicoCTF{");

        byte[] myBytes = {
                0x3b, 0x65, 0x21, 0xa, 0x38, 0x0, 0x36, 0x1d,
                0xa, 0x3d, 0x61, 0x27, 0x11, 0x66, 0x27, 0xa,
                0x21, 0x1d, 0x61, 0x3b, 0xa, 0x2d, 0x65, 0x27,
                0xa, 0x6c, 0x61, 0x6d, 0x37, 0x6d, 0x6d, 0x6d,
        };
        for (int i = 0; i < 32; i++) {
            System.out.print((char) (myBytes[i] ^ 0x55));
        }
        System.out.println("}\n");
    }
}
```

...
End of writeup
