# slackchess

## Modifications

This is a modification of the slackchess client build by user NotNil (Logan Spears) for deployment on Digital Ocean.  This fork of the repository includes changes necessary to deploy the slackbot to Heroku, a free alternative to to Digital Ocean.

## How can you play chess on any device?  

Slack!  

This project gives you a turn key solution for tranforming slack into a chess client. With slackchess you can:
- challenge another slack user
- play against @slackbot powered by [Stockfish](https://stockfishchess.org)
- offer draws and resign
- export your game as a PGN

## Screenshot
<img src="https://raw.githubusercontent.com/loganjspears/slackchess/master/screen_shots/screen_shot_1.png" width="600">

## Installation Guide

### Slack Integration Guide

1. Login to Slack and go to https://slack.com/apps
2. Go to Configure > Custom Integrations > Slash Commands > Add Configuration
3. For "Choose a Command" type "/chess" and press "Add Slash Command Integration"
4. Set "URL" to http://45.55.141.331/command where "45.55.141.331" is your IP
5. Make sure "Method" is POST
6. Copy and paste the generated "Token" somewhere, you will need it later
7. For "Customize Name" you can enter anything (ex. "ChessBot")
8. For "Customize Icon" I used this image: https://upload.wikimedia.org/wikipedia/commons/thumb/f/f0/Chess_kdt45.svg/45px-Chess_kdt45.svg.png
9. Click "Save Integration"

![slack integration](/screen_shots/screen_shot_3.png)

### Heroku Setup

First install docker and heroku on your development machine.

Install the container-registry plugin by running:
```
heroku plugins:install heroku-container-registry
```

Log in to the Heroku container registry:
```
heroku container:login
```

Navigate to the root of the project directory and create your heroku server:
```
heroku create
```

### Heroku Config

The last step of the setup process is to add the token and url parameters to the heroku configuratoin page.

Login to heroku, and select your app from the list of available applications.  Click settings and locate the option for "Config Variables".

Add two new variables:
```
TOKEN: [The token set in the slack config screen]
URL: [https://theUrlOfYourHerokuServer.com]
```

### Push it up

Push the code up to Heroku and start it running
```
hroku container:push web
```

Thats it!

## Commands

Play against user:
```
/chess play @user
```

Play against bot:
```
/chess play @slackbot
```

You can view all commands by using the help command.
```
/chess help
```
 
![slackchess](/screen_shots/screen_shot_2.png)

