1.Copy the contents of ca_base64,clientcert_base64,clientkey_base64 and create ca.cert, clientcert.cert, clientkey.cert

that is what available in between <ca></ca>,<cert></cert>,<key></key>

2.convert all these files to based64 decoding
openssl base64 -d -in <infile> -out <outfile>

3. convert der to pem
openssl x509 -inform der -in ca.crt -out ca.pem

convert der key to der value

 openssl rsa -inform der -in clientkey.key -out clientkey.pem

4.p12 generation file

 openssl pkcs12 -export -out clientp12.p12 -inkey clientkey.pem -in clientcert.pem -certfile ca.pem

5. verify p12

openssl pkcs12 -in client.p12 -nodes -passin pass:"password of p12" | openssl x509 -noout -subject

The certs OVPN and MobileConfig that I have shared might and might not work.I haven’t checked it


Note:
More working samples can be found here https://goo.gl/wBTpX2
i.e OVPN and its related Mobileconfig I have confirmed it works.

To get access to it mail me I’ll share you those.
 
