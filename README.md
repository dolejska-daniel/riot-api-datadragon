# RiotAPI PHP7 wrapper
> Version v1.0.0

[![Build Status](https://img.shields.io/travis/dolejska-daniel/riot-api-datadragon/master)](https://travis-ci.com/dolejska-daniel/riot-api-datadragon)
[![Test Coverage](https://img.shields.io/codeclimate/coverage/dolejska-daniel/riot-api-datadragon?logo=code-climate)](https://codeclimate.com/github/dolejska-daniel/riot-api-datadragon/coverage)
[![Packagist](https://img.shields.io/packagist/dm/dolejska-daniel/riot-api-datadragon)](https://packagist.org/packages/dolejska-daniel/riot-api-datadragon)
[![Packagist](https://img.shields.io/packagist/l/dolejska-daniel/riot-api-datadragon)](https://packagist.org/packages/dolejska-daniel/riot-api-datadragon)
[![Support Project](https://img.shields.io/badge/support_project-PayPal-blue)](https://www.paypal.me/dolejskad)


# Table of Contents
1. [Introduction](#introduction)
2. [Downloading](#downloading)
3. [DataDragon API](#datadragon-api)


# [Introduction](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/Home#introduction)
Welcome to the RiotAPI PHP7 library repo!
The goal of this library is to create easy-to-use library for anyone who might need one.
This is fully object oriented API wrapper for League of Legends' API.
A small DataDragon API wrapper is also included.

Here are some handy features:

- **[Rate limit caching](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-Rate-limiting)** and limit exceeding prevention - fully automatic.
- **[Call caching](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-Call-caching)** - enables the library to re-use already fetched data within given timespan - saves time and key's rate limit.
- **[StaticData endpoints](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-StaticData-endpoints)** - you can work with StaticData endpoints as if they were never deprecated.
- **[StaticData linking](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-StaticData-linking)** - library can automatically link related StaticData right into the returned object.
- **[Custom callbacks](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-Callback-functions)** - you can set custom function which will be called before or after the request is processed.
- **[Object extensions](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-Extensions)** - you can implement your own methods to the fetched API objects and enable yourself to use them later to ease of your work.
- **[CLI supported](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/LeagueAPI:-CLI-support)** - usage of this library in console is extremely easy.
- **Interim mode** support - you are going to be able to use the library the same way whether your key is in `interim mode` or not (meaning you won't need to change anything when you jump to production).
- **Objects everywhere** - API calls return data in special objects, this allows modern IDEs to hint existing properties and methods.

Please, refer mainly to the [wiki pages](https://github.com/dolejska-daniel/riot-api-datadragon/wiki).
This file contains only general introduction to library features.


# [Downloading](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/Home#downloading)
The easiest way to download and use this library is via [Composer](https://getcomposer.org/).
If you are not using Composer yet, you should start **right now**!

While having Composer installed on your machine it takes only `composer require "dolejska-daniel/riot-api-datadragon:^1"` command to get the library ready to roll!

For additional information about downloading and initial setup, please see [the wiki pages](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/Home#downloading).


# [DataDragon API](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/DataDragonAPI:-How-to-begin)
How easy is it to work with static images? For instance, to get loading screen art of Orianna?

**Source**:
```php
echo DataDragonAPI::getChampionLoading('Orianna');
echo DataDragonAPI::getChampionLoading('Orianna', 7);
```

**Output**:
```html
<img alt="Orianna" class="dd-icon dd-loading" src="http://ddragon.leagueoflegends.com/cdn/img/champion/loading/Orianna_0.jpg">
<img alt="Orianna" class="dd-icon dd-loading" src="http://ddragon.leagueoflegends.com/cdn/img/champion/loading/Orianna_7.jpg">
```

**Render**:

![Orianna](http://ddragon.leagueoflegends.com/cdn/img/champion/loading/Orianna_0.jpg)
![Dark Star Orianna](http://ddragon.leagueoflegends.com/cdn/img/champion/loading/Orianna_7.jpg)


...a bit of nostalgia?

**Source**:
```php
DataDragonAPI::iniByVersion('0.151.2');
echo DataDragonAPI::getItemIcon(3132);
echo DataDragonAPI::getItemIcon(3126);
echo DataDragonAPI::getItemIcon(3138);
```

**Output**:
```html
<img alt="3132" class="dd-icon dd-item" src="http://ddragon.leagueoflegends.com/cdn/0.151.2/img/item/3132.png">
<img alt="3126" class="dd-icon dd-item" src="http://ddragon.leagueoflegends.com/cdn/0.151.2/img/item/3126.png">
<img alt="3138" class="dd-icon dd-item" src="http://ddragon.leagueoflegends.com/cdn/0.151.2/img/item/3138.png">
```

**Render**:

![Heart of Gold](http://ddragon.leagueoflegends.com/cdn/0.151.2/img/item/3132.png)
![Madred's Bloodrazor](http://ddragon.leagueoflegends.com/cdn/0.151.2/img/item/3126.png)
![Leviathan](http://ddragon.leagueoflegends.com/cdn/0.151.2/img/item/3138.png)


...or to display icon of champion and its spells based on its object from API?

**Source**:
```php
// ...

$orianna = $api->getStaticChampion(61, true);
echo DataDragonAPI::getChampionSplashO($orianna);

foreach($orianna->spells as $spell)
    echo DataDragonAPI::getChampionSpellIconO($spell);
```

**Output**:
```html
<img alt="Orianna" class="dd-icon dd-icon-champ" src="https://ddragon.leagueoflegends.com/cdn/8.24.1/img/champion/Orianna.png">

<img alt="OrianaIzunaCommand" class="dd-icon dd-spell" src="http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaIzunaCommand.png">
<img alt="OrianaDissonanceCommand" class="dd-icon dd-spell" src="http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaDissonanceCommand.png">
<img alt="OrianaRedactCommand" class="dd-icon dd-spell" src="http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaRedactCommand.png">
<img alt="OrianaDetonateCommand" class="dd-icon dd-spell" src="http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaDetonateCommand.png">
```

**Render**:

![Orianna](https://ddragon.leagueoflegends.com/cdn/8.24.1/img/champion/Orianna.png)
![OrianaIzunaCommand](http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaIzunaCommand.png)
![OrianaDissonanceCommand](http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaDissonanceCommand.png)
![OrianaRedactCommand](http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaRedactCommand.png)
![OrianaDetonateCommand](http://ddragon.leagueoflegends.com/cdn/8.24.1/img/spell/OrianaDetonateCommand.png)

For more, please see [the wiki pages](https://github.com/dolejska-daniel/riot-api-datadragon/wiki/DataDragonAPI:-How-to-begin).
More usage examples for DataDragonAPI can be found [here](https://github.com/dolejska-daniel/riot-api/blob/master/examples/DataDragonAPI/README.md).


# Other Riot APIs

| Library Description                                                               | Latest Version | Stable Version |
| --------------------------------------------------------------------------------- | -------------- | -------------- |
| [All APIs](https://github.com/dolejska-daniel/riot-api) (metapackage)             | ![GitHub Latest Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api?include_prereleases) | ![GitHub Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api) ![PHP Version](https://img.shields.io/packagist/php-v/dolejska-daniel/riot-api) |
| [DataDragon API](https://github.com/dolejska-daniel/riot-api-datadragon)          | ![GitHub Latest Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-datadragon?include_prereleases) | ![GitHub Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-datadragon) ![PHP Version](https://img.shields.io/packagist/php-v/dolejska-daniel/riot-api-datadragon) |
| [Teamfight Tactics API](https://github.com/dolejska-daniel/riot-api-tft)          | ![GitHub Latest Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-tft?include_prereleases) | ![GitHub Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-tft) ![PHP Version](https://img.shields.io/packagist/php-v/dolejska-daniel/riot-api-tft) |
| [Legends of Runeterra API](https://github.com/dolejska-daniel/riot-api-runeterra) | ![GitHub Latest Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-runeterra?include_prereleases) | ![GitHub Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-runeterra) ![PHP Version](https://img.shields.io/packagist/php-v/dolejska-daniel/riot-api-runeterra) |
| [Valorant API](https://github.com/dolejska-daniel/riot-api-valorant)              | ![GitHub Latest Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-valorant?include_prereleases) | ![GitHub Release](https://img.shields.io/github/v/release/dolejska-daniel/riot-api-valorant) ![PHP Version](https://img.shields.io/packagist/php-v/dolejska-daniel/riot-api-valorant) |
