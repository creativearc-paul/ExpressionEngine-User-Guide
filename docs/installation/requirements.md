<!--
    This source file is part of the open source project
    ExpressionEngine User Guide (https://github.com/ExpressionEngine/ExpressionEngine-User-Guide)

    @link      https://expressionengine.com/
    @copyright Copyright (c) 2003-2020, Packet Tide, LLC (https://packettide.com)
    @license   https://expressionengine.com/license Licensed under Apache License, Version 2.0
-->

# System Requirements

[TOC]

## Recommended Requirements

It has always been a core goal to ensure that ExpressionEngine is usable on a broadly diverse and accessible range of machines by a broad and diverse range of people. 

**For the best experience**, this version of ExpressionEngine should use:

- [PHP](https://www.php.net/) 7.4 **OR** 8.2, running with [PHP-FPM](https://php.net/manual/en/install.fpm.php)
- [MySQL](https://www.mysql.com/) 5.6 or newer [including MySQL 8](https://u.expressionengine.com/article/mysql-8-and-expressionengine-tips-for-the-trailblazers) **OR** [Percona](https://www.percona.com/software/mysql-database/percona-server) 5.6 or newer

PHP 8.3 is fully supported, though there may be third-party add-ons that are not updated as rapidly as EE is. We also note there does not seem to be any noticeable performance improvement for EE from PHP 8.2 to 8.3.

[MariaDB](https://mariadb.org/) has long been a drop-in replacement for MySQL and has been used as the database by many EE sites. MariaDB often appears more performant than MySQL; however, there are a few edge cases and queries where the opposite is true. As is true with any database option, testing and fine-tuning the server settings as needed will give you optimal results.

While ExpressionEngine achieves compatibility with the newest releases of PHP and MySQL, there's also a lot of effort made to keep EE stable and running properly with older versions. [See the chart](#php-version-requirements-across-ee-versions) below for full details of EE and PHP version compatibility.

## The Bare Minimums

The developers recognize that not only are there a wide range of server setups, but also that sometimes we're not able to build our site on the machine of our dreams. Besides, no one likes it when they're forced to update an underlying tool unnecessarily.

If you are stuck in an older environment, ExpressionEngine _can_ run on PHP 7.2.5+ with 32M of memory, and MySQL 5.6.4+. 

PHP-FPM is also optional, but [tends to handily outperform mod_php](https://www.cloudways.com/blog/php-fpm-on-cloud/). 

That said, running older versions not only hurts performance—increasing the cost of your website—but most importantly puts your site **at risk of security vulnerabilities**. The PHP Group stopped providing support for PHP 5.6 [on December 31, 2018](https://php.net/supported-versions.php) and for PHP 7.1 [on December 1, 2019](https://www.php.net/eol.php). Oracle also ceased providing support for MySQL 5.5 at the same time.

Why not save yourself worry and hassle, and enjoy a faster and more secure site that costs less to maintain, by upgrading now? Here's an email you can send to your host if they need a little nudge:

```md
Hey there!

I'm running the PHP/MySQL-based content management system ExpressionEngine,
and would like to make sure it's speedy, secure, and making the most efficient
use of the resources available on my server.

Could I speak with someone about moving to an environment that has PHP 8+
and MySQL 5.6+? If they are available, I'd love to use PHP-FPM to implement PHP,
and Percona as a drop-in replacement for MySQL, too.

Thanks!
```


## Server Compatibility Wizard

If you're not sure whether your server meets the minimum requirements, the server wizard will run some tests and give you an answer.

- [Download](https://github.com/ExpressionEngine/ExpressionEngine-Server-Wizard/archive/refs/heads/master.zip) and unzip the archive.
- Upload the folder to your server.
- Point your web browser to the folder. For example: `https://example.com/ee_wizard`

## Browser Requirements for the Control Panel

ExpressionEngine's Control Panel targets compatibility with the final-release versions of the web browsers listed here, so it's important to keep your browser up to date. These browser requirements apply only to ExpressionEngine's Control Panel, not to your website, which **you are 100% in control of**.

- Chrome
- Safari
- Firefox
- Opera
- Microsoft Edge

NOTE: **Note:** In all cases, JavaScript must be enabled to use the Control Panel.

## Details and Notes

You can safely ignore the rest of this page unless you are experiencing problems, or are a sysadmin setting up a custom environment. All of the following are readily available in most managed environments.

### PHP Extensions Required

Though the following are available in PHP by default, some hosts may have them disabled until you ask for them.

- [GD (or GD 2) library](https://www.php.net/manual/en/ref.image.php)
- [File Information (fileinfo)](https://php.net/manual/en/book.fileinfo.php)
- [ZIP](https://www.php.net/manual/en/book.zip.php)
- [iconv](https://www.php.net/manual/en/book.iconv.php)


NOTE: **Note:** If you're on MediaTemple you will need [to create a phprc file](https://help.dreamhost.com/hc/en-us/articles/214894037-How-do-I-create-a-phprc-file-via-FTP-) that contains the following: `extension = fileinfo.so`

### PHP Extensions Recommended

These are recommended, but not required.

- The [Internationalization](https://php.net/manual/en/book.intl.php) extension, for full functionality of [variable modifiers](templates/variable-modifiers.md)
- [Multibyte String](https://php.net/manual/en/mbstring.installation.php) handling

### MySQL Privileges

The MySQL user connecting to the database must have the following privileges:

- `SELECT`
- `INSERT`
- `UPDATE`
- `DELETE`
- `CREATE`
- `INDEX`
- `ALTER`
- `DROP`

### Apache Server

If you are hosted on an Apache server, the `AcceptPathInfo` option needs to be enabled for URLs to work properly. Most servers are configured this way by default, but if yours is not, you have a few options:

- Include `AcceptPathInfo On` in your `.htaccess` file to enable it
- Ask your web host or server admin to enable the option
- Set your site's URLs to use [query strings](general/url-structure.md#query-strings)

### URL Segment Support

If the [Server Compatibility Wizard](#server-compatibility-wizard) lists URL Segment Support as _Unsupported_, you will need to set your site's URLs to use [query strings](general/url-structure.md#query-strings).

## Local Development

ExpressionEngine can be run locally on a number of local development environments. Below are just a few to help you get started.

NOTE: **Note:** When setting up your local environment, you must make sure it still meets the requirements listed above.

- **[Valet](https://laravel.com/docs/8.x/valet)** - (macOS only) Valet is the ExpressionEngine's team recommended local development environment. Super fast and easy to use.

- **[DDEV Local](https://www.ddev.com/ddev-local/)** - (macOS, Windows, Linux) DDEV Local makes working with Docker containers a breeze. Quickly set up and share environments that mirror your production.

- **[Devilbox](http://devilbox.org/)** - (macOS, Windows, Linux) Devilbox is another great stack which allows user to quickly get up and running with Docker environments. To install ExpressionEngine on Devilbox simply follow the [Setup ExpressionEngine Docs](https://devilbox.readthedocs.io/en/latest/examples/setup-expressionengine.html).

- **[MAMP](https://www.mamp.info/en/)** - (macOS, Windows) MAMP can be very convenient for local development, but it has some quirks. If you are using MAMP, you will need to use PHP 7+ due to outdated cURL and OpenSSL libraries that MAMP ships with its older versions of PHP.

## PHP Version Requirements Across EE Versions


<div class="ee-version-compatiblity">
    <div class="table-wrapper">
        <table>
            <thead>
                <tr>
                    <th><strong></strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>4.0</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>5.6</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>7.0</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>7.2</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>7.4</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>8.0</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>8.2</strong></th>
                    <th><img src="../_images/php-logo.svg" class="php-logo"><strong>8.3</strong></th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 7.4"><strong>7.4</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-fail"><span>PHP 5.6</span></td>
                    <td class="ee-maybe"><span>PHP 7.0</span></td>
                    <td class="ee-maybe"><span>PHP 7.2</span></td>
                    <td class="ee-works"><span>PHP 7.4</span></td>
                    <td class="ee-works"><span>PHP 8.0</span></td>
                    <td class="ee-works"><span>PHP 8.2</span></td>
                    <td class="ee-works"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 7.2.8">
                            <strong>7.2.8</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-fail"><span>PHP 5.6</span></td>
                    <td class="ee-maybe"><span>PHP 7.0</span></td>
                    <td class="ee-maybe"><span>PHP 7.2</span></td>
                    <td class="ee-works"><span>PHP 7.4</span></td>
                    <td class="ee-works"><span>PHP 8.0</span></td>
                    <td class="ee-works"><span>PHP 8.2</span></td>
                    <td class="ee-maybe"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 7.0">
                            <strong>7.0</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-fail"><span>PHP 5.6</span></td>
                    <td class="ee-maybe"><span>PHP 7.0</span></td>
                    <td class="ee-works"><span>PHP 7.2</span></td>
                    <td class="ee-works"><span>PHP 7.4</span></td>
                    <td class="ee-works"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 6.4.15">
                            <strong>6.4.15</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-maybe"><span>PHP 5.6</span></td>
                    <td class="ee-works"><span>PHP 7.0</span></td>
                    <td class="ee-works"><span>PHP 7.2</span></td>
                    <td class="ee-works"><span>PHP 7.4</span></td>
                    <td class="ee-works"><span>PHP 8.0</span></td>
                    <td class="ee-works"><span>PHP 8.2</span></td>
                    <td class="ee-maybe"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 6.0.0">
                            <strong>6.0.0</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-works"><span>PHP 5.6</span></td>
                    <td class="ee-works"><span>PHP 7.0</span></td>
                    <td class="ee-works"><span>PHP 7.2</span></td>
                    <td class="ee-works"><span>PHP 7.4</span></td>
                    <td class="ee-works"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 5.4.3">
                            <strong>5.4.3</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-works"><span>PHP 5.6</span></td>
                    <td class="ee-works"><span>PHP 7.0</span></td>
                    <td class="ee-works"><span>PHP 7.2</span></td>
                    <td class="ee-works"><span>PHP 7.4</span></td>
                    <td class="ee-works"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 4.3.8">
                            <strong>4.3.8</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-works"><span>PHP 5.6</span></td>
                    <td class="ee-works"><span>PHP 7.0</span></td>
                    <td class="ee-works"><span>PHP 7.2</span></td>
                    <td class="ee-maybe"><span>PHP 7.4</span></td>
                    <td class="ee-fail"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 3.5.1">
                            <strong>3.5.17</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-works"><span>PHP 5.6</span></td>
                    <td class="ee-works"><span>PHP 7.0</span></td>
                    <td class="ee-maybe"><span>PHP 7.2</span></td>
                    <td class="ee-fail"><span>PHP 7.4</span></td>
                    <td class="ee-fail"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 2.11.9">
                            <strong>2.11.9</strong>
                        </span>
                    </td>
                    <td class="ee-fail"><span>PHP 4.0</span></td>
                    <td class="ee-works"><span>PHP 5.6</span></td>
                    <td class="ee-works"><span>PHP 7.0</span></td>
                    <td class="ee-maybe"><span>PHP 7.2</span></td>
                    <td class="ee-fail"><span>PHP 7.4</span></td>
                    <td class="ee-fail"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
                <tr>
                    <td class="ee-version">
                        <span>
                            <img src="../_assets/images/ee-logo-black.svg" alt="ExpressionEngine 1.7.3">
                            <strong>1.7.3</strong>
                        </span>
                    </td>
                    <td class="ee-works"><span>PHP 4.0</span></td>
                    <td class="ee-works"><span>PHP 5.6</span></td>
                    <td class="ee-fail"><span>PHP 7.0</span></td>
                    <td class="ee-fail"><span>PHP 7.2</span></td>
                    <td class="ee-fail"><span>PHP 7.4</span></td>
                    <td class="ee-fail"><span>PHP 8.0</span></td>
                    <td class="ee-fail"><span>PHP 8.2</span></td>
                    <td class="ee-fail"><span>PHP 8.3</span></td>
                </tr>
            </tbody>
        </table>
    </div>
</div>

<div class="ee-version-compatiblity-legend">

<span class="ee-works"></span> - the PHP version is fully supported by this ExpressionEngine version

<span class="ee-fail"></span> - the system will not work under this PHP version, or a significant part of functionality will not work

<span class="ee-maybe"></span> - some of the functionality might work incorrectly, or compatibility has not been checked

</div>
