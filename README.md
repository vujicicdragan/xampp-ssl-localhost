# xampp-ssl-localhost
Validan HTTPS localhost SSL sertifikat sa SAN poljem (localhost + 127.0.0.1) za XAMPP

# xampp-ssl-localhost

---

## 📜 Opis (Srpski)

Ovaj repozitorijum sadrži validan **HTTPS localhost SSL sertifikat** sa pravilno definisanim **Subject Alternative Name (SAN)** poljem, koji uključuje:

- `localhost`
- `127.0.0.1`

Konfigurisano i testirano za **XAMPP** okruženje na Windows-u.

### ✅ Funkcionalnosti
- Generisani `.crt`, `.csr` i `.key` fajlovi spremni za upotrebu
- Kompatibilnost sa modernim pregledačima (Chrome, Firefox, Edge…)
- Stabilna lokalna HTTPS veza za razvoj

### 📂 Struktura fajlova
ssl.crt/ -> Sertifikat (.crt)  
ssl.csr/ -> CSR fajl (Certificate Signing Request)  
ssl.key/ -> Privatni ključ (.key)  

### ⚙️ Instalacija
1. Kopiraj `ssl.crt`, `ssl.csr` i `ssl.key` u `C:\xampp\apache\conf\`
2. U fajlu `httpd-ssl.conf` ažuriraj putanje:
   ```apache
   SSLCertificateFile "conf/ssl.crt/server.crt"
   SSLCertificateKeyFile "conf/ssl.key/server.key"
   ```
3. U fajlu `httpd-vhosts.conf` dodaj sledeću konfiguraciju:
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

This repository contains a valid **HTTPS localhost SSL certificate** with a properly set **Subject Alternative Name (SAN)** field, including:

- `localhost`
- `127.0.0.1`

Configured and tested for **XAMPP** environment on Windows.

### ✅ Features
- Pre-generated `.crt`, `.csr`, and `.key` files ready to use
- Compatible with modern browsers (Chrome, Firefox, Edge…)
- Stable local HTTPS connection for development

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
3. In `httpd-vhosts.conf` add the following configuration:
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


