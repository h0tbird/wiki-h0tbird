# GPG

## Generate a new key pair

```
cat > roy.gpg << EOF
%echo Generating key
Key-Type: RSA
Key-Length: 4096
Subkey-Type: ELG-E
Subkey-Length: 2048
Name-Real: Roy Batty
Name-Comment: Nexus-6
Name-Email: roy.batty@tyrell.com
Expire-Date: 0
Passphrase: Tears in rain
%pubring roy.pub
%secring roy.sec
%commit
%echo done
EOF
```

```
gpg2 --batch --gen-key roy.gpg
```


## Section 2

Nulla vitae elit libero, a pharetra augue. Cras justo odio, dapibus ac facilisis in, egestas eget quam. Cras mattis consectetur purus sit amet fermentum. Cum sociis natoque penatibus et magnis dis parturient montes, nascetur ridiculus mus.
