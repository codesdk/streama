# streama

Ever had a huge bookshelf full of shows and movies? Ever wanted to digitalize them, but didn't have a good way of organizing the files? Worry no more! Streama is your own personal netflix for just such a purpose! 

The application uses Grails for the REST-API, and AngularJS for the frontend. If you don't like grails, you can also just use the frontend components and add your own REST-API for handling all the data :) 


#### Getting Started
- For local setup, please refer to [Local Streama Setup](https://github.com/dularion/streama/wiki/Local-Streama-Setup)
- For remote setup, please refer to [Setup Streama on Ubuntu 14.04](https://github.com/dularion/streama/wiki/Setup-Streama-on-Ubuntu-14.04)

#### Breaking Changes
Please refer to [Change Log](https://github.com/dularion/streama/blob/master/CHANGELOG.md)


#### Roadmap
This app is still being developed. 
These [enhancement-issues](https://github.com/dularion/streama/issues?q=is%3Aopen+is%3Aissue+label%3Aenhancement) are the features that I will be working on in the near future.

Join the chat here:
[![Join the chat at https://gitter.im/dularion/streama](https://badges.gitter.im/Join%20Chat.svg)](https://gitter.im/dularion/streama?utm_source=badge&utm_medium=badge&utm_campaign=pr-badge&utm_content=badge)

# The Application

### Settings
![Streama Settings Validation](http://i.imgur.com/oEMXLPk.gif)

When you first run the application, you will be redirected to the settings page. Here you enter your desired upload directory for the video files, your [theMovieDb.org API key](https://www.themoviedb.org/documentation/api) and a different base url if so desired (useful for remote hosting). 

Once you made adjustments to any of the settings, make sure to validate the value before saving. 
- For the API-Key, the validation checks against theMovieDb.org to see if you've entered a valid API-key. 
- For the upload directory, the application checks if it has read/write permissions for it. 


### The Dashboard
![Streama Dashboard](http://new.tinygrab.com/d9072ef564654c6e245c442e9c7d95facd4b738538.png)

On the dashboard a user can see their recently watched Tv-shows and Movies and their progress (they can continue where they left off) as well start new shows and movies that they haven't yet seen. The "Continue Watching" Feature works by periodically updating the database (only while watching, of course!) with info about the currently watched Video and how far it has been seen.

If a Movie or Episode does not contain any video-files, it won't show up in the dashboard.


### The Player
![Streama Player](http://new.tinygrab.com/d9072ef56407e5d1ac40fab040aedc398a9abb3609.png)

The Streama-Player is (heavily) inspired by netflix, so you get all the good stuff from there. For Shows, there is a "next episode" button and a handy episode/season browser.  There are also the basics: volume-control, play/pause, and fullscreen. 
Later down the road I will add a feature to add subtitles and switch between video-files (for instance for different quality uploads). 
The player is html5-based and has only really been tested in chrome so far.

##### The Episode Browser
I am especially proud of the Episode-Browser, which aims to function just like on netflix. By default, the current video-file's season is selected. The user gets an overview of which other episodes there are in the season, how many seasons there are, and, as an added feature, the user sees all the added episodes, even if no video-files are added to them (thus greyed out).

![Streama Episode Browser](http://i.imgur.com/MLE6TpH.gif)

### The Admin-Panel
![Streama Admin](http://new.tinygrab.com/d9072ef56484ebb444cc2fc7bc11f18e9f1706f68f.png)

One of the most important things to me was to make managing shows, movies, and episodes as easy and fun as possible. For this I made heavy use of the API from (theMovieDatabase.org)[https://www.themoviedb.org/], which auto-fills the episodes, shows and movies with useful information and great images. This eases the user's role in adding content.

For example, creating a new Tv-show and the episodes for the first season looks something like this: 

![Streama Creating Show](http://i.imgur.com/TLptKdp.gif)


Uploading video-files for each episode is as easy as drag-and-drop! 


![Streama Uploading Episode](http://i.imgur.com/StgES0S.gif)

### The Users
![Streama User Management](http://new.tinygrab.com/d9072ef564717c22dde948c726144b1b707a607adc.png)
Users can be invited and managed in the admin-panel. By default, they are non-admins, meaning they can only view videos, not create them. You can make them admins with the press of a button. Since there is user-administration in place, I plan on expanding on this a lot! Another feature I want to add is the ability for users to add and administer some form of playlists. There is a lot of potential to make this even better! 

## The Technical Details
This application is web-based and is programmed with [Grails 2.4.4](https://grails.org/) and MySQL. For login & user-handling [SpringSecurity](http://projects.spring.io/spring-security/) is used. For the most part, Grails is only there to generate REST-endpoints for the frontend. For all the front-end components, [AngularJS](https://angularjs.org/) is used. The player is completely html5-based, meaning there are limitations as to which file-types can be played at the moment. 

As an API for all the movies and shows I used the awesome API from theMovieDatabase. 
![theMovieDatabase](https://d3a8mw37cqal2z.cloudfront.net/images/header_v2.png)


### Development Setup: 
Coming Soon


## Work-in-Progress
Lastly, I would like to mention that this project is still very much a work-in-progress. Just today I was using it and noticed that it would be nice if the browser remembered the latest volume-setting. 
I will be adding new features and bugfixes often and quickly, but this is first and foremost a hobby project, so the time that I can spend on it is limited. If you want to contibute, feel free! I will be honored by each and every pull-request :) 

Btw, if you have any issues getting started, let me know. I will gladly help out and then improve the docs accordingly. 

## Known Issues
- When streaming a video, an exception occurs `getOutputStream() has already been called for this response` because springSecurity applies a filter that adds more data to the outputStream, even though I already added all the data and closed it. This error is merely cosmetic, and does not influence the video streaming. I still want to get this fixed. 
- There is no video-conversion currently, meaning you are reliant upon html5 browser compatibilities. I will implement server-side conversion soon which will enable this functionality.


## License
Streama is distributed under the terms of the MIT license.
See [LICENSE.md](https://github.com/dularion/streama/blob/master/LICENSE.md) for details.
