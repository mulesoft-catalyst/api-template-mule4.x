# API Template for Mule 4

API Templates act as foundations for developers to start building APIs. They need not worry about adding dependencies and configure autodiscovery as all is handled by the template. The template utilizes 2 Mule Extensions as follows,

1. JSON Logger: This is used for Logging in the API and is custom plugin built by Andres Ramirez from Services and is present at https://github.com/mulesoft-catalyst/json-logger/tree/mule-4.x . Please publish this to your private Exchange before publishing the template. The guide to publiush it present the above link
2. Error Handler Plugin: This is a common error handler that is fully customizable and is used by the template to handle errors. In case of an error the On Error Propgate is used which sends the information to the error handler which then handles the error, maps to the error object and prints it. This was built by Biswa Mohanty from Services and is present at https://github.com/mulesoft-catalyst/error-handler-plugin. You need to publish this to Exchange before using the template.

## Template Features

1. Logging - Uses the JSON Logger to take care of logging
2. Error Handling - Uses the Error Handler Plugin to conduct error handling
3. API Autodiscovery - Is preconfigured with API Autodiscovery and only the API ID needs to be provided.
4. Preconfigured APIKIT Router - Uses the APIKit router which has been configured with the necessary information
5. End to End Transaction Handling

## Deploying to Exchange
To deploy to Exchange, run the script named deploy.sh as follows,

./deploy.sh <YOUR_ORG_ID>

Please ensure that your settings.xml has been configured with the correct Exchange credentials so that the publish can succeed.

## Local Install
For local install, give any groupId. Issue `mvn clean install`

## Usage

Import the API Template from Exchange and into Studio and start building the business logic for your API

Also view the readme.txt file that explains how to use template
