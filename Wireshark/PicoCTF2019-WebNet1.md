<h1><b>WebNet1</b></h1>
<p>Diberikan 1 file pcap dan key</p>
<p align="center">
  <img src="https://github.com/enomarozi/CTF-Writeup/blob/master/Wireshark/Images/WebNet2.jpg">
</p>
<h3><b>Solution</b></h3>
<p>Jika kita buka file pcap dengan wireshark terdapat penyadapan trafik HTTPS yang pastinya ter-encrypt seperti pada setiap protokol TLSv1.2, dan sekarang gunakan key yang diberikan untuk decrypt semua protokol HTTPS</p>
<p>Seperti yang anda ketahui pada info protokol TLSv2.1 disana terdapat key-exchange yang berkemungkinan besar stream HTTPS ter-encrypt dengan kriptografi RSA</p>
<p>Decrypt protokol, <b>Pilih Tab menu Edit --> Preference --> Protocols --> TLS --> Edit</b>, dan insert key seperti pada gambar dibawah lalu OK</p>
<p align="center">
  <img width='500' src="https://github.com/enomarozi/CTF-Writeup/blob/master/Wireshark/Images/WebNet0_3.jpg">
</p>
<p>Terakhir, periksa TLS stream <b>Klik 1 protokol TLS --> Follow --> TLS Stream</b>, dan flag terdapat pada stream index 0 yang sebenarnya terdapat pada raw bytes file jpg seperti pada gambar dibawah<p>
<p align="center">
  <img src="https://github.com/enomarozi/CTF-Writeup/blob/master/Wireshark/Images/WebNet1.jpg">
</p>
<p>Cara sederhana menggunakan tool tshark melalui terminal</p> 
<p>eksekusi <b>tshark -r capture.pcap -o "ssl.keys_list:172.31.22.220,443,http,picopico.key" -qz follow,ssl,ascii,0 | grep -i pico</b> dan periksa setiap streamnya</p>
<h3><b>Flag</b></h3>
<pre>
picoCTF{honey.roasted.peanuts}
</pre>
