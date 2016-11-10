###### Google Geocoding
Provides an abstraction for requests to Google Maps geocoding service.

## Installation
You can install this package via Composer using this command:

```bash
composer require navjobs/google-geocoder
```

## Laravel Installation
This package comes with a service provider for use with Laravel. To install the service provider:

```php
// config/app.php
'providers' => [
    // other providers
    'NavJobs\GoogleGeocoder\GoogleGeocoderServiceProvider'
];
```

Also you must publish the config file:

```php
php artisan vendor:publish --provider="NavJobs\GoogleGeocoder\GoogleGeocoderServiceProvider"
```

The config file allows you to set your `api key`, `language` and `region`.

## Usage

There are three ways that you may use this package.

```php
// Geocode an address
$geocoder = new Geocoder;
$geocoder->geocode('New York, NY');

// Reverse geocode from coordinates
$geocoder = new Geocoder;
$geocoder->reverseByCoordinates(40.7127837, -74.0059413);

// Reverse geocode from a Google place id.
$geocoder = new Geocoder;
$geocoder->reverseByPlaceId('ChIJOwg_06VPwokRYv534QaPC8g');
```

All of these methods return a standard repose format as follows:

```php
[
    'address' => 'New York, NY, USA',
    'latitude' => 40.7127837,
    'longitude' => -74.0059413,
    'place_id' => ChIJOwg_06VPwokRYv534QaPC8g,
    'types' => [
        'locality',
        'political'
    ]
    $bounds = [
        'northeast' => [
            'latitude' => 40.9152555,
            'longitude' => -73.7002721,
        ],
        'southwest' => [
            'latitude' => 40.496044,
            'longitude' => -74.255735,
        ]
    ];
}
```
