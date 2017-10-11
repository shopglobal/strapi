# API

## Introduction

The API folder contains most of your backend application. Here, you have all your business logic and content types REST API.

It’s in this folder that you will spend the major part of your time. Now we will see how to work with it.

### Structure

The API main folder contains one folder per API. One API can be a content type generated by the command line or by the content type builder plugin. You can also create your own API which contains a business logic with it’s own routes, controller actions and services.

config - Config contains a `route.json` file with your API routes (see documentation routing) and json files for every custom config you want to add to your API (this configs are not by env)
controllers - Controllers contains all your controllers' files (see controllers documentation for more informations)
models - Models contains all your models' files (see models documentation for more informations)
services - Services contains all your services' files (see services documentation for more informations)

### References

All your APIs are in the strapi global variable. You can access to an API using `strapi.api`

For example if you define a `hash` function for the user API's service, you will be able to access it everywhere in your app with `strapi.api.user.services.user.hash()`

configs, controllers, models and services are exposed in `strapi.api` object.

### Create an API

Link to https://docs.google.com/document/d/1kQKpeBUfZXap3nwPkxMMA0gAQW6VB_0qaUM30PPkGCg/edit