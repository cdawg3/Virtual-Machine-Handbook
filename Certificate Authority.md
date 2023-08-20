```shell
sudo apt-get update
```

```shell
sudo apt-get install openssl
```

```shell
mkdir -p ~/CA/newcerts
```

```shell
touch ~/CA/index.txt
```

```shell
echo '01' > ~/CA/serial
```

```shell
sudo nano ~/CA/CA.cnf
```
### Paste this in ~/CA/CA.cnf
```shell
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
```shell
openssl genpkey -algorithm RSA -out ~/CA/CA.key
```
### Create the Certificate Authorities self-signd key
```shell
openssl req -x509 -new -nodes -key ~/CA/CA.key -sha256 -days 1825 -out ~/CA/CA.crt -config ~/CA/CA.cnf
```
### Verify that the certificate was created
```shell
openssl x509 -in ~/CA/CA.crt -text -noout
```
### On target VM generate the key
```shell
openssl genpkey -algorithm RSA -out server.key
```
### Create signing request
```shell
openssl req -new -key server.key -out server.csr
```
### Transfer the CSR to the Certificate Authority VM
```shell
scp server.csr user@CA-VM-IP:/path/to/destination
```
### On the Certificate Authority VM sign the CSR
```shell
openssl ca -config /path/to/CA.cnf -in /path/to/server.csr -out server.crt
```
### Transfer signed certificate back to the target VM
```shell
scp server.crt user@Target-VM-IP:/path/to/destination
```
