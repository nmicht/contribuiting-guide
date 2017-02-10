# Contribution Guidelines

To contribute to this API, please be sure to have the following technologies:
- PHP 7
- [Laravel 5.4](https://laravel.com/docs/5.4).
- CodeSniffer
- MySQL


#### Table of contents
[Pull Requests](#pull-requests)
[Tests](#tests)
[Styleguides](#styleguides)
  * [Git Commit Messages](#git-commit-messages)
  * [Specs Styleguide](#specs-styleguide)
  * [Coding Styleguide](#coding-styleguide)
  * [Documentation Styleguide](#documentation-styleguide)


## Pull Request
[GitHub pull requests](https://help.github.com/articles/using-pull-requests) are a great way for team to contribute to this API.

In order to keep the codebase clean, stable and at high quality, some guidelines are necessary for high-quality pull requests:

- **Branch:** Unless they are immediate documentation fixes relevant for old versions, pull requests should be sent to the `develop` branch only. Make sure to select that branch as target when creating the pull request (GitHub will not automatically select it.)
- **Documentation:** If you are adding a new feature or changing the API in any relevant way, this should be documented. The documentation files can be found directly in the core repository.
- **Unit tests:** To keep old bugs from re-appearing and generally hold quality at a high level, the Laravel core is thoroughly unit-tested. Thus, when you create a pull request, it is expected that you unit test any new code you add. For any bug you fix, you should also add regression tests to make sure the bug will never appear again. If you are unsure about how to write tests, the core team or other contributors will gladly help.

### How Do I Submit a (Good) Pull Request

* Fill in [the required template](PULL_REQUEST_TEMPLATE.md)
* Include screenshots and animated GIFs in your pull request whenever possible.
* Follow the [Coding Style](#coding-styleguide) styleguides.
* Include thoughtfully-worded, well-structured specs. See the [Specs Styleguide](#specs-styleguide) below.
* Document new code based on the
  [Documentation Styleguide](#documentation-styleguide)
* End files with a newline.
* Place class properties in the following order:
    * Class methods and properties (methods starting with a `@`)
    * Instance methods and properties
* Avoid platform dependent code
* Using a plain `return` when returning explicitly at the end of a function.
    * Not `return null`, `return undefined`, `null`, or `undefined`

## Tests


## Styleguides

### Git Commit Messages
Write a [good commit message](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).
* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
* Limit the first line to 72 characters or less
* Reference issues and pull requests liberally
* When only changing documentation, include `[ci skip]` in the commit description

### Specs Styleguide
* Use [Swagger specification](http://swagger.io/specification/) to create API specs.

### Coding Styleguide
* Same as Laravel, follow the [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md) coding standard and the [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md) autoloading standard.

The easiest way to apply these conventions is using [PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer) and configure your editor using our .editorconfig from Laravel.

We have a pre-commit hook to make sure code is formatted properly and vetted before you commit any changes.

### Documentation Styleguide
* Use [PHPDoc](https://www.phpdoc.org/docs/latest/references/phpdoc/basic-syntax.html).

#### Example

```php
/**
 * Register a binding with the container.
 *
 * @param  string|array  $abstract
 * @param  \Closure|string|null  $concrete
 * @param  bool  $shared
 * @return void
 */
public function bind($abstract, $concrete = null, $shared = false)
{
    //
}
```

Note that the @param attribute is followed by two spaces, the argument type, two more spaces, and finally the variable name
