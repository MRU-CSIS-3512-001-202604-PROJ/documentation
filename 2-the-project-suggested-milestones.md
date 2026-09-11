# The Project: Suggested Milestones

**COMP3512-001**

**Fall 2026**

_Weeks start on Monday and end on Sunday._

_These milestones assume you have carefully read and understood the requirement docs for the administrative portal and public-facing app._

_I will complete the suggested milestones for WK-07 onward by October 9._

---

## WK-01: Week of 2026-09-07

_I intentionally won't be releasing the starting repository for the Project until next week — I don't want you to get lost in the Project plumbing at this point...aaaaaand (full dislosure!) I'm still playing catchup._

- Read all currently-released Project documentation, starting with the Overview.

- Create rough sketches of the four administrative portal pages in any format you want — it doesn't have to be digital; in fact there are many benefits to just sketching something out on a whiteboard or piece of paper!
  - _I will be using Google Chrome's Device Mode at Laptop L size (1440px wide) to view your administrative portal site, so remember that when you're designing your layouts._

- Create markup and CSS for your portal pages, using hardcoded data for now.
  - _Place the markup and CSS files in some convenient place for the time being. You can name your markup pages **admin.html**, **dashboard.html**, **members.html**, and **venues.html** for now, but realize you will eventually need to rearrange things to follow the controller/view patterns we will cover in lecture._

  - _Your pages aren't meant to be functional yet — it's just a static site like you worked on in Web 1. The goal for now is to **see** what the pages will look like when complete, allowing you to catch issues with layout, content, and design early on._

- Validate the Member Data Page and the Venue Listings Page using the W3C Markup Validation Service and correct any errors.

## WK-02: Week of 2026-09-14

_PHP Lab Test 1 is on Wednesday. Add/drop deadline is this week._

- Receive the project's starting repository.

- Refactor your static site so that it now uses controllers and views, with partials used for repeated portions of markup.

- Use the provided Router class to ensure that you can access the four pages by going to the required URLs. For example, **http://somehost/admin/members** should take you to the Member Data page.
  - _Your pages still don't have to be functional at this point._

  - _There is still no authorization functionality at this point: you don't need to be logged in to access pages — they're all freely available._

## WK-03: Week of 2026-09-21

_This is the heaviest database week of the term. Start early._

