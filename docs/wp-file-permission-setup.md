# Secure WordPress File & Folder Permissions Setup

To allow installing themes and plugins directly from the WordPress dashboard on your local/server setup while keeping things secure, follow the recommended server-level permission configuration for your site folder:

`/var/www/html/sitename`

---

## ✅ Final Server-Level WordPress Permissions (for plugin/theme installation)

### 1. Give Full Ownership to `www-data` (Web Server User)

This lets Apache/Nginx create, update, and delete files from the WordPress dashboard.

```bash
sudo chown -R www-data:www-data /var/www/html/sitename
```

### 2. Set Directory Permissions to `755`

```bash
sudo find /var/www/html/sitename -type d -exec chmod 755 {} \;
```

### 3. Set File Permissions to `644`

```bash
sudo find /var/www/html/sitename -type f -exec chmod 644 {} \;
```

### 4. Secure `wp-config.php`

```bash
sudo chmod 640 /var/www/html/sitename/wp-config.php
```

---

## 🛠 Optional: Allow SFTP/Manual File Edit via User (e.g., `nikk`)

If you also want your user (`nikk`) to be able to manually edit files:

```bash
sudo usermod -a -G www-data nikk
newgrp www-data
```

Then give group write access:

```bash
sudo find /var/www/html/sitename -type d -exec chmod 775 {} \;
sudo find /var/www/html/sitename -type f -exec chmod 664 {} \;
```

---

## 💡 Pro Tip: Prevent FTP Prompt in WP Dashboard

Add this line to your `wp-config.php`:

```php
define('FS_METHOD', 'direct');
```

This tells WordPress to write files directly without asking for FTP credentials.