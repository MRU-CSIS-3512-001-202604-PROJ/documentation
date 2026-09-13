# The Project: Public-Facing App Requirements

**COMP3512-001**

**Fall 2026**

_Members can log in, keep a list of games they want to play, log the plays they've had, and find other members who want to play a given game._

# Required Site Pages w/ Their Expected Functionalities & Implementations

_Assume the "I" in the following requirements is the person using that page._

_Note: Each functionality below has a number in brackets after it, prefixed with **P** for Public-Facing App. Those numbers are not decorative - the submission checklist you'll use at the end of term refers to them directly, so when the checklist says something like `[P14]`, you can come back here and see exactly which requirement it's testing._

_Note: As the term goes on (and on and on...) I will occasionally clarify a requirement. When I do, the clarification appears inline, tagged with the date it was added, like this: [2026-10-31]. Skim for those tags when you come back to this document._

_Note: The word "page" used here is a little deceptive, as you are technically creating one "page" that only \***\*looks\*\*** like different pages to the user. Still, the word "page" is the most convenient to use, so we'll stick with that._

_Note: There are a TON of useful features missing from these requirements - this is by design, for two reasons. First, the requirement list has to be kept small, given the limited amount of time we have. Second, missing requirements could be something you decide to implement at a future date if you want to continue to hone your web skills._

## **_Login_** Page

_Last year this page simulated a one-time-password flow. I've dropped that this year - not because it wasn't useful, but because the term is compressed and I'd rather you spend that effort on the play-logging work, which is new. You still get your **&lt;dialog&gt;** experience; it just happens somewhere more sensible now._

### Functionalities

- I want to get to this page by going to **http://somedomain** [P1]

- I want to be able to log in to the app using either a cell phone number or email address, so I should see a way to select one of these methods and enter the necessary information. [P2]

- I want only known members to be able to log in to the app, so if an unknown email/cell number is provided, a useful message should be displayed and I should remain on this page. [P3]

- If I am a known member, I want to be taken to the **Personal Dashboard** Page. [P4]
  - _The member displayed on the Personal Dashboard is the member identified by the email/cell number provided._

### How the API Fits In

_Here's the flow for a successful login attempt, so you know how the pieces connect:_

1. _The user fills in the form and submits it._

1. _On submission, your JS code sends a_ **POST /api/login** _request with an email or cell number (depending on what was submitted) in the body of that request._

1. _On the receiving end (in PHP), your code checks whether a member exists with that email or cell number, and sends back a response._

1. _If no such member was found, the response should indicate an error with an appropriate HTTP status code._

1. _If a member was found, the response should indicate success with an appropriate HTTP status code, along with the id number associated with that member._

1. _When the JS receives the response:_
   1. _If the response indicates failure, the user is informed of the issue and stays on the Login page._

   1. _If the response indicates success, the Dashboard is displayed, and the member id from the response is used to make_ **GET /api/member** _and_ **GET /api/wishlist** _requests. The data from those responses populates the Dashboard._

### Implementation Restrictions

- All login handling is done with vanilla JS and your own API. No library, no CSS framework JavaScript.

## **_Personal Dashboard_** Page

_The main purpose of this page is to see my personal information and the games I want to play - to add and remove those games, and to log the plays I've actually had._

### Functionalities

- I can only see this page by successfully logging in through the **Login** Page. [P5]

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page that has been reset. [P6]

- I want to see my name, email address, cell phone number, my preferred venues, and whether I am a standard or premium member. [P7]

- I want to see the titles of all games on my wishlist; each game shown on this page should show its typical play time in minutes, its player count range, and which of my preferred venues currently feature that game. [P8]
  - _If none of my preferred venues currently feature the game, that should be clearly shown._

- I want to be able to remove any of the games displayed on this page. [P9]

- I want to be able to add a game to this page; as I type the title of a game I want to play, after the third character is entered, a dropdown list of titles starting with what I've typed (case insensitive) is shown. [P10]

- I want to see an easy way to find someone to play a given game with; doing so should take me to the **Find a Player** Page. [P11]

- I want to be able to log a play from this page. See the **_Log a Play_** section below. [P12]

### Implementation Restrictions

- The name, email address, cell phone number, preferred venues, and member type information must be obtained through an API call to an endpoint you design and implement on your PHP backend. (See Custom API Requirements.)

