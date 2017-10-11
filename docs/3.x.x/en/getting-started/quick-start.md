# Quick start

This section explains how to handle Strapi for the first time.

**Table of contents:**
- [Create your first project](#create-your-first-project)
- [Create your first API](#create-your-first-api)
  - [Content Type Builder plugin](#content-type-builder-plugin)
  - [Files structure](#files-structure)
- [Manage your data](#manage-your-data)
  - [Content Manager Plugin](#content-manager-plugin)
  - [Create a product](#create-a-product)
  - [Edit a product](#edit-a-product)
  - [Delete a product](#delete-a-product)
- [Consume your API](#consume-your-api)
  - [List entries](#list-entries)
  - [Get a specific entry](#get-a-specific-entry)
  - [Create data (POST)](#create-data-post)
  - [Update data (PUT)](#update-data-put)
  - [Delete data (DELETE)](#delete-data-delete)

***

## Create your first project

Creating your first project with Strapi is easy:

1. **Open your terminal**

  Open your terminal in the directory you want to create your application in.

2. **Run the following command line in your terminal:**

  ```bash
  strapi new my-project
  ```

  ![Generate a Strapi project](../assets/new-project.png)

  This action creates a new folder named `my-project` with the entire [files structure](../concepts/concepts.md#files-structure) of a Strapi application.

3. **Go to your project and launch the server:**

  In your terminal run the following commands:

  ```bash
  cd my-project
  strapi start
  ```
  ![Start Strapi](../assets/strapi-start.png)

Now that your app is running let's see how to [create your first api](#create-your-first-api).

***

## Create your first API

To create your first API, start your server (`strapi start`) and go to : http://localhost:1337/admin.

At this point, your application is empty. You can solve that by creating a CRUD (Create, Read, Update, Delete) API.

The easiest way to create your first API is to use the Content Type Builder plugin: a powerful UI to help you create an API in a few clicks.

Let's take the example of an e-commerce API, which manages products.

### Content Type Builder plugin

![Strapi Content Type Builder](../assets/content-type-builder.png)

To create your API using the Content Type Builder:
 - Start your project and visit the admin panel at the following address: http://localhost:1337/admin/plugins/content-type-builder.
 - Click on "Create Content Type" (it should open a form modal), fill the name field with `product` and submit the form.
 - Then, click on "Add fields", add the following fields:
   - A `string` field named `name`.
   - A `text` field named `description`.
   - A `number` field named `price` (with `float` as number format).
 - Save.
 - Refresh your browser to make it appear in the main menu.

That's it: your API is created!

*Note: See the [CLI documentation](../cli/CLI.md#strapi-generateapi) for informations about how to do it the hacker way*

### Files structure

A new directory has been created in the `/api` folder of your application which contains all the needed stuff for your `Product` Content Type: API, routes, controller, service and model. Take a look at the [API structure documentation](../concepts/concepts.md#files-structure) for more informations.


Well done, you created your first Strapi API!

***

## Manage your data

After creating [your first Content Type](#create-your-first-api), we need to create, edit and delete data.

In this section, we will discover the Content Manager Plugin that Strapi provides to help you for this task.

### Plugin Content Manager

If you visit the admin panel at http://localhost:1337/admin, you can access the Content Manager plugin. This powerful interface is auto-generated according to your Content Types and lets you create, update and delete your data from UI.

#### Create a product

Try to create a new product by clicking on "New entry". Give it a name, a description and a price. Submit the form. You can see the new product in the products list.

#### Edit a product

From the list view, you can click on a product and edit its values.

#### Delete a product

From the list view and the edit view, you can delete a product.

Great work! You are now able to create, update and delete data from the Content Manager plugin.

***

## Consume your API

Your API is now ready and [contains data](#manage-your-data). At this point, you'll probably want to use this data in mobile or desktop applications.

When you create your API using the command line or the Content Type Builder plugin, it automatically creates the needed files to build your Content Types REST API.

### List entries (GET)

To retrieve the list of products, use the `GET /your-content-type` route.

Generated APIs provide a handy way to filter and order queries. In that way, ordering products by price is as easy as `GET http://localhost:1337/product?_order=price:asc`. For more informations, read the [filters documentation](TODO)

Here is an example using jQuery.

```js
$.ajax({
  type: 'GET',
  url: 'http://localhost:1337/product_order=price:asc', // Order by price.
  done: function(products) {
    console.log('Well done, here is the list of products: ', products);
  },
  fail: function(error) {
    console.log('An error occurred:', error);
  }
});
```

### Get a specific entry (GET)

If you want to get a specific entry, add the `id` of the wanted product at the end of the url.

```js
$.ajax({
  type: 'GET',
  url: 'http://localhost:1337/product/123', // Where `123` is the `id` of the product.
  done: function(product) {
    console.log('Well done, here is the product having the `id` 123: ', product);
  },
  fail: function(error) {
    console.log('An error occurred:', error);
  }
});
```

### Create data (POST)

Use the `POST` route to create a new entry.

jQuery example:

```js
$.ajax({
  type: 'POST',
  url: 'http://localhost:1337/product',
  data: {
    name: 'Cheese cake',
    description: 'Chocolate cheese cake with ice cream',
    price: 5
  },
  done: function(product) {
    console.log('Congrats, your product has been successfully created: ', product); // Remember the product `id` for the next steps.
  },
  fail: function(error) {
    console.log('An error occurred:', error);
  }
});
```

### Update data (PUT)

Use the `PUT` route to update an existing entry.

jQuery example:

```js
$.ajax({
  type: 'PUT',
  url: 'http://localhost:1337/product/123', // Where `123` is the `id` of the product.
  data: {
    description: 'This is the new description'
  },
  done: function(product) {
    console.log('Congrats, your product has been successfully updated: ', product.description);
  },
  fail: function(error) {
    console.log('An error occurred:', error);
  }
});
```

### Delete data (DELETE)

Use the `DELETE` route to delete an existing entry.

jQuery example:

```js
$.ajax({
  type: 'DELETE',
  url: 'http://localhost:1337/product/123', // Where `123` is the `id` of the product.
  done: function(product) {
    console.log('Congrats, your product has been successfully deleted: ', product);
  },
  fail: function(error) {
    console.log('An error occurred:', error);
  }
});
```

***

Congratulations! You successfully finished the Getting Started guide! Read the [concepts](../concepts/concepts.md) to understand more advanced concepts.

Also, feel free to join the community thanks to the different channels listed in the [community page](http://strapi.io/community): team members, contributors and developers will be happy to help you.