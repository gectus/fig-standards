Руководство Оформления Кода
===========================

Это руководство продолжает и расширяет [PSR-1][], основной стандарт написания кода.

Целью данного руководства является снижение когнитивных трений при беглом 
осмотре кода от разных авторов. Оно делает это путем перечисления общих наборов 
правил и ожиданий о том, как оформлять PHP код.

Эти правила оформления являются производным от сходства между разными участвующими 
проектами. Когда разные авторы сотрудничают в нескольких проектах, это помогает 
иметь один набор нормативов для использования между всеми этими проектами. Таким 
образом польза этого руководства не в самих правилах, а в обмене этими правилами.

Ключевые слова "ДОЛЖЕН", "НЕ ДОЛЖЕН", "ТРЕБУЕТСЯ", "БУДЕТ", "НЕ БУДЕТ", "СЛЕДУЕТ",
"НЕ СЛЕДУЕТ", "РЕКОМЕНДУЕТСЯ", "МОЖЕТ", и "ДОПОЛНИТЕЛЬНО" в этом документе должны 
быть истолкованы как описано в [RFC 2119][].

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-1-basic-coding-standard.md


1. Обзор
--------

- Код ДОЛЖЕН следовать [PSR-1][].

- Код ДОЛЖЕН использовать 4 пробела для отступов, не табуляцию.

- НЕ ДОЛЖНО быть жесткого ограничения на длину строки; мягкое ограничение 
  ДОЛЖНО быть 120 знаков; строкам СЛЕДУЕТ быть 80 символов или менее.

- ДОЛЖНА быть одна пустая строка после объявления `namespace`, и ДОЛЖНА быть 
  одна пустая строка после блока с объявлениями `use`.

- Открывающие фигурные скобки для классов ДОЛЖНЫ быть на новой строке, и
  закрывающие фигурные скобки ДОЛЖНЫ быть на новой строке после тела класса.

- Открывающие фигурные скобки для методов ДОЛЖНЫ быть на новой строке, и 
  закрывающие фигурные скобки ДОЛЖНЫ быть на новой строке после тела метода.

- Область видимости ДОЛЖНА быть описана у всех свойств и методов; `abstract` и
  `final` ДОЛЖНЫ быть описаны перед областью видимости; `static` ДОЛЖНО быть 
  описано после области видимости.
  
- Ключевые слова управляющих конструкций ДОЛЖНЫ иметь один пробел после себя;
  вызовы методов и функции НЕ ДОЛЖНЫ.

- Открывающие фигурные скобки для управляющих конструкций ДОЛЖНЫ быть на той же
  строке, а закрывающие фигурные скобки ДОЛЖНЫ быть на новой строке после тела
  конструкции.

- Открывающие круглые скобки для управляющих конструкций НЕ ДОЛЖНЫ иметь пробел 
  после себя, а закрывающие круглые скобки для управляющих конструкций НЕ ДОЛЖНЫ 
  иметь пробел перед собой.

### 1.1. Пример

Этот пример как краткий обзор включает в себя некоторые из ниже указанных правил:

```php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleFunction($a, $b = null)
    {
        if ($a === $b) {
            bar();
        } elseif ($a > $b) {
            $foo->bar($arg1);
        } else {
            BazClass::bar($arg2, $arg3);
        }
    }

    final public static function bar()
    {
        // тело метода
    }
}
```

2. Общее
--------

### 2.1 Основной стандарт написания кода

Код ДОЛЖЕН следовать всем правилам изложенным в [PSR-1][].

### 2.2 Файлы

Все PHP файлы ДОЛЖНЫ использовать переводы строк Unix LF (linefeed).

Все PHP файлы ДОЛЖНЫ оканчиваться одной пустой строкой.

Закрывающий `?>` тег ДОЛЖЕН быть исключен из файлов содержащих только PHP.

### 2.3. Строки

НЕ ДОЛЖНО быть жесткого ограничения на длину строки.

Мягкое ограничение на длину строки ДОЛЖНО быть 120 знаков; автоматические проверки 
стиля ДОЛЖНЫ предупредить но НЕ ДОЛЖНЫ выдавать ошибку на мягкие ограничения.

