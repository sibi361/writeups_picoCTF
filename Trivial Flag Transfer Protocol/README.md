# picoCTF Trivial Flag Transfer Protocol

---

author: sibi361
date: "2023-02-15"
category: Forensics

---

We're given a ["packet dump" file](https://wiki.wireshark.org/Development/PcapNg) named `tftp.pcapng` which we open using [Wireshark](https://en.wikipedia.org/wiki/Wireshark).

![Wireshark Opened](images/opened_in_wireshark.png)

---

Most of the packets are of the "TFTP" protocol with some [ARP](https://en.wikipedia.org/wiki/Address_Resolution_Protocol) packets in between. Also there seems to be a data transfer taking place using this very protocol as there are multiple [transmit-acknowledge sequences](https://en.wikipedia.org/wiki/Transmission_Control_Protocol#Connection_establishment). All the acknowledgement packets seem to be identical so we use the following search filter to filter them out

```
ip.src == 10.10.10.12 && tftp
```

On inspecting the packets further we see that packet number 23 is one of the first data packets and thus it's header carries the string "control.tar.gz" hence indicating that a compressed tar archive is being transmitted.

![possible_targz](images/possible_targz.png)

---

Thus we try to piece together the data packets so as to obtain the compressed tarball, hoping that this is not an encrypted protocol like HTTPS.

https://stackoverflow.com/questions/2916612/reconstructing-data-from-pcap-sniff suggests using [tcptrace](https://web.archive.org/web/20221201043700/http://tcptrace.org/) to piece together the packets but that's only for [TCP](https://en.wikipedia.org/wiki/Transmission_Control_Protocol) packets and here we are dealing with a made up protocol named `TFTP`.

---

Came across another tool like tcptrace: [Justniffer](https://onotelli.github.io/justniffer/) but it's development stopped long ago, unable to install it.

---

#### PENDING

...
End of writeup
