<h1><b>john_pollard</b></h1>
<p>Diberikan file cert.pem pada soal, dan kita diminta untuk mendapatkan nilai prime1(p) dan prime2(q)</p>
<h3><b>Solution</b></h3>
<p>Ekstrak file cert.pem</p>

```console
root@Python:/home/venom/Downloads# openssl x509 -pubkey -noout -in cert > pubkey
root@Python:/home/venom/Downloads# cat pubkey 
-----BEGIN PUBLIC KEY-----
MCIwDQYJKoZIhvcNAQEBBQADEQAwDgIHEaTUUhKxfwIDAQAB
-----END PUBLIC KEY-----
root@Python:/home/venom/Downloads# openssl rsa -in pubkey -pubin -text -noout
RSA Public-Key: (53 bit)
Modulus: 4966306421059967 (0x11a4d45212b17f)
Exponent: 65537 (0x10001)
```
<p>Setelah didapatkan modulus(n), kita bisa mencari nilai prime1(p) dan prime2(q) dengan <a href="factordb.com">factordb</a></p>
<p>Hasil</p>
<pre>
p = 73176001
q = 67867967
</pre>
<h3><b>Flag</b></h3>
<pre>
picoCTF{73176001,67867967}
</pre>
