# Coding procedures

## PHP coding standards

The code in the each of the Siteworks plugins is written in PHP with a few JavaScript files and CSS files.

PHP code follows PSR-1 (https://www.php-fig.org/psr/psr-1/) and PSR-12 (https://www.php-fig.org/psr/psr-12/). However we use underscores for all function and variable names.

Comments should such as to make the code easily followed by a new reader.

The overall structure of the main plugin "core" is described by the file "u3a Siteworks Core structure.odt" within that repository, and should be updated as necessary.

## Security

We follow the guidance given in https://developer.wordpress.org/plugins/security/

## Code editor

Any text editor may be used, but Visual Studio Code is recommended as it provides built-in help for checking the syntax of PHP functions and other useful features.

## Code checker

To check conformance with the above code is tested using PHP_CodeSniffer. Note that PHP_CodeSniffer can be integrated with Visual Studio Code.

This uses with a rule set in the file phpcs.xml, included in each plugin.

Where appropriate we may use phpcs:ignore to overrule a rule that should not apply to the following section of code.

## Code change control

Version management uses the "git" approach and the code is stored in GitHub.
Our documentation repository contains a powerpoint presentation about the basics of GitHub, and a description our use of GitHub is in "Github version control and update servers.docx"

This describes how the latest version of each plugin in always in branch 'main'. Changes are made in branches cloned from main.

Note that each plugin has a Changelog in the readme.txt file.

When merging a change into main a summary description of the change must be added to the top of the changelog.

## Versions

From time to time a new version of the plugin is released.

The new version number must entered into the base PHP file of the plugin in two places

* the initial comment section
* The PHP constant set at the top of this file

It must also be added to the change log in the readme.txt file.

## Update server

The latest published release of each plugin is held on an update server.

Each plugin uses the plugin update service provided in the Configuration plugin. This means that if the update service for Siteworks is changed, only the Configuration plugin needs to be changed.

