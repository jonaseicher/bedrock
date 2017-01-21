# Bedrock
Bedrock lets you set up a production-ready webapp in under 10 minutes. It is a collection of popular frameworks that work well together. 


## [Go to Documentation Site](https://tilomitra.github.io/bedrock)

---

#### [Watch a video showing how to get a production-ready web app with user authentication set up in 5 minutes using Bedrock](https://www.youtube.com/watch?v=EdUuhdbhfDo)

## Features Overview

- An Sails (Express) server with user authentication
- Auto-generated REST API for all your models
- Signup, Login, Reset Password Pages
- SMTP Email Support
- Server-side rendered pages
- Client-side rendered components using React
- Communication between React and Server-side API with Flux. 
- Client-side routing with React Router
- Incremental builds using Webpack, facilitated through Grunt.
- Migrations to help coordinate database changes
- Production-ready such as API access tokens, CSRF protection, CORS, and more.
- Support for multiple environments (dev, stage, prod)

## Why should you use it?
Use Bedrock to set up a production-ready Node webapp in under 10 minutes. 

You get user authentication, security, a front-end framework, and more.

At SoundHound, we use a version of Bedrock for many of our internal web applications. It is great for dashboards, CRUD webapps, and more.


## Quickstart
We will talk about the installation in more detail in the next section, but here is the quickstart guide.

```
git clone git@github.com:tilomitra/bedrock.git <project-name>
cd <project-name>
npm install
```
Then, open config/connections.js and update your database connection details.

Then, run the migrations to create the relevant database tables.

```
# Run migrations
grunt db:migrate:up
```

Then, build (and watch for changes) in the CSS and JS assets.

```
# Build and watch css/js
grunt build
```

Finally, start the server. You will be taken to the signup page.

```
# Start the server
sails lift
```

## Detailed Installation and Setup
Bedrock is the *starting point* of your Node application. To install, you should clone the project, and then build on top of it.

```
git clone ... <project-name>
cd <project-name>
npm install
```

### Configure Database Connection

Go into `config/connections.js`. Update the `mysql` connection details. At this point, you may need to create a new database.

If you want to use a different database (PostgreSQL or Mongo), remove the `mysql` connection, and create a new connection, as shown in the comments in the file.

### Migrate database tables
Bedrock sets up authentication for your server, and creates Login, Signup, and Reset password pages. It uses PassportJS to accomplish this.

To facilitate this, you need to run a migration to create the `Users` and `Passports` table. Just run this from the command line:

```
grunt db:migrate:up
```
After it runs, check your database and you should see `Users` and `Passports` table created.

We will talk more about migrations in the Best Practices section.

### Build JS/CSS assets
Bedrock uses Grunt to build the CSS and JS assets. To build, just run:

```
grunt build
```

This will run the CSS and JS assets. It will also start watching for CSS and JS changes.

### Run the server
To run the server, run:

```
sails lift
```

By default, it will start up the server on port 1337. To configure the PORT or NODE_ENV, you can prefix those variables:

```
NODE_ENV=staging PORT=9999  sails --debug lift
```

## Server-side Features
Bedrock is built on [Sails](http://sailsjs.org), so it has all of the great features that Sails ships with. 

This includes, but is not limited to:

- It's just an Express server under the hood, so all Express modules still work
- Reusable Security Policies (Middleware)
- Configurable via a global `config` object.
- Encourage use of reusable services, like a `Mailer` service.
- Waterline ORM that works well with multiple databases. Can be swapped out if you need.
- Auto-generate REST APIs (optional)
- Follows MVC conventions, which keeps your code organized as your project grows.

[Check out all the features](http://sailsjs.com/features) on the Sails documentation page. I've used raw Express and I've used Sails, and I will take Sails everytime guys. 


## Client-side Features
Bedrock lets you build reusable components using React and call its API via Flux Actions. Pages are linked together using React Router

Here's how it works at a high level:

1. User navigates to a page
2. Page route triggers React Router to display a component, and execute certain Flux Actions.
3. Flux actions trigger API requests.
4. API responses trigger Flux Stores to change.
5. Flux stores change automatically re-renders React components that are watching the store.

It is simple, one-way communication that scales to hundreds of components (We have 100+ components in our internal fork of Bedrock).

## More Documentation
Learn more about Bedrock on [Node Web Apps](http://nodewebapps.com). Here are some useful tutorials:

* [Learn how to set up Bedrock](http://nodewebapps.com/2016/12/20/create-a-web-app-with-user-authentication-in-under-10-minutes/)
* [Learn how to set up Reset Password Flow in Bedrock](http://nodewebapps.com/2016/12/21/how-to-send-emails-in-sails-bedrock/)
* [Learn how to use migrations to make your database more stable](http://nodewebapps.com/2016/12/20/how-to-update-database-schema-for-a-production-web-app/)

Sign up to the Node Web Apps newsletter to stay up to date on new tutorials.

## Built With
Bedrock is composed of these open-source frameworks.

[Sails](http://sailsjs.com/): Sails makes it easy to build custom, enterprise-grade Node.js apps. It is designed to emulate the familiar MVC pattern of frameworks like Ruby on Rails, but with support for the requirements of modern apps: data-driven APIs with a scalable, service-oriented architecture

[React](https://facebook.github.io/react/): A JavaScript Library for building user interfaces

[React Router](https://github.com/ReactTraining/react-router): React Router is a complete routing library for React.

[NuclearJS](https://github.com/optimizely/nuclear-js): Traditional Flux architecture built with ImmutableJS data structures. Very similar to Redux.

[Webpack](https://webpack.github.io/): A module bundler for front-end assets. It is used in Bedrock for chunking JavaScript files to be loaded on demand.


