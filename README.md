Symfony Standard Edition + FOSUserBundle + HWIOAuthBundle (http://symfonytest.com/)
===================================================================================

Installing and Configuring Symfony
----------------------------------

[Installing] (http://symfony.com/doc/current/book/installation.html)

`curl -LsS http://symfony.com/installer > symfony.phar`

`sudo mv symfony.phar /usr/local/bin/symfony`

`chmod a+x /usr/local/bin/symfony`

To make your project work you need to add credentials to your app/config/parameters.yml.

Setting up Permissions
----------------------

`cd ProjectDir`

`rm -rf app/cache/*`

`rm -rf app/logs/*`

Some systems don't support chmod +a, but do support another utility called setfacl. 
You may need to enable ACL support on your partition and install setfacl before using it (as is the case with Ubuntu). 
This uses a command to try to determine your web server user and set it as HTTPDUSER:

        HTTPDUSER=`ps aux | grep -E '[a]pache|[h]ttpd|[_]www|[w]ww-data|[n]ginx' | grep -v root | head -1 | cut -d\  -f1`
        
        sudo setfacl -R -m u:"$HTTPDUSER":rwX -m u:`whoami`:rwX app/cache app/logs
        
        sudo setfacl -dR -m u:"$HTTPDUSER":rwX -m u:`whoami`:rwX app/cache app/logs


Generating a New Bundle Skeleton
--------------------------------

[New Bundle](http://symfony.com/doc/current/bundles/SensioGeneratorBundle/commands/generate_bundle.html)

`app/console generate:bundle`

Generating a New Doctrine Entity Stub
-------------------------------------

[New Entity](http://symfony.com/doc/current/bundles/SensioGeneratorBundle/commands/generate_doctrine_entity.html)

`app/console generate:doctrine:entity`

Add FOSUserBundle
-----------------

[FOSUserBundle](https://github.com/FriendsOfSymfony/FOSUserBundle)

Add HWIOAuthBundle
------------------

[HWIOAuthBundle](https://github.com/hwi/HWIOAuthBundle)

FOSUserBundle + HWIOAuthBundle
------------------------------

[FOSUserBundle + HWIOAuthBundle](https://gist.github.com/danvbe/4476697)

Enjoy!
