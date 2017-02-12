# Contribution Guidelines

The following is a set of guidelines for contributing to this API. These are 
just guidelines, not rules. Use your best judgment, and feel free to propose 
changes to this document in a pull request.


#### Table of contents
* [Pull Requests](#pull-requests)  
* [Tests](#tests)  
* [Styleguides](#styleguides)  
  * [Git Commit Messages](#git-commit-messages)
  * [Specs Styleguide](#specs-styleguide)
  * [Branch Styleguide](#branch-styleguide)
  * [Coding Styleguide](#coding-styleguide)
  * [Documentation Styleguide](#documentation-styleguide)


## Pull Requests
[GitHub pull requests](https://help.github.com/articles/using-pull-requests)
are a great way for team to contribute to this API. All changes must be
reviewed before being merged into the codebase, and some additional changes may
be requested before the pull request is accepted.

In order to keep the codebase clean, stable and at high quality, some
guidelines are necessary for high-quality pull requests:

- **Select your merge target** Unless they are immediate documentation fixes
relevant for old versions, pull requests should be sent to the `dev` branch
only.
Make sure to follow [Gitlab Flow](https://about.gitlab.com/2014/09/29/gitlab-flow/) and select the correct branch as target when creating the pull request (GitHub will not automatically select it.)
as target when creating the pull request.
- **Provide a general summary** of the changes you've made in 1-3 sentences
- **Provide specific summaries in check-list format** (skip any that do not
    apply)
	* The application/testing changes should come first
	* The database changes should come next
	* The documentation changes should come last
- **Update any related documentation and tests**
- **Link any related issues** using their issue number, by pasting a link
- **Unit tests** To keep old bugs from re-appearing and generally hold quality
at a high level, this API is thoroughly unit-tested.

### How Do I Submit a (Good) Pull Request

* Fill in [the required template](PULL_REQUEST_TEMPLATE.md)
* Include screenshots and animated GIFs in your pull request whenever possible.
* Follow the [Coding Style](#coding-styleguide) styleguides.
* Include thoughtfully-worded, well-structured specs. See the
[Specs Styleguide](#specs-styleguide) below.
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

When you add new code, it is expected that you unit test any new code you add.
For any bug you fix, you should also add regression tests to make sure the bug
will never appear again.
- Use [Mockery](http://docs.mockery.io/en/latest/) to create your own mocks
- Extend your classes from our **ApiTestCase** instead TestCase from Laravel

#### Example

```php
class FooTest extends ApiTestCase
{
    public function testGetIndex()
    {
        Cache::shouldReceive('get')
                    ->once()
                    ->with('key')
                    ->andReturn('value');

        $this->visit('/users')->see('value');
    }
}
```

## Styleguides

### Git Commit Messages
Write a [good commit message](http://tbaggery.com/2008/04/19/a-note-about-git-commit-messages.html).
* Use the present tense ("Add feature" not "Added feature")
* Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
* Limit the first line to 50 characters or less
* Reference issues and pull requests liberally
* When only changing documentation, include `[ci skip]` in the commit
description

### Specs Styleguide
* Use [Swagger specification](http://swagger.io/specification/) to create API
specs.

We will not approve pull requests if documentation in swagger is not updated.

### Branch Styleguide

Attempt to name your branches in a sensible way, and prefix the branch name
with the type of changes that will be made. Moreover, keep the branch entirely
lowercase.
For instance, `feature/example` would be a branch that implements an "example"
feature.

Make sure to select work according to our
[Gitflow Workflow](https://docs.google.com/a/allbound.com/document/d/1xQVn5zBZVppiP5AF2XcLiu0VuSQFTReb6grNFoKYdyw/edit?usp=sharing)

In general, these rules should be followed:
* Issues that are marked as `feature` should have a branch that is prefixed
with `feature/`
* Issues that are marked as `refactor` should have a branch that is prefixed
with `refactor/`
* Issues that are marked as `bug` should have a branch that is prefixed
with `fix/`
* Other miscellaneous issues or changes do not need to be prefixed

### Coding Styleguide
* Same as Laravel, follow the [PSR-2](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-2-coding-style-guide.md)
coding standard and the [PSR-4](https://github.com/php-fig/fig-standards/blob/master/accepted/PSR-4-autoloader.md)
autoloading standard.

The easiest way to apply these conventions is using
[PHP_CodeSniffer](https://github.com/squizlabs/PHP_CodeSniffer). Also we
encourage to [configure your editor](http://editorconfig.org/#download) using
our .editorconfig file.

We have a pre-commit hook to make sure code is formatted properly and vetted
before you commit any changes.

### Documentation Styleguide
* Use [PHPDoc](https://www.phpdoc.org/docs/latest/references/phpdoc/basic-syntax.html)
* Remember to use [PHP7 type hints](http://php.net/manual/en/functions.arguments.php#functions.arguments.type-declaration)


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

Note that the `@param` attribute is followed by two spaces, the argument type,
two more spaces, and finally the variable name
