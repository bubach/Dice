[Dice PHP Dependency Injection Container](https://r.je/dice.html)
======================================

Dice is a minimalist Dependency Injection Container for PHP with a focus on being lightweight and fast as well as requiring as little configuration as possible.

[![Latest Stable Version](https://poser.pugx.org/garrettw/dice/v/stable.svg)](https://packagist.org/packages/garrettw/dice) [![Total Downloads](https://poser.pugx.org/garrettw/dice/downloads.svg)](https://packagist.org/packages/garrettw/dice) [![Latest Unstable Version](https://poser.pugx.org/garrettw/dice/v/unstable.svg)](https://packagist.org/packages/garrettw/dice) [![License](https://poser.pugx.org/garrettw/dice/license.svg)](https://packagist.org/packages/garrettw/dice)

[![Code Climate](https://codeclimate.com/github/garrettw/Dice/badges/gpa.svg)](https://codeclimate.com/github/garrettw/Dice) [![SensioLabsInsight](https://insight.sensiolabs.com/projects/b685aa59-9df5-410e-8262-3d64b65b4153/mini.png)](https://insight.sensiolabs.com/projects/b685aa59-9df5-410e-8262-3d64b65b4153)

Project Goals
-------------

1) To be lightweight and not a huge library with dozens of files (Currently Dice is just one 100 line file with only 3 classes) yet support all features (and more) offered by much more complex containers

2) To "just work". Basic functionality should work with zero configuration

3) Where configuration is required, it should be as minimal and reusable as possible as well as easy to use.

4) Speed!


Installation
------------

Just include the lightweight `Dice.php` in your project and it's usable without any further configuration:

Simple example:

```php
<?php
class A {
	public $b;

	public function __construct(B $b) {
		$this->b = $b;
	}
}

class B {

}

require_once 'Dice.php';
$dice = new \Dice\Dice;

$a = $dice->create('A');

var_dump($a->b); //B object

?>
```


Full Documentation
------------------

For complete documentation please see the [Dice PHP Dependency Injection container home page](https://r.je/dice.html)


PHP version compatibility
-------------------------

Dice is compatible with PHP5.4 and up, there are archived versions of Dice which supports PHP5.3 however this is no longer maintanied.


Updates
------------

28/06/2014
* Greatly improved efficienty. Dice is now the fastest Dependency Injection Container for PHP!

06/06/2014
* Added support for cyclic references ( https://github.com/TomBZombie/Dice/issues/7 ). Please note this is poor design but this fix will stop the infinite loop this design creates.

27/03/2014
* Removed assign() method as this duplicated functionality available using $rule->shared
* Removed $callback argument in $dice->create() as the only real use for this feature can be better achieved using $rule->shareInstances
* Tidied up code, removing unused/undocumented features. Dice is now even more lightweight and faster.
* Fixed a bug where when using $rule->call it would use the substitution rules from the constructor on each method called
* Updated [Dice documentation](https://r.je/dice.html) to use shorthand array syntax


01/03/2014
* Added test cases for the Xml Loader and Loader Callback classes
* Added a JSON loader + test case
* Added all test cases to a test suite
* Moved to PHP5.4 array syntax. A PHP5.3 compatible version is now available in the PHP5.3 branch.
* Fixed an issue where using named instances would trigger the autoloader with an invalid class name every time a class was created


28/02/2014
* Added basic namespace support. Documentation update will follow shortly. Also moved the XML loader into its own file, you'll need to include it separately if you're using it.
* Please note: CHANGES ARE NOT BACKWARDS COMPATIBLE. However they are easily fixed by doing the following find/replaces:

```php
	new Dice => new \Dice\Dice
	new DiceInstance => new \Dice\Instance
	new DiceRule => new \Dice\Rule
```
