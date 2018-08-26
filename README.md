# PSR-2: Руководство по стилю написания кода

Данные правила являются переводом на русский язык правил [PSR-2] от компании PHP Framework Interop Group.

Это руководство дополняет и расширяет [PSR-1], основной стандарт кода.

Цель этого руководства - уменьшить когнитивное разногласие при сканировании кода от разных авторов. Оно делает это, перечисляя общий набор правил и ожиданий относительно того, как форматировать PHP код.

Правила стиля в данном документе основаны на общих чертах среди различных членов
проектов. Когда различные авторы сотрудничают по нескольким проектам, это помогает
иметь один набор руководящих принципов для всех проектов. Таким образом
преимущество этого руководства не в самих правилах, а в обмене
этими правилами.

Ключевые слова «ОБЯЗАН», «ОБЯЗАН НЕ», «ТРЕБУЕТСЯ», «ДОЛЖЕН», «ДОЛЖЕН НЕ», «СЛЕДУЕТ»,
«СЛЕДУЕТ НЕ», «РЕКОМЕНДУЕТСЯ», «МОЖЕТ» и «ПО ЖЕЛАНИЮ» в этом документе нужно
интерпретировать, как описано в стандарте [RFC 2119].

[RFC 2119]: http://www.ietf.org/rfc/rfc2119.txt
[PSR-0]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-0.md
[PSR-1]: https://github.com/nk-sn/PSR-1
[PSR-2]: https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md

## 1. Обзор

- Код ОБЯЗАН следовать "основному стандарту кода" PSR [[PSR-1]].

- Код ОБЯЗАН использовать 4 пробела для отступов, а не табы.

- ОБЯЗАНО НЕ быть жестких пределов длины строки; мягкий предел ОБЯЗАН быть 120 символов; СЛЕДУЕТ чтобы строки были 80 символов или меньше.
  
- ОБЯЗАНА быть одна пустая строка после объявления `namespace`, и ОБЯЗАНА быть одна пустая строка после блока объявления `use`.  
  
- Открывающие фигурные скобки для классов ОБЯЗАНЫ переходить на следующую строку, а закрывающие фигурные скобки ОБЯЗАНЫ переходить на следующую строку после тела класса.
  
- Открывающие фигурные скобки для методов класса ОБЯЗАНЫ переходить на следующую строку, а закрывающие фигурные скобки ОБЯЗАНЫ переходить на следующую строку после тела метода.

- Видимость ОБЯЗАНА быть объявлена во всех свойствах и методах; `abstract` и `final` ОБЯЗАНЫ объявляться перед видимостью; `static` ОБЯЗАНО объявляться после видимости.

- Ключевые слова управляющих структур ОБЯЗАНЫ иметь один пробел после них; методы и вызовы функций ОБЯЗАНЫ НЕ.

- Открывающие фигурные скобки для управляющих структур ОБЯЗАНЫ идти по одной и той же линии, и закрывающие фигурные скобки ОБЯЗАНЫ переходить на следующую строку после тела управлябщей структуры.
  
- Открытие круглых скобок для управляющих структур ОБЯЗАНО НЕ иметь пробела после них, и закрывающие круглые скобки для управляющих структур ОБЯЗАНЫ НЕ иметь пробела до.

### 1.1. Пример

Этот пример включает некоторые из приведенных ниже правил в качестве краткого обзора:

~~~php
<?php
namespace Vendor\Package;

use FooInterface;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class Foo extends Bar implements FooInterface
{
    public function sampleMethod($a, $b = null)
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
        // method body
    }
}
~~~

## 2. Общие

### 2.1. Основной стандарт кода

Код ОБЯЗАН следовать всем правилам изложенным в [PSR-1].

### 2.2. Файлы

Все PHP файлы ОБЯЗАНЫ использовать окончание строки Unix LF (linefeed).

Все файлы PHP ОБЯЗАНЫ заканчиваться одной пустой строкой.

Закрывающий тег `?>` ОБЯЗАН быть опущен из файлов, содержащих только PHP.