- Install [DB Browser for SQLite](https://sqlitebrowser.org/) if you haven't already. You will be living in it this week.

- Work out the full data model for the administrative portal. Sketch it as an ERD before you type a single `CREATE TABLE`.
  - _Members are straightforward. Sessions are not. A session involves one game, one venue, one date, several players, and a score for each of those players. That is not one table. Work out how many it is, and how they connect, before you build anything._

- Create all the tables you have determined you need, and populate them with data.

- _Table definitions go below the `YOUR TABLES` marker in `database/schema.sql`; data goes below the `YOUR DATA` marker in `database/seed.sql`. Rebuild with `php database/build.php`._

- _Each table should have **100 or more** records. Do **not** go crazy here — if you make a ton of records, you will run into issues; not necessarily performance issues, just PITA issues for you as a developer._

- _Session data must be spread across **this month and last month**, or your Dashboard analytics will be empty or meaningless. Plan your generated data accordingly — this catches people out every single year._

- Build and test the queries that return the four required Dashboard analytics. Do the same for the queries that sort and filter member data.

- _Keep these queries somewhere so that you can eventually implement them with PHP. Getting them right in DB Browser for SQLite first is far easier than debugging them through PHP — you see the result set immediately, with nothing else in the way._

## WK-04: Week of 2026-09-28

_Wednesday, September 30 is a campus closure (Truth & Reconciliation) — no lecture and no lab._

- Remove hardcoded data and instead use the provided database helper class to populate the Dashboard, Member Data, and Venue Listings pages using data from the database.

- _The analytics functionality can be completed at this point, but the filtering and sorting functionality is not operational yet._

- _The "display previous login time" functionality will not be functional at this point._

- Complete the Venue Listings Page by implementing the addition and removal of featured games for a given venue.

- Validate the Member Data and Venue Listings Pages using the W3C Markup Validation Service and correct any errors.

- _There's a good chance that you may have introduced some markup errors when you populated these pages with database data._

## WK-05: Week of 2026-10-05

_This is going to be a rough week: you have PHP Lab Test 2 on Wednesday and the PHP Midterm on Friday. The milestone is deliberately light._

- Complete the Member Data Page by implementing the filtering and sorting requirements.

## Week of 2026-10-12 (READING WEEK)

_No new work is assigned. If you are on schedule, rest — you've earned it._

_If you are behind, this is your catch-up week, and you should use it. The JavaScript half of the course starts immediately afterward and does not slow down._

## WK-06: Week of 2026-10-19

_JavaScript lectures begin this week. This is your last scheduled week on the administrative portal._

- Complete the "display previous login time" functionality using cookies.

- Implement the Login page fully, including error messages and persistence of the previously-entered email.

- Refer to the Admin Portal Authentication document for guidance.

- Ensure that authorization functionality is now in place: only logged-in users can access the administrative portal pages.

- Perform final testing, bug fixes, and design touchups on your Admin Portal site. Use the submission checklist to guide this process.

- Run `npm run check` and fix anything it reports.

## WK-07: Week of 2026-10-26

_JS Lab Test 1 is on Wednesday._

- (Re)read the Public-Facing App Requirements doc and make sure you have a general idea of the requirements.

- Create rough sketches or wireframes for the public-facing app's views (Login, Personal Dashboard, Find a Player).

- _Remember to design for a mobile screen width of 375px._

- Design and create the additional database tables required for the public-facing app — wishlists, preferred venues, and the connections between members that let one member find another.

- _Same routine as WK-03: definitions into `schema.sql`, data into `seed.sql`, rebuild with `php database/build.php`._

- Populate your new tables with at least 100 records of realistic data each.

## WK-08: Week of 2026-11-02

_The 25% feedback deadline is Friday, November 6._

### Static Design Tasks

- Build the static markup and CSS for the public-facing app's views (Login, Personal Dashboard, Find a Player).

- _You will START this by having separate HTML documents for each view, BUT keep in mind that you will eventually be moving all of this work onto ONE page, with the DOM content changing based on what "page" the member is currently viewing._

- _I strongly recommend that you hardcode data at this point — member name, email, wishlist titles and play times, a game title and a few players with their details. Seeing the finished shape early is what lets you catch layout problems while they're still cheap to fix._

- _Don't forget to validate these pages using the W3C Markup Validation Service and fix any reported errors._

## WK-09: Week of 2026-11-09

_Wednesday, November 11 is a campus closure (Remembrance Day) — no lecture and no lab. This is a short week; plan accordingly._

### PHP API Endpoint Tasks

- Create the custom PHP API endpoints:

- **POST /api/login**

- **GET /api/member**

- **GET /api/wishlist**

- _These are PHP. Every rule that applied to the administrative portal still applies: database access goes through the provided helper, with bound parameters._

### Login Page Tasks

- Implement the client-side JavaScript for the Login Page, calling your **POST /api/login** endpoint.

- _Handle both outcomes: an unknown email or cell number keeps the member on the Login page with a useful message; a known one moves them to the Personal Dashboard._

### Personal Dashboard Tasks

- Use vanilla JS to call your **GET /api/member** endpoint and display the member's name, email, cell phone number, preferred venues, and member type.

- Use vanilla JS to call your **GET /api/wishlist** endpoint and display the games on the wishlist, along with which of the member's preferred venues currently feature each game.

## WK-10: Week of 2026-11-16

_JS Lab Test 2 is on Wednesday. Withdrawal deadline is this week._

### PHP API Endpoint Tasks

- Create the custom PHP API endpoints:

- **GET /api/games** (title search)

- **POST /api/wishlist**

- **DELETE /api/wishlist/:game_id**

### Personal Dashboard Tasks

- Implement the "add a game" feature.

- _This includes calling your **GET /api/games** endpoint to show a dropdown of game titles as the user types, after the third character._

- _This also involves using your **POST /api/wishlist** endpoint to add a game to the wishlist table in the database._

- Implement the "remove a game" feature using your **DELETE /api/wishlist/:game_id** endpoint.

- Implement wishlist caching using localStorage to prevent unnecessary API calls.

- Ensure event listeners for adding and removing games use **Event Delegation**.

## WK-11: Week of 2026-11-23

_Wednesday is a Project Work Lab. You will want it._

_This is the heaviest week of the second half. If you are going to fall behind anywhere, it will be here — so get as much of it done early in the week as you can._

### PHP API Endpoint Tasks

- Create the custom PHP API endpoints:

- **GET /api/players/:game_id**

- **POST /api/sessions**

- _`POST /api/sessions` writes to more than one table. It has to write them consistently — a session row with no player rows, or player rows with no session, is a bug you will not notice until I do._

### Find a Player Tasks

- Clearly display the title of the game you are finding a player for.

- Call your **GET /api/players/:game_id** endpoint and display the list of members who also want to play that game, including their name, contact info, preferred contact method, and preferred venues.

- _Properly handle and display messages for the cases where the member has no connections at all, and where none of their connections want to play the selected game._

- Implement the ability to close the view and return to the Personal Dashboard.

### Log a Session Tasks

- Build the Log a Session modal using vanilla JS and the HTML `<dialog>` element.

- _No library and no CSS framework code here — this one is on you._

- Capture the game, the venue, the date, the players, and each player's score, and send it to your **POST /api/sessions** endpoint.

- Ensure event listeners for logging sessions use **Event Delegation**.

## WK-12: Week of 2026-11-30

_The JS Midterm is on Wednesday, December 2. Wednesday's lab is a Project Work Lab. The Project is due Saturday, December 5._

_There are no new features in this week's milestone. That is deliberate — if you are still building features this week, you are behind, and you should be triaging rather than adding._

- Thoroughly test all application functionality using the submission checklist, fixing any issues.

- _Do NOT forget to test W3C validation after adding a game and again after removing a game, to ensure your DOM manipulation does not introduce invalid markup._

- Run `npm run check` one last time and fix anything it reports.

- Confirm that `database/schema.sql` and `database/seed.sql` are both committed, that `php database/build.php` runs cleanly from a fresh clone, and that the resulting database produces non-zero Dashboard analytics for November and December.

- _Test this properly. Clone your own repository into a new folder, run the build, and start the site. If it doesn't work there, it won't work for me either._

- Confirm the test member account required by the submission process exists and has the required data.

- Submit your project, including your completed submission checklist.
