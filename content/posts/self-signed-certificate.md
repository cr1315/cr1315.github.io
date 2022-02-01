---
title: "テスト用の証明書について"
date: "2021-12-26T11:50:00+0900"
---

# 手取り早く使えるやつ

[まさかこんな簡単に出来たとはね](https://kuttsun.blogspot.com/2020/04/openssl-san.html)

[gist simple instructions](https://gist.github.com/bitoiu/9e19962b991a71165268)

[gist simple instructions 2](https://gist.github.com/ykst/2a666d3d41785f9a41d403889f45d82e)

３ステップで作成出来る  
最新のChromeでも認めるSAN付きの自己署名証明書を作成する手順

1. private key作成  
    `openssl genrsa -out pk.pem 4096`
1. csr作成
1. 先のprivate keyで先のcsrを承認する

# 自分のCAを立てた上で使う場合

# 各証明書をもっと綺麗にする
PTi4bNqVnHAR!R5








# 補足
Convert a certificate from PEM to DER format:

 openssl x509 -in cert.pem -inform PEM -out cert.der -outform DER
Convert a certificate to a certificate request:

 openssl x509 -x509toreq -in cert.pem -out req.pem -key key.pem
Convert a certificate request into a self-signed certificate using extensions for a CA:

 openssl x509 -req -in careq.pem -extfile openssl.cnf -extensions v3_ca \
        -key key.pem -out cacert.pem
Sign a certificate request using the CA certificate above and add user certificate extensions:

 openssl x509 -req -in req.pem -extfile openssl.cnf -extensions v3_usr \
        -CA cacert.pem -CAkey key.pem -CAcreateserial
Set a certificate to be trusted for SSL client use and change set its alias to "Steve's Class 1 CA"

 openssl x509 -in cert.pem -addtrust clientAuth \
        -setalias "Steve's Class 1 CA" -out trust.pem


## openssl.cnfの説明

[detail about openssl.cnf](https://www.phildev.net/ssl/creating_ca.html)




