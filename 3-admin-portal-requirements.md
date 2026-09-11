# The Project: Administrative Portal Requirements

**COMP3512-001**

**Fall 2026**

_Administrators can log in, view site analytics, access member data, and manage which games are featured at venues across Canada. You will use PHP to accomplish this._

# Required Site Pages w/ Their Expected Functionalities & Implementations

_Assume the "I" in the following requirements is the person using that page._

_Note: Each functionality below has a number in brackets after it. Those numbers are not decorative — the submission checklist you'll use at the end of term refers to them directly, so when the checklist says something like "[14]", you can come back here and see exactly which requirement it's testing._

_Note: As the term goes on I will occasionally clarify a requirement. When I do, the clarification appears inline, tagged with the date it was added, like this: [2026-10-10]. Skim for those tags when you come back to this document._

## **_Login_** Page

### Functionalities

- I want to get to this page by going to **http://somedomain/admin** [1]

- I want to log in to the administrative portal with an email and a password. [2]

- If this is the first time I've attempted to log in for this session, the login form should be empty. [3]

- When I type my password, it should be obfuscated. [4]

- When I submit the login form, I should be notified if the login wasn't successful, but not told what specifically (email, password, or both) was incorrect, since that's a security risk. [5]

- When I submit the login form, if the login wasn't successful, I want my email to be pre-filled to make logging in again easier for me, but I don't want my password to be pre-filled. [6]

- When I submit the login form, if my login is successful, I want to be taken to the **_Dashboard_** Page. [7]

- I want only authorized administrators to be able to log in to the portal. [8]

### Implementation Restrictions

