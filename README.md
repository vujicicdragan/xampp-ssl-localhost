# XAMPP Localhost HTTPS SSL Certificate with SAN Support

🚀 Secure your XAMPP localhost with a ready-to-use HTTPS SSL certificate (SAN: localhost & 127.0.0.1) – no browser warnings!

---

## 📜 Opis (Srpski)

Ovaj repozitorijum sadrži prekonfigurisani **HTTPS localhost SSL sertifikat** sa pravilno definisanim **Subject Alternative Name (SAN)** poljem, koji uključuje:

- `localhost`
- `127.0.0.1`

Konfigurisano i testirano za **XAMPP** okruženje na Windows-u.

### ✅ Funkcionalnosti
- Spremni `.crt`, `.csr` i `.key` fajlovi
- Kompatibilnost sa modernim pregledačima (Chrome, Firefox, Edge…)
- Bez upozorenja o nesigurnoj konekciji na `https://localhost`

### 📂 Struktura fajlova
ssl.crt/ -> Sertifikat (.crt)  
ssl.csr/ -> CSR fajl (Certificate Signing Request)  
ssl.key/ -> Privatni ključ (.key)  

### ⚙️ Instalacija
1. Kopiraj `ssl.crt`, `ssl.csr` i `ssl.key` u `C:\xampp\apache\conf\`
2. U `httpd-ssl.conf` ažuriraj putanje:
   ```apache
   SSLCertificateFile "conf/ssl.crt/server.crt"
   SSLCertificateKeyFile "conf/ssl.key/server.key"
   ```
3. U `httpd-vhosts.conf` dodaj:
   ```apache
   <VirtualHost *:80>
       ServerName localhost
       DocumentRoot "C:/xampp/htdocs"

       # Redirect all to HTTPS
       Redirect permanent / https://localhost/
   </VirtualHost>

   <VirtualHost _default_:443>
       DocumentRoot "C:/xampp/htdocs"
       ServerName localhost
       SSLEngine on
       SSLCertificateFile "C:/xampp/apache/conf/ssl.crt/server.crt"
       SSLCertificateKeyFile "C:/xampp/apache/conf/ssl.key/server.key"
   </VirtualHost>
   ```
4. Restartuj Apache iz XAMPP Control Panel-a
5. Otvori `https://localhost`

---

## 📜 Description (English)

This repository contains a pre-configured **HTTPS localhost SSL certificate** with a properly set **Subject Alternative Name (SAN)** field, including:

- `localhost`
- `127.0.0.1`

Configured and tested for **XAMPP** environment on Windows.

### ✅ Features
- Ready `.crt`, `.csr`, and `.key` files
- Compatible with modern browsers (Chrome, Firefox, Edge…)
- No insecure connection warnings on `https://localhost`

### 📂 File Structure
ssl.crt/ -> Certificate (.crt)  
ssl.csr/ -> CSR file (Certificate Signing Request)  
ssl.key/ -> Private key (.key)  

### ⚙️ Installation
1. Copy `ssl.crt`, `ssl.csr`, and `ssl.key` into `C:\xampp\apache\conf\`
2. In `httpd-ssl.conf` update the paths:
   ```apache
   SSLCertificateFile "conf/ssl.crt/server.crt"
   SSLCertificateKeyFile "conf/ssl.key/server.key"
   ```
3. In `httpd-vhosts.conf` add:
   ```apache
   <VirtualHost *:80>
       ServerName localhost
       DocumentRoot "C:/xampp/htdocs"

       # Redirect all to HTTPS
       Redirect permanent / https://localhost/
   </VirtualHost>

   <VirtualHost _default_:443>
       DocumentRoot "C:/xampp/htdocs"
       ServerName localhost
       SSLEngine on
       SSLCertificateFile "C:/xampp/apache/conf/ssl.crt/server.crt"
       SSLCertificateKeyFile "C:/xampp/apache/conf/ssl.key/server.key"
   </VirtualHost>
   ```
4. Restart Apache from XAMPP Control Panel
5. Open `https://localhost`

---

**📌 Topics (GitHub Tags):**  
xampp, apache, ssl, https, localhost, san, certificate, development, webdev, php
