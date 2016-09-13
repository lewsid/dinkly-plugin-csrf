Dinkly CSRF Protect v1.00 (dinkly-plugin-csrf)
==============================================

Protect your Dinkly application from CSRF exploits


Installation
------------

  1. Move the contents of the `plugins` folder into your dinkly project's `plugins` folder.

  2. Copy `csrf_protect.js` into `web/js`

  3. If it's not already present in config.yml, add the following lines under the 'plugins' section:

    ```yaml
    csrf_protect:
            apps:
                csrf_protect:
                    app_name: CsrfProtect
                    is_plugin: true
                    base_href: /protect
                    enabled: true
                    default_module: tokenizer
    ```

  4. Include the js in the header.php file of each app you wish to lock down: `<script type="text/javascript" src="/js/bootstrap.min.js"></script>`

  5. Enable CSRF protect at the app or module level by calling the static enforce function: 

  ```php
  class FrontendController extends Dinkly
  {
    /**
     * Default Constructor
     * 
     * @return bool: always returns true on successful construction of view
     * 
     */
    public function __construct()
    {
      CsrfProtect::enforce();

      return true;
    }
  }
  ```

Usage
-----

Ensure that all forms are being sent via POST. Assuming no one is trying anything funny, everything should work without issue.

If an invalid token is detected, an exception will be thrown. Override the CsrfProtect::enforce() function to customize behavior.


License
-------

The Dinkly CsrfProtect plugin is open-sourced software licensed under the MIT License.


Contact
-------

  - lewsid@lewsid.com
  - github.com/lewsid
