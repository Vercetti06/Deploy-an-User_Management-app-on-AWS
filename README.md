# Simple Node.js Welcome App

This is a minimal Node.js application using Express that serves a simple "Welcome to the page" message.

## Application Code

### package.json

{
"name": "simple-node-welcome-app",
"version": "1.0.0",
"description": "Simple Node.js app showing a welcome message",
"main": "app.js",
"scripts": {
"start": "node app.js"
},
"dependencies": {
"express": "^4.18.2"
}
}

##########################################################

### app.js

const express = require('express');
const app = express();
const port = process.env.PORT || 3000;

app.get('/', (req, res) => {
res.send('<h1>Welcome to the page</h1>');
});

app.listen(port, '0.0.0.0', () => {
console.log(App listening at http://0.0.0.0:${port});
});

###########################################################

## Explanation of Code

- **package.json** defines project metadata and dependencies. It specifies `express` as the dependency and defines a start script to run `app.js`.
- **app.js** uses Express framework to set up a simple web server that listens on port 3000 (or a port defined in environment variable `PORT`).
- The app responds to HTTP GET requests at the root URL `/` by sending a simple HTML welcome message.
- Binding the server to `0.0.0.0` ensures it listens on all network interfaces, allowing external access via the EC2 public IP.

## Prerequisites

- An AWS EC2 instance running Ubuntu or Amazon Linux.
- Node.js and npm installed on the instance.
- Git installed on the instance.
- Proper security group settings to allow inbound traffic on the port used (default 3000).

## Deployment Steps

1. **Clone the repository on your EC2 instance**:
git clone https://github.com/your-username/your-repo.git

cd your-repo


2. **Install dependencies**:
npm install



3. **Start the Node.js app**:
node app.js

This will start the server, listening on all interfaces on port 3000.

4. **Open EC2 security group inbound rules**:
- Allow TCP inbound traffic on port 3000 from your IP address or 0.0.0.0/0 for public access.

5. **Access your app**:
Open a web browser and visit:
http://<your-ec2-public-ip>:3000


You should see "Welcome to the page" displayed.

6. **Stopping the app**:
- Press `Ctrl + C` in the terminal running the app or kill the Node.js process.

## Notes

- For production deployment, consider using a process manager like PM2 to keep the app running and auto-restart on failures.
- Optionally, configure a reverse proxy (e.g., NGINX) to serve the app on standard HTTP port 80.
- The app listens on `0.0.0.0` to allow external network access, not just localhost.

## License

Open source and free to use
