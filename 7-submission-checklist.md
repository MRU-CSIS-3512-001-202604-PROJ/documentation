# The Project: Submission Checklist

**COMP3512-001**

**Fall 2026**

[Still needs a lookthrough! JP, 2026-09-12]

**Instructions:** Before submitting your project, go through this entire checklist in order. Test each feature and place a check (`x`) in the box only if you can confirm it works exactly as described. If a feature is buggy, note that by putting a `B` in the box instead AND note it in the `Known Bugs` section at the bottom of this document. Submitting an accurately completed checklist is part of the project's professionalism requirements.

**Student Name:** xxxxx

---

## Part 1: Underlying Code & Submission Checks

Any entry marked as **[DEALBREAKER]** must be checked for your Project submission to be marked.

- [ ] `/the-project-template/database/schema.sql` and `/the-project-template/database/seed.sql` are both committed to my repository. **[DEALBREAKER]**
- [ ] `php database/build.php` runs cleanly from a fresh clone and produces a working database. **[DEALBREAKER]**
- [ ] `database/app.db` is **not** committed to my repository.
- [ ] My scripts create and populate all tables necessary for both sites to work properly, with at least 100 records each. (You do not need 100 administrators.)
- [ ] `npm run check` reports no problems.
- [ ] My completed copy of this checklist is in the root of my repository. **[DEALBREAKER]**

### Administrative Portal (PHP)

- [ ] The digests in my administrators table begin with `$2y$15`, proving I've used the bcrypt algorithm with a cost of 15.
- [ ] My login code uses the `password_verify()` function. **[DEALBREAKER]**
- [ ] My forms do not use any client-side (HTML or JS) validation.
- [ ] My site uses the provided Router class for all page requests, and I have not modified `www/core/Router.php`. **[DEALBREAKER]**
- [ ] All my database access goes through the provided `DatabaseHelper::run()` method, and I have not modified `www/core/DatabaseHelper.php`. **[DEALBREAKER]**
- [ ] Every database query using request data uses bound parameters. **[DEALBREAKER]**
- [ ] Every value echoed into a view is escaped with `e()`.
- [ ] I never pass a request superglobal to `view()`. **[DEALBREAKER]**
- [ ] My code does not use any external PHP libraries, and there is no `vendor/` directory or Composer file in my repository. **[DEALBREAKER]**
- [ ] My administrative portal does not use any JavaScript. **[DEALBREAKER]**
- [ ] My `/admin/dashboard` page passes W3C validation with no errors. (Warnings are acceptable.)
- [ ] My `/admin/members` page passes W3C validation with no errors. (Warnings are acceptable.)
- [ ] My `/admin/venues` page passes W3C validation with no errors. (Warnings are acceptable.)

### Public-Facing App (JS)

- [ ] My app is a single page (one PHP view) that uses external JS to modify the DOM. **[DEALBREAKER]**
- [ ] All my JavaScript is in external files loaded via `<script type="module">`. **[DEALBREAKER]**
- [ ] My code does not use `onclick` or other `on...` event attributes in the HTML. **[DEALBREAKER]**
- [ ] My code does not use the `innerHTML` property. **[DEALBREAKER]**
- [ ] My code does not use `alert()`.
- [ ] My code does not use third-party JS libraries (unless I received permission). **[DEALBREAKER]**
- [ ] My code uses an HTML `<dialog>` element and vanilla JS to implement the Log a Play modal. **[DEALBREAKER]**
- [ ] All my custom API endpoints follow the `/api/...` format.
- [ ] All my API endpoints return a content type of `application/json`.
- [ ] My API endpoint code obeys the same database rules as the administrative portal: `DatabaseHelper::run()` with bound parameters, no exceptions. **[DEALBREAKER]**
- [ ] My Personal Dashboard page passes W3C validation after adding _and_ after removing a game.
- [ ] I have used event delegation for handling clicks on dynamic elements (e.g. removing a game).
- [ ] I have used Promise chaining to consume at least one API endpoint.
- [ ] I have used `async`/`await` to consume at least one API endpoint.
- [ ] I have implemented caching of wishlist data using the Web API's localStorage.

