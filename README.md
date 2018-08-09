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

When making a method or function call, there MUST NOT be a space between the
method or function name and the opening parenthesis, there MUST NOT be a space
after the opening parenthesis, and there MUST NOT be a space before the
closing parenthesis. In the argument list, there MUST NOT be a space before
each comma, and there MUST be one space after each comma.

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

## 5. Control Structures

The general style rules for control structures are as follows:

- There MUST be one space after the control structure keyword
- There MUST NOT be a space after the opening parenthesis
- There MUST NOT be a space before the closing parenthesis
- There MUST be one space between the closing parenthesis and the opening
  brace
- The structure body MUST be indented once
- The closing brace MUST be on the next line after the body

The body of each structure MUST be enclosed by braces. This standardizes how
the structures look, and reduces the likelihood of introducing errors as new
lines get added to the body.

### 5.1. `if`, `elseif`, `else`

An `if` structure looks like the following. Note the placement of parentheses,
spaces, and braces; and that `else` and `elseif` are on the same line as the
closing brace from the earlier body.

~~~php
<?php
if ($expr1) {
    // if body
} elseif ($expr2) {
    // elseif body
} else {
    // else body;
}
~~~

The keyword `elseif` SHOULD be used instead of `else if` so that all control
keywords look like single words.

### 5.2. `switch`, `case`

A `switch` structure looks like the following. Note the placement of
parentheses, spaces, and braces. The `case` statement MUST be indented once
from `switch`, and the `break` keyword (or other terminating keyword) MUST be
indented at the same level as the `case` body. There MUST be a comment such as
`// no break` when fall-through is intentional in a non-empty `case` body.

~~~php
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
~~~

### 5.3. `while`, `do while`

A `while` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

~~~php
<?php
while ($expr) {
    // structure body
}
~~~

Similarly, a `do while` statement looks like the following. Note the placement
of parentheses, spaces, and braces.

~~~php
<?php
do {
    // structure body;
} while ($expr);
~~~

### 5.4. `for`

A `for` statement looks like the following. Note the placement of parentheses,
spaces, and braces.

~~~php
<?php
for ($i = 0; $i < 10; $i++) {
    // for body
}
~~~

### 5.5. `foreach`

A `foreach` statement looks like the following. Note the placement of
parentheses, spaces, and braces.

~~~php
<?php
foreach ($iterable as $key => $value) {
    // foreach body
}
~~~

### 5.6. `try`, `catch`

A `try catch` block looks like the following. Note the placement of
parentheses, spaces, and braces.

~~~php
<?php
try {
    // try body
} catch (FirstExceptionType $e) {
    // catch body
} catch (OtherExceptionType $e) {
    // catch body
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

## Appendix A. Survey

In writing this style guide, the group took a survey of member projects to
determine common practices.  The survey is retained herein for posterity.

### A.1. Survey Data

    url,http://www.horde.org/apps/horde/docs/CODING_STANDARDS,http://pear.php.net/manual/en/standards.php,http://solarphp.com/manual/appendix-standards.style,http://framework.zend.com/manual/en/coding-standard.html,https://symfony.com/doc/2.0/contributing/code/standards.html,http://www.ppi.io/docs/coding-standards.html,https://github.com/ezsystems/ezp-next/wiki/codingstandards,http://book.cakephp.org/2.0/en/contributing/cakephp-coding-conventions.html,https://github.com/UnionOfRAD/lithium/wiki/Spec%3A-Coding,http://drupal.org/coding-standards,http://code.google.com/p/sabredav/,http://area51.phpbb.com/docs/31x/coding-guidelines.html,https://docs.google.com/a/zikula.org/document/edit?authkey=CPCU0Us&hgd=1&id=1fcqb93Sn-hR9c0mkN6m_tyWnmEvoswKBtSc0tKkZmJA,http://www.chisimba.com,n/a,https://github.com/Respect/project-info/blob/master/coding-standards-sample.php,n/a,Object Calisthenics for PHP,http://doc.nette.org/en/coding-standard,http://flow3.typo3.org,https://github.com/propelorm/Propel2/wiki/Coding-Standards,http://developer.joomla.org/coding-standards.html
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

### A.2. Survey Legend

`indent_type`:
The type of indenting. `tab` = "Use a tab", `2` or `4` = "number of spaces"

`line_length_limit_soft`:
The "soft" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

`line_length_limit_hard`:
The "hard" line length limit, in characters. `?` = not discernible or no response, `no` means no limit.

`class_names`:
How classes are named. `lower` = lowercase only, `lower_under` = lowercase with underscore separators, `studly` = StudlyCase.

`class_brace_line`:
Does the opening brace for a class go on the `same` line as the class keyword, or on the `next` line after it?

`constant_names`:
How are class constants named? `upper` = Uppercase with underscore separators.

`true_false_null`:
Are the `true`, `false`, and `null` keywords spelled as all `lower` case, or all `upper` case?

`method_names`:
How are methods named? `camel` = `camelCase`, `lower_under` = lowercase with underscore separators.

`method_brace_line`:
Does the opening brace for a method go on the `same` line as the method name, or on the `next` line?

`control_brace_line`:
Does the opening brace for a control structure go on the `same` line, or on the `next` line?

`control_space_after`:
Is there a space after the control structure keyword?

`always_use_control_braces`:
Do control structures always use braces?

`else_elseif_line`:
When using `else` or `elseif`, does it go on the `same` line as the previous closing brace, or does it go on the `next` line?

`case_break_indent_from_switch`:
How many times are `case` and `break` indented from an opening `switch` statement?

`function_space_after`:
Do function calls have a space after the function name and before the opening parenthesis?

`closing_php_tag_required`:
In files containing only PHP, is the closing `?>` tag required?

`line_endings`:
What type of line ending is used?

`static_or_visibility_first`:
When declaring a method, does `static` come first, or does the visibility come first?

`control_space_parens`:
In a control structure expression, is there a space after the opening parenthesis and a space before the closing parenthesis? `yes` = `if ( $expr )`, `no` = `if ($expr)`.

`blank_line_after_php`:
Is there a blank line after the opening PHP tag?

`class_method_control_brace`:
A summary of what line the opening braces go on for classes, methods, and control structures.

### A.3. Survey Results

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
