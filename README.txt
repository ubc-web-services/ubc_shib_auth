
-- SUMMARY --

This module is an add-on the the regular shibboleth module to handle custom functionality related to Shibboleth.
In place of the standard shibboleth module's vhost path protection this module provides a user interface to select a 
content type, view modes and user roles that can access content using Shibboleth SSO.

Also to circumvent 'Session not generated on the first redirect to Drupal' https://www.drupal.org/node/1430242
when logging in with Shibboleth this module presents an intermediate login page with a customisable message block.

-- REQUIREMENTS --

Shibboleth

-- INSTALLATION --

Normal Drupal module installation, see http://drupal.org/node/70151 for further information.

-- CONFIGURATION --

Use the admin configuration page to configure settings at admin/config/people/shib_auth/ubc

You may also need to remove any existing Shibboleth path protection strings in existing vhost inc files:

<Directory "/www_data/aegir/platforms/drupalXXXX">   
        AuthType shibboleth
        ShibRequireSession Off
        require shibboleth      
</Directory>

<Location />
   AuthType shibboleth
   ShibRequireSession Off   
</Location>

<Location /old-path-base-url-to-remove/>
   Authtype shibboleth
   ShibRequireSession On
   require shibboleth
</Location>