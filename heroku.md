# Heroku

The following are basic steps needed to quickly set up a Node.js app with Express and deploy to Heroku.

### Step 1 - Heroku account

Make sure you have a Heroku account set up

### Step 2 - Install Heroku Toolbelt

Download and install the tool belt package specific for your OX

##### OSX

[https://toolbelt.heroku.com/osx](https://toolbelt.heroku.com/osx)

#### Windows

[https://toolbelt.heroku.com/windows](https://toolbelt.heroku.com/windows)

#### Linux

  $ wget -qO- https://toolbelt.heroku.com/install-ubuntu.sh | sh

### Step 3 - Log into you account

Once toolbelt is installed, you should be able to access your account

  $ heroku login
  Enter your Heroku credentials.
  Email: adam@example.com
  Password:
  Could not find an existing public key.
  Would you like to generate one? [Yn]
  Generating new SSH public key.
  Uploading ssh public key /Users/adam/.ssh/id_rsa.pub