Строкам НЕ СЛЕДУЕТ быть длиннее 80 знаков; более длинные строки СЛЕДУЕТ 
разбивать на несколько последующих строк не более чем 80 знаков в каждой.

НЕ ДОЛЖНО быть замыкающий пробелов в конце строки на не пустых строках.

Пустые строки МОГУТ быть добавлены для улучшения читабельности и указания 
связанных блоков кода.

НЕ ДОЛЖНО быть более одного оператора в строке.

### 2.4. Отступы

Код ДОЛЖЕН использовать отступ в 4 пробела, и НЕ ДОЛЖЕН использовать табуляцию 
для отступов.

> Обратите особое внимание: Использование только пробелов, и не смешивание 
> пробелов и табуляции, помогает избежать проблем с диффами, патчами, историей, 
> и аннотациями. Использование пробелов также позволяет легко вставить 
> тонко-настроенный суб-отступ для межстрочного выравнивания.

### 2.5. Ключевые слова и True/False/Null

PHP [Ключевые слова][] ДОЛЖНЫ быть в нижнем регистре.

PHP константы `true`, `false`, и `null` ДОЛЖНЫ быть в нижнем регистре.

[Ключевые слова]: http://php.net/manual/en/reserved.keywords.php



3. Объявление Пространства имен и Use
-------------------------------------

Если они присутствуют, то ДОЛЖНА быть одна пустая строка после объявления 
`namespace`.

Если они присутствуют, все объявления `use` ДОЛЖНЫ идти после объявления 
`namespace`.

ДОЛЖНО быть ключевое слово `use` на каждое объявление.

ДОЛЖНА быть одна пустая строка после блока `use`.

Например:

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... дополнительный PHP код ...

```


4. Классы, Свойства, и Методы
-----------------------------

Термин "класс" относится ко всем классам, интерфейсам и трейтам.

### 4.1. Extends и Implements

Ключевые слова `extends` и `implements` ДОЛЖНЫ быть объявлены на той же строке, 
что и имя класса.

Открывающая фигурная скобка для класса ДОЛЖНА идти на своей собственной строке; 
закрывающая фигурная скобка для класса ДОЛЖНА идти на следующей строке после тела 
класса.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // константы, свойства, методы
}
```

Список `implements` МОЖЕТ быть разделен на несколько строк, где каждая 
последующая строка с одним отступом. При этом первый элемент в списке ДОЛЖЕН 
быть на следующей строке, и ДОЛЖЕН быть только один интерфейс на строку.

```php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements
    \ArrayAccess,
    \Countable,
    \Serializable
{
    // константы, свойства, методы
}
```

### 4.2. Свойства

Область видимости ДОЛЖНА быть объявлена на все свойства.

Ключевое слово `var` НЕ ДОЛЖНО быть использовано для объявления свойства.

НЕ ДОЛЖНО быть более одного свойства объявленного на оператор.

Имена свойств НЕ СЛЕДУЕТ делать с подчеркиванием в качестве приставки для 
обозначения области видимости protected или private.

Объявление свойства выглядит следующим образом.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
```

### 4.3. Методы

Область видимости ДОЛЖНА быть объявлена на все методы.

Имена методов НЕ СЛЕДУЕТ делать с подчеркиванием в качестве приставки для 
обозначения области видимости protected или private.

Имена методов НЕ ДОЛЖНЫ быть объявлены с пробелом после имени метода. Открывающая 
фигурная скобка ДОЛЖНА идти на своей собственной строке, а закрывающая фигурная 
скобка ДОЛЖНА быть на следующей строке после тела метода. НЕ ДОЛЖНО быть пробела 
после открытия круглой скобки, и НЕ ДОЛЖНО быть пробела перед закрывающей круглой 
скобкой.

Объявление метода выглядит следующим образом. Обратите внимание на размещение
круглых скобок, запятых, пробелов и фигурных скобок:

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // тело метода
    }
}
```    

### 4.4. Аргументы Метода

В списке аргументов, НЕ ДОЛЖНО быть пробела перед каждой запятой, и
ДОЛЖЕН быть один пробел после каждой запятой.

