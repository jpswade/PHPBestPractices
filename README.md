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
13. Avoid using the PHP mail() function direction as your mail may be subjected to [header injection](http://www.php.net/manual/en/function.mail.php#56788), PHP mail(), swiftmailer and phpmailer sucks. Try [PEAR Mail](http://pear.php.net/package/mail) instead.
14. [Avoid reinventing the wheel](http://talks.php.net/show/php-best-practices/6), [Don't repeat yourself](http://reinholdweber.com/php/php-programmers-evolution-scribble/) [(DRY)](http://en.wikipedia.org/wiki/Don't_repeat_yourself), use existing functions, extensions (PECL) libraries (PEAR), frameworks (CodeIgniter, Zend, Laravel) as they will often already be optimised
15. [Avoid using functions inside of loops](http://wayback.archive.org/web/20100706232020/http://www.php.lt/benchmark/phpbench.php), such as for ($x=0; $x < count($array); $x) as count() function would get called each time
16. [Always declare static methods](http://www.ilia.ws/files/zend_performance.pdf), when the method has no dynamic content
17. Use [Class Constants](http://www.ilia.ws/files/zend_performance.pdf)
18. Use [full paths](http://wayback.archive.org/web/20100201223601/http://t3.dotgnu.info/blog/php/include_once-mostly-harmless.html) in includes and requires, less time spent on resolving the file system paths
19. [Avoid function calls](http://www.ilia.ws/files/zend_performance.pdf) if there's a constant or variable (eg: PHP_VERSION vs php_version() or [$_SERVER['REQUEST_TIME'] vs time()](http://www.php.net/time))
20. [Cache your web pages](http://phplens.com/phpeverywhere/tuning-apache-php) using systems built into your framework or a library such as [PEAR Cache:Lite](http://pear.php.net/Cache_Lite)
21. [Profile your code](http://talks.php.net/show/php-best-practices/39). A profiler shows you, which parts of your code consumes how many time. The [Xdebug debugger](http://xdebug.org/) already contains a profiler. Profiling shows you the bottlenecks in overview
22. [Separate code, content and presentation](http://wayback.archive.org/web/20090209025333/http://www.ibm.com/developerworks/library/wa-phprock1/index.html): keep complex logic separate from presentation markup, akin to the Model–View–Controller (MVC) architectural pattern
23. Learn [how to store passwords safely](https://alias.io/2010/01/store-passwords-safely-with-php-and-mysql/), [never store passwords as clear text or simple md5 hash](http://talks.php.net/show/php-best-practices/28)
24. Use an IDE, the most important thing for me is the Integrated Development Environment (IDE), notepad simply won't cut it and there's [plenty of great IDEs out there that support PHP](http://www.smashingmagazine.com/2009/02/the-big-php-ides-test-why-use-oneand-which-to-choose/), Find an IDE that works with your existing toolset, try [NetBeans](https://netbeans.org/), see what works for you.
25. [Turn on error reporting](http://talks.php.net/show/php-best-practices/11), use strict code, avoid suppressing errors, notices and warnings, resulting in cleaner code and less overheads, set error_reporting(E_ALL) always on
26. [Use the standards <?php ... ?> tags](http://talks.php.net/show/php-best-practices/10) when declaring PHP as all other styles are depreciated, including short tags.
27. Upgrade to the latest version of PHP, it's (often) faster, [PHP7](http://talks.php.net/oz15#/) is the fastest yet!
28. [Avoid blindly using empty()](http://www.zachstronaut.com/posts/2009/02/09/careful-with-php-empty.html), consider isset() or count() or strlen() if they are more appropriate
29. [The mysql_ functions are deprecated](https://wiki.php.net/rfc/mysql_deprecation) and will be removed in the future: use [mysqli](http://php.net/manual/en/book.mysqli.php) or [PDO](http://php.net/manual/en/ref.pdo-mysql.php) instead
30. Work with automated and repeatable development environments using tools such as [Vagrant, Virtualbox](http://talks.php.net/velocity15#/php_contribute2) and [Puppet](https://puphpet.com/) makes it easy
31. Use version control to help [tame PHP projects as they scale](http://talks.php.net/show/taming-large-scale/0), learn to use [git](https://en.wikipedia.org/wiki/Git_(software)), [PHP is one of the most popular languages on GitHub](http://adambard.com/blog/top-github-languages-2014/) so it's here to stay, get used to it.
32. [Document your code](http://talks.php.net/show/php-best-practices/16), use tools such as [phpDocumentor](http://www.phpdoc.org/)
33. Learn how to do [Unit Testing](http://talks.php.net/show/tdd-dpc7/4) using tools such as [phpUnit](https://phpunit.de/)
34. Use the type safe comparison operators (===) to [compare type and value rather than just value (==)](http://talks.php.net/show/php-best-practices/8)
35. [Avoid SQL injection](http://talks.php.net/show/php-best-practices/21) by not trusting user input and preparing your statements using parameterised queries (in [mysqli](http://php.net/manual/en/mysqli.prepare.php) or [PDO](http://www.php.net/manual/en/pdo.prepare.php))
36. Avoid email address validation using complex regular expressions, consider [filter_var()](http://www.php.net/filter_var) and [FILTER_VALIDATE_EMAIL](http://php.net/manual/en/filter.filters.validate.php) and [verify the email address exists by sending a confirmation email to it](http://davidcel.is/posts/stop-validating-email-addresses-with-regex/)
37. [Use pre-increment where possible](http://talks.php.net/show/php-best-practices/32), ++$i is faster than $i++
38. Consider using [isset() in replace of strlen()](http://blog.dynom.nl/archives/String-length-vs-isset-to-check-string-lengths_20070807_5.html) where possible, for example: if (strlen($foo) < 5) vs. if (!isset($foo{5})), language constructs are faster than functions
39. When [parsing HTML or XML](http://wayback.archive.org/web/20090206223245/http://htmlparsing.icenine.ca/doku.php), don't use regular expressions, use a [DOM parser](http://www.php.net/dom)
40. [RTFM](http://en.wikipedia.org/wiki/RTFM)! PHP offers a [fantastic manual](http://www.php.net/manual/), possibly one of the best out there, which makes it a very hands on language, providing working examples and talking in plain English. [Please USE IT!](http://xkcd.com/293/)

## QUOTES

PHP has a few quirks which we sometimes approach with best practices while they can otherwise be addressed with a quote.

Listed here are a number of quotes that may go some way to help explain why certain things are certain ways.

* Never memorize something that you can look up -- [Albert Einstein](http://www.goodreads.com/quotes/24194-never-memorize-something-that-you-can-look-up)
* I'm not a real programmer. I throw together things until it works then I move on. The real programmers will say "Yeah it works but you're leaking memory everywhere. Perhaps we should fix that." I'll just restart Apache every 10 requests. -- [Rasmus Lerdorf](http://itc.conversationsnetwork.org/shows/detail3298.html)
* The sooner you start to code, the longer the program will take -- [Roy Carlson, University of Wisconsin](http://www.bowdoin.edu/~ltoma/teaching/cs340/spring05/coursestuff/Bentley_BumperSticker.pdf)
* PHP is just a hammer. Nobody has ever gotten rich making hammers. -- [Rasmus Lerdorf](https://twitter.com/rasmus/status/466911047044300800)
* Some people, when confronted with a problem, think "I know, I'll use regular expressions." Now they have two problems. -- [Jamie Zawinski, in comp.lang.emacs](http://regex.info/blog/2006-09-15/247)
* We should forget about small efficiencies, say about 97% of the time: premature optimization is the root of all evil. Yet we should not pass up our opportunities in that critical 3% -- [Donald Knuth](http://en.wikipedia.org/wiki/Donald_Knuth)
* Everything in the box is kind of weird and quirky, but maybe not enough to make it completely worthless. And there's no clear problem with the set as a whole; it still has all the tools -- [Alex Munroe](http://blog.codinghorror.com/the-php-singularity/)
* The echo chamber of geeks sitting around playing with their tools means absolutely nothing to me compared to seeing the code actually saving peoples' lives -- Rasmus Lerdorf](http://www.infoworld.com/article/2609877/web-development/believe-the-hype--php-founder-backs-facebook-s-hiphop-technology.html)
* Talk is cheap. Show me the code. -- [Linus Torvalds](https://lkml.org/lkml/2000/8/25/132)
* Release early, release often -- [Eric S. Raymond](https://en.wikipedia.org/wiki/The_Cathedral_and_the_Bazaar)
* "A problem well stated is a problem half-solved." - [Charles Kettering](http://www.levyinnovation.com/a-problem-well-stated-is-half-solved)
* "For many events, roughly 80% of the effects come from 20% of the causes" - [Vilfredo Pareto](http://www.goodreads.com/author/quotes/386776.Vilfredo_Pareto)

## BOOKS

* [Modern PHP: New Features and Good Practices -- Josh Lockhart](http://amzn.to/1MooHQw)
* [PHP Cookbook: Solutions & Examples for PHP Programmers -- David Sklar](http://amzn.to/1Ij4Zmn)
* [PHP: Crash Course - The Ultimate Beginner's Course to Learning PHP Programming in Under 12 Hours -- Eprogramy](http://amzn.to/1Ij5aOJ)
* [Head First PHP & MySQL -- Lynn Beighley](http://amzn.to/1Mop9ye)
* [PHP and MySQL for Dynamic Web Sites -- Larry Ullman](http://amzn.to/1Mopfpw)
* [Learning PHP, MySQL, JavaScript, & CSS -- Robin Nixon](http://amzn.to/1KkyGpu)
* [Beginning PHP and MySQL: From Novice to Professional -- W Jason Gilmore](http://amzn.to/1MopvEX)
* [Programming PHP -- Kevin Tatroe](http://amzn.to/1GD0gqi)
* [Professional WordPress: Design and Development -- Brad Williams, David Damstra, Hal Stern](http://amzn.to/1GD0Vry)
* [PHP Pocket Reference -- Rasmus Lerdorf](http://amzn.to/1Ij4HvQ)

## THANKS

* [James Wade](http://wade.be/)
* [Phurix Web Hosting](http://www.phurix.co.uk/)
* [Stoneacre Motor Group](http://www.stoneacre.co.uk/)