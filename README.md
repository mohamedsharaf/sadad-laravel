# sadad-laravel 


transaction request library for sadad

## usage
### installation
``composer require rfmhb2/sadad-laravel``


## laravel ready
this package is going to work with all kinds of projects, but for laravel i add provider to make it as easy as possible.
just add **(if you are using laravel 5.5 or higher skip this one)**:
```php
'providers' => [
    ...
    Sadad\Laravel\SadadServiceProvider::class
    ...
]
``` 
to providers list in "config/app.php". then add this to `config/services.php`
```php
'sadad' => [
    'merchantID' => '00000000000000',
    'terminalId' => '00000000',
    'key' => 'XXXXXXXXXXXXXXXXXXXXXXXXXXXXXXXX',
],
```
and you are good to go (legacy config still works)
now you can access the sadad lib like this:
```php
use Sadad\Laravel\Facade\Sadad;

$results = Sadad::request(
    "example.com/testVerify.php",          //required
    1000,                                  //required
    'YOUR_DATE'                            //required format=>m/d/Y g:i:s a
);
// save $results['Authority'] for verifying step
Sadad::redirect(); // redirect user to sadad

// after that verify transaction by that $results['Authority']
Sadad::verify('token');
```

