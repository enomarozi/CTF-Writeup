<h1><b>shark on wire 1</b></h1>
<p align='center'>
  <img src="https://github.com/enomarozi/CTF-Writeup/blob/master/Wireshark/Images/shark%20on%20wire%201_1.png">
</p>
<h3><b>Solution</b></h3>
<p>Perhatikan seluruh paket UDP, disana terdapat ada beberapa flag, tetapi hanya ada 1 flag yang benar yaitu pada ip sumber 10.0.0.2 ke tujuan 10.0.0.12 atau UDP stream ke-6</p>
<p align="center">
  <img src="https://github.com/enomarozi/CTF-Writeup/blob/master/Wireshark/Images/shark%20on%20wire%201_2.png">
</p>


```python3
from scapy.all import *

pcap = rdpcap("capture.pcap")
for i in pcap[UDP]:
    try:
        if i[IP].src=="10.0.0.2" and i[IP].dst=="10.0.0.12":
            print((i[Raw].load).decode("utf-8"),end="")
    except:
        pass
```
<h3><b>Flag</b></h3>
<pre>
picoCTF{StaT31355_636f6e6e}
</pre>
