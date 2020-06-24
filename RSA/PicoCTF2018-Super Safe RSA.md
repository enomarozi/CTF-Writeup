<h1><b>Super Safe RSA </b></h1>

<p><b>Connect nc 2018shell.picoctf.com 3609</b> Diberikan modulus(n), eksponen(e) dan ciphertext(c) pada soal
<pre>
e: 65537
c: 9353081038206120793627985283298954272422883560657560482474115940242058079032880
n: 11515021802033315859347229367319673967150840107767451889591797570238004514985717
</pre>
<h3><b>Solution</b></h3>
<p>Generate p dan q dari modulus(n), pertama coba dengan <a href="factordb.com">factordb</a>, jika p dan q tidak didapatkan, maka coba generate dengan <a href="https://www.alpertron.com.ar/ECM.HTM">alpetron</a>
, disini kita akan menghabiskan waktu kisaran menit untuk memperoleh p dan q dari modulus(n), dan Hasil :
<pre>
p = 102058149618223245648851660072233885271
q = 112828047981552103555863251398946260225427
</pre>
<p>Terakhir, generate privatekey(d) lalu decrypt ciphertext(c)</p>

```python
import gmpy2

e = 65537
n = 11515021802033315859347229367319673967150840107767451889591797570238004514985717
p = 102058149618223245648851660072233885271
q = 112828047981552103555863251398946260225427
c = 9353081038206120793627985283298954272422883560657560482474115940242058079032880
phi=(p-1)*(q-1)
d = gmpy2.invert(e,phi)
print(bytes.fromhex(hex(pow(c,d,n))[2:]))
```

<h3><b>Flag</b></h3>
<pre>
picoCTF{us3_l@rg3r_pr1m3$_1379}
</pre>
