# GPG

## Generate a new key pair

The command --gen-key may be used along with the option --batch for unattended key generation. The parameters are either read from stdin or given as a file on the command line.

```
cat > roy.gpg << EOF
%echo Generating key
%pubring roy.pub
%secring roy.sec
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
%commit
%echo done
EOF
```

```
gpg2 --batch --gen-key roy.gpg
```

## Generate entropy

This feeds data from a random number generator to the kernel's random number entropy pool, after first checking the data to ensure that it is properly random.

```
sudo rngd -f -r /dev/urandom
```

## List all keys from the secret keyrings

```
gpg2 --no-default-keyring --secret-keyring ./roy.sec \
--keyring ./roy.pub --list-secret-keys
```
