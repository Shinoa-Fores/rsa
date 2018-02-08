rsa - The RSA Encryption Algorithm in Common Lisp
-------------------------------------------------

Encrypt and decrypt messages using a key and the beauty of mathematics.

This library does not solve the key exchange problem.

--

First, get a Common Lisp implementation and install it:

    http://sbcl.org

Run your lisp:

```sh
    $ ./sbcl
```

Load this file:

```cl
(load "rsa.lisp")
```

Generate a key:

```cl
(defparameter *key* (rsa-gen-key "me"))
```

Encrypt:

```cl
(defparameter *cyphertext* (rsa-encrypt-text *key* "this is a test"))
```

Decrypt:

```cl
(multiple-value-bind (from plaintext)(rsa-decrypt-text *key* *cyphertext*) 
    plaintext)
```

Encrypt text and store into file
```cl
(rsa-encrypt-and-save *key* "Very secret message" "message.enc")

```

Decrypt text stored in file
```cl
(rsa-load-and-decrypt *key* "message.enc")

```

Key management DB
-----------------

List keys:

```cl
(rsa-list-keys)
```

Find a key by name:

```cl
(rsa-find-key "me")
```

Load a key into the db:

```cl
(rsa-load-key "me.rsa-key")
```

Save a key to a file:

```cl
(rsa-save-key *key* "me.rsa-key")
```

Save key database
```cl
(rsa-save-db "db.rsa")
```

Load key database (please note that function does not clear the internal database before loading, so you are merging keys from file passed to internal DB)
```cl
(rsa-load-db "rsa.db")
```

Added utility function 'encrypt-file' and 'decrypt-file':

```cl

(encrypt-file "me.rsa-key" "infile" "infile.rsa")

(decrypt-file "me.rsa-key" "infile.rsa" "infile,2")
```
	
Bonus
-----

You will also find a fast, self contained impmentation of the Miller
Rabkin primality test.

TODO
----

- [X] save/load key db to/from file

- [X] save encrypted message to a file 

- [X] load and decrypt a message from a file 

- make ASDF installable

- get into quicklisp

--
Burton Samograd
burton.samograd@gmail.com
2016

Laci Kosco
laci.kosco@gmail.com, 2017 (implementation of TODO)
