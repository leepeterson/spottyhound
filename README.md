# spottyhound
Create collaborative Spotify playlists via Slack! It's fun! You'll friggen love it and your coworkers will think you're cool!

Inspired by Big Mama Thornton's 1952 version of "Hound Dog", recorded August 13, 1952 and copywritten September 9, 1952, which is credited with helping to spur the evolution of black R&B into rock music.

[![Deploy](https://www.herokucdn.com/deploy/button.png)](https://heroku.com/deploy)

Simply create a Slash Command, such as `/spottyhound`, which accepts a track name (also the artist too for a less fuzzy search) to add to a pre-defined Spotify playlist:

    /spottyhound Big Mama Thornton - Hound Dog

##Installation

First you'll want to create your Slack Slash Command, which you can do by going to your [Slash Commands page](https://my.slack.com/services/new/slash-commands).

During setup, have your slash command submit a POST to your app's `/store` endpoint, e.g. `https://app-name.herokuapp.com/store`.

Make a note of the `token`, as you'll need it later to help guard against cross-site request forgery.

###Spotify

Head over to [Spotify's Developer Site](http://developer.spotify.com) and create a new Application. Make sure you add whatever spottyhound's callback URI as a valid callback URI. If you're running locally, this will be `http://localhost:5000/callback` or on Heroku `https://app-name.herokuapp.com/callback`

Make a note of the `key`, `secret` and `callback URI` too, as you'll need these later as well.

Also, don't forget to make a playlist. If you do this through [Spotify's web interface](http://play.spotify.com) (which unfortunately requires that you run Flash) then the `playlist identifier` will be the last segment of the URI - make a note of this too! If there's a better way of finding this out, howl. If you do this through the app, right-click the playlist to get it's web URL and again, you need the last segment of the URI.

###Environment variables

Once you've cloned spottyhound or hit the "Deploy with Heroku" button you'll need to setup the following environment variables. These can either be stored in a `.env` or set up as config variables in Heroku.

* `SLACK_TOKEN` - The token from Slack's Slash Command.
* `SPOTIFY_KEY` - Your Spotify application key (a.k.a Client ID).
* `SPOTIFY_SECRET` - Your Spotify application secret (a.k.a Client Secret).
* `SPOTIFY_USERNAME` - Your Spotify username.
* `SPOTIFY_PLAYLIST_ID` - Your playlist identifier.
* `SPOTIFY_REDIRECT_URI` - URI to redirect to once your user has allowed the application's permissions.

###Authentication

Visit your spottyhound home page to authenticate yourself with Spotify and you should be all set!
