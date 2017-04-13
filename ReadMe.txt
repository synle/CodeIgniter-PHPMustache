The integration is done via the use of helper loader.

-Navigate to application/helper.  cd application/helper
-Use composer to get all the dependencies by calling composer install
-(Optional) :  look at application/helper/composer.json for the version of php mustache in case you need to download some new stuffs.

application/helper/composer.json
{
    "require": {
        "mustache/mustache": "~2.5"
    }
}


By default this code autoload vendor helper
application/config/autoload.php - line 55
$autoload['helper'] = array('vendor');



Then rendering the mustache template is as easy as 
application/controller/welcome.php - line 22

$m = new Mustache_Engine;
echo $m->render('Hello {{planet}}', array('planet' => 'World!')); // "Hello World!"


For more information, please visit


-Code Igniter : http://ellislab.com/codeigniter
-Bobthecow PHP Mustache : https://github.com/bobthecow/mustache.php
