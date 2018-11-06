# typo3-developer-resources


* [TYPOSCRIPT](#typoscript)

* [EXTBASE](#extbase)
    * [Command Controller](#command_controller)
    * [Use Command Controller on the CLI](#use_command_controller)
    * [Plugin wizard](#plugin_wizard)

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
## <a name="use_command_controller">Use Command Controller on the CLI</a>  
location: ../typo3_src/typo3
```
./cli_dispatch.php extbase commandControllerName:runActionName   
```

## <a name="plugin_wizard">Plugin wizard</a>
in your Extensions **ext_local_conf.php** file:
```
// add plugin content element wizard
\TYPO3\CMS\Core\Utility\ExtensionManagementUtility::addPageTSConfig(
	'mod {
     	wizards.newContentElement.wizardItems.someName {
       		header = wizard_header
			elements {
				pluginName {
					iconIdentifier = extension-my_identifier
					title = wizard_title
					description = wizard_description
					tt_content_defValues {
						CType = list
						list_type = extensionKey_pluginName
					}
				}
			}
		  show = *
		}
	}
	mod.wizards.newContentElement.wizardItems.someName.before = *'
);
```

# <a name="tca">TCA</a>
## <a name="display_cond">Display Conditions</a>
# <a name="flexform">FLEXFORM</a>
# <a name="sql">SQL</a>
# <a name="forms">FORMS</a>
# <a name="bash">BASH</a>