### 2.3. Строки

ОБЯЗАНО НЕ быть жестких ограничений длины строки.

Мягкий предел длины строки ОБЯЗАН быть 120 символов; автоматические проверки стиля ОБЯЗАНЫ предупредить, но ОБЯЗАН НЕ выводить ошибку при мягком пределе.

НЕ СЛЕДУЕТ чтобы строки были длиннее 80 символов; строки длиннее этого предела СЛЕДУЕТ
разбивать на несколько последующих строк длиной не более 80 символов.

ОБЯЗАНО НЕ быть конечных пробелов в конце непустых строк.

Пустые строки МОГУТ добавляться для улучшения читаемости и указания соответствующих
блоков кода.

ОБЯЗАНО НЕ быть более одного оператора на строке.

### 2.4. Отступы

Код ОБЯЗАН использовать отступы в 4 пробела и ОБЯЗАН НЕ использовать табы для отступов.

> N.b.: Использование только пробелов и не смешивание пробелов и табов помогает избежать
> проблем со сравнением файлов, патчами, историей и аннотацией. Использование пробелов
> также упрощает ввод мелкозернистых подзадач для межстрочного выравнивания.

### 2.5. Ключевые слова и true/false/null

[Ключевые слова PHP] ОБЯЗАНЫ быть в нижнем регистре.

Константы PHP `true`, `false`, и `null` ОБЯЗАНЫ быть в нижнем регистре.

[Ключевые слова PHP]: http://php.net/manual/en/reserved.keywords.php

## 3. Объявление Namespace и Use

При наличии, ОБЯЗАНА быть одна пустая строка после объявления `namespace`.

При наличии, все объявления `use` ОБЯЗАНЫ идти после объявления `namespace`.

Для каждого объявления ОБЯЗАНО быть одно ключевое слова `use`.

ОБЯЗАНА быть одна пустая строка после блока `use`.

К примеру:

~~~php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

// ... дополнительный PHP код ...

~~~

## 4. Классы, свойства и методы

Термин "класс" относится ко всем классам, интерфейсам и трейтам.

### 4.1. Extends и Implements

Ключевые слова `extends` and `implements` ОБЯЗАНЫ быть объявлены на той же линии где и имя класса.

Открывающая фигурная скобка для класса ОБЯЗАНА идти со своей новой строки; закрывающая фигурная скобка для класса ОБЯЗАНА быть на следующей строке после тела класса.

~~~php
<?php
namespace Vendor\Package;

use FooClass;
use BarClass as Bar;
use OtherVendor\OtherPackage\BazClass;

class ClassName extends ParentClass implements \ArrayAccess, \Countable
{
    // константы, свойства, методы
}
~~~

Список `implements` МОЖЕТ быть разбит на несколько строк, где каждая последующая строка с отступом. При этом, первый элемент списка ОБЯЗАН быть со следущей строки, и ОБЯЗАН быть только один интерфейс на каждую строку.

~~~php
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
~~~

### 4.2. Свойства

Видимость ОБЯЗАНА быть объявлена для всех свойств.

Ключевое слово `var` ОБЯЗАНО НЕ быть использовано для объявления свойства.

ОБЯЗАНО НЕ быть больше одного свойства, объявленного для каждого оператора.

Названиям свойств СЛЕДУЕТ НЕ иметь префикс с единственным подчеркиванием для указания видимости `protected` или `private`.

Объявление свойств выглядит следующим образом.

~~~php
<?php
namespace Vendor\Package;

class ClassName
{
    public $foo = null;
}
~~~

### 4.3. Методы

Видимость ОБЯЗАНА быть объявлена для всех методов.

Названиям методов СЛЕДУЕТ НЕ иметь префикс с единственным подчеркиванием для указания видимости `protected` или `private`.

Названия методов ОБЯЗАНЫ быть объявлены без пробела после названия метода. Открывающая фигурная скобка ОБЯЗАНА идти со своей новой строки, и закрывающая фигурная скобка ОБЯЗАНА идти со следующей строки после тела метода. ОБЯЗАНО НЕ быть пробела после открывающей круглой скобки, и ОБЯЗАНО НЕ быть пробела до закрывающей круглой скобки.