- The wishlist games, their details, and which preferred venues feature them must be obtained through an API call to an endpoint you design and implement on your PHP backend.

- The dropdown of matching game titles must be obtained through an API call to an endpoint you design and implement on your PHP backend. It must **not** be built by fetching every game in the database and filtering in JavaScript.

- Adding and removing games must involve API endpoint calls to endpoints you design and implement on your PHP backend, which will add and remove records from appropriate database tables.

- To get some experience with caching, wishlist data must be stored using the Web API's localStorage feature; if no wishlist data is stored in local storage, then API calls will be required, but if there **is** data, that data must be used in order to save a call to the API.

- Removal of games, finding players, and logging plays should involve Event Delegation.

## **_Log a Play_** (Modal)

_This is the piece that makes the whole thing worth building. Everything the administrative portal reports on comes from the plays members log here._

### Functionalities

- I want to open this from the **Personal Dashboard**. [P13]

- I want to record which game was played, at which venue, on what date. [P14]

- I want to record who played, and what each player scored. [P15]
  - _The people I can add as players are myself and the members I am connected to._

- I can close the modal without effect. [P16]

- When I save a play successfully, I want a brief confirmation that tells me who won. [P17]
  - _The winner is whoever scored highest. If there's a tie for the highest score, show all tied names._

  - _The winner is worked out from the scores you just captured - it is not something you store in the database._

### Implementation Restrictions

- The modal must be created using vanilla JS and an [HTML dialog element](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Elements/dialog). No library can be used, nor can any CSS framework (Bootstrap, Tailwind, etc.) code be used here.

- Saving a play must involve an API endpoint call to an endpoint you design and implement on your PHP backend, which will add records to the appropriate database tables.
  - _Note the plurals in that last point. A play is one row in one table plus one row per player in another. Your endpoint has to write both, and it has to write them consistently._

## **_Find a Player_** Page

_The main purpose of this page is to help me find someone to play a game with._

### Functionalities

- I want to have an easy way to close this page and go back to my **Personal Dashboard** Page. [P18]

- I want to clearly see the title of the game I'm looking to play with someone. [P19]

- If I have no connections at all, I want to see that clearly here. [P20]

- If I have connections, but none of them have that game on their wishlist, I should see that clearly here. [P21]

- If I have connections who want to play my game, then I should see this additional information to help me decide who I want to contact and how to contact them: [P22]
  - Their name.

  - Their email.

  - Their cell phone number.

  - Their preferred contact method.

  - Their preferred venues.

### Implementation Restrictions

- The information displayed on this page must come from an API endpoint call to an endpoint you design and implement on your PHP backend.

# Required Database Tables & Records

Now that you've read the page requirements, you will need to make additional database tables and records, and possibly modify tables you created for the Administrative Portal as well. (But hopefully not too much if you looked through these app requirements ahead of time.)

As before, table definitions go below the `YOUR TABLES` marker in **`/the-project-template/database/schema.sql`**, data goes below the `YOUR DATA` marker in **`/the-project-template/database/seed.sql`**, and `php database/build.php` rebuilds `database/app.db` from the two. The `.db` file stays gitignored - if a table exists only there and not in the `.sql` files, it doesn't exist as far as I'm concerned.

Some suggestions:

- Determine what additional tables will be necessary to meet the app's requirements. For example, the functional requirements strongly suggest that preferred venues are something that need to be tracked for each member. How will you do this? The same goes for wishlists.

- Since there is no requirement for a feature that lets members add or remove connections, you must instead create a table that indicates what connections exist between the members you created for the Administrative Portal.
  - _You already built your plays tables back in WK-03 so that the admin Dashboard analytics had something to report on. Now the public app writes to them. If your data model was sound, this costs you nothing. If it wasn't, you're going to find out this week - and this is exactly why I told you to do some planning back then._

- Add the new tables to `schema.sql`, add their data to `seed.sql`, and rebuild.

  _Don't forget: you will need to tie some tables together through foreign keys!_

- Populate those tables with realistic data. Each table (except your administrator table!) should have **100 or more** records. Do **_not_** go crazy here - if you make a ton of records, you will run into issues; not necessarily performance issues, just PITA issues for you as a developer.

