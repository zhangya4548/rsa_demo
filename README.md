# XRSA
OpenSSL RSA Encryption, Decryption, and Key Generation. Java, Php GoLang Support, Large Data Support.

## Installation

### Php
*Make sure `openssl` extension is enabled*.
Just copy `php/src/XRsa.php` and `php/src/helpers.php` to your project. Alternatively, you can use composer to install:
```cmd
composer require liamylian/x-rsa
```

### GoLang
*Make sure your golang version is greater than `1.10.3`*.
Just Copy `golang/xrsa/xrsa.go` to your project, or use command:
```cmd
go get github.com/liamylian/x-rsa
```

### Java
Just Copy `XRsa.java` to your project

## Usage

### Php
```php
    $keys = XRsa::createKeys(2048);
    $rsa = new XRsa($keys['publicKey'], $keys['privateKey']);
    
    $data = "Hello, World";
    $encrypted = $rsa->publicEncrypt($data);
    $decrypted = $rsa->privateDecrypt($encrypted);
    $sign = $rsa->sign($data);
    $is_valid = $rsa->verify($data, $sign);
```

### GoLang
```golang
    publicKey := bytes.NewBufferString("")
    privateKey := bytes.NewBufferString("")

    err := CreateKeys(publicKey, privateKey, 2048)
    if err != nil {
        return
    }
    xrsa, err := NewXRsa(publicKey.Bytes(), privateKey.Bytes())
    if err != nil {
        return
    }

    data := "Hello, World"
    encrypted, _ := xrsa.PublicEncrypt(data)
    decrypted, _ := xrsa.PrivateDecrypt(encrypted) 
    sign, err := xrsa.Sign(data)
    err = xrsa.Verify(data, sign)
```
    
### Java
```java
    Map<String, String> keys = XRsa.createKeys(2048);
    XRsa rsa = new XRsa(keys.get("publicKey"), keys.get("privateKey"));
    
    String data = "hello world";
    String encrypted = rsa.publicEncrypt(data);
    String decrypted = rsa.privateDecrypt(encrypted);
    String sign = rsa.sign(data);
    Boolean isValid = rsa.verify(data, sign);
```
