Linting Talk
============

What is linting
---------------

   A linter or lint refers to tools that analyze source code to flag programming
   errors, bugs, stylistic errors, and suspicious constructs. The term originates
   from a Unix utility that examined C language source code.

   — https://en.wikipedia.org/wiki/Lint_(software)

Why do I need it?
-----------------

* Prevent syntax errors = 500 http error in production.

* Prevent bugs.

* Validate coding guideline = Prevent unnecessary merge conflicts.

* Reduce complexity and mental overhead.

What to lint
------------

PHP
^^^

* PHP Native

  Local::

     php -l broken.php
     php -l valid.php

  For CI::

     php -l broken.php > /dev/null; echo $?
     php -l valid.php > /dev/null; echo $?

     find localPackages/ -name \*.php | parallel --gnu php -d display_errors=stderr -l {} > /dev/null \;

* PHP Code Sniffer
  Checks for Coding Guideline, best practices like no debugging code.

  Extendable, Multiple languages, php, js, typoscript, …
  Lint and fix.
  Integrated into IDEs, Editors and CI.

* PHPMD
  https://phpmd.org/
  https://phpmd.org/rules/index.html

* phpstan
  https://github.com/phpstan/phpstan
  https://packagist.org/packages/saschaegerer/phpstan-typo3

  PHP >= 7.1
  No configuration necessary

* phan
  https://github.com/phan/phan

  Awesome, but needs configuration file.

* https://phpqa.io/

* https://www.owasp.org/index.php/OWASP_WAP-Web_Application_Protection

TypoScript
^^^^^^^^^^

https://github.com/martin-helmich/typo3-typoscript-lint

XML / XLIFF
^^^^^^^^^^^

http://xmlsoft.org/xmllint.html

JSON / composer.json
^^^^^^^^^^^^^^^^^^^^

`composer validate`

YAML (Form extension)
^^^^^^^^^^^^^^^^^^^^^

https://github.com/adrienverge/yamllint

Summary
-------

Check out possible linter. Integrate linter in CI, optionally also in local IDEs
/editors.

Prevent "dumb" issues like invalid PHP syntax.

Prevent some security issues.

Further reading
---------------

* https://www.owasp.org/index.php/Static_Code_Analysis

* https://en.wikipedia.org/wiki/List_of_tools_for_static_code_analysis

* https://phpqa.io/