### Test Data for Marking

_I need a member I can log in as, whose data exercises every case. Set this up deliberately - don't assume your generated data happens to cover it._

- [ ] There is a member I can log in as, and I have included their email and cell number in my submission email. **[DEALBREAKER]**
- [ ] That member has 2 or more connections.
- [ ] That member has at least two games on their wishlist: one that none of their connections want to play, and one that 2 or more connections want to play.
- [ ] That member has at least one wishlist game featured at one of their preferred venues, and at least one that is featured at none of them.
- [ ] My database contains plays in **both** November and December, spread across different days of the week and different games, so the Dashboard analytics show meaningful non-zero numbers when I mark in December.

---

## Part 2: Page Functionality Checks

The bracketed numbers refer to functionalities listed in the Requirements docs. **A** numbers come from the Administrative Portal Requirements document and **P** numbers from the Public-Facing App Requirements document. For example, `[A2]` is functionality A2 in the Administrative Portal Requirements: "I want to log in to the administrative portal with an email and a password."

### Administrative Portal (PHP)

_Before starting, I have opened my browser in **Laptop L mode** (1440px wide)._

#### Login Page

- [ ] When logged out, trying to access `/admin/dashboard` redirects me to `/admin`. [A10]
- [ ] When logged out, trying to access `/admin/members` redirects me to `/admin`. [A17]
- [ ] When logged out, trying to access `/admin/venues` redirects me to `/admin`. [A26]
- [ ] When logged out, if I go to `/admin`, I see an empty login form. [A1,A3]
- [ ] The login form obfuscates the password. [A4]
- [ ] When I log in with `foo@foo.com` and `comp3512`, I wind up back at the login form with `foo@foo.com` filled in, the password field empty, and a suitably vague notification telling me the login was unsuccessful. [A5,A6,A8]
- [ ] When I log in with `jpratt@mtroyal.ca` and `foo`, I wind up back at the login form with `jpratt@mtroyal.ca` filled in, the password field empty, and a suitably vague notification telling me the login was unsuccessful. [A5,A6,A8]
- [ ] When I log in with `jpratt@mtroyal.ca` and `comp3512`, I land on the `/admin/dashboard` page, with the date and time in MST/MDT of my last login clearly visible. [A7,A8,A14]

#### Dashboard Page

- [ ] There is a clear way to log out; doing so takes me back to the Login Page with an empty login form. [A11]
- [ ] There is a clear way to get to the Member Data Page and it has resource path `/admin/members`. [A12,A16]
- [ ] There is a clear way to get to the Venue Listings Page and it has resource path `/admin/venues`. [A13,A25]
- [ ] If I leave this page and come back, the date/time of my last login is no longer visible, and I've used cookies to accomplish this. [A14]
- [ ] **Analytic 1:** plays logged this calendar month, shown alongside plays logged last calendar month. [A15]
- [ ] **Analytic 2:** average plays per member this month, separately for standard and premium members, each to one decimal place. [A15]
- [ ] **Analytic 3:** plays logged on each day of the week, with all seven days shown including any with none. [A15]
- [ ] **Analytic 4:** the five games played most this calendar month, in descending order of play count, with ties shown alphabetically. [A15]

#### Member Data Page

- [ ] There is a clear way to log out; doing so takes me back to the Login Page with an empty login form. [A18]
- [ ] There is a clear way to get to the Dashboard Page and it has resource path `/admin/dashboard`. [A19,A9]
- [ ] There is a clear way to get to the Venue Listings Page and it has resource path `/admin/venues`. [A20,A25]
- [ ] Every member is displayed with their full name, email, cell number (or "Not Provided"), plan type, enrollment date, and total plays logged. [A21]
- [ ] I can filter the display by plan type, using a form. [A22]
- [ ] I can sort by member name ascending and descending, using hyperlinks and query strings rather than a form, and it is clear which way the data is currently sorted. [A23]
- [ ] When I filter and then sort, only the filtered results are sorted. [A24]

#### Venue Listings Page

