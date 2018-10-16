# typo3-developer-resources


* [TYPOSCRIPT](#typoscript)

* [EXTBASE](#extbase)
    * [Command Controller](#command_controller)

* [TCA](#tca)

    * [Display Conditions](#display_cond)

* [FLEXFORM](#flexform)

* [SQL](#sql)

* [FORMS](#forms)

* [BASH](#bash)




# <a name="typoscript">TYPOSCRIPT</a>
# <a name="extbase">EXTBASE</a>
## <a name="command_controller">Command Controller</a>
**ext_localconf.php**

    // register command controllers
    $GLOBALS['TYPO3_CONF_VARS']['SC_OPTIONS']['extbase']['commandControllers'][] = Vendor\Extension\NameCommandController::class;

**the controller class**

    use TYPO3\CMS\Extbase\Mvc\Controller\CommandController;

    /**
     * Command controller
     */
    class NameCommandController extends CommandController {

    	public function runNameCommand() {
    		// implementation
    	}
    }
# <a name="tca">TCA</a>
## <a name="display_cond">Display Conditions</a>
# <a name="flexform">FLEXFORM</a>
# <a name="sql">SQL</a>
# <a name="forms">FORMS</a>
# <a name="bash">BASH</a>
