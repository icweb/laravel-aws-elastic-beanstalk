# Laravel + AWS Elastic Beanstalk Integration

This project demonstrates the integration of the AWS SDK for PHP Elastic Beanstalk client into a Laravel project, covering two functions of the service: describing applications, and describing application environments. This project is a demonstration and requires you to integrate your own use case.
___

### Prerequisites

#### __AWS Account & Access Keys__

You will need to get your `AWS Secret Access Key` and `Access Key ID` to use the SDK. [Click here](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_access-keys.html?icmpid=docs_iam_console) to visit the Managing Access Keys for IAM Users page and learn how to find these keys.

#### __About Elastic Beanstalk__

* [https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-elasticbeanstalk-2010-12-01.html#describeapplications](https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-elasticbeanstalk-2010-12-01.html#describeapplications)
* [https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-elasticbeanstalk-2010-12-01.html#describeenvironments](https://docs.aws.amazon.com/aws-sdk-php/v3/api/api-elasticbeanstalk-2010-12-01.html#describeenvironments)

___

### Installation

Begin by installing the AWS SDK for PHP package with Composer. Edit your `composer.json` file to require `aws/aws-sdk-php` version 3.

```json
"require": {
  "aws/aws-sdk-php": "3.*"
}
```


Then update your project by running this command in your terminal at your project root.

```
composer update
```

___

### Configuration

Add two new environment variables to your `.env` file and populate the values with your keys found in the prerequisites section.

```
AWS_SECRET_ACCESS_KEY=ENTER_YOUR_KEY
AWS_ACCESS_KEY_ID=ENTER_YOUR_KEY
```

___


### Usage

#### __Create the Client__

Create a new  `ElasticBeanstalkClient` and fill in your region to begin making requests.

```php
use Aws\ElasticBeanstalk\ElasticBeanstalkClient;

$client = new ElasticBeanstalkClient([
    'region'    => 'ENTER_YOUR_REGION',
    'version'   => 'latest'
]);
```

#### __Create the Request__

Create a request to Elastic Beanstalk.

__Describe Applications__

```php
$applications = $client->describeApplications([])['Applications'];
```

 
 __Describe Environments__
 
 ```php
$environments = $client->describeEnvironments(['ApplicationNames' => ['NAME_OF_APPLICATION']])['Environments'];
 ```