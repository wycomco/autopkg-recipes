autopgk-recipes
===============

wycomco Recipes for use with AutoPkg (https://github.com/autopkg/autopkg)

Main target is to support wycomco's naming convention for munki repositories. Furthermore we are translating the munki relevant information to display German descriptions for our user base.

munki naming conventions
------------------------

We use site specific catalogs and a globally unique catalog named *generic*. Each catalog gets a equally named directory on the root level the munki directories. Inside these catalog directories we use a well defined folder structure to reflect the *category* of a munki package:

* apps (Applications)
* documents (Documents)
* drivers (Hardware specific drivers, p.e. for printers)
* fonts (Fonts)
* misc (All other types of packages)
* plugins (Usually internet plugins or application specific plugins)
* scripts (Here's the place for payload-free packages: printer-setups, system config commands etc.)

Inside these categories we then organize the packages by vendor/origin and product name.

As for application packages we distinguish between full applications (app\_\*) and updaters (upd\_\*) which require a previously installed application.

The resulting structure of our munki repository then will look like the following:

* catalogs
    * all
    * generic
    * siteA
* manifests
    * generic
    * siteA\_default
    * siteA\_computerGroup1
* pkgs
    * generic
        * apps
            * google
                * chrome
                    * app\_googlechrome-30.0.1599.101.dmg
                    * app\_googlechrome-31.0.1650.48.dmg
                    * ...
                * earth
                    * ...
            * mozilla
                * firefox
                    * app\_firefox-25.0.0.dmg
                    * app\_firefox-25.0.1.dmg
                    * ...
            * ...
        * documents
            * apple
                * documentation.dmg
                * ...
            * ...
        * drivers
            * printers
                * canon
                    * ir3035-ufr-ii-2.21.dmg
                    * ...
            * ...
        * fonts
        * misc
        * plugins
            * adobe
                * flashplayer
                    * flashplayer-11.9.900.152.dmg
                    * ...
            	* shockwave
            	* ...
        * scripts
            * wycomco
                * disableJava
                    * disableJava-1.4.dmg
                * disableUpdates
                * ...
    * siteA
        * apps
            * adobe
                * acrobatprox
                    * acrobatprox-10.4.1.dmg
            * ...
        * documents
            * siteA
                * templates-1.5.dmg
                * ...
        * drivers
        * fonts
            * siteA
                * mainfont-1.0.2.dmg
        * misc
        * plugins
        * scripts
* pkgsinfo
    * corresponding to *pkgs*
