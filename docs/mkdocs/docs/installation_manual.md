# Manual Installation (Website Mode)

## Introduction 

Here, you'll find step-by-step instructions to help you set up the software manually. Follow the provided resources to ensure a smooth installation process and get up and running in no time. 

---------------

## Requirements

### General Information

!!! info "Notice"
	This is the requirement area to install suitefish on website-level. Please read the instructions carefully if you choose this method.

These requirements apply if you are only using the website functionalities of this CMS on a standard web hosting service or your own apache2 web server. In this setup, the background worker will not function, and modules requiring advanced access will also be unavailable without the background worker. 

You can install the CMS in two ways: Root-Level Installation gives you full server control and access to advanced features, but requires a dedicated VPS or root server. Website Mode runs the CMS as a standard website, making it easy to deploy on shared or managed hosting without root access. Choose the method that best fits your hosting environment and needs.

For website mode installation, the CMS runs as a standard website without requiring root-level access. This method is ideal for shared hosting or web hosting environments where you don’t manage the entire server. You can deploy the software on most web hosts without needing a dedicated VPS or root server, making it accessible and easy to set up. Website mode is perfect if you want a straightforward installation and management experience using default hosting features.

### Requirements Checklist

This checklist helps you verify that all requirements are met for installing suitefish-cms as a website.

- Apache2 version 2.4 or higher is required.
	- Nginx untested, NOT expected to work, but can be used as reverse proxy.
- MySQL Version 5.7 or higher required. MySQL 8.0+ recommended for optimal performance.
- PHP version 8.4 required.
	- Do not use versions outside this range, as they are not supported.
	- The software is primarily developed and tested for PHP 8.4, and official support is focused on this version.
- A minimum of 5 GB web space is required; at least 10 GB is recommended.
- You must be able to configure cronjobs on your web server or through your hosting provider.
- Verify that the necessary Apache2 modules are installed as described in the "Apache2 Modules" section.
- Confirm that the required PHP modules are available as outlined in the "PHP Modules" section.

### Apache2 Modules

The following apache2 modules should be installed and activated.

| Module Name       | Purpose (Short Description)                                 |
|-------------------|-------------------------------------------------------------|
| ssl               | Enables HTTPS (SSL/TLS) support (optional)      |
| rewrite           | URL rewriting and redirection                               |
| headers           | Manipulate HTTP headers (optional)                      |
| cgi               | Support for running CGI scripts (optional)                  |
| cgid              | CGI support using a daemon (for threaded MPMs) (optional)              |
| deflate           | Compress content before sending to clients (gzip) (optional)           |
| http2             | HTTP/2 protocol support (optional)                                   |

### PHP Modules

You should have the following PHP Modules installed and activated.

| Package Name       | Purpose (Short Description)                    | Included in PHP 8.4 Core? |
|--------------------|------------------------------------------------|---------------------------|
| php8.4-cli         | Command-line interface for PHP scripts         | Yes                       |
| php8.4-mysql       | MySQL database driver (mysql_* functions), this package may be an alias of php8.4_mysqli.     | No                        |
| php8.4-mysqli      | Improved MySQL driver (mysqli_* functions), this package may be included in php8.4-mysql.     | No                        |
| php8.4-xml         | XML parsing support                             | Yes                       |
| php8.4-mbstring    | Multibyte string support                        | Yes                       |
| php8.4-curl        | cURL library support                            | No                        |
| php8.4-zip         | ZIP archive support                             | Yes                       |
| php8.4-intl        | Internationalization functions                  | Yes                       |
| php8.4-common      | Common PHP files                                | Yes                       |
| php8.4-soap        | SOAP protocol support (optional)           | No                        |
| php8.4-opcache     | Opcode caching for performance (optional)                 | Yes                       |
| php8.4-gd          | Image processing (GD library)                   | No                        |
| php8.4-bcmath      | Arbitrary precision math                         | Yes                       |
| php8.4-bz2         | bzip2 compression support (optional)                        | No                        |
| php8.4-imap        | IMAP email protocol support (optional)                      | No                        |
| php8.4-tidy        | HTML tidy library support (optional)                        | No                        |
| php8.4-ssh2        | SSH2 protocol support (optional)                            | No                        |
| php8.4-imagick     | ImageMagick image processing (optional)        | No                        |
| php8.4-sqlite3     | SQLite3 database support (optional)                         | Yes                       |
| php8.4-ldap        | LDAP protocol support (optional)                            | No                        |
| php8.4-memcached   | Memcached caching support (optional)                        | No                        |
| php8.4-redis       | Redis caching support (optional)                            | No                        |
| php8.4-fpm         | FastCGI Process Manager (optional)                          | Yes                       |

