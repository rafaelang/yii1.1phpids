This extension uses the project PHPIDS like a application component for apply rules for attack detection and prevention. Perform a predefined reaction.
Credits and Thanks...

http://php-ids.org/contact/

#Requirements

Tested in Yii 1.1.5 and 1.1.4

#Usage

-Download and unzip the file in components directory.

Make .../components/ids/IDS/tmp writable.

-In config file change version 0.2...

```php
//'preload'=>array('log'),
'preload'=>array('log','ids'),
...
components = array(
...
        'ids'=>array(
            'class'=>'application.components.ids.CPhpIds',
            'genericMessage'=>'Error!!!',
                        'callback'=>create_function('',"echo 'Error!'; Yii::app()->end(); return false;"),
                        'enable'=>create_function('','return $_GET["r"] != "site/contact";'),
        ),
)
```

in version 0.2 and enable the callback parameters were added.

callback - is passed as parameter to call_user_func, see php manual

enable - performs the functions of the IDS is true. If false ignores the IDS. Receives a BOOL value or a function that returns a bool value, if passed a parameter is_callable, this parameter is passed to call_user_func (see PHP manual).