Аргументы Метода со значениями по умолчанию должны идти в конце списка
аргументов.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // тело метода
    }
}
```

Список аргументов МОЖЕТ быть разделен на несколько строк, где каждая
последующая строка с одним отступом. При этом первый элемент в списке ДОЛЖЕН 
быть на следующей строке, и ДОЛЖЕН быть только один аргумент на строку.

Когда список аргументов разделен на несколько строк, закрывающая круглая скобка 
и открывающая фигурная скобка ДОЛЖНЫ быть установлены вместе на их собственную 
строку с одним пробелом между ними.

```php
<?php
namespace Vendor\Package;

class ClassName
{
    public function aVeryLongMethodName(
        ClassTypeHint $arg1,
        &$arg2,
        array $arg3 = []
    ) {
        // тело метода
    }
}
```

### 4.5. `abstract`, `final`, и `static`

Если они присутствуют, то `abstract` и `final` ДОЛЖНЫ предшествовать перед 
объявлением области видимости.

Если присутствует объявление `static`, то оно ДОЛЖНО идти после объявления 
области видимости.

```php
<?php
namespace Vendor\Package;

abstract class ClassName
{
    protected static $foo;

    abstract protected function zim();

    final public static function bar()
    {
        // тело метода
    }
}
```

### 4.6. Вызовы Метода и Функции

При выполнении вызова метода или функции, НЕ ДОЛЖНО быть пробела между
именем метода или функции и открывающей круглой скобкой, НЕ ДОЛЖНО быть пробела 
после открытия круглой скобки, а также НЕ ДОЛЖНО быть пробела перед 
закрывающей круглой скобкой. В списке аргументов, НЕ ДОЛЖНО быть пробела перед
каждой запятой, и ДОЛЖЕН быть один пробел после каждой запятой.

```php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
```

Списки аргументов МОГУТ быть разделены на несколько строк, где каждая
последующая строка с одним отступом. При этом первый элемент в списке ДОЛЖЕН 
быть на следующей строке, и ДОЛЖЕН быть только один аргумент на строку.

```php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
```

5. Управляющие конструкции
--------------------------

Общие правила стиля для управляющих конструкций следующие:

- ДОЛЖЕН быть один пробел после ключевого слова управляющей конструкции
- НЕ ДОЛЖНО быть пробела после открывающих круглых скобок
- НЕ ДОЛЖНО быть пробела перед закрывающими круглыми скобками
- ДОЛЖЕН быть один пробел между закрывающей круглой скобкой и открывающей
  фигурной скобкой
- Тело конструкции должно быть с одним отступом
- Закрывающая фигурная скобка ДОЛЖНА быть на следующей строке после тела 
  управляющей конструкции

Тело каждой конструкции ДОЛЖНО быть заключено в фигурные скобки. Это 
стандартизирует вид конструкций, и уменьшает вероятность внесения ошибок 
при добавлении новых строк к телу управляющей конструкции.


### 5.1. `if`, `elseif`, `else`

Оператор `if` выглядит следующим образом. Обратите внимание на размещение
круглых скобок, пробелов и фигурных скобок; и что `else` и `elseif` находятся 
на одной линии, как и закрывающая фигурная скобка тела оператора.

```php
<?php
if ($expr1) {
    // тело оператора if
} elseif ($expr2) {
    // тело оператора elseif
} else {
    // тело оператора else;
}
```

Ключевое слово `elseif` СЛЕДУЕТ использовать вместо `else if` так что все 
управляющие ключевые слова выглядят как единые слова.


### 5.2. `switch`, `case`

Конструкция `switch` выглядит следующим образом. Обратите внимание на размещение
круглых скобок, пробелов и фигурных скобок. Оператор `case` ДОЛЖЕН быть с одним 
отступом от `switch`, а ключевое слово `break` (или другое завершающее ключевое 
слово) ДОЛЖНО быть с таким же отступом как тело оператора `case`. ДОЛЖЕН быть 
комментарий, такой как `// no break` когда есть преднамеренное падение в не-пустое
тело оператора `case`.

```php
<?php
switch ($expr) {
    case 0:
        echo 'First case, with a break';
        break;
    case 1:
        echo 'Second case, which falls through';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Third case, return instead of break';
        return;
    default:
        echo 'Default case';
        break;
}
```


