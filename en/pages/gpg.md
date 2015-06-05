# GPG

## Generate a new key pair

```
cat > roy.gpg << EOF
%echo Generating key
Key-Type: RSA 
Key-Length: 4096
Subkey-Type: RSA 
Subkey-Length: 4096
Name-Real: Roy Batty
Name-Comment: Nexus-6
Name-Email: roy.batty@tyrell.com
Expire-Date: 0
Passphrase: Tears in rain
Preferences: SHA512 SHA384 SHA256 SHA224 AES256 AES192 AES CAST5 ZLIB BZIP2 ZIP Uncompressed
%pubring roy.pub
%secring roy.sec
%commit
%echo done
EOF
```

```
gpg2 --batch --gen-key roy.gpg
```

## Generate entropy

This daemon feeds data from a random number generator to the kernel's random number entropy pool, after first checking the data to ensure that it is properly random.

```
sudo rngd -f -r /dev/urandom
```
