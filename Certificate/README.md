# Generate certificate and push it to AWS ACM
```
openssl genrsa 2048 > my-aws-private.key
```
```
openssl req -new -x509 -nodes -sha1 -days 3650 -key my-aws-private.key > my-aws-public.crt
```
```
openssl pkcs12 -inkey my-aws-private.key -in my-aws-public.crt -export -out my-aws-public.p12
```
Import certificate to AWS ACM
```
aws acm import-certificate \
--certificate file://my-aws-public.crt \
--private-key file://my-aws-private.key \
--region us-east-1
```