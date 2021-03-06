## PHP

```php
<?php

$key = 'YOUR_SECRET_KEY';
$userID = 'YOUR_USER_ID';

// to HEX(Base16)
hash_hmac('sha256', $userID, $key);
```

## NodeJS

```js
var crypto = require('crypto');

var key = 'YOUR_SECRET_KEY';
var userID = 'YOUR_USER_ID';

var hash = crypto.createHmac('sha256', key).update(userID);

// to HEX(Base16)
hash.digest('hex');
```

## Ruby

```rb
require 'openssl'

key = 'YOUR_SECRET_KEY'
userID = 'YOUR_USER_ID'

# to HEX(Base16)
OpenSSL::HMAC.hexdigest('sha256', key, userID)
```

## Elixir

```elixir
key = 'YOUR_SECRET_KEY'
userID = 'YOUR_USER_ID'

signature = :crypto.hmac(:sha256, key, userID)

# to HEX(Base16)
Base.encode16(signature, case: :lower)
```

## Go

```go
package main

import (
	"crypto/hmac"
	"crypto/sha256"
	"encoding/hex"
)

func main() {
	secret := []byte("YOUR_SECRET_KEY")
	userID := []byte("YOUR_USER_ID")

	hash := hmac.New(sha256.New, secret)
	hash.Write(userID)

	// to HEX(Base16)
	hex.EncodeToString(hash.Sum(nil))
}
```

## Python 2

```py
import hashlib
import hmac

userID = bytes('YOUR_USER_ID').encode('utf-8')
secret = bytes('YOUR_SECRET_KEY').encode('utf-8')

hash = hmac.new(secret, userID, hashlib.sha256)

# to HEX(Base16)
hash.hexdigest()
```

## Python 3

```py
import hashlib
import hmac

userID = bytes('YOUR_USER_ID', 'utf-8')
secret = bytes('YOUR_SECRET_KEY', 'utf-8')

hash = hmac.new(secret, userID, hashlib.sha256)

# to HEX(Base16)
hash.hexdigest()
```

## C&#35;

```cs
using System;
using System.Security.Cryptography;
using System.Text;

class MainClass {
  public static void Main (string[] args) {
    string key = "YOUR_SECRET_KEY";
    string userID = "YOUR_USER_ID";

    byte[] keyByte = new ASCIIEncoding().GetBytes(key);
    byte[] userIDBytes = new ASCIIEncoding().GetBytes(userID);

    byte[] hashmessage = new HMACSHA256(keyByte).ComputeHash(userIDBytes);

    // to HEX(Base16)
    String.Concat(Array.ConvertAll(hashmessage, x => x.ToString("x2")));
  }
}
```

## Java

```java
import javax.crypto.Mac;
import javax.crypto.spec.SecretKeySpec;
import java.security.NoSuchAlgorithmException;
import java.security.InvalidKeyException;
import javax.xml.bind.DatatypeConverter;

class Main {
  public static void main(String[] args) {
  	try {
	    String key = "YOUR_SECRET_KEY";
	    String userID = "YOUR_USER_ID";

	    Mac hasher = Mac.getInstance("HmacSHA256");
	    hasher.init(new SecretKeySpec(key.getBytes(), "HmacSHA256"));

	    byte[] hash = hasher.doFinal(userID.getBytes());

	    // to HEX(Base16)
	    DatatypeConverter.printHexBinary(hash);
  	}
  	catch (NoSuchAlgorithmException e) {}
  	catch (InvalidKeyException e) {}
  }
}
```
