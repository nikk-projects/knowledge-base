# ✅ Secure WordPress File & Folder Permissions Setup (Ubuntu/Apache)

## 1. Set Correct Ownership

```bash
sudo chown -R www-data:www-data /var/www/html/your-site
```

---

## 2. Set Folder Permissions

```bash
sudo find /var/www/html/your-site -type d -exec chmod 755 {} \;
```

---

## 3. Set File Permissions

```bash
sudo find /var/www/html/your-site -type f -exec chmod 644 {} \;
```

---

## 4. Secure wp-config.php

```bash
sudo chmod 640 /var/www/html/your-site/wp-config.php
```

---

## 5. Fix Uploads Directory

```bash
sudo chown -R www-data:www-data /var/www/html/your-site/wp-content/uploads
sudo find /var/www/html/your-site/wp-content/uploads -type d -exec chmod 755 {} \;
sudo find /var/www/html/your-site/wp-content/uploads -type f -exec chmod 644 {} \;
```

---

## 6. (Optional) Developer Access

```bash
sudo usermod -a -G www-data nikk
newgrp www-data
sudo find /var/www/html/your-site -type d -exec chmod 775 {} \;
sudo find /var/www/html/your-site -type f -exec chmod 664 {} \;
```

---

## 7. Prevent FTP Prompt

Add in `wp-config.php`:

```php
define('FS_METHOD', 'direct');
```

---

## 8. Restart Web Server

```bash
sudo systemctl restart apache2
# or
sudo systemctl restart nginx
```

---

## 9. Verify

- Upload media via **Media → Add New**
- Install plugin via **Plugins → Add New**
- Test image URL:

  ```
  http://localhost/your-site/wp-content/uploads/test.jpg
  ```
