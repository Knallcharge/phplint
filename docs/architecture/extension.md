# Extension

PHPLint may be extended with many other new features by using concept of extension. 
Each extension is based on [Event Driven Architecture](./event.md)

## UML Diagram

![UML Diagram](../assets/extension-uml-diagram.svg)

Generated by [bartlett/umlwriter][bartlett/umlwriter] package.

## OutputFormat

This extension is responsible to print results to target defined by option. See Example below.

**NOTE**: Version 9.0 supports JSON (`log-json`) and Junit (`log-junit`) format.

Whatever you specify zero or more option, results will always be printed to standard output (see `Overtrue\PHPLint\Output\ConsoleOutput` object).
unless you give `--quiet`.

## ProgressPrinter

This extension is responsible to print progress of file checking.

Here is preview of what it will look like : 

![Progress Printer Normal](../assets/progress-printer-normal.png)

![Progress Printer Verbose](../assets/progress-printer-verbose.png)

## ProgressBar

This extension is responsible to print progress of file checking with the [Symfony ProgressBar Console Helper][symfony-progressbar]

Here is preview of what it will look like :

![Progress Bar Normal](../assets/progress-bar-normal.png)

![Progress Bar Verbose](../assets/progress-bar-verbose.png)

![Progress Bar Verbose Max](../assets/progress-bar-verbose-max.png)

## Example(s)

Default progress printer widget:

```php 
<?php
use Overtrue\PHPLint\Extension\ProgressPrinter;

$extensions = [new ProgressPrinter()];

```

Default progress bar widget:

```php 
<?php
use Overtrue\PHPLint\Extension\ProgressBar;

$extensions = [new ProgressBar()];

```

Default outputs (console, JSON and Junit formats):

```php 
<?php
use Overtrue\PHPLint\Configuration\OptionDefinition;
use Overtrue\PHPLint\Extension\OutputFormat;

$extensions = [
    new OutputFormat([
        OptionDefinition::OPTION_JSON_FILE,
        OptionDefinition::OPTION_JUNIT_FILE,
    ])
];

```

[bartlett/umlwriter]: https://github.com/llaville/umlwriter
[symfony-progressbar]: https://symfony.com/doc/current/components/console/helpers/progressbar.html
