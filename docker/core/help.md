To create the `agent.key`:

    $ ssh-keygen -t rsa -f shield/agent.key -N '' >/dev/null

To create a self signed CA:

    $ openssl req -x509 -newkey rsa:2048 -sha256 -nodes -keyout CA.key -out CA.pem -subj "/CN=vaultca" -days 365

Create a cert:

    $ openssl req -newkey rsa:2048 -sha256 -nodes -keyout vault.key -out vault.csr -subj "/CN=vault"

Sign the cert with the CA:

    $ openssl x509 -days 3065 -sha256 -req -in vault.csr -CA CA.pem -CAkey CA.key -set_serial 01 -out vault.crt