Объявление метода выглядит следующим образом. Обратите внимание на расположение круглых скобок, запятых, пробелом, и фигурных скобок:

~~~php
<?php
namespace Vendor\Package;

class ClassName
{
    public function fooBarBaz($arg1, &$arg2, $arg3 = [])
    {
        // тело метода
    }
}
~~~

### 4.4. Аргументы метода

В списке аргументов ОБЯЗАНО НЕ быть пробела перед каждой запятой, и ОБЯЗАН быть один пробел после каждой запятой.

Аргументы метода со значениями по умолчанию ОБЯЗАНЫ идти в конце списка аргументов. 

~~~php
<?php
namespace Vendor\Package;

class ClassName
{
    public function foo($arg1, &$arg2, $arg3 = [])
    {
        // тело метода
    }
}
~~~

Список аргументов МОЖЕТ быть разбит на несколько строк, где каждая последующая строка с отступом. При этом первый элемент в списке ОБЯЗАН быть со следующей строки, и ОБЯЗАНО быть только по одному аргументу на строку.

Когда спискок аргументов разбит на несколько строк закрывающая круглая скобка и открывающая фигурная скобка ОБЯЗАНЫ быть помещены вместе на одной строке с одним пробелом между ними. 

~~~php
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
~~~

### 4.5. `abstract`, `final`, и `static`

Когда пристутствуют объявления `abstract` и `final` они ОБЯЗАНЫ предшествовать объявления видимости.

Когда пристутствует объявление `static` оно ОБЯЗАНО идти после объявления видимости.

~~~php
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
~~~

### 4.6. Методы и вызовы функций

При вызове метода или функции ОБЯЗАНО НЕ быть пробела между именем метода или функции и открывающей круглой скобки, ОБЯЗАНО НЕ быть пробела после открывающей круглой скобки, ОБЯЗАНО НЕ быть пробела до закрывающей круглой скобки. В списке аргументов ОБЯЗАНО НЕ быть пробела перед каждой запятой и ОБЯЗАН быть один пробел после каждой запятой.

~~~php
<?php
bar();
$foo->bar($arg1);
Foo::bar($arg2, $arg3);
~~~

Список аргументов МОЖЕТ быть разбит на несколько строк, где каждая последующая строка с отступом. При этом первый элемент в списке ОБЯЗАН быть с новой строки и ОБЯЗАНО быть только по одному элементу на строку. 

~~~php
<?php
$foo->bar(
    $longArgument,
    $longerArgument,
    $muchLongerArgument
);
~~~

## 5. Управляющие конструкции

Общие правила для управляющих конструкций следующие:

- ОБЯЗАН быть один пробел после ключевого слова контролирующей конструкции
- ОБЯЗАНО НЕ быть пробела после открывающей круглой скобки
- ОБЯЗАНО НЕ быть пробела до закрывающей круглой скобки
- ОБЯЗАН быть один пробел между закрывающей круглой скобкой и открывающей фигурной скобкой
- Тело конструкции ОБЯЗАНО быть с одним отступом
- Закрывающая круглая скобка ОБЯЗАНА быть с новой строки после тела конструкции

Тело каждой конструкции ОБЯЗАНО быть замкнуто круглыми скобками. Это стандартизирут вид конструкций, и уменьшает вероятность введения ошибок таких как добавление новых строк в тело конструкции.

### 5.1. `if`, `elseif`, `else`

Конструкция `if` выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок; и что `else` и `elseif` на той же строке что и закрывающая фигурная скобка из предыдущего тела.

~~~php
<?php
if ($expr1) {
    // тело if
} elseif ($expr2) {
    // тело elseif
} else {
    // тело else
}
~~~

Ключевое слово `elseif` СЛЕДУЕТ использовать вместо `else if`, чтобы все управляющие ключевые слова выглядила как единые слова.

