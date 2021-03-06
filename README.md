# Sample Phoenix App Showing How to Use Nanobox with Semaphore

This repo is a companion to the article, [Continuous Integration with Semaphore & Nanobox](https://content.nanobox.io/semaphore-nanobox-continuous-integration-the-easy-way) showing how to use Nanobox in your Semaphore workflow.

## Nanobox
[Nanobox](https://nanobox.io) is a "micro-platform" that builds and runs your app anywhere - your local machine, a CI server, or in production.

## Semaphore
[Semaphore](https://semaphoreci.com) is a continuous integration platform that allows you to thoroughly test code as it moves through your development/deployment workflow.

## Running This App Locally
### Download & Install Nanobox
Create a Nanobox account (it's free), then [Download & Install Nanobox](https://dashboard.nanobox.io/download).

### Clone This Repo
```sh
# clone the code
git clone https://github.com/sanderson/phoenix-semaphore-example.git

# cd into the project directory
cd phoenix-semaphore-example
```

### Add a Convenient Way to Access the App
Nanobox provides a simple way to add DNS aliases for apps running locally, so you can easily access them from a browser.

```sh
nanobox dns add local phoenix.dev
```

### Start Your Local Dev Environment
Nanobox will spin up a virtualized local dev environment isolated from your host machine.

```sh
nanobox run
```

This will drop you into a console inside your Nanobox container.

### Setup Phoenix
To get everything in place, you just need to install dependencies and seed your database. From inside your Nanobox console, run:

```sh
# install dependencies
mix deps.get

# seed the database
mix ecto.create && mix ecto.migrate

# install Node.js dependencies
npm install
```

### Run the App
With dependencies in place and data seeded, run the app with the following command (in the Nanobox console):

```sh
mix phoenix.server
```

Now you can visit [`phoenix.dev:4000`](http://phoenix.dev:4000) from your browser.

## Using the App with Semaphore
Semaphore environments and tests are configured through their dashboard. If tests are successful, you can deploy to a Nanobox app.