- [ ] There is a clear way to log out; doing so takes me back to the Login Page with an empty login form. [A27]
- [ ] There is a clear way to get to the Dashboard Page and it has resource path `/admin/dashboard`. [A28,A9]
- [ ] There is a clear way to get to the Member Data Page and it has resource path `/admin/members`. [A29,A16]
- [ ] All venues in the database are shown, grouped by Province. [A30]
- [ ] Clicking a venue shows the names of the games featured there - three or fewer. [A31]
- [ ] I can add a featured game to a venue using a form, and the record is added to the database. [A32]
- [ ] I can remove a featured game from a venue using a hyperlink, and the record is removed from the database. [A32]
- [ ] A venue with no featured games displays sensibly rather than breaking. [A31]

### Public-Facing App (JS)

_Before starting, I have opened my browser in **Mobile M mode** (375px wide)._

#### Login Page

- [ ] Going to `/` shows me the login page. [P1]
- [ ] I can choose whether to log in with an email address or a cell number, and enter the corresponding value. [P2]
- [ ] An unknown email or cell number leaves me on this page with a useful message. [P3]
- [ ] A known email or cell number takes me to the Personal Dashboard. [P4]

#### Personal Dashboard Page (Reduced)

- [ ] I cannot reach this page except by successfully logging in. [P5]
- [ ] There is an obvious way to log out here; when I do, I'm returned to a reset login page. [P6]
- [ ] My member information (name, email, cell number, preferred venues, and plan type) is correctly displayed here, fetched from my own API. [P7]

#### Personal Dashboard Page (Full)

- [ ] Everything in the Reduced section above still holds. [P5,P6,P7]
- [ ] My wishlist correctly displays each game's title, typical play time in minutes, and player count range. [P8]
- [ ] For each wishlist game, the preferred venues of mine that currently feature it are shown. [P8]
- [ ] For wishlist games featured at none of my preferred venues, this is clearly indicated. [P8]
- [ ] I can remove a game from my wishlist, and it disappears without a page reload. [P9]
- [ ] The "add a game" feature only shows the type-ahead dropdown after I have typed at least 3 characters (case-insensitive). [P10]
- [ ] The dropdown comes from an API call, not from fetching every game and filtering in JavaScript. [P10]
- [ ] Selecting a game from the dropdown adds it to my wishlist without a page reload. [P10]
- [ ] There's an obvious way to find a player for any game on my wishlist; when I use it, I am taken to the Find a Player Page. [P11]

#### Find a Player Page

- [ ] The title of the game I selected on the Personal Dashboard is clearly displayed. [P19]
- [ ] A clear message is displayed if I have no connections at all. [P20]
- [ ] A clear message is displayed if I have connections, but none of them want to play the selected game. [P21]
- [ ] If I have connections who want to play the game, their full details (name, email, cell number, preferred contact method, preferred venues) are all displayed. [P22]
- [ ] This page can be closed, returning me to the Personal Dashboard. [P18]

#### Log a Play

- [ ] There is an obvious way to log a play from the Personal Dashboard. [P12,P13]
- [ ] The modal is an HTML `<dialog>` element, built with vanilla JS. [P13]
- [ ] I can record which game was played, at which venue, and on what date. [P14]
- [ ] I can record who played, and what each of them scored. [P15]
- [ ] The people I can add as players are myself and my connections - nobody else. [P15]
- [ ] I can close the modal without anything being saved. [P16]
- [ ] Saving a play writes both the play itself and one record per player to the database. [P15]
- [ ] After saving, I see a brief confirmation naming who won. [P17]
- [ ] If the highest score is tied, the confirmation names all tied players. [P17]
- [ ] The winner is worked out from the scores, not stored in the database. [P17]
- [ ] A play I log here appears in the administrative portal's Dashboard analytics. [P15]

---

### Known Bugs

_(Use this space to list any features you know are not working correctly. Honesty is a key part of professionalism.)_

---

---

---

---

**By submitting this checklist, I affirm that I have personally tested each of the checked features and that this document accurately reflects the state of my project at the time of submission.**
