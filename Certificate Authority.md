```
sudo apt-get update
```

```
sudo apt-get install openssl
```

```
mkdir -p ~/CA/newcerts
```

```
touch ~/CA/index.txt
```

```
echo '01' > ~/CA/serial
```

```
sudo nano ~/CA/CA.cnf
```
### Paste this in ~/CA/CA.cnf
```
[ ca ]
default_ca = CA_section

[ CA_section ]
dir = ~/CA
database = $dir/index.txt
new_certs_dir = $dir/newcerts
serial = $dir/serial
certificate = $dir/CA.crt
private_key = $dir/CA.key
default_days = 365
default_md = sha256
policy = CA_policy
x509_extensions = usr_cert

[ CA_policy ]
commonName = supplied
stateOrProvinceName = optional
countryName = optional
emailAddress = optional
organizationName = optional
organizationalUnitName = optional

[ req ]
default_bits = 2048
prompt = no
default_md = sha256
distinguished_name = dn

[ dn ]
C = US
ST = Alabama
O = MyOrganization
OU = MyUnit
CN = MyCommonName

[ usr_cert ]
basicConstraints = CA:FALSE
keyUsage = nonRepudiation, digitalSignature, keyEncipherment
```
### Generate Certificate Authorities private key
```
openssl genpkey -algorithm RSA -out ~/CA/CA.key
```
### Create the Certificate Authorities self-signd key
```
openssl req -x509 -new -nodes -key ~/CA/CA.key -sha256 -days 1825 -out ~/CA/CA.crt -config ~/CA/CA.cnf
```
### Verify that the certificate was created
```
openssl x509 -in ~/CA/CA.crt -text -noout
```
### On target VM generate the key
```
openssl genpkey -algorithm RSA -out server.key
```
### Create signing request
```
openssl req -new -key server.key -out server.csr
```
### Transfer the CSR to the Certificate Authority VM
```
scp server.csr user@CA-VM-IP:/path/to/destination
```
### On the Certificate Authority VM sign the CSR
```
openssl ca -config /path/to/CA.cnf -in /path/to/server.csr -out server.crt
```
### Transfer signed certificate back to the target VM
```
scp server.crt user@Target-VM-IP:/path/to/destination
```
