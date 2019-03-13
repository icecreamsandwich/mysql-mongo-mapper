# MySQL to MongoDB data migration tool

A Node.js script to migrate MySQL data to MongoDB, mapping MySQL tables to MongoDB collections.

Will allow migrations from and to remote sites.

![mysql-to-mongo](https://user-images.githubusercontent.com/17042186/50631158-694f8780-0f54-11e9-89b4-465fc98eb2dd.gif)

## Migrate your existing MySQL data into MongoDB

Open terminal in your working directory and .....

**Method I**

1. Clone project
    > git clone https://github.com/dannysofftie/mysql-mongo-migrate.git
2. Install dependencies
    > npm install
3. Make it happen :wink:
    > npm run migrate

**Method II**

1. Install package globally
    > npm i -g mysql-mongo-migrate
2. Run command
    > \$> mysql-mongo-migrate

---

Issues might occur if you don't have authentication set up in your MongoDB database, as read and write roles are required when inserting bulk data into MongoDB.

Follow below steps to enable authentication in your server:

> This set up is for Linux distros only. Check online for your operating system if not a linux distro.

-   Uncomment the following code block at the bottom of `/etc/mongo.conf`

    ```bash
    $> sudo vi /etc/mongo.conf

       # security:
       #      authorization: enabled
    ```

-   Login to your server and create a user for your database.

    ```bash
    $>  mongo
    >   use databaseName
    >   db.createUser({user: "username", pwd: "password", role: [{roles: "readWrite", db: "databaseName"}]})

    ```

    _Replace with your preferred credentials. You will use them to do migration in the other steps_

-   Exit the mongo shell and restart mongod service.

    ```bash
    $>  sudo service restart mongo
    ```

    You should be ready to migrate your data now.

### Roadmap

-   [x] Retrieve MySQL database models and data
-   [x] Generate Mongoose schemas in Typescript
-   [x] Dump MySQL data into MongoDB