_Keep using [DB Browser for SQLite](https://sqlitebrowser.org/) to check your queries against `app.db` before you wire them into an endpoint. Remember that anything you change there is wiped on the next rebuild._

# Custom API Requirements

You have to build a number of API endpoints for your pages. You must follow these requirements for your API. **Normally, you'd need to have some kind of authentication system in place for this, but these endpoints will be freely available.**

| **Purpose**                        | **HTTP Method**          | **URL**                 | **Notes**                                                                                                                                                                                                                                                                                       |
| ---------------------------------- | ------------------------ | ----------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Initiate login.                    | POST                     | /api/login              | Will need to send an email/cell number in the POST body.                                                                                                                                                                                                                                        |
| Get data for logged-in member.     | GET w/ query parameter   | /api/member?key=value   | Name, email, cell phone, preferred venues, member type.                                                                                                                                                                                                                                         |
| Get wishlist for logged-in member. | GET w/ query parameter   | /api/wishlist?key=value | Wishlist info (for example, game ids + associated venue names + venue ids).                                                                                                                                                                                                                     |
| Search games by title.             | GET w/ query parameter   | /api/games?search=value | Titles starting with the search value, case insensitive. Return at most 10 matches.                                                                                                                                                                                                             |
| Add game to wishlist.              | POST                     | /api/wishlist           | Will need to send a game id in the POST body.                                                                                                                                                                                                                                                   |
| Delete game from wishlist.         | DELETE w/ path parameter | /api/wishlist/:game_id  | Removes the provided game from the wishlist. You can pass in an additional parameter (like the member id) using a standard query string.                                                                                                                                                        |
| Get players for a game.            | GET w/ path parameter    | /api/players/:game_id   | Three cases: no connections, connections but none who want this game, and connections who do. What kind of JSON will you return for each? Note that an empty array can't distinguish the first two. You can pass in an additional parameter (like the member id) using a standard query string. |
| Log a play.                        | POST                     | /api/plays              | Will need to send the game, venue, date, and a set of players with their scores.                                                                                                                                                                                                                |

# Additional Public-Facing App Requirements & Restrictions

### Requirements

- The **_Personal Dashboard_** Page must not generate any errors when validated by the [W3C Markup Validation Service](https://validator.w3.org/). This will be tested twice:
  - Once after adding a new game.

  - Once after removing a different game.

- Your app only has one route: /

- All your JavaScript lives in external files, loaded with `<script type="module">`.

- At least one of your API endpoints is consumed using **Promise chaining**, and at least one other is consumed using **`async`/`await`**.

- _Yes, both. You'll meet both approaches in lecture, and I want to see that you can work with each of them rather than picking one and avoiding the other for the rest of your career. Which endpoint gets which is up to you._

- All your API endpoints return a content type of `application/json`.

- All database access still goes through the provided database helper's `run()` method, using bound parameters. Your API endpoints are PHP, and the same rules apply to them as applied to the administrative portal.

### Restrictions

- No JavaScript framework or library is used without first clearing it with your instructor.

- No inline JavaScript is present (i.e. `on…` event HTML attributes like onclick, onsubmit, etc. are not present): all JavaScript is contained in external files.

- The innerHTML property is not used in any JS files.

- No alert calls are used.

- Only specified data is stored in session storage and/or local storage.

_Run `npm run check` before you submit. It catches most of the above._

# Design Expectations

## What should the pages look like?

I will be using [Google Chrome's Device Mode](https://developer.chrome.com/docs/devtools/device-mode) at Mobile M size (375 px wide) to view your public-facing app. There are no restrictions on the height of your pages. Design accordingly.

I'm **_deliberately_** leaving the design of the sites open-ended. **You are responsible** for interpreting the functional requirements, designing an effective User Interface (UI) and User Experience (UX) that delivers them, and then implementing your design. These are crucial skills you need to develop.

**However, I am available for guidance.** If you would like me to **review** a design (e.g., wireframes or mockups) for either site, I am happy to do so. There's one catch, though: these reviews must be conducted in person. You know where to find my schedule, so when you're ready to chat, shoot me an email, and we'll set up a time to meet.

## Can I use a CSS framework?

If you want to use a framework like Bootstrap (or even more industry-relevant, Tailwind), that is fine. You cannot, however, use any JavaScript-based functionality from these frameworks.

_The same CDN rule applies here as in the administrative portal: a remote `<link rel="stylesheet">` is allowed, but Tailwind's Play CDN is a `<script>` and is not. Tailwind users build locally and commit the generated stylesheet._
