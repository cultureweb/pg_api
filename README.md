# Build a Full Stack JavaScript CRUD App with Node/Express/Handlebars/Bootstrap/Postgres/Knex


## Technologies Used

We'll be using:
* postgres for our database
* knex.js for our database migrations, seeds and queries.
* express.js for our routes and rendering
* handlebars.js for our server side view templates
* boostrap for our UI

## Full Stack Check List
* [x] Generate Express App
* [x] Create database/table
* [x] Seed table with sample data
* [x] List all records with GET /todo
* [x] Add Bootstrap
* [x] Show new form with /todo/new
* [x] Create a record with POST /todo
* [x] Show one record with GET /todo/:id
* [x] Show an edit form with GET /todo/:id/edit
* [x] Update a record with PUT /todo/:id
* [x] Delete a record with DELETE /todo/:id
* [x] Redirect on create / update / delete

## Installation
This is a Node.js module available through the npm registry.

Before installing, download and install Node.js. Node.js 0.10 or higher is required.

Installation is done using the npm install command:


```
npm install express
```
## Quick Start

The quickest way to get started with express is to utilize the executable express(1) to generate an application as shown below:


```
sudo npm install -g express-generator@4
```

## Create the app:

```
mkdir server 
cd server
npx express --git --hbs
```
## Install dependencies:

Use npm install(or 

```
npm install
```
or yarn if you use to it
```
yarn install
```

## Start the server:

```
npm start
```
Open [http://localhost:3000](http://localhost:3000) to view it in the browser.

## Installing Knex & PostgreSQL
Ubuntu's default repositories contain Postgres packages, so you can install these using the apt packaging system.

```
yarn add knex pg
```
Update the latest version
```
npm install --save pg@latest
```
## Create Knex file

```
npx knex init
```
## Created Migration: server$ npx
```
npx knex seed:make todo
```
you might need to install :

```
npm install sqlite3 --save
```

## Using PostgreSQL Roles and Databases
By default, Postgres uses a concept called "roles" to handle in authentication and authorization. These are, in some ways, similar to regular Unix-style accounts, but Postgres does not distinguish between users and groups and instead prefers the more flexible term "role".

Upon installation, Postgres is set up to use ident authentication, meaning that it associates Postgres roles with a matching Unix/Linux system account. If a role exists within Postgres, a Unix/Linux username with the same name is able to sign in as that role.

The installation procedure created a user account called postgres that is associated with the default Postgres role. In order to use Postgres, you can log into that account.

There are a few ways to utilize this account to access Postgres.

## Switching Over to the postgres Account
Switch over to the postgres account on your server by typing:
```
sudo -i -u postgres
```
You can now access a Postgres prompt immediately by typing:
```
psql
```
This will log you into the PostgreSQL prompt, and from here you are free to interact with the database management system right away.

Exit out of the PostgreSQL prompt by typing:
```
\q
```
This will bring you back to the postgres Linux command prompt.

## Accessing a Postgres Prompt Without Switching Accounts
You can also run the command you'd like with the postgres account directly with sudo.

For instance, in the last example, you were instructed to get to the Postgres prompt by first switching to the postgres user and then running psql to open the Postgres prompt. You could do this in one step by running the single command psql as the postgres user with sudo, like this:
```
sudo -u postgres psql
```
This will log you directly into Postgres without the intermediary bash shell in between.

Again, you can exit the interactive Postgres session by typing:
```
\q
```
Many use cases require more than one Postgres role. Read on to learn how to configure these.

## Creating a New Role

Currently, you just have the postgres role configured within the database. You can create new roles from the command line with the createrole command. The --interactive flag will prompt you for the name of the new role and also ask whether it should have superuser permissions.

If you are logged in as the postgres account, you can create a new user by typing:
```
createuser --interactive
```
If, instead, you prefer to use sudo for each command without switching from your normal account, type:
```
sudo -u postgres createuser --interactive
```
The script will prompt you with some choices and, based on your responses, execute the correct Postgres commands to create a user to your specifications.
```
Output
Enter name of role to add: sammy
Shall the new role be a superuser? (y/n) y
```
You can get more control by passing some additional flags. Check out the options by looking at the man page:
```
man createuser
```
Your installation of Postgres now has a new user, but you have not yet added any databases. The next section describes this process.

## Creating a New Database
Another assumption that the Postgres authentication system makes by default is that for any role used to log in, that role will have a database with the same name which it can access.

This means that, if the user you created in the last section is called cedric, that role will attempt to connect to a database which is also called “cedric” by default. You can create the appropriate database with the createdb command.

If you are logged in as the postgres account, you would type something like:
```
createdb my_db
```
If, instead, you prefer to use sudo for each command without switching from your normal account, you would type:
```
sudo -u postgres createdb mydb
```
This flexibility provides multiple paths for creating databases as needed.

## Knex Installation
```
npm install knex --save
```
## Add PostGre 
```
yarn add knex pg
```
## Create Knex file

```
npx knex init
```
### Replace knexfile.js' content by this below :
```
 module.exports = {
  development: {
    client: 'pg',
    connection: {
      host: '127.0.0.1',
      user: 'postgres',
      password: 'toor',
      database: 'my_db',
      charset: 'utf8'
    }
  },
  staging: {
    client: 'postgresql',
    connection: {
      database: 'my_db',
      user: 'postgres',
      password: 'password'
    },
    pool: {
      min: 2,
      max: 10
    },
    migrations: {
      tableName: 'knex_migrations'
    }
  },
  production: {
    client: 'postgresql',
    connection: {
      database: 'my_db',
      user: 'username',
      password: 'password'
    },
    pool: {
      min: 2,
      max: 10
    },
    migrations: {
      tableName: 'knex_migrations'
    }
  }
};
```
## Created Migration: server$ npx
```
npx knex seed:make todo
```

