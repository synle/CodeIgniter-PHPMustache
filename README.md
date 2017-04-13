CodeIgniter-PHPMustache
=======================

Integrating PHP Mustache Engine (bobthecow) into Code Igniter


======================


The integration is done via the use of helper loader.

-Navigate to application/helpers.
<pre>
cd application/helpers
</pre>

-Use composer to get all the dependencies by calling
<pre>
composer install
</pre>
-(Optional) :  look at application/helper/composer.json for the version of php mustache in case you need to download some new stuffs.

application/helper/composer.json
<pre>
{
    "require": {
        "mustache/mustache": "~2.5"
    }
}
</pre>

By default this code autoload vendor helper
application/config/autoload.php - line 55
<pre>
$autoload['helper'] = array('vendor');
</pre>

When you don't require the helper always and don't want to autoload the `vendor` helper, you can also load Mustache in a controller/model this way:

<pre>
class Some_Model extends CI_Model
{
    private $mustache = NULL;
    
    public function __construct()
    {
        parent::__construct();

        $this->load->helper('vendor');
        $this->mustache = new Mustache_Engine;
    }
    
    private function loadMustacheTemplate()
    {
        $mustacheData = $this->getMyMustacheData();

        // the view data is returned (last parameter = true)
        $tpl = $this->load->view('mustached-template', '', true);
        $output = $this->mustache->render($tpl, $mustacheData);
        
        return $output;
    }
</pre>

Then rendering the mustache template is as easy as 
application/controller/welcome.php - line 22
<pre>
$m = new Mustache_Engine;
echo $m->render('Hello {{planet}}', array('planet' => 'World!')); // "Hello World!"
</pre>

For more information, please visit


-Code Igniter : http://ellislab.com/codeigniter <br />
-Bobthecow PHP Mustache : https://github.com/bobthecow/mustache.php <br/>
-Composer : http://getcomposer.org/
