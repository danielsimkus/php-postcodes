# PHP Postcodes

This library handles various UK postcode related tasks.

## Features

* Address lookup by postcode
* Postcode validation
* Generate valid UK postcodes

## Installation

To install, just run the following composer command.

`composer require rapidwebltd/php-postcodes`

## Setup

### Ideal Postcodes

Using some of the data retrieval features provided by this library requires an Ideal Postcodes 
API key. Sign up at https://ideal-postcodes.co.uk if you need to use these features.

If you are using a `.env` file or another way of manage environment variables in your 
project, set the following variable to specify the Ideal Postcode.

```
IDEAL_POSTCODES_API_KEY=abcdef
```

You can then use the following code to get an `IdealPostcodes` object.

```php
$idealPostcodes = \RapidWeb\Postcodes\Factories\IdealPostcodesFactory::getByEnvironment();
```

If you are not using environment variables in your project, simple pass through the API
key as follows.

```php
$idealPostcodes = \RapidWeb\Postcodes\Factories\IdealPostcodesFactory::getByAPIKey('abdef');
```

## Usage

### Get addresses by postcode

To retrieve the addreses associated with a UK postcode, just pass it to the method shown below. 
You will receive an array of addresses, appropriately split by their address lines.

```php
$addresses = $idealPostcodes->getAddressesByPostcode('ST163DP');
```

### Validate postcode

You can validate a UK postcode is correct using the `Validator` utility class. An example of 
how to do so is shown below.

```php
$validated = \RapidWeb\Postcodes\Utils\Validator::validatePostcode('ST163DP');
```

Please note that the postcode validation is case insensitive.

### Generate postcode

This library allows you generate a random, validate, UK postcode. This makes use of the
`Generator` utility class, as shown below.

```php
$postcode = \RapidWeb\Postcodes\Utils\Generator::generatePostcode();
```
