# ElasticsearchDSL

Introducing Elasticsearch DSL library to provide objective query builder for [Elasticsearch bundle](https://github.com/ongr-io/ElasticsearchBundle) and [elasticsearch-php](https://github.com/elastic/elasticsearch-php) client. You can easily build any Elasticsearch query and transform it to an array.

If you need any help, [stack overflow](http://stackoverflow.com/questions/tagged/ongr)
is the preffered and recommended way to ask ONGR support questions.
 
[![Build Status](https://travis-ci.org/ongr-io/ElasticsearchDSL.svg?branch=master)](https://travis-ci.org/ongr-io/ElasticsearchDSL)
[![Coverage Status](https://coveralls.io/repos/ongr-io/ElasticsearchDSL/badge.svg?branch=master&service=github)](https://coveralls.io/github/ongr-io/ElasticsearchDSL?branch=master)
[![Latest Stable Version](https://poser.pugx.org/ongr/elasticsearch-dsl/v/stable)](https://packagist.org/packages/ongr/elasticsearch-dsl)
[![Total Downloads](https://poser.pugx.org/ongr/elasticsearch-dsl/downloads)](https://packagist.org/packages/ongr/elasticsearch-dsl)
[![Scrutinizer Code Quality](https://scrutinizer-ci.com/g/ongr-io/ElasticsearchDSL/badges/quality-score.png?b=master)](https://scrutinizer-ci.com/g/ongr-io/ElasticsearchDSL/?branch=master)

## Version matrix

| Elasticsearch version | ElasticsearchDSL version    |
| --------------------- | --------------------------- |
| >= 5.0, >= 2.0        | >=2.2                       |
| >= 2.0, < 5.0         | >=2.0  <2.2                 |
| >= 1.0, < 2.0         | 1.x                         |
| <= 0.90.x             | not supported               |

> ElasticsearchDSL from version >=2.2 works with both Elasticsearch >=2.0 and >=5.0 versions. 

## Documentation

[The online documentation of the bundle is here](docs/index.md)

## Try it!

### Installation

Install library with [composer](https://getcomposer.org):

```bash
$ composer require ongr/elasticsearch-dsl
```

### Search

Elasticsearch DSL was extracted from [Elasticsearch Bundle](https://github.com/ongr-io/ElasticsearchBundle) to provide standalone query dsl for [elasticsearch-php](https://github.com/elastic/elasticsearch-php). Examples how to use it together with [Elasticsearch Bundle](https://github.com/ongr-io/ElasticsearchBundle) can be found in the [Elasticsearch Bundle docs](https://github.com/ongr-io/ElasticsearchBundle/blob/master/Resources/doc/search.md).

If you dont want to use Symfony or Elasticsearch bundle, no worries, you can use it in any project together with [elasticsearch-php](https://github.com/elastic/elasticsearch-php). Here's the example:

Install `elasticsearch-php`:

```bash
$ composer require elasticsearch/elasticsearch
```

Create search:

```php
 <?php
  require 'vendor/autoload.php';
  $client = ClientBuilder::create()->build();
  
  $matchAll = new ONGR\ElasticsearchDSL\Query\MatchAllQuery();
  
  $search = new ONGR\ElasticsearchDSL\Search();
  $search->addQuery($matchAll)
  
  $params = [
    'index' => 'your_index',
    'body' => $search->toArray(),
  ];
  
  $results = $client->search($params);
```

Elasticsearch DSL covers every elasticsearch query, all examples can be found in [the documentation](docs/index.md)
