# Enabling Asymmetric Encryption for Web Services

This is a system for using asymmetric encryption to authenticate users for some web service. 

There are two parts: the client that will generate keys for a user and answer challenges from the service, and the service that will accept public keys and generate encrypted challenge strings for the client.

# Manual for running the code

## Installing the browser extension

### Firefox
- Open Firefox and type `about:debugging#/runtime/this-firefox` in the address bar.
- Click on "Load Temporary Add-on".
- Choose the file `client/manifest.json` from this repository.

### Chrome
- Open Chrome and type `chrome://extensions` in the address bar.
- Toggle on the "Developer mode" option in the top right corner.
- Click on the "Load unpacked" button.
- Select the `client` directory from this repository.

## Running the server

### Prerequisites
- Download and install MySQL from the official website (https://dev.mysql.com/).
- Ensure MySQL is running.
- Create a database named `vault`.
    -   Start the MySQL command-line client by running the following command: `/usr/local/mysql/bin/mysql -u root -p`
    -   Once you are in the MySQL command-line client, run the following command to create the "vault" database:`CREATE DATABASE vault;`
    -   You can verify that the database has been created by running the following command: `SHOW DATABASES;`
    -   You can exit the MySQL command-line client by running the following command: `exit;`
- Set the user credentials in the `.env` file.
    -   Navigate to the `server` directory of this repository.
    -   Once you are in the server directory, use a text editor like Nano or Vim to open the .env file: `nano .env`
    -   Inside the .env file, you will find various configuration options. Look for the lines related to user credentials, such as `DB_USER` and `DB_PASSWORD`and update.
- Set the `DATABASE_SOCKET_PATH` to the location of your `mysql.sock` file.
    -   Start the MySQL command-line client by running the following command:`/usr/local/mysql/bin/mysql -u root -p`
    -   Once you are in the MySQL command-line client, run the following command to find the location of the mysql.sock file: `SHOW VARIABLES LIKE 'socket';`
    -   Exit the MySQL command-line client by running the following command: `exit;`
    -   Navigate to the `server` directory of this repository.
    -   Once you are in the server directory, use a text editor like Nano or Vim to open the .env file: `nano .env`
    -   Update the value of DATABASE_SOCKET_PATH with the path to your mysql.sock file: `DATABASE_SOCKET_PATH=/tmp/mysql.sock`
- If needed, modify the `DATABASE_PORT` field. You can find the port your MySQL server is running on by following the instructions at (https://www.tutorialspoint.com/how-to-find-out-port-of-mysql-server).
- If you encounter the error `Client does not support authentication protocol requested by server; consider upgrading MySQL client` with MySQL 8.0, follow the instructions at (https://stackoverflow.com/a/50131831) to resolve it.
- Install the required Node modules by navigating to the `server` directory and running `npm install`.

### Running the server
- Open a command prompt or terminal.
- Navigate to the `server` directory of this repository.
- Run the command `node app.js` to start the server.
- To access the webpage, open your browser and go to `localhost:8000`.

