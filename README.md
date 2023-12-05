# events

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)

A minimal PHP event dispatcher.

## Install

Via Composer

``` bash
$ composer require vakata/events
```

## Usage

``` php
// create a dispatcher
$dispatcher = new \vakata\events\Dispatcher();

// listen for various events and/or namespaces
$dispatcher->listen('eventName', function () { })
$dispatcher->listen('eventName.namespace', function () { });
$dispatcher->listen('*.namespace', function () { });
$dispatcher->listen('*', function (EventInterface $event) {
    $event->stopPropagation();
    var_dump(
        $event->getName(),
        $event->getNamespaces(),
        $event->getPayload(),
        $event->isPropagationStopped()
    );
});

// create an event
$event = new \vakata\events\Event("eventName", [ 'pay' => 'load' ]);

// dispatch the event (listeners are called immediately)
$dispatcher->dispatch($event);

// the event can also be dispatched in a lazy fashion (listeners are called after `run`)
$dispatcher->dispatch($event, true);
// dispatch lazy events
$dispatcher->run();
```

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) for details.

## Security

If you discover any security related issues, please email github@vakata.com instead of using the issue tracker.

## Credits

- [vakata][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information. 

[ico-version]: https://img.shields.io/packagist/v/vakata/events.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/vakata/events.svg?style=flat-square

[link-packagist]: https://packagist.org/packages/vakata/events
[link-downloads]: https://packagist.org/packages/vakata/events
[link-author]: https://github.com/vakata
[link-contributors]: ../../contributors
[link-cc]: https://codeclimate.com/github/vakata/events

