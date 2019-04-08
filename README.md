# typo3-developer-resources


* [DOCTRINE](#doctrine)
    * [A simple query](#simple_query)
    
* [TYPOSCRIPT](#typoscript)

* [EXTBASE](#extbase)
    * [Command Controller](#command_controller)
    * [Use Command Controller on the CLI](#use_command_controller)
    * [Plugin wizard](#plugin_wizard)

* [TCA](#tca)

    * [Display Conditions](#display_cond)

* [FLEXFORM](#flexform)

* [JAVASCRIPT](#javascript)
    * [Backend JavaScript with Require.js](#backend)
* [SQL](#sql)

* [FORMS](#forms)

* [BASH](#bash)

* [USEFUL LINKS](#links)




# <a name="doctrine">DOCTRINE</a>
## <a name="simple_query">A simple query</a>
The following query retrieves an array of all page fields:
```
$queryBuilder = GeneralUtility::makeInstance(ConnectionPool::class)->getConnectionForTable(
	'pages'
)->createQueryBuilder();

$pageArray = $queryBuilder->select('*')
	->from('pages')
	->where(
		$queryBuilder->expr()->eq('uid', $pageUid)
	)
	->execute()->fetchAll();
```

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
A display condition renders a field in the tca, only if the given condition is met. With the onChange setting, you can enforce a frame reload.
```
'field_a' => [
	'displayCond' => 'FIELD:field_b:<:1',
	'exclude' => TRUE,
	'label' => 'This is field a,  showing only if field b is checked',
	'config' => [
		'type' => 'input',
		'eval' => 'required, trim'
	],
],
'field_b' => [
	'l10n_mode' => 'exclude',
	'exclude' => TRUE,
	'onChange' => 'reload',
	'label' => 'This field reload the frame when changed, so field_a can render',
	'config' => [
		'type' => 'check',
	],
],
```
# <a name="flexform">FLEXFORM</a>
# <a name="javascript">JAVASCRIPT</a>
## <a name="backend">Backend JavaScript with Require.js</a>
```
/** @var PageRenderer $pageRenderer */
$pageRenderer = GeneralUtility::makeInstance(PageRenderer::class);
$pageRenderer->loadRequireJsModule('TYPO3/CMS/ExtName/Modules/MyModule');
```
This works only for JS Modules. Example from the core:

```

/**
 * Module: TYPO3/CMS/Backend/AjaxDataHandler
 * Javascript functions to work with AJAX and interacting with Datahandler
 * through \TYPO3\CMS\Backend\Controller\SimpleDataHandlerController->processAjaxRequest (record_process route)
 */
define(['jquery',
  'TYPO3/CMS/Backend/Modal',
  'TYPO3/CMS/Backend/Icons',
  'TYPO3/CMS/Backend/Notification',
  'TYPO3/CMS/Backend/Severity'
], function($, Modal, Icons, Notification, Severity) {
  'use strict';
....
```
The first parameter is an array of modules, the second one is a function. The parameters of the function correspondend with the modules from the first array.

# <a name="sql">SQL</a>
# <a name="forms">FORMS</a>
# <a name="bash">BASH</a>
# <a name="links">Useful Links</a>
https://docs.typo3.org/typo3cms/CoreApiReference/
https://typo3.github.io/TYPO3.Icons/action.html
https://typo3worx.eu/2018/12/master-challenging-typo3-upgrade-projects/
