<h1>RSA Noob</h1>

<p align="center">
  <img src="https://github.com/enomarozi/RSA-CTF-Writeup/blob/master/RSA/Image/RSA%20Noob.png">
</p>
</p>
<p>pada soal diberikan e,c dan n yang sifatnya publik, dan kita diminta untuk me-decrypt cipher tersebut menjadi text/flag,
	pertama kita lakukan factor dari nilai modulus n <a href="factordb.com">factordb</a> dan didapatkanlah p dan q</p>
<p>p = 416064700201658306196320137931</p>
<p>q = 590872612825179551336102196593</p>
<p>Kemudian cari euler totient dari n --> (p-1)*(q-1). terakhir, 
	cari nilai invert atau d dengan library gmpy2 fungsi invert d=gmpy2.invert(e,phi)</p>

<b><h2>Solution</h2></b>
```python
import gmpy2

e = 1
c = 9327565722767258308650643213344542404592011161659991421
n = 245841236512478852752909734912575581815967630033049838269083
p = 416064700201658306196320137931 #factordb
q = 590872612825179551336102196593 #factordb
phi = (p-1)*(q-1) 
d = gmpy2.invert(e,phi)
print(bytes.fromhex(hex(pow(c,d,n))[2:]).decode("ascii"))
```
<b><h2>Flag</h2></b>
<pre>abctf{b3tter_up_y0ur_e}</pre>
