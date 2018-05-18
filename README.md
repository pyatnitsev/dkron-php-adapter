[![Build Status](https://travis-ci.com/gromo/dkron-php-adapter.svg?branch=master)](https://travis-ci.com/gromo/dkron-php-adapter)
[![PHP](https://img.shields.io/badge/PHP-%5E7.0-blue.svg)](https://packagist.org/packages/gromo/dkron-php-adapter)
[![Dkron version](https://img.shields.io/badge/Dkron-v0.10.0-green.svg)](https://github.com/victorcoder/dkron/releases/tag/v0.10.0)



# Dkron PHP Adapter

Adapter to communicate with [Dkron](https://dkron.io) v0.10.0.

Please read [API](https://dkron.io/usage/api/) for usage details

### Install:
- add `"gromo/dkron-php-adapter": "dev-master"` to your project `composer.json`
- run `composer install`

### Use:
```php
$httpClient = new \GuzzleHttp\Client([
    'base_uri' => 'http://URL_TO_DKRON_AGENT/',
]);

$api = new \Dkron\Api($httpClient);

// create new job
$newJob = new \Dkron\Models\Job('my-job', '@every 5m');
$newJob->setExecutor('shell');
$newJob->setExecutorConfig([
    'command' => 'ls -la /'
]);
$api->saveJob($newJob);

// get job by name
$existingJob = $api->getJob('my-job');

// get all jobs
$jobs = $api->getJobs();

$leader = $api->getLeader();

$members = $api->getMembers();

$status = $api->getStatus();


```
