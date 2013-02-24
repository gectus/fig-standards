Ниже описаны обязательные требования, которые должны соблюдаться в
автозагрузчике для взаимодействия.

Обязательные
------------

* Полностью сформированное пространство имен и класс должны иметь следующую
  структуру `\<Vendor Name>\(<Namespace>\)*<Class Name>`
* Каждое пространство имен должно иметь пространство имен верхнего уровня  ("Vendor Name").
* Каждое пространство имен может содержать столько вложенных пространств имен, 
  сколько ему необходимо.
* Каждый разделитель пространств имен преобразуется в `DIRECTORY_SEPARATOR` при 
  загрузке из файловой системы.
* Каждый символ `_` в ИМЕНИ КЛАССА преобразуется в `DIRECTORY_SEPARATOR`.
  Символ `_` не имеет особого значения в пространстве имен.
* Полностью сформированное пространство имен и класс дополняются `.php` при 
  загрузке из файловой системы.
* Буквы в именах поставщиков, пространствах имен, и именах классов могут в любой комбинации
  строчных и прописных букв.

Примеры
-------

* `\Doctrine\Common\IsolatedClassLoader` => `/path/to/project/lib/vendor/Doctrine/Common/IsolatedClassLoader.php`
* `\Symfony\Core\Request` => `/path/to/project/lib/vendor/Symfony/Core/Request.php`
* `\Zend\Acl` => `/path/to/project/lib/vendor/Zend/Acl.php`
* `\Zend\Mail\Message` => `/path/to/project/lib/vendor/Zend/Mail/Message.php`

Подчеркивания в Пространствах имен и Именах классов
---------------------------------------------------

* `\namespace\package\Class_Name` => `/path/to/project/lib/vendor/namespace/package/Class/Name.php`
* `\namespace\package_name\Class_Name` => `/path/to/project/lib/vendor/namespace/package_name/Class/Name.php`

Стандарты установленные здесь должны быть наименьшим общим знаменателем для 
безболезненного взаимодействия с автозагрузчиком. Вы можете проверить, что вы следуете 
этим стандартам, используя предложенный пример SplClassLoader, реализующий возможность 
загружать PHP 5.3 классы.


Пример реализации
-----------------

Ниже приведен пример функции, чтобы просто показать, как выше
предложенные стандарты будут автоматически загружены.
```php
<?php

function autoload($className)
{
    $className = ltrim($className, '\\');
    $fileName  = '';
    $namespace = '';
    if ($lastNsPos = strrpos($className, '\\')) {
        $namespace = substr($className, 0, $lastNsPos);
        $className = substr($className, $lastNsPos + 1);
        $fileName  = str_replace('\\', DIRECTORY_SEPARATOR, $namespace) . DIRECTORY_SEPARATOR;
    }
    $fileName .= str_replace('_', DIRECTORY_SEPARATOR, $className) . '.php';

    require $fileName;
}
```

Реализация SplClassLoader
-------------------------

Следующий gist представляет собой пример реализации SplClassLoader, который может
загружать ваши классы, если вы будете следовать выше предложенным стандартам для 
автозагрузчика. На данным момент это рекомендованный способ загружать PHP
5.3 классы, которые следуют этим стандартам.

* [http://gist.github.com/221634](http://gist.github.com/221634)

