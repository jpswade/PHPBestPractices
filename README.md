#PHP Best Practices
A list of best practices tips for better PHP

## CODING STANDARDS

Historically PHP developers have received bad reputations mainly due to poor coding and not escaping SQL from injection.

One way to improve the over-all quality of a product, help reduce problems, increase productivity and development and generally make life a little easier in the long run is to stick to a set of Coding Standards as closely as possible.

All projects should take the same approach and stick to one set of coding standards. This will solve many common problems, especially projects which have more than one developer.

There's lots of well established Coding Standards out there. One such is [PEAR Coding Standards](http://pear.php.net/manual/en/standards.php). PEAR is a library of useful classes for PHP, as an attempt to help users from re-inventing the wheel to achieve the same task.

PEAR has grown larger over the years and has many packages on offer, as such like everyone else some packages in PEAR had common problems. The PEAR team decided it was best to employ coding standards for everyone to work to.

PEAR, which attempted to be the standard for years now participates in [PHP Standards Recommendation (PSR)](http://www.php-fig.org/psr/).

It would be worth noting the difference between "Coding Standards" and "Best Practices".

Coding Standards should be guidelines that we should be aiming to stick to, relating to the way code is written and its readability.

Best Practices, however, are recommendations that may help with security, performance, or architectural patterns that are solutions to a commonly occurring problems.

## BEST PRACTICES

1. [Stick to coding standards](http://talks.php.net/show/php-best-practices/15), it will make it easier for you to understand other people's code and other people will be able to understand yours
2. Avoid using uppercase booleans (TRUE, FALSE, NULL) as it can be [difficult to debug](http://3v4l.org/4Ze6h)
3. Declare "Class Methods" visibility, precede [private or protected functions with an underscore](http://framework.zend.com/manual/1.12/en/coding-standard.naming-conventions.html) (eg: private function _test ($string) { ... })
4. Avoid using regular expression functions (preg_), [they can be slow](http://talks.php.net/show/php-best-practices/36), string functions are faster
5. Avoid using switch/case statements, [else/if is faster](http://wayback.archive.org/web/20100706232020/http://www.php.lt/benchmark/phpbench.php) and often easier to read
6. Avoid Error Control Operator (@) for error suppression, it's [slow and hard to debug](http://michelf.com/weblog/2005/bad-uses-of-the-at-operator/)
7. Avoid using [print](http://www.php.net/print) instead of [echo](http://www.php.net/echo), it's [slower](http://www.phpbench.com/)
8. Use the [alternative syntax](http://php.net/manual/en/control-structures.alternative-syntax.php), colon (:), for control structures such as 'if, while, for, foreach, and switch', when working with markup or templates
9. Avoid "[Unnecessary Closing Delimiter](https://blogs.oracle.com/netbeansphp/entry/improve_your_code_with_new)" (?>), this avoids outputting unwanted whitespace
10. Avoid accessing the superglobals ($_GET, $_POST, $_REQUEST, etc) directly as [user input cannot be trusted](http://talks.php.net/show/php-best-practices/19), consider using [filter_input()](http://www.php.net/filter_input)
11. Avoid [too many nested blocks in functions](http://phpmd.org/rules/codesize.html), instead consider breaking them out into new functions
12. Return early [[citation]](https://gist.github.com/jpswade/624074588ec55efd7537)
13. Avoid using the PHP mail() function direction as your mail may be subjected to [header injection](http://www.php.net/manual/en/function.mail.php#56788)
14. [Avoid reinventing the wheel](http://talks.php.net/show/php-best-practices/6), [Don't repeat yourself](http://reinholdweber.com/php/php-programmers-evolution-scribble/) [(DRY)](http://en.wikipedia.org/wiki/Don't_repeat_yourself), use existing functions, extensions (PECL) libraries (PEAR), frameworks (CodeIgniter, Zend, Laravel) as they will often already be optimised
15. [Avoid using functions inside of loops](http://wayback.archive.org/web/20100706232020/http://www.php.lt/benchmark/phpbench.php), such as for ($x=0; $x < count($array); $x) as count() function would get called each time
16. [Always declare static methods](http://www.ilia.ws/files/zend_performance.pdf), when the method has no dynamic content
17. Use [Class Constants](http://www.ilia.ws/files/zend_performance.pdf)
18. Use [full paths](http://wayback.archive.org/web/20100201223601/http://t3.dotgnu.info/blog/php/include_once-mostly-harmless.html) in includes and requires, less time spent on resolving the file system paths
19. [Avoid function calls](http://www.ilia.ws/files/zend_performance.pdf) if there's a constant or variable (eg: PHP_VERSION vs php_version() or [$_SERVER[’REQUEST_TIME’] vs time()](http://www.php.net/time))
20. [Cache your web pages](http://phplens.com/phpeverywhere/tuning-apache-php) using systems built into your framework or a library such as [PEAR Cache:Lite](http://pear.php.net/Cache_Lite)
21. [Profile your code](http://talks.php.net/show/php-best-practices/39). A profiler shows you, which parts of your code consumes how many time. The [Xdebug debugger](http://xdebug.org/) already contains a profiler. Profiling shows you the bottlenecks in overview
22. [Separate code, content and presentation](http://wayback.archive.org/web/20090209025333/http://www.ibm.com/developerworks/library/wa-phprock1/index.html): keep complex logic separate from presentation markup, akin to the Model–View–Controller (MVC) architectural pattern
23. Learn [how to store passwords safely](https://alias.io/2010/01/store-passwords-safely-with-php-and-mysql/), [never store passwords as clear text or simple md5 hash](http://talks.php.net/show/php-best-practices/28)
24. Use your IDE, there's [plenty of great IDEs out there that support PHP](http://www.smashingmagazine.com/2009/02/the-big-php-ides-test-why-use-oneand-which-to-choose/)
25. [Turn on error reporting](http://talks.php.net/show/php-best-practices/11), use strict code, avoid suppressing errors, notices and warnings, resulting in cleaner code and less overheads, set error_reporting(E_ALL) always on
26. [Use the standards <?php ... ?> tags](http://talks.php.net/show/php-best-practices/10) when declaring PHP as all other styles are depreciated, including short tags.
27. Upgrade to the latest version of PHP, it's (often) faster, [PHP7](http://talks.php.net/oz15#/) is the fastest yet!
28. [Avoid blindly using empty()](http://www.zachstronaut.com/posts/2009/02/09/careful-with-php-empty.html), consider isset() or count() or strlen() if they are more appropriate
29. [The mysql_ functions are deprecated](https://wiki.php.net/rfc/mysql_deprecation) and will be removed in the future: use [mysqli](http://php.net/manual/en/book.mysqli.php) or [PDO](http://php.net/manual/en/ref.pdo-mysql.php) instead
30. 
[RTFM](http://en.wikipedia.org/wiki/RTFM)! PHP offers a [fantastic manual](http://www.php.net/manual/), possibly one of the best out there, which makes it a very hands on language, providing working examples and talking in plain English. [Please USE IT!](http://xkcd.com/293/)

