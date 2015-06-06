# GnuPG 2.1 and later

## Generate a new key pair

The parameters are either read from stdin or given as a file on the command line. Here is an example on how to create a primary RSA key and a sign only RSA sub key.

```
cat > roy.txt << EOF
%echo Generating key
Key-Type: RSA
Key-Length: 4096
Subkey-Type: RSA
Subkey-Length: 4096
Subkey-Usage: sign
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

The command --gen-key may be used along with the option --batch for unattended key generation.

```
gpg2 --batch --gen-key roy.txt
```

## Generate entropy

This feeds data from a random number generator to the kernel's random number entropy pool, after first checking the data to ensure that it is properly random. Run in parallel in another terminal.

```
sudo rngd -f -r /dev/urandom
```

## List keys

List all keys from the public keyrings.

```
gpg2 --list-keys
```

List  all  keys  from  the secret keyrings.

```
gpg2 --list-secret-keys
```

## Export the public key

Export keys from those of the given name.

```
gpg2 --output ~/RPM-GPG-KEY-tyrell --armor --export roy.batty@tyrell.com
```
