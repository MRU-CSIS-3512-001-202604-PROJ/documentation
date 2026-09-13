# The Project: Suggested Milestones

**COMP3512-001**

**Fall 2026**

_Weeks start on Monday and end on Sunday._

_These milestones assume you have carefully read and understood the requirement docs for the administrative portal and public-facing app._

---

## WK-01: Week of 2026-09-07

_No Project milestone this week._

_This week went to getting you (somewhat) comfortable with the framework we'll be using all semester. The framework is the thing every other week depends on, and there was no sense starting the Project on top of shaky ground. And besides, I assume you will want to spend your time focusing on the lab test._

_The consequence of this decision is that WK-02 is heavier than it would otherwise have been. There is a silver lining, though: because you already know the framework, you can build your pages as controllers and views from the start, and skip the "build it static, then refactor it" step I'd originally planned. That saves you most of what this week cost. So...yay?_

## WK-02: Week of 2026-09-14

_Add/drop deadline is Monday. PHP Lab Test 1 is on Wednesday. This is a full week!_

- Read all Project documentation, starting with the Overview.

- Receive the Project's starting repository.

- Run `npm install` once in your project folder so that `npm run check` works.
  - _You only need to do this once per machine, and it's why `node_modules/` is gitignored. Node is already installed on the lab machines._

- Create rough sketches of the four administrative portal pages in any format you want - it doesn't have to be digital; in fact there are many benefits to just sketching something out on a whiteboard or piece of paper!
  - _I will be using Google Chrome's Device Mode at Laptop L size (1440px wide) to view your administrative portal site, so remember that when you're designing your layouts._

- Build the four pages as controllers and views, with partials used for repeated portions of markup, using hardcoded data for now.
  - _You're going straight to controllers and views rather than building static HTML first. This is the one benefit of how WK-01 went: you already know the framework, so there's no reason to build something you'd only have to take apart again._

- Use the provided Router class to ensure that you can access the four pages by going to the required URLs. For example, **http://somehost/admin/members** should take you to the Member Data page.
  - _Your pages aren't meant to be functional yet. The goal is to **see** what the pages will look like when complete, so you can catch issues with layout, content, and design early - while they're still cheap to fix._

  - _There is no authorization functionality at this point: you don't need to be logged in to access pages - they're all freely available._

- **Suggested, not required this week:** on the Dashboard, start presenting the day-of-week and top-five-games analytics visually, using **CSS only**, with hardcoded values. See the Design Expectations section of the Administrative Portal Requirements.
  - _This is a requirement of the finished Project - you do have to do it eventually. But it is the one thing in this week you can safely defer, and this week is full enough. If you skip it, WK-05 is deliberately light and is your fallback. Don't let it drift past there, because from WK-06 onward you're on the JavaScript half and won't want to come back._

  - _The reason to do it now if you can: with hardcoded numbers there's no query to debug, so it's pure markup and CSS. In WK-04 the only thing that changes is where the number comes from._

### Hints for the CSS bars

_Since this is optional this week, here's enough to get you started. A bar is a block element with a computed width. That's the entire technique - there is no library and no cleverness involved._

_Markup for one row:_

```html
<li class="bar-row">
  <span class="bar-label">Monday</span>
  <span class="bar-track"
    ><span class="bar-fill" style="--pct: 100"></span
  ></span>
  <span class="bar-value">14</span>
</li>
```

_And the CSS:_

```css
.bar-row {
  display: grid;
  grid-template-columns: 6rem 1fr 3rem;
  gap: 0.5rem;
  align-items: center;
}
.bar-track {
  background: #eee;
}
.bar-fill {
  display: block;
  height: 1.25rem;
  width: calc(var(--pct) * 1%);
  background: #4a7;
}
```

_Four things worth understanding about that, because they're what makes WK-04 easy:_

- **_`--pct` is a percentage of the largest value in the set, not of some total._** _If Monday is your busiest day with 14 plays, Monday is 100 and a day with 7 plays is 50. Work that out with your hardcoded numbers now - it is much easier than working it out while also debugging a query._

