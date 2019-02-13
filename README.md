# WordPress Upgrade Task Runner

[![PHP from Packagist](https://img.shields.io/packagist/php-v/thefrosty/wp-upgrade-task-runner.svg)]()
[![Latest Stable Version](https://img.shields.io/packagist/v/thefrosty/wp-upgrade-task-runner.svg)](https://packagist.org/packages/thefrosty/wp-upgrade-task-runner)
[![Total Downloads](https://img.shields.io/packagist/dt/thefrosty/wp-upgrade-task-runner.svg)](https://packagist.org/packages/thefrosty/wp-upgrade-task-runner)
[![License](https://img.shields.io/packagist/l/thefrosty/wp-upgrade-task-runner.svg)](https://packagist.org/packages/thefrosty/wp-upgrade-task-runner)
[![Build Status](https://travis-ci.org/thefrosty/wp-upgrade-task-runner.svg?branch=master)](https://travis-ci.org/thefrosty/wp-upgrade-task-runner)
[![Beerpay](https://beerpay.io/thefrosty/wp-upgrade-task-runner/badge.svg?style=flat)](https://beerpay.io/thefrosty/wp-upgrade-task-runner)

A library containing my standard development resources.

### Requirements

```
PHP >= 7.1
WordPress >= 4.8
```

The required WordPress version will always be the most recent point release of
the previous major release branch.

For both PHP and WordPress requirements, although this library may work with a
version below the required versions, they will not be supported and any
compatibility is entirely coincidental.

### Installation

To install this library, use Composer:

```
composer require thefrosty/wp-upgrade-task-runner:~1.0
```

## Getting Started

If a new task is needed, there are only three required steps that are needed.

1. A class needed to be created within the `/Upgrades/Tasks/` directory. This class needs to extend the `AbstractTaskRunner`
class. See the `ExampleMigrationTask` example class.
2. Add the new task to the `/Upgrades/Tasks/fields.php` array.
3. Finally, instantiate the new class in the `/Upgrades/Tasks/TaskLoader` class.

### The task class.

When a class is added, it needs to have a few pre-defined class values. Both the DATE and TITLE constant are required
to be unique. These are what register a one off cron task when manually _running_ the task from the admin page.

### The `TaskLoader`.

Add the new class as a property in the `TaskLoader` class and instantiate it in the `register_tasks` method (just like
the `ExampleMigrationTask`).