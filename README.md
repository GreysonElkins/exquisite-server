# Exquisite Corpse

 [Exquisite Corpse](https://exquisite-corpse-2005fe.herokuapp.com/) is a collaborative creative writing game. Participants take turns writing a story, and pass their last sentence as a a prompt to the next contributor. The result is a fun and unpredictable collection of ideas and writing styles that form very unique bodies of text.

 Users of Exquisite Corpse are able to:
 * Read published (completed) stories.
 * Log in with a username and password (or create a new username if it doesn't already exist).
 * When logged in, users can contribute to stories in progress, or start new stories. 
 * When starting a new story, users can select a prompt from a variety of genres, or start from scratch.
 * A user has 2 minutes to write, and then they can pass their story on for contribution. 
 * Stories in progress will show up on the home page. 
 * Any user who is continuing a story can choose to end and publish a story if they see fit!

This was a Mod 3 project in Turing School of Software and Design's Front End Engineering program during the 2008 inning. This project was designed to help students better understand how to:
- Build an application with a React architecture.
- Learn a new technology in under a week.
- Test component and asynchronous functionality with the React Testing Library.
- Understand and utilize CRUD requests to interact with data. 
- Practice a professional GitHub workflow

The biggest learning goal of this project was to research and implement a completely new technology. For our project, we decided to build a back end and a homespun API using PostgresQL, Knex, and Express. this back end keeps track of all of our user's data, all of the stories and writing prompts. 

## Setup/Installation
### To run this server locally: 

- Clone down this repo and cd into this directory
- Run `npm install` in the root of the newly created directory to install the necessary dependencies
- If you haven't already, install [PostgreSQL](https://www.postgresql.org/download/) on your computer 
- Then create a file called `.env` in the root directory
  - create variables in `.env` with your PostgreSQL super-user account name and the password you created during setup, like so:
```
  DB_USER=postgres
  DB_PASSWORD=examplePassword
```
- In the terminal, run `psql -U postgres`, enter your password when prompted
- Create a new data base with the line `CREATE DATABASE exquisite`
- Close out of psql
- Run `knex migrate:latest`
- Run `knex seed:run`
- Run `npm start`

### To access it online: 
#### GET:
- `https://exquisite-server.herokuapp.com/api/v2/authors/` - returns an array of all authors
- `https://exquisite-server.herokuapp.com/api/v2/authors/:id` - returns the author with the provided id
- `https://exquisite-server.herokuapp.com/api/v2/prompts` - returns an array of all prompts
- `https://exquisite-server.herokuapp.com/api/v2/prompts/:id` - returns the prompt with the  provided id
- `https://exquisite-server.herokuapp.com/api/v2/prompts/:detail` - if detail is `any` it will respond with a random prompt of any genre. Random prompts from specific genres can also be fetched by specifying `detail` as the desired genre. 
- `https://exquisite-server.herokuapp.com/api/v2/stories` - returns an array of all stories
- `https://exquisite-server.herokuapp.com/api/v2/stories/:id` - returns the specific story with the provided id
#### POST:
- `https://exquisite-server.herokuapp.com/api/v2/authors`- creates a new Author in the data-base. Requires a body-object with `name`, `email`, and `password` key value pairs. Responds with the new user object and it's id. (Users and authors are interchangable)
- `https://exquisite-server.herokuapp.com/api/v2/authors/login` - respods with the user object if the credentials provided are correct. Requires a body with `username` and `password` key value pairs, `username` can be an email or a user name, both are currently case-sensitive.
- `https://exquisite-server.herokuapp.com/api/v2/authors/stories` - requires a request body with the following key value pairs: `[title, contributions, prompt, contributors]`. `Contributors` and `prompt` should be the id of their corresponding user or prompt. The rest are strings. The server will respond with and create a new story. 
#### PATCH:
- `https://exquisite-server.herokuapp.com/api/v2/authors/:id` - requires a request body with at least one of the following key value pairs `[email, password, bio]` and will change the corresponding values for the author with the id provided. 
- `https://exquisite-server.herokuapp.com/api/v2/authors/stories/:id` - requires a request body with `contributions` and `contributors`, a string and a number respectively. Also accepts `is_complete` as a boolean. Will update the story corresponding with the id provided in the endpoint, and will respond with the updated story. 






## Contributors
V1 of this project was submitted on 9/15/2020 by [Aaron Burris-DeBoskey](https://github.com/Abdeboskey), [Carly Clift](https://github.com/carlymclift), [Greyson Elkins](https://github.com/GreysonElkins), and [Nick Hart](https://github.com/nickhartdev) and is visible at [Exquisite Sever V1](https://github.com/nickhartdev/exquisite-corpse-server), it was tweaked from the ground up for deployment here, and this is the current version.
