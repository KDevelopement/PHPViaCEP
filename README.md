# ViaCEP PHP SDK

[![Latest Version on Packagist][ico-version]][link-packagist]
[![Software License][ico-license]](LICENSE.md)
[![Total Downloads][ico-downloads]][link-downloads]
[![Coverage Status](https://coveralls.io/repos/github/KS7ven/PHPViaCEP/badge.svg?branch=master)](https://coveralls.io/github/KS7ven/PHPViaCEP?branch=master)
[![](https://github.com/KS7ven/PHPViaCEP/workflows/PHPUnit/badge.svg)](https://github.com/KS7ven/PHPViaCEP/actions/workflows/phpunit.yml)
[![](https://github.com/KS7ven/PHPViaCEP/workflows/PHPStan/badge.svg)](https://github.com/KS7ven/PHPViaCEP/actions/workflows/phpstan.yml)
[![](https://github.com/KS7ven/PHPViaCEP/workflows/Deptrac/badge.svg)](https://github.com/KS7ven/PHPViaCEP/actions/workflows/deptrac.yml)

Pesquise endereços por CEP usando a API REST [ViaCEP](https://viacep.com.br).

## Instalar

Via Composer

``` bash
$ composer require kseven/phpviacep
```

## Uso

### findByZipCode (Sem retorno de chamada)

Encontre o endereço pelo código postal.

```php
use KSeven\ViaCEP\VCRun AS ViaCEP;

$ViaCEP = new ViaCEP;

$Address = $ViaCEP->findByZipCode('01001-000')->toArray();

/*
Deve retornar algo assim:

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
Deve retornar algo assim:

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

### findByZipCode (Com retorno de chamada)

Encontre o endereço por código postal, com retorno de chamada.

```php
use KSeven\ViaCEP\VCRun AS ViaCEP;

$ViaCEP = new ViaCEP;

$Address = $ViaCEP->findByZipCode('01001-000', 'callback_name')->withCallback();

/*
Deve retornar algo assim:

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

Pesquise endereços usando estado, cidade e nome de uma rua.

```php
use KSeven\ViaCEP\VCRun AS ViaCEP;

$ViaCEP = new ViaCEP;

$Addresses = $ViaCEP->findByStreetName('SP', 'São Paulo', 'Gomes de Carvalho');

/*
Deve retornar algo assim:

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

## Registo de alterações

Consulte [CHANGELOG](CHANGELOG.md) para obter mais informações sobre o que mudou recentemente.

## Contribuindos

Consulte [CONTRIBUINDO](CONTRIBUINDO.md) e [CONDUTA](CONDUTA.md) para obter detalhes.

## Segurança

Se você descobrir algum problema relacionado à segurança, envie um e-mail para contato@kseven.dev.br em vez de usar o rastreador de problemas.

## Credits

- [K'Seven][link-author]
- [All Contributors][link-contributors]

## Licença

A licença MIT (MIT). Consulte [Arquivo de licença](LICENSE.md) para obter mais informações..

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