### 5.2. `switch`, `case`

Конструкция `switch` выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок. Конструкция `case` ОБЯЗАНА быть с новой строки после `switch`, и ключевое слово `break` (или другое завершающее ключевое слово) ОБЯЗАНО быть с новой строки на том же уровне, что и тело `case`. ОБЯЗАН быть комментарий такой как `// no break`, когда провал является намеренным в непустом теле `case`.

~~~php
<?php
switch ($expr) {
    case 0:
        echo 'Первый случай с паузой';
        break;
    case 1:
        echo 'Второй случай с провалом';
        // no break
    case 2:
    case 3:
    case 4:
        echo 'Третий случай return вместо break';
        return;
    default:
        echo 'Случай по умолчанию';
        break;
}
~~~

### 5.3. `while`, `do while`

Конструкция `while` выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок.

~~~php
<?php
while ($expr) {
    // тело конструкции;
}
~~~

По аналогии, конструкция `do while`выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок. 


~~~php
<?php
do {
    // тело конструкции;
} while ($expr);
~~~

### 5.4. `for`

Конструкция `for` выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок.

~~~php
<?php
for ($i = 0; $i < 10; $i++) {
    // тело конструкции;
}
~~~

### 5.5. `foreach`

Конструкция `foreach` выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок.

~~~php
<?php
foreach ($iterable as $key => $value) {
    // тело конструкции;
}
~~~

### 5.6. `try`, `catch`

Блок `try catch` выглядит следующим образом. Обратите внимание на размещение круглых скобок, пробелов и фигурных скобок.

~~~php
<?php
try {
    // тело try
} catch (FirstExceptionType $e) {
    // тело catch
} catch (OtherExceptionType $e) {
    // тело catch
}
~~~

## 6. Closures

Closures MUST be declared with a space after the `function` keyword, and a
space before and after the `use` keyword.

The opening brace MUST go on the same line, and the closing brace MUST go on
the next line following the body.

There MUST NOT be a space after the opening parenthesis of the argument list
or variable list, and there MUST NOT be a space before the closing parenthesis
of the argument list or variable list.

In the argument list and variable list, there MUST NOT be a space before each
comma, and there MUST be one space after each comma.

Closure arguments with default values MUST go at the end of the argument
list.

A closure declaration looks like the following. Note the placement of
parentheses, commas, spaces, and braces:

~~~php
<?php
$closureWithArgs = function ($arg1, $arg2) {
    // body
};

$closureWithArgsAndVars = function ($arg1, $arg2) use ($var1, $var2) {
    // body
};
~~~

Argument lists and variable lists MAY be split across multiple lines, where
each subsequent line is indented once. When doing so, the first item in the
list MUST be on the next line, and there MUST be only one argument or variable
per line.

When the ending list (whether of arguments or variables) is split across
multiple lines, the closing parenthesis and opening brace MUST be placed
together on their own line with one space between them.

The following are examples of closures with and without argument lists and
variable lists split across multiple lines.

~~~php
<?php
$longArgs_noVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) {
    // body
};

$noArgs_longVars = function () use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // body
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
    // body
};

$longArgs_shortVars = function (
    $longArgument,
    $longerArgument,
    $muchLongerArgument
) use ($var1) {
    // body
};

$shortArgs_longVars = function ($arg) use (
    $longVar1,
    $longerVar2,
    $muchLongerVar3
) {
    // body
};
~~~

Note that the formatting rules also apply when the closure is used directly
in a function or method call as an argument.

~~~php
<?php
$foo->bar(
    $arg1,
    function ($arg2) use ($var1) {
        // body
    },
    $arg3
);
~~~

## 7. Conclusion

There are many elements of style and practice intentionally omitted by this
guide. These include but are not limited to:

- Declaration of global variables and global constants

- Declaration of functions

- Operators and assignment

- Inter-line alignment

- Comments and documentation blocks

- Class name prefixes and suffixes

- Best practices

Future recommendations MAY revise and extend this guide to address those or
other elements of style and practice.