### 5.3. `while`, `do while`

Оператор `while` выглядит следующим образом. Обратите внимание на размещение
круглых скобок, пробелов и фигурных скобок.

```php
<?php
while ($expr) {
    // structure body
}
```

Кроме того, оператор `do while` выглядит следующим образом. Обратите внимание 
на размещение круглых скобок, пробелов и фигурных скобок.

```php
<?php
do {
    // structure body;
} while ($expr);
```

### 5.4. `for`

Оператор `for` выглядит следующим образом. Обратите внимание на размещение
круглых скобок, пробелов и фигурных скобок.

```php
<?php
for ($i = 0; $i < 10; $i++) {
    // тело оператора for
}
```

### 5.5. `foreach`
    
Оператор `foreach` выглядит следующим образом. Обратите внимание на размещение
круглых скобок, пробелов и фигурных скобок.

```php
<?php
foreach ($iterable as $key => $value) {
    // тело оператора foreach
}
```

### 5.6. `try`, `catch`

Блок `try catch` выглядит следующим образом. Обратите внимание на размещение
круглых скобок, пробелов и фигурных скобок.

```php
<?php
try {
    // тело оператора try
} catch (FirstExceptionType $e) {
    // тело оператора catch
} catch (OtherExceptionType $e) {
    // тело оператора catch
}
```

6. Замыкания
------------

Замыкания ДОЛЖНЫ быть объявлены с пробелом после ключевого слова `function`,
и пробелом перед и после ключевого слова `use`.

Открывающая фигурная скобка ДОЛЖНА идти на той же строке, а закрывающая 
фигурная скобка ДОЛЖНА идти на следующей строке после тела функции.

НЕ ДОЛЖНО быть пробела после открывающей круглой скобки списка аргументов
или списка переменных, и НЕ ДОЛЖНО быть пробела перед закрывающей круглой 
скобкой списка аргументов или списка переменных.

В списке аргументов и списке переменных НЕ ДОЛЖНО быть пробела перед каждой 
запятой, и ДОЛЖЕН быть один пробел после каждой запятой.

Аргументы замыкания со значениями по умолчанию должны идти в конце списка
аргументов.

Объявление замыкания выглядит следующим образом. Обратите внимание на 
размещение круглых скобок, запятых, пробелов и фигурных скобок:

```php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // тело функции
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // тело функции
};
```

Список аргументов и список переменных МОЖЕТ быть разделен на несколько строк, 
где каждая последующая строка с одним отступом. При этом первый элемент 
в списке ДОЛЖЕН быть на следующей строке, и ДОЛЖЕН быть только один аргумент 
или переменная на строку.

Когда конечный список (или аргументов или переменных) разделен на несколько 
строк, закрывающая круглая скобка и открывающая фигурная скобка ДОЛЖНЫ быть 
установлены вместе на их собственную строку с одним пробелом между ними.

Ниже приведены примеры замыканий с и без списка аргументов и списка
переменных разбитого на несколько строк.

```php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
   // тело функции
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // тело функции
};

$longArgs_longVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // тело функции
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
   // тело функции
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
   // тело функции
};
```

Обратите внимание, что правила форматирования применяются также когда
замыкание используется прямо как аргумент при вызове метода или функции.

```php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // тело функции
    },
    $arg3
);
```


7. Заключение
-------------

Есть много элементов оформления и практик умышленно опущенных в этом
руководстве. Они включают, но не ограничиваются:

- Объявление глобальных переменных и глобальных констант

- Объявление функций

- Операторы и присваивания

- Вписанное выравнивание

- Комментарии и блоки документации

- Приставки и окончания имен классов

- Практический опыт

Будущее рекомендации МОГУТ пересмотреть и расширить это руководство для решения 
тех или иных элементов оформления и практик.


Приложение A. Опрос
-------------------

При написании этого руководства оформления, группа провела опрос участвующих 
проектов для определения общих практик. Опрос сохраняется в настоящем 
документе для потомков.

