# ViaCEP PHP SDK

[![Latest Version on Packagist][ico-version]][link-packagist]
[![CircleCI][icon-circleci]][link-circleci]
[![Codecov][icon-codecov]][link-codecov]
[![Software License][ico-license]](LICENSE.md)
[![Total Downloads][ico-downloads]][link-downloads]

Search for addresses by zip code using the [ViaCEP](https://viacep.com.br) REST API.

## Install

Via Composer

``` bash
$ composer require kseven/phpviacep
```

## Usage

### findByZipCode (No Callback)

Find address by zip code.

```php
use KSeven\ViaCEP\VCRun AS ViaCEP;

$ViaCEP = new ViaCEP;

$Address = $ViaCEP->findByZipCode('01001-000')->toArray();

/*
Should return something like this:

[
    'zipCode' => '01001-000',
    'street' => 'Praça da Sé',
    'complement' => 'lado ímpar',
    'neighborhood' => 'Sé',
    'city' => 'São Paulo',
    'state' => 'SP',
    'ibge' => '3550308',
]
*/

$Address = $ViaCEP->findByZipCode('01001-000')->toJson();

/*
Should return something like this:

{
    "zipCode": "01001-000",
    "street": "Praça da Sé",
    "complement": "lado ímpar",
    "neighborhood": "Sé",
    "city": "São Paulo",
    "state": "SP",
    "ibge": "3550308"
}
*/
```

### findByZipCode (With Callback)

Find address by zip code, with callback.

```php
use KSeven\ViaCEP\VCRun AS ViaCEP;

$ViaCEP = new ViaCEP;

$Address = $ViaCEP->findByZipCode('01001-000', 'callback_name')->withCallback();

/*
Should return something like this:

callback_name({
    "cep": "01001-000",
    "logradouro": "Praça da Sé",
    "complemento": "lado ímpar",
    "bairro": "Sé",
    "localidade": "São Paulo",
    "uf": "SP",
    "ibge": "3550308",
    "gia": "1004",
    "ddd": "11",
    "siafi": "7107"
});
*/
```

### findByStreetName

Search for addresses using state, city and a street name.

```php
use KSeven\ViaCEP\VCRun AS ViaCEP;

$ViaCEP = new ViaCEP;

$Addresses = $ViaCEP->findByStreetName('SP', 'São Paulo', 'Gomes de Carvalho');

/*
Should return something like this:

[
    [
        'zipCode' => '01001-000',
        'street' => 'Praça da Sé',
        'complement' => 'lado ímpar',
        'neighborhood' => 'Sé',
        'city' => 'São Paulo',
        'state' => 'SP',
        'ibge' => '3550308',
    ],
    [
        'zipCode' => '01001-000',
        'street' => 'Praça da Sé',
        'complement' => 'lado ímpar',
        'neighborhood' => 'Sé',
        'city' => 'São Paulo',
        'state' => 'SP',
        'ibge' => '3550308',
    ]
]
*/
```

## Change log

Please see [CHANGELOG](CHANGELOG.md) for more information what has changed recently.

## Contributing

Please see [CONTRIBUTING](CONTRIBUTING.md) and [CONDUCT](CONDUCT.md) for details.

## Security

If you discover any security related issues, please email contato@kseven.dev.br instead of using the issue tracker.

## Credits

- [K'Seven][link-author]
- [All Contributors][link-contributors]

## License

The MIT License (MIT). Please see [License File](LICENSE.md) for more information.

[ico-version]: https://img.shields.io/packagist/v/kseven/phpviacep.svg?style=flat-square
[ico-license]: https://img.shields.io/badge/license-MIT-brightgreen.svg?style=flat-square
[ico-downloads]: https://img.shields.io/packagist/dt/kseven/phpviacep.svg?style=flat-square
[icon-circleci]: https://img.shields.io/circleci/project/github/kseven/phpviacep.svg?style=flat-square
[icon-codecov]: https://img.shields.io/codecov/c/github/kseven/phpviacep.svg?style=flat-square

[link-circleci]: https://circleci.com/gh/kseven/phpviacep
[link-codecov]: https://codecov.io/gh/kseven/phpviacep
[link-packagist]: https://packagist.org/packages/kseven/phpviacep
[link-downloads]: https://packagist.org/packages/kseven/phpviacep
[link-author]: https://github.com/KS7ven
[link-contributors]: ../../contributors
