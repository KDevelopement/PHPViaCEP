# Changelog
All Notable changes to `viacep-php` will be documented in this file.
Updates should follow the [Keep a CHANGELOG](http://keepachangelog.com/) principles.

## v1.0.1

### Added
- Search addresses by zip code using the [ViaCEP](https://viacep.com.br) API with Callback.

### Removed
- Test mode removed.

## v1.0.0

### Changed
- Class `ZipCode` renamed to `ViaCEP`.
- Method `findByCep` renamed to `findByZipCode`.
- Method `findByAddress` renamed to `findByStreetName`.

### Fixed
- Error `403 Forbidden` when trying to search for addresses.

### Added
- Search addresses by zip code using the [ViaCEP](https://viacep.com.br) API.
- Search addresses using city, state and street name.

### Removed
- Method `find` (deprecated) removed. 