### A.1. Данные опроса

    url,http://www.horde.org/apps/horde/docs/CODING_STANDARDS,http://pear.php.net/manual/en/standards.php,http://solarphp.com/manual/appendix-standards.style,http://framework.zend.com/manual/en/coding-standard.html,http://symfony.com/doc/2.0/contributing/code/standards.html,http://www.ppi.io/docs/coding-standards.html,https://github.com/ezsystems/ezp-next/wiki/codingstandards,http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html,https://github.com/UnionOfRAD/lithium/wiki/Spec%3A-Coding,http://drupal.org/coding-standards,http://code.google.com/p/sabredav/,http://area51.phpbb.com/docs/31x/coding-guidelines.html,https://docs.google.com/a/zikula.org/document/edit?authkey=CPCU0Us&hgd=1&id=1fcqb93Sn-hR9c0mkN6m_tyWnmEvoswKBtSc0tKkZmJA,http://www.chisimba.com,n/a,https://github.com/Respect/project-info/blob/master/coding-standards-sample.php,n/a,Object Calisthenics for PHP,http://doc.nette.org/en/coding-standard,http://flow3.typo3.org,https://github.com/propelorm/Propel2/wiki/Coding-Standards,http://developer.joomla.org/coding-standards.html
    voting,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,no,no,no,?,yes,no,yes
    indent_type,4,4,4,4,4,tab,4,tab,tab,2,4,tab,4,4,4,4,4,4,tab,tab,4,tab
    line_length_limit_soft,75,75,75,75,no,85,120,120,80,80,80,no,100,80,80,?,?,120,80,120,no,150
    line_length_limit_hard,85,85,85,85,no,no,no,no,100,?,no,no,no,100,100,?,120,120,no,no,no,no
    class_names,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,studly,lower_under,studly,lower,studly,studly,studly,studly,?,studly,studly,studly
    class_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,next,next,next,next,next,next,same,next,next
    constant_names,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper,upper
    true_false_null,lower,lower,lower,lower,lower,lower,lower,lower,lower,upper,lower,lower,lower,upper,lower,lower,lower,lower,lower,upper,lower,lower
    method_names,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel,lower_under,camel,camel,camel,camel,camel,camel,camel,camel,camel,camel
    method_brace_line,next,next,next,next,next,same,next,same,same,same,same,next,next,same,next,next,next,next,next,same,next,next
    control_brace_line,same,same,same,same,same,same,next,same,same,same,same,next,same,same,next,same,same,same,same,same,same,next
    control_space_after,yes,yes,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes,yes
    always_use_control_braces,yes,yes,yes,yes,yes,yes,no,yes,yes,yes,no,yes,yes,yes,yes,no,yes,yes,yes,yes,yes,yes
    else_elseif_line,same,same,same,same,same,same,next,same,same,next,same,next,same,next,next,same,same,same,same,same,same,next
    case_break_indent_from_switch,0/1,0/1,0/1,1/2,1/2,1/2,1/2,1/1,1/1,1/2,1/2,1/1,1/2,1/2,1/2,1/2,1/2,1/2,0/1,1/1,1/2,1/2
    function_space_after,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no,no
    closing_php_tag_required,no,no,no,no,no,no,no,no,yes,no,no,no,no,yes,no,no,no,no,no,yes,no,no
    line_endings,LF,LF,LF,LF,LF,LF,LF,LF,?,LF,?,LF,LF,LF,LF,?,,LF,?,LF,LF,LF
    static_or_visibility_first,static,?,static,either,either,either,visibility,visibility,visibility,either,static,either,?,visibility,?,?,either,either,visibility,visibility,static,?
    control_space_parens,no,no,no,no,no,no,yes,no,no,no,no,no,no,yes,?,no,no,no,no,no,no,no
    blank_line_after_php,no,no,no,no,yes,no,no,no,no,yes,yes,no,no,yes,?,yes,yes,no,yes,no,yes,no
    class_method_control_brace,next/next/same,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/next,same/same/same,same/same/same,same/same/same,same/same/same,next/next/next,next/next/same,next/same/same,next/next/next,next/next/same,next/next/same,next/next/same,next/next/same,same/same/same,next/next/same,next/next/next

### A.2. Условные обозначения опроса 

`indent_type`:
Тип отступов. `tab` = "использование табуляции", `2` или `4` = "количество пробелов"

