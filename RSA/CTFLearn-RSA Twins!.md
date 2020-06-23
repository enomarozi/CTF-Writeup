<h1>RSA Twins!</h1>
<p align="center">
	<img src="https://github.com/enomarozi/RSA-CTF-Writeup/blob/master/RSA/Image/RSA%20Twins!.png">
</p>
<p>pada soal diberikan e,c dan n yang sifatnya publik, dan kita diminta untuk me-decrypt cipher tersebut menjadi text/flag,
	pertama kita lakukan factor dari nilai modulus n <a href="factordb.com">factordb</a> dan didapatkanlah p dan q</p>
<p>p = 121588253559534573498320028934517990374721243335397811413129137253981502291629</p>
<p>q = 121588253559534573498320028934517990374721243335397811413129137253981502291631</p>
<p>Kemudian cari euler totient dari n --> (p-1)*(q-1). terakhir, 
	cari nilai invert atau d dengan library gmpy2 fungsi invert d=gmpy2.invert(e,phi)</p>

<b><h2>Solution</h2></b>
```python
import gmpy2

e = 65537
c = 684151956678815994103733261966890872908254340972007896833477109225858676207046453897176861126186570268646592844185948487733725335274498844684380516667587
n = 14783703403657671882600600446061886156235531325852194800287001788765221084107631153330658325830443132164971084137462046607458019775851952933254941568056899
p = 121588253559534573498320028934517990374721243335397811413129137253981502291629 #factordb
q = 121588253559534573498320028934517990374721243335397811413129137253981502291631 #factordb
phi = (p-1)*(q-1) 
d = gmpy2.invert(e,phi)
print(bytes.fromhex(hex(pow(c,d,n))[2:]).decode("ascii"))
```
<b><h2>Flag</h2></b>
<pre>flag{i_l0v3_tw1N_pr1m3s}</pre>
