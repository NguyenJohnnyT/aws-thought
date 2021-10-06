# AWS Deep Thoughts
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
#
## [Deployed Link](http://3.22.175.224/) `(warning: http route)`
![Example gif](Deep_Thoughts.gif)

## Table of Contents
* [Description](#Description)
* [Installation](#Installation)
* [Usage](#Usage)
* [Credits](#Credits)
* [License](#License)

## Description

A Twitter-esque web application that utilizes React, NodeJS, and AWS services.  With a username and a thought, anyone can make a post in a list of user thoughts.  Users may also post an image uploaded from their device.

## Installation
Important documentation for using AWS and its services:
[DynamoDB](https://aws.amazon.com/dynamodb/), [S3](https://aws.amazon.com/s3/?nc2=type_a), [EC2](https://aws.amazon.com/ec2/)

While the API end points are functional, there are multiple AWS procceses that the user will need to go through in order to create their own working server, database, and storage.  For new AWS users, it would be important to find a tutorial on how to create a accounts, setting AWS credentials with the AWS CLI, and creating security policies while also setting up DynamoDB, S3, and EC2 so that the application works.

Users with AWS credentials that have set up an IAM user, S3 bucket, DynamoDB, and E2 will be interested in the following lines of code:
```
in ./server/utils/params-config.js
...
const imageParams = {
    Bucket: <name of your bucket here>,
    ...
...
```

```
When modifying API Calls in the Virtual Machine EC2 Instance
Make sure to change the fetch URLs in the following client-side files and add the public IP4 address for the EC2 instance:
  *In client pages: Home.js, Profile.js
  *In client components: ThoughtForm/index.js
  Example in Home.js:
    const Profile = Props => {
      ...
      useEffect(() => {
        const fetchData = async () => {
          try {
                              //!Insert Public IP address here!
                                  // vvv
            const res = await fetch(`   /api/users/${userParam}`, {
              ...
            })
          }
          ...
        }
      }
      ...)
    }
```

NPM packages required (`npm install` at root folder to install all the packages):

Client-side:\
[React](https://reactjs.org) Viewing framework

Server-side:\
[aws-sdk](https://www.npmjs.com/package/aws-sdk) Connecting to AWS services\
[express](https://www.npmjs.com/package/express) Server package\
[multer](https://www.npmjs.com/package/multer) For uploading images\
[uuid](https://www.npmjs.com/package/uuid) Creating unique ids for images uploaded\

Setting up EC2 environment:\
[AWS-CLI](https://aws.amazon.com/cli/) Use AWS services through a command line\
[Git](https://github.com/git-guides/install-git) Use git\
[npm & nodejs](https://nodejs.org/en/) Use nodejs in our instance\
[nginx](http://nginx.org/) Application server that will expose EC2 instance\
[pm2](https://www.npmjs.com/package/pm2) Process manager--keeps application running after we have logged out of server

## Usage

The thoughts is populated from a DynamoDB database and an S3 bucket.  DynamoDB enables scalability for large amounts of requests and posts while S3 enables users to upload their own images--URLs to these images are also part of each dynamoDB item.

As users post, they may select user profiles to see all thoughts written by the a user.

Future ideas: Delete routes to delete any thoughts, actual user log ins

## Credits

[UC Berkeley Bootcamp](https://bootcampspot.com/)\
[AWS](https://aws.amazon.com/)

## License

This application is licensed under [MIT](https://opensource.org/licenses/MIT).

## Questions
Please direct any questions to me at jtn.mechocreamy@gmail.com.
