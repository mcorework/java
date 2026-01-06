# Java Keystore (JKS) Documentation

## Overview
This document describes the Java Keystore used for SSL/TLS configuration in the application environment.  
The keystore stores private keys and trusted certificates required for secure communication.

> **Important:**  
> - Do **NOT** commit actual keystore files (`.jks`, `.p12`) or passwords to source control.  
> - This document is for reference and operational guidance only.  

---

## Keystore Details

| Property        | Value                        |
|-----------------|------------------------------|
| Keystore Type   | JKS (Java KeyStore)          |
| File Name       | `gaoprod.keystore`           |
| Java Version    | Java 8+                      |
| Used By         | Apache Tomcat                |
| Purpose         | HTTPS / SSO / SSL configuration |

---

## Keystore Entries

### Private Key Entry
- **Alias:** `tomcat`  
- **Entry Type:** `PrivateKeyEntry`  
- **Key Algorithm:** RSA  
- **Key Size:** 2048 bits  
- **Certificate Chain:** Yes  

### Trusted Certificate Entries

| Alias            | Type             | Purpose             |
|------------------|-----------------|-------------------|
| root-ca          | trustedCertEntry | Root CA certificate |
| intermediate-ca  | trustedCertEntry | Intermediate CA    |

---

## Keystore Passwords

| Password Type        | Description                     |
|---------------------|---------------------------------|
| Keystore Password    | Protects the keystore file      |
| Key Password         | Protects private key entries    |

> Passwords should be stored securely using Vault, environment variables, or encrypted secrets.

---

## Keytool Commands

### List Keystore Contents
```bash
keytool -list \
  -keystore gaoprod.keystore \
  -storepass <keystore_password>


## Links

- [Java Keytool - Introduction - Cyber Hashira](https://www.youtube.com/watch?v=NH49dTEYPg0)