- **_The number is the only thing PHP ever has to produce._** _One custom property in one style attribute. Everything else lives in your stylesheet, where it belongs._

- **_The value has to be there as text._** _`<span class="bar-value">14</span>` is not decoration. A coloured rectangle tells a screen reader nothing, and tells everyone else only roughly._

- **_A zero-count day still gets a row,_** _with `--pct: 0` and a visible `0`. The bar collapses to nothing, which is correct - the row disappearing entirely is not._

_Vertical bars, colour coding, rounded corners, a `<table>` instead of a list - all fine. I'm assessing that the data is legible, not that it matches a particular look._

- Validate all four pages using the W3C Markup Validation Service and correct any errors.

- _Yes, the Dashboard too. Bars mean nested elements and inline style attributes, which is exactly where markup errors like to hide._

### A word about your commit history

_Development History is worth 6% of your Project mark, and it's assessed by looking at your repository rather than by anything you write. What I want to see is a history that looks like someone building software: work showing up across the weeks, with messages that say what changed._

_The practical version:_

- **_Commit when you finish a thing, not when you finish a session._** _"Add venue grouping by province" is a commit. "Work on project" covering six hours and four features is not._

- **_Push when you commit._** _A local history I can't see is worth nothing to you._

- **_Weeks where you were busy with other things in your life and didn't touch the Project are expected_** _- there are eleven working weeks and the top band asks for seven. You don't need to commit on a schedule._

_Ten thoughtful commits across ten weeks beats two hundred across three days._

## WK-03: Week of 2026-09-21

_This is the heaviest database week of the semester. Start early._