---------------

## Website-Mode

!!! info "Notice"
	This is the installation area to install suitefish on website-level. Please read the instructions carefully if you choose this method.
	
For website mode installation, the CMS runs as a standard website without requiring root-level access. This method is ideal for shared hosting or web hosting environments where you don’t manage the entire server. You can deploy the software on most web hosts without needing a dedicated VPS or root server, making it accessible and easy to set up. Website mode is perfect if you want a straightforward installation and management experience using default hosting features.

1. **Requirements:** Before getting started, make sure your system meets the requirements to run suitefish-cms.

2. **Download the Repository:** Visit the download section of the website, where you’ll find the download links for the latest release or choose to clone the repository directly from there: [https://github.com/bugfishtm/suitefish-cms](https://github.com/bugfishtm/suitefish-cms)
```bash
git clone https://github.com/bugfishtm/suitefish-cms
```

3. **Copy the Files:** Navigate to the `/source` directory in the repository or extract the chosen release file. Copy all files from the `/source` folder (or the extracted release file) to your web server's public HTML directory.

4. Set the file permissions for all uploaded files to `chmod 770` and ensure the owner and group are set to the correct web-server user (if not already).

5. **Configure the Website:** Open the website in your browser and follow the installation wizard. The wizard will guide you through the initial setup, where you’ll configure the database, administrative user, and other required settings.

6. **Set Up Cronjob:** See the "Setup Cronjob" section inside this documentation for information on how to setup the suitefish cronjob!

---------------

## Setup Cronjob

!!! info "Information"
	This step is required for both, website and root level instances.

!!! warning "Warning"
	Before setting up the cronjob, ensure you are using a compatible PHP version and specify the correct path to the PHP executable and the suitefish cronjob php script. The cronjob must be configured to run as your web server user (typically www-data), and both the PHP binary path and the script path should be adjusted to match your server setup for proper operation.
	
Choose one cronjob installation method below and use only that method. The cronjob should run every **5 minutes**.

### Method 1

If you use hosting software (like cPanel, Plesk) or a managed provider, use their interface to schedule the cronjob. You should setup `PATHTOSUITEFISH/_cronjob/cronjob.php` to run every 5 minutes. Be sure the scripts is executed with the php version stated in the documentation "Requirements" section.


### Method 3

If you have root access to the server you can add this cronjob to /etc/crontab:

```bash
*/5 * * * * www-data /usr/bin/php8.4 /PATHTOSUITEFISH/_cronjob/cronjob.php >/dev/null 2>&1
```

---------------

## Initial Login

!!! danger "For your security, change the default password immediately after your first login."
	**Important:** To ensure the security of your account and system, it is strongly recommended to change the password right after your first login. Failing to do so may expose your system to potential security risks.

Once the installation is complete, you can log in using the default credentials provided below.

**Username:** admin@admin.local  
**Password:** changeme

---------------

## Troubleshooting

If the `installer.php` script fails to generate the `settings.php` file for any reason, you can manually create the `settings.php` file by using the `settings.php` file located in the `_source/_sample` folder of this project. Simply rename the file from `_samples/settings_sample.php` to `settings.php` and make the necessary configuration changes. You also need to move this file to your suitefish websites root directory to work. Get sure permissions are set to the correct apache user, because the settings.php file should been written without problems. Wrong permissions may lead to problems in later use of suitefish-cms.