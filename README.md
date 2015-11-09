# About
[Uguu.se](http://uguu.se) source code, stores files and deletes after X amount of time.

# Install
Tested with:
* Nginx+PHP5-FPM (PHP 5.4) on Debian 7 Wheezy 
* Apache (PHP 5.4) on Ubuntu 14.04 LTS
* Nginx+PHP5-FPM (PHP 5.6) on Debian 8 Jessie

Modify 
* Modify includes/core.php where to save files and other paths.
* Set correct paths in several other files. (Will add fix for this via config file instead).
* Change uguu.se to your own name in several files.
* Cron with check.sh: `crontab -e`
* After running `crontab -e`, add `0,15,30,45 * * * * bash /path/to/check.sh`, or read up on how cron works.
* Some extensions are blocked by default, this can be changed via includes/core.php's $block array.
* Everything else to your likings.

Change php.ini and nginx.conf settings to allow bigger uploads.

Make the uguu/ directory modifiable to the nginx user:
`setfacl -m u:www-data:rwx /path/to/uguu/directory/`

# Todo

* Restructure files.
* Make global config file.
* Probably a lot of things but I'm a lazy fuck, come with suggestions.


# Using the API

  * Leaving POST value 'name' empty will cause it to save using the original filename.
  * Leaving POST value 'randomname' empty will cause it to use original filename or custom name if 'name' is set to file.ext.
  
  * Putting anything into POST value 'randomname' will cause it to return a random filename + ext (xxxxxx.ext).
  * Putting a custom name into POST value 'name' will cause it to return a custom filename (yourpick.ext).
  
  E.g:
  * curl -i -F name=test.jpg -F file=@localfile.jpg http://uguu.se/api.php?d=upload (HTML Response)
  * curl -i -F name=test.jpg -F file=@localfile.jpg http://uguu.se/api.php?d=upload-tool (Plain text Response)


This will probably get changed later since it's messy and unpractical.

# Contact

[neku@pomf.se](mailto:neku@pomf.se) or [@Nekunekus](https://twitter.com/nekunekus).
