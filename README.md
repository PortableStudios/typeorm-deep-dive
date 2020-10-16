# Portable Tech Team Deep Dive - TypeORM

## Introduction

When we build our web applications, we often will have to store data in
a database. There are a number of web frameworks that will handle the
creation of models and database tables for you.

* In Wordpress, Drupal and Silverstripe you can do this by defining a
  schema for the content model and then running a script (or perhaps on
  visiting a URL) that will create those for you
* In Laravel, Ruby on Rails and NestJS you might write specific database
  migrations to add tables, remove columns, add indexes and more to the
  database

### What is an ORM?

An ORM is an Object Relational Mapper - which is responsible for mapping
data from the database, into objects in you code that you can use in
your applications.


### Today we are going to look at... TypeORM

TypeORM is an ORM that can run in NodeJS, Browser, Cordova, PhoneGap,
Ionic, React Native, NativeScript, Expo, and Electron platforms and can
be used with TypeScript and JavaScript (ES5, ES6, ES7, ES8). Its goal is
to always support the latest JavaScript features and provide additional
features that help you to develop any kind of application that uses
databases - from small applications with a few tables to large scale
enterprise applications with multiple databases.

## Agenda

* Get started with TypeORM
* Learn to create some models in our code and update the database
* Add some relationships to those models and create some related data in
  the database
* Query the database via the models
* Write our first migration and run it

### Getting started

To get all of the dependencies installed, run `yarn install`
You will also need `sqlite` installed. You can do that with `brew
install sqlite` on OS X.

Everything in the repo thus far, was just created by running
```
yarn run typeorm init --database sqlite --express
```

`yarn start` to run the application. Which will:

* create a sqlite database for you in the root directory of the project
  called `database.sqlite`
* automatically create the required tables and columns in the database
  based on the `User` entity
* insert 2 test records as listed in `src/index.ts`
* start an expressjs server that will render those two records as JSON

Let's walkthrough each of those steps individually to understand what is
going on.

### Create a new model

Come up with a new data model. It can be anything you like! Try to use
some new database column types as well as some restrictions on your
fields. Some hints:

* try to add a datetime column that automatically stores the timestamp
  of when the record was created
* look at adding a limit of characters to string or text columns

Here is some documentation to help you try these things and more:
https://typeorm.io/#/entities

**** Have you created your model yet? ****

Great! Now create some records for your new model to confirm that it is
working!

### Relationships

We'll start to look at the many-to-one/one-to-many relationships.

Go ahead and implement the `Photo` entity so that a `User` has-many
`Photos`

Details and instructions here: https://typeorm.io/#/many-to-one-one-to-many-relations

Once you've created the relationship, try to save a photo record to a specific user.
Then save a few photos to 2 or more users.

**** Have you saved photos to users? ****

Great, now it's time to query the data.

### Querying the database

Now that we have Users that have Photos, let's write a query that will
return all of the photos for one user.

Once you've done that, try to:
* return all photos from the first 2 users
* return only the first photo from all users

Take a look at the query builder documentation for some assistance.
https://typeorm.io/#/select-query-builder


### Migrations

OK, so now we have a situation where actually, it makes more sense to
rename a field in our User model from `lastName` to `surname`. How will
we achieve this without destroying the data or causing the application
to break?

Work through the https://typeorm.io/#/migrations page to:

* generate a migration to rename the `User` entity column from
  `lastName` to `surname` using the typeorm CLI
* run the migration and make sure that the application still functions
* rollback the migration and make sure that the application still
  functions

## Fin

To learn more about this, there is some training available in the
official NestJS course (Chapter 3) and overall, the official TypeORM
documentation is full of example code that will help you to create and
experiment with many different entity configurations and relationships.

Enjoy!!