- Install [DB Browser for SQLite](https://sqlitebrowser.org/) if you haven't already. You will be living in it this week.
  - _Use the app to browse the seeded `games` and `venues` tables._

- Work out the full data model for the administrative portal. Sketch it as an ERD (remember those?) before you type a single `CREATE TABLE`.
  - _Members are straightforward. Plays are not. A play involves one game, one venue, one date, several players, and a score for each of those players. That is not one table. Work out how many it is, and how they connect, before you build anything._

- Create all the tables you have determined you need, and populate them with data.
  - _Table definitions go below the `YOUR TABLES` marker in `database/schema.sql`; data goes below the `YOUR DATA` marker in `database/seed.sql`. Rebuild with `php database/build.php`._

  - _Each table (except your administrator table) should have **100 or more** records. Do **not** go crazy here - if you make a ton of records, you will run into issues; not necessarily performance issues, just PITA issues for you as a developer._

  - _`play` data must be spread across **September through December**, across **all seven days of the week**, and concentrated on a subset of games rather than scattered evenly - **250 or more plays across 30 to 40 games** gives you a top-five list with real winners in it, where 100 plays scattered across the whole catalogue gives you a twenty-way tie at one play each. Plan your generated data accordingly - this catches people out every single year._

- Build and test the queries that return the four required Dashboard analytics. Do the same for the queries that sort and filter member data.
  - _Keep these queries somewhere so that you can eventually implement them with PHP. Getting them right in DB Browser for SQLite first is far easier than debugging them through PHP - you see the result set immediately, with nothing else in the way._

## WK-04: Week of 2026-09-28

_Wednesday, September 30 is a campus closure (Truth & Reconciliation) - no lecture and no lab._

- Remove hardcoded data and instead use the provided database helper class to populate the Dashboard, Member Data, and Venue Listings pages using data from the database.
  - _The analytics functionality can be completed at this point, but the filtering and sorting functionality need not be operational yet._

  - _The "display previous login time" functionality will not be functional at this point._

- Complete the Venue Listings Page by implementing the addition and removal of featured games for a given venue.

- Validate the Member Data and Venue Listings Pages using the W3C Markup Validation Service and correct any errors.
  - _There's a good chance that you may have introduced some markup errors when you populated these pages with database data._

## WK-05: Week of 2026-10-05

_This is going to be a rough week: you have PHP Lab Test 2 on Wednesday and the PHP Midterm on Friday. The milestone is deliberately light._

- Complete the Member Data Page by implementing the filtering and sorting requirements.

## Week of 2026-10-12 (READING WEEK)

_No new work is assigned. If you are on schedule, rest - you've earned it._

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

- If you haven't done so earlier, design and create the additional database tables required for the public-facing app - wishlists, preferred venues, and the connections between members that let one member find another.
  - _Same routine as WK-03: definitions into `schema.sql`, data into `seed.sql`, rebuild with `php database/build.php`._

- Populate your new tables with at least 100 records of realistic data each.

## WK-08: Week of 2026-11-02

_The 25% feedback deadline is Friday, November 6._

### Static Design Tasks

- Build the static markup and CSS for the public-facing app's views (Login, Personal Dashboard, Find a Player).
  - _You will START this by having separate HTML documents for each view, BUT keep in mind that you will eventually be moving all of this work onto ONE page, with the DOM content changing based on what "page" the member is currently viewing._

  - _I strongly recommend that you hardcode data at this point - member name, email, wishlist titles and play times, a game title and a few players with their details. Seeing the finished shape early is what lets you catch layout problems while they're still cheap to fix._

  - _Don't forget to validate these pages using the W3C Markup Validation Service and fix any reported errors._

## WK-09: Week of 2026-11-09

_Wednesday, November 11 is a campus closure (Remembrance Day) - no lecture and no lab. This is a short week; plan accordingly._

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

_JS Lab Test 2 is on Wednesday. Withdrawal deadline is Friday._

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

_This is the heaviest week of the second half. If you are going to fall behind anywhere, it will be here - so get as much of it done early in the week as you can._

### PHP API Endpoint Tasks

- Create the custom PHP API endpoints:

- **GET /api/players/:game_id**

- **POST /api/plays**

- _`POST /api/plays` writes to more than one table. It has to write them consistently - a play row with no player rows, or player rows with no play, is a bug you will not notice until I do._

### Find a Player Tasks

- Clearly display the title of the game you are finding a player for.

- Call your **GET /api/players/:game_id** endpoint and display the list of members who also want to play that game, including their name, contact info, preferred contact method, and preferred venues.
  - _Properly handle and display messages for the cases where the member has no connections at all, and where none of their connections want to play the selected game._

- Implement the ability to close the view and return to the Personal Dashboard.

### Log a Play Tasks

- Build the Log a Play modal using vanilla JS and the HTML `<dialog>` element.
  - _No library and no CSS framework code here - this one is on you._

- Capture the game, the venue, the date, the players, and each player's score, and send it to your **POST /api/plays** endpoint.

- Ensure event listeners for logging plays use **Event Delegation**.

## WK-12: Week of 2026-11-30

_The JS Midterm is on Wednesday, December 2. Wednesday's lab is a Project Work Lab. The Project is due Saturday, December 5._

_There are no new features in this week's milestone. That is deliberate - if you are still building features this week, you are behind, and you should be triaging rather than adding._

- **Friday, December 4 is a final feedback opportunity.** Bring me something specific - a page that isn't behaving, a checklist item you can't get to pass, a query that returns the wrong numbers. I'll look at it there and then.
  - _This is not a code review of your whole project, and there isn't time for one the day before the deadline. One focused question each, so everyone who wants a turn gets one. If you need longer than that, come and find me earlier in the week - Wednesday's Project Work Lab is the better slot for anything substantial._

- Thoroughly test all application functionality using the submission checklist, fixing any issues.
  - _Do NOT forget to test W3C validation after adding a game and again after removing a game, to ensure your DOM manipulation does not introduce invalid markup._

- Run `npm run check` one last time and fix anything it reports.

- Confirm that `database/schema.sql` and `database/seed.sql` are both committed, that `php database/build.php` runs cleanly from a fresh clone, and that the resulting database produces non-zero Dashboard analytics for November and December.
  - _Test this properly. Clone your own repository into a new folder, run the build, and start the site. If it doesn't work there, it won't work for me either._

- Confirm the test member account required by the submission process exists and has the required data.

- Submit your project, including your completed submission checklist. Celebrate - you certainly deserve it.