- All form validation is done using PHP: there is no [built-in HTML form validation](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#using_built-in_form_validation) or JS form validation present.

- A database table must be created to hold records for authorized administrators; the table needs email and digest fields. You may add other fields to the table if you like — with the exception of a raw password field, obviously! _A small hint: the "previous login" requirement for the Dashboard will be more easily implemented if you add certain additional fields to your administrator table…._

- You must make user **jpratt@mtroyal.ca** with password **comp3512** an authorized administrator.

- The hashed passwords stored in the administrator table's digest field must be created using PHP's **password_hash()** function, using the **PASSWORD_BCRYPT** algorithm with a cost of **15**.

- To verify that a login attempt is valid, you must use PHP's **password_verify()** function.

## **_Dashboard_** Page

### Functionalities

- If I've logged in, I can always get to this page by going to **http://somedomain/admin/dashboard** [9]

- If I haven't logged in, if I try and go to **http://somedomain/admin/dashboard**, I wind up at **http://somedomain/admin** [10]

_The remaining functionalities assume I have logged in successfully:_

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page with an empty login form. [11]

- I want to be able to go to the **_Member Data_** Page easily. [12]

- I want to be able to go to the **_Venue Listings_** Page easily. [13]

- I want to clearly see the date and time (in MST/MDT) when I had previously logged in — but only when I first land on this page after logging in; otherwise, I don't want to see that information. [14]

- _What if the admin is logging in for the very first time? You can either sidestep the issue by making sure your db tables contain data that don't represent that situation, or you can display some kind of message indicating that the admin has never logged in before. (When I assess your Project, I will be logging in as myself, logging out, and then logging back in again.)_

- I want to clearly see the following analytics: [15]

- The percentage of members that are **standard** members vs **premium** members.

- The game that was played the most **this** calendar month and the game that was played the most **last** calendar month. If there is a tie in a given month, all tied games in that month should be displayed in alphabetic order.

- The average number of plays logged this month by **standard** members vs **premium** members.

- The average number of players per play this month, shown to one decimal place.

### Implementation Restrictions

- All analytics are pulled from database tables; they're not hard-coded or generated programmatically. Because of this, you will need to make additional tables and records for those tables. See the Required Database Tables & Records section below.

- The "show previous login time" feature must be done using cookies.

- _Read those analytics carefully, because they have a consequence you may not have noticed yet. To report on games played, plays per member, and players per session, you need somewhere to record that a game **was** played — by whom, where, when, and with what score. That's the sessions data. You are building it now, in the PHP half of the term, for this dashboard. In the JavaScript half, the public-facing app is going to write to those very same tables. If your data model is sound, that costs you nothing later. If it isn't, you'll find out in November, which is a much worse time to find out. This is why I keep telling you to sketch the ERD first._

## **_Member Data_** Page

### Functionalities

- If I've logged in, I can always get to this page by going to **http://somedomain/admin/members** [16]

- If I haven't logged in, if I try and go to **http://somedomain/admin/members**, I wind up at **http://somedomain/admin** [17]

_The remaining functionalities assume I have logged in successfully:_

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page with an empty login form. [18]

- I want to be able to go to the **_Dashboard_** Page easily. [19]

- I want to be able to go to the **_Venue Listings_** Page easily. [20]

- I want to clearly see the following information about every member: [21]

- Full name.

- Email.

- Cell phone number if available; "Not Provided" otherwise.

- Current plan type (standard or premium).

- Date of initial enrollment.

- The total number of sessions they have logged.

- I want to be able to filter the member display by the plan type. [22]

- I want to be able to sort the member data by member name, both in ascending and descending order, and see clearly which way that data is currently being sorted. [23]

- If I filter the display by plan type, and then sort the filtered results, I want only the filtered results to be sorted. [24]

### Implementation Restrictions

- Sorting is done without the use of forms; hyperlinks and query strings are used instead.

- Filtering is done using a form.

## **_Venue Listings_** Page

### Functionalities

- If I've logged in, I can always get to this page by going to **http://somedomain/admin/venues** [25]

- If I haven't logged in, if I try and go to **http://somedomain/admin/venues**, I wind up at **http://somedomain/admin** [26]

_The remaining functionalities assume I have logged in successfully:_

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page with an empty login form. [27]

- I want to be able to go to the **_Dashboard_** Page easily. [28]

- I want to be able to go to the **_Member Data_** Page easily. [29]

- I want to see the names of all venues in the database, grouped by Province. [30]

- I want to be able to show which games are currently featured at a given venue by clicking on that venue; when I do, I see the names of the three games (or fewer) that are featured there. [31]

- I want to easily add and remove featured games for a given venue. [32]

- _No more than 3 games will ever be featured at a given venue._

- _There \***\*may\*\*** be no games featured at a venue!_

- _Games must come from the **games** table provided to you in **database/seed.sql**._

- _This requirement does NOT add games to the provided games table; instead, you are marking pre-existing games as featured at pre-existing venues._

- _To make your life easier, you can handle adding a featured game in \***\*one\*\*** of three ways:_

- _Assume that the admin will enter a valid game id in a text field, or_

- _Assume that the admin will enter a valid game title in a text field, or_

- _Use a dropdown — yes, there will be a lot of games in it!_

### Implementation Restrictions

- Adding featured games is done using a form.

- Removing featured games is done using hyperlinks.

- Addition and removal of featured games causes records to be added/removed from appropriate database tables.

# Required Database Tables & Records

_Time to dust off those COMP2521 skills._

The project uses **SQLite** — one file, no server, nothing to install beyond what the template already needs. Three files in the template's `database/` directory matter to you:

- **`database/schema.sql`** — your table definitions. This is the source of truth for the shape of your database.
- **`database/seed.sql`** — your data.
- **`database/build.php`** — run `php database/build.php` to rebuild `database/app.db` from those two files.

The `.db` file itself is generated and gitignored. **Never commit it.** If your tables and data exist only in your local `app.db` and not in the two `.sql` files, they don't exist as far as I'm concerned, and your project will not mark.

You are given the **games** and **venues** tables, already defined and already populated. Your own tables go below the `YOUR TABLES` marker in `schema.sql`, and your own data below the `YOUR DATA` marker in `seed.sql`.

Two tables are nowhere near enough to fulfil the requirements. This is where you come in.

- Determine what additional tables are necessary to meet the administrative portal requirements. The functional requirements strongly suggest some sort of members table, for instance — what fields do you suppose it needs? The analytics requirements suggest something else again, and that something else is the important one.

- Add those tables to `schema.sql` and their data to `seed.sql`, then rebuild with `php database/build.php`.

  _Don't forget: you will need to tie some tables together through foreign keys! Both `build.php` and the database helper turn foreign key enforcement on, so a bad reference will fail loudly rather than quietly._

- Populate your tables with realistic data. Each table should have **100 or more** records. Do **_not_** go crazy here — if you make a ton of records, you will run into issues; not necessarily performance issues, just PITA issues for you as a developer. For tables that track time-sensitive events like play sessions, make sure your data is spread across both the current and previous months, or your analytics will show you nothing useful.

**Use [DB Browser for SQLite](https://sqlitebrowser.org/) to poke at `app.db`** while you're developing — it's far quicker than writing a page just to see whether a query works. Just remember that anything you change there is wiped the next time you rebuild. The `.sql` files are where changes go to last.

_Unless you're very lucky, or a database savant, chances are you will need to revisit this process multiple times over the semester. This doesn't indicate a deficiency on your part — it's simply the nature of non-trivial projects. Consider each revisit a good thing: you're going to the DB dojo and gaining skills._

## Using AI for Table & Record Creation

As much as I dislike much of what current LLMs represent, I grudgingly admit that there are some situations where the tools can do grunt work that would otherwise take an onerous amount of time.

For example, I used a prompt along these lines to generate the venues data you've been given. _Naturally, I had to look over the result and draw on my experience with databases and SQL before I was happy with it._

_Create realistic data for a SQLite database holding information about 100 board game cafés and game shops in Canada. The fields should hold an id, venue name, address, city, abbreviated province, postal code, latitude, longitude, phone number. Output it as SQLite-compatible INSERT statements._

Generating rows is a reasonable use of these tools. Designing your schema is not — that's the part you're being assessed on, and it's the part that will hurt you in November if you outsource it now.

# Additional Administrative Portal Requirements & Restrictions

### Requirements

- You have to use the directory structure provided in the starting project repository.

- All database access goes through the provided database helper's `run()` method, using bound parameters. Do not construct a `PDO` object yourself.

- Every value echoed into a view must be escaped with `e()`.

- Authorization is handled through the provided Router class.

- The **_Member Data_** Page and the **_Venue Listings_** Page must not generate any errors when validated by the [W3C Markup Validation Service](https://validator.w3.org/).

### Restrictions

- **`www/core/Router.php` and `www/core/DatabaseHelper.php` are not modified.**

- **No dependencies.** No Composer, no `vendor/`, no npm runtime packages, no third-party JavaScript. There is one exception, covered below, for CSS.

- **Never pass a request superglobal to `view()`.**

- **No JavaScript anywhere in the administrative portal.** This rule is deliberate: it forces you to solve sorting, filtering and analytics in PHP, which is the point of this half of the course.

- Do not use any other PHP framework (Symfony, Laravel, and so on).

_Most of the above is checked automatically — run `npm run check` before you submit anything, and fix what it reports._

# Design Expectations

## What should the pages look like?

I will be using [Google Chrome's Device Mode](https://developer.chrome.com/docs/devtools/device-mode) at Laptop L size (1440 px wide) to view your administrative portal site. There are no restrictions on the height of documents; ideally, the only pages that will require scrolling are the Venue Listings and Member Data Pages. Design accordingly.

I'm **_deliberately_** leaving the design of both sites open-ended. **You are responsible** for _interpreting_ the functional requirements, _designing_ an effective User Interface (UI) and User Experience (UX) that delivers them, and _implementing_ your design. These are crucial skills you need to develop.

**However, I am available for guidance.** If you would like me to **review** a design (e.g., wireframes or mockups) for either site, I am happy to do that. There's one catch, though: these reviews must be conducted in person. This allows you to practice presenting and discussing your design decisions — another vital skill — and is significantly more efficient than lengthy email chains. You know where to find my schedule, so when you're ready to chat, shoot me an email, and we'll set up a time to meet.

## Can I use a CSS framework?

Yes, and this is the one exception to the no-dependencies rule. A remote stylesheet brought in with `<link rel="stylesheet" href="https://…">` is fine — Bootstrap, for example.

Tailwind needs a warning. Its Play CDN is a `<script>` tag, not a stylesheet, so it is **not** permitted and `npm run check` will flag it. If you want Tailwind, build the stylesheet locally and commit the generated CSS file.

You cannot use any JavaScript-based functionality from a CSS framework, in any case. See the restrictions above.
