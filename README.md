## Endpoints
### This is a JSON API server, it both expects JSON and returns JSON.
/auth/token
* POST Creates an auth token. Requires valid ```email``` and ```password``` (created when you make a user account). Returns a JWT token named ```authToken```.

/swipe/:userId
* GET Get the queue of possible matches. Requires the ```userId```. Returns an JSON object with the key ```queue``` and the value is an array of all possible matches for the user to swipe on. 
* POST When a user "approves" of a match it will add them to their matches table. Requires ```userId``` in params which is the Id of the current logged in user and ```id``` in the body which is the id of the user who was approved. Returns nothing but a status 201 when successful.

/user/
* GET Gets all user profiles. Requires nothing. Returns all users in the database as an array of objects. Each object will have a ```user_id```, ```display_name```, ```bio```, ```lfm_in```, and ```avatar```.
* POST Creates a new user profile. Requires an ```email```, ```display_name```, and ```password```. Returns the a JSON object with an ```id```, ```email```, ```display_name```, ```bio```, ```lfm_in```, and ```avatar```.

/user/:userId
* GET Gets the data for a specific user profile. Requires ```userId``` from params. Returns a JSON object with ```display_name```, ```bio```, ```lfm_in```, ```avatar```, ```genres```, and ```platforms```.
* PATCH Updates a user profile. Requires the ```userId``` in params and in the body the requires values to update include: ```display_name```, ```bio```, ```lfm_in```, and ```avatar```. However it optionally will take ```genres``` and ```platforms```. Returns a 203 with the updated user information if successful.

/user/:userId/matches
* GET Get all matches that our logged in user has "approved" during swiping. Requires ```userId``` of the logged in user. Returns an array of Objects for each match with their ```display_name```, ```bio```, ```lfm_in```, and ```avatar```.
* POST Functionally the same as POST /swipe/:userId

### ENDPOINTS TODO:
* /user/:userId/avatar
Requires profileImg: the image file and title:

# Express Boilerplate!

This is a boilerplate project used for starting new projects!

## Set up

Complete the following steps to start a new project (NEW-PROJECT-NAME):

1. Clone this repository to your local machine `git clone https://github.com/gage117/express-app-boilerplate.git NEW-PROJECTS-NAME`
2. `cd` into the cloned repository
3. Make a fresh start of the git history for this project with `rm -rf .git && git init`
4. Install the node dependencies `npm install`
5. Move the example Environment file to `.env` that will be ignored by git and read by the express server `mv example.env .env`
6. Edit the contents of the `package.json` to use NEW-PROJECT-NAME instead of `"name": "express-boilerplate",`

## Scripts

Start the application `npm start`

Start nodemon for the application `npm run dev`

Run the tests `npm test`

## Deploying

When your new project is ready for deployment, add a new Heroku application with `heroku create`. This will make a new git remote called "heroku" and you can then `npm run deploy` which will push to this remote's master branch.