`line_length_limit_soft`:
"Мягкое" ограничение на длину строки, в знаках. `?` = не различимо или нет ответа, `no` значит нет лимита.

`line_length_limit_hard`:
"Жесткое" ограничение на длину строки, в знаках. `?` = не различимо или нет ответа, `no` значит нет лимита.

`class_names`:
Как классы называются? `lower` = только строчные, `lower_under` = строчные с подчеркиванием разделителем, `studly` = StudlyCase.

`class_brace_line`:
Идет ли открывающая фигурная скобка класса на той же (`same`) линии что и ключевое слово класса, или на следующей (`next`) линии после нее?

`constant_names`:
How are class constants named? `upper` = Uppercase with underscore separators.

`true_false_null`:
Ключевые слова `true`, `false`, и `null` написаны полностью строчными (`lower`), или полностью прописными (`upper`)?

`method_names`:
Как методы называются? `camel` = `camelCase`, `lower_under` = строчные с подчеркиванием разделителем.

`method_brace_line`:
Идет ли открывающая фигурная скобка метода на той же (`same`) линии что и ключевое слово метода, или на следующей (`next`) линии после нее?

`control_brace_line`:
Идет ли открывающая фигурная скобка управляющей конструкции на той же (`same`) линии, или на следующей (`next`)?

`control_space_after`:
Есть ли пробел после ключевого слова управляющей конструкции?

`always_use_control_braces`:
Всего использовать фигурные скобки для управляющих конструкций?

`else_elseif_line`:
Когда используется `else` или `elseif`, идет ли оно на той же (`same`) линии, что и предыдущая закрывающая фигурная скобка, или оно идет на следующей (`next`) линии?

`case_break_indent_from_switch`:
На сколько отступов `case` и `break` от открывающего оператора `switch`?

`function_space_after`:
При вызове функций есть ли пробел после имени функции и перед открывающими круглыми скобками?

`closing_php_tag_required`:
В файлах содержащих только PHP необходим ли закрывающий `?>` тег?

`line_endings`:
Какой тип окончания строки используется?

`static_or_visibility_first`:
Когда объявляется метод, то `static` идет впереди, или область видимости идет впереди?

`control_space_parens`:
В выражении управляющей конструкции, есть ли пробел после открывающей круглой скобки, и пробел перед закрывающей круглой скобкой? `yes` = `if ( $expr )`, `no` = `if ($expr)`.

`blank_line_after_php`:
Есть ли пустая строка после открытия PHP тега?

`class_method_control_brace`:
Сводка на какой линии идет открывающая фигурная скобка после классов, методов, и управляющих конструкций.

### A.3. Результаты опроса

    indent_type:
        tab: 7
        2: 1
        4: 14
    line_length_limit_soft:
        ?: 2
        no: 3
        75: 4
        80: 6
        85: 1
        100: 1
        120: 4
        150: 1
    line_length_limit_hard:
        ?: 2
        no: 11
        85: 4
        100: 3
        120: 2
    class_names:
        ?: 1
        lower: 1
        lower_under: 1
        studly: 19
    class_brace_line:
        next: 16
        same: 6
    constant_names:
        upper: 22
    true_false_null:
        lower: 19
        upper: 3
    method_names:
        camel: 21
        lower_under: 1
    method_brace_line:
        next: 15
        same: 7
    control_brace_line:
        next: 4
        same: 18
    control_space_after:
        no: 2
        yes: 20
    always_use_control_braces:
        no: 3
        yes: 19
    else_elseif_line:
        next: 6
        same: 16
    case_break_indent_from_switch:
        0/1: 4
        1/1: 4
        1/2: 14
    function_space_after:
        no: 22
    closing_php_tag_required:
        no: 19
        yes: 3
    line_endings:
        ?: 5
        LF: 17
    static_or_visibility_first:
        ?: 5
        either: 7
        static: 4
        visibility: 6
    control_space_parens:
        ?: 1
        no: 19
        yes: 2
    blank_line_after_php:
        ?: 1
        no: 13
        yes: 8
    class_method_control_brace:
        next/next/next: 4
        next/next/same: 11
        next/same/same: 1
        same/same/same: 6
