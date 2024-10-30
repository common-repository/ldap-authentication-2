=== LDAP Authentication 2 ===
Contributors: OrbitaNET, redgecko
Donate link: http://coder-notes.com/
Tags: ldap, authentication
Requires at least: 2.7
Tested up to: 3.4
Stable tag: 1.0
License: GPLv2 or later
License URI: http://www.gnu.org/licenses/gpl-2.0.html

Authenticates users through LDAP.

== Description ==

This plug-in extends Simple LDAP Authentication plug-in [Simple LDAP Authentication](http://wordpress.org/extend/plugins/simple-ldap-authentication).
Plug-in works as followed:

Entered credentials are checked by all hash types available on LDAP-server (ssha, smd5, crypt/standart-des, crypt/enhanced, crypt/md5, crypt/blowfish, sha, clear, md5) by specified login.

If password is correct:

If user already exist in WordPress database 

* Password, name, surname, e-mail are changed to those existing on LDAP-server.

If no such user is in WordPress database:

If automatic user transfer is disabled by plug-in settings:

* Existing user data is updated

If automatic user transfer is enabled by plug-in settings:

* Existing user data is updated

* New user is created with profile received from LDAP-server.

If the password was incorrect:

* Wrong password error is shown.

Features

1. Update user data
2. Updates user password
3. Checks password hash using crypt/standart-des, crypt/enhanced, crypt/md5, crypt/blowfish, ssha, smd5, sha, md5

== Installation ==

This section describes how to install the plugin and get it working.

e.g.

1. Upload and unzip `ldap-authentication-2.zip` to the `/wp-content/plugins/` directory
1. Activate the plugin through the 'Plugins' menu in WordPress
1. Place `<?php do_action('plugin_name_hook'); ?>` in your templates

== Screenshots ==

1. /trunc/screenshot1.png. 

== Frequently Asked Questions ==

**Can I use SSL on LDAP connection?**

Yes. You can enable SSL connection in the option page.

**Can I customize LDAP search filter?**

Yes. You can customize the search filters (user ID and group) in the option page.

**How do I use debug mode?**

This plugin has a built-in debug mode. When WP_DEBUG is enabled in wp-config.php, it will turn on the notices that some authenticatin information are added on the log entry.

== Changelog ==

= 1.0 =

Following functions are added to original plug-in:

updates user data

* _update_user ($username, $email, $first_name, $last_name, $role = '')

updates user password

* _update_user_password ($username , $password)

checks password hash using crypt/standart-des, crypt/enhanced, crypt/md5, crypt/blowfish

* _check_CRYPT ($plainTextPass, $ldapPass)

checks password hash using ssha

* _check_SSHA ($plainTextPass, $ldapPass)

checks password hash using smd5

* _check_SMD5 ($plainTextPass, $ldapPass)

checks password hash using sha

* _check_SHA ($plainTextPass, $ldapPass)

checks password for exact match

* _check_CLEAR ($plainTextPass, $ldapPass)

checks password hash using md5

* _check_MD5 ($plainTextPass, $ldapPass)

checks entered credentials

* _get_crypt_pass_by_type ($type, $password, $full_password)

== Upgrade Notice ==