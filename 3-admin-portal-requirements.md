# The Project: Administrative Portal Requirements

**COMP3512-001**

**Fall 2026**

_Administrators can log in, view site analytics, access member data, and manage which games are featured at venues across Canada. You will use PHP to accomplish this._

# Required Site Pages w/ Their Expected Functionalities & Implementations

_Assume the "I" in the following requirements is the person using that page._

_Note: Each functionality below has a number in brackets after it, prefixed with **A** for Administrative Portal. Those numbers are not decorative - the submission checklist you'll use at the end of term refers to them directly, so when the checklist says something like `[A14]`, you can come back here and see exactly which requirement it's testing._

_Note: As the term ~~grinds~~ goes on I will occasionally clarify a requirement. When I do, the clarification appears inline, tagged with the date it was added, like this: [2026-10-31]. Skim for those tags when you come back to this document._

## **_Login_** Page

### Functionalities

- I want to get to this page by going to **http://somedomain/admin** [A1]

- I want to log in to the administrative portal with an email and a password. [A2]

- If this is the first time I've attempted to log in for this session, the login form should be empty. [A3]

- When I type my password, it should be obfuscated. [A4]

- When I submit the login form, I should be notified if the login wasn't successful, but not told what specifically (email, password, or both) was incorrect, since that's a security risk. [A5]

- When I submit the login form, if the login wasn't successful, I want my email to be pre-filled to make logging in again easier for me, but I don't want my password to be pre-filled, because that's a security no-no. [A6]

- When I submit the login form, if my login is successful, I want to be taken to the **_Dashboard_** Page. [A7]

- I want only authorized administrators to be able to log in to the portal. [A8]

### Implementation Restrictions

- All form validation is done using PHP: there is no [built-in HTML form validation](https://developer.mozilla.org/en-US/docs/Learn_web_development/Extensions/Forms/Form_validation#using_built-in_form_validation) or JS form validation present.

- A database table must be created to hold records for authorized administrators; the table needs email and digest fields. You may add other fields to the table if you like - with the exception of a raw password field, obviously! _A small hint: the "previous login" requirement for the Dashboard will be more easily implemented if you add certain additional fields to your administrator table…._

- You must make user **jpratt@mtroyal.ca** with password **comp3512** an authorized administrator.

- The hashed passwords stored in the administrator table's digest field must be created using PHP's **password_hash()** function, using the **PASSWORD_BCRYPT** algorithm with a cost of **15**.

- To verify that a login attempt is valid, you must use PHP's **password_verify()** function.

## **_Dashboard_** Page

### Functionalities

- If I've logged in, I can always get to this page by going to **http://somedomain/admin/dashboard** [A9]

- If I haven't logged in, if I try and go to **http://somedomain/admin/dashboard**, I wind up at **http://somedomain/admin** [A10]

_The remaining functionalities assume I have logged in successfully:_

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page with an empty login form. [A11]

- I want to be able to go to the **_Member Data_** Page easily. [A12]

- I want to be able to go to the **_Venue Listings_** Page easily. [A13]

- I want to clearly see the date and time (in MST/MDT) when I had previously logged in - but only when I first land on this page after logging in; otherwise, I don't want to see that information. [A14]

- _What if the admin is logging in for the very first time? You can either sidestep the issue by making sure your db tables contain data that don't represent that situation, or you can display some kind of message indicating that the admin has never logged in before. (When I assess your Project, I will be logging in as myself, logging out, and then logging back in again.)_

- I want to clearly see the following analytics: [A15]

- The number of plays logged **this** calendar month, shown alongside the number logged **last** calendar month.

- The average number of plays per member this month, for **standard** members and for **premium** members, each shown to one decimal place.

- The number of plays logged on each day of the week. All seven days are shown, including any day with no plays.

- The five games played the most **this** calendar month, in descending order of play count. If a tie means more than five games qualify, all tied games are shown, in alphabetic order within the tie.

### Implementation Restrictions

- All analytics are pulled from database tables; they're not hard-coded or generated programmatically. Because of this, you will need to make additional tables and records for those tables. See the Required Database Tables & Records section below.

- The "show previous login time" feature must be done using cookies.

- _Read those analytics carefully, because they have a consequence you may not have noticed yet. To report on how many plays happened, when they happened, which games were played, and who was involved, you need somewhere to record that a game **was** played - by whom, where, when, and with what score. That's the plays data. You are building it now, in the PHP half of the term, for this dashboard. In the JavaScript half, the public-facing app is going to write to those very same tables. If your data model is sound, that costs you nothing later. If it isn't, you'll find out in November, which is a much worse time to find out. This is why I keep telling you to think carefully about your DB design :)._

## **_Member Data_** Page

### Functionalities

- If I've logged in, I can always get to this page by going to **http://somedomain/admin/members** [A16]

- If I haven't logged in, if I try and go to **http://somedomain/admin/members**, I wind up at **http://somedomain/admin** [A17]

_The remaining functionalities assume I have logged in successfully:_

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page with an empty login form. [A18]

- I want to be able to go to the **_Dashboard_** Page easily. [A19]

- I want to be able to go to the **_Venue Listings_** Page easily. [A20]

- I want to clearly see the following information about every member: [A21]
  - Full name.

  - Email.

  - Cell phone number if available; "Not Provided" otherwise.

  - Current plan type (standard or premium).

  - Date of initial enrollment.

  - The total number of plays they have logged.

- I want to be able to filter the member display by the plan type. [A22]

- I want to be able to sort the member data by member name, both in ascending and descending order, and see clearly which way that data is currently being sorted. [A23]

- If I filter the display by plan type, and then sort the filtered results, I want only the filtered results to be sorted. [A24]

### Implementation Restrictions

- Sorting is done without the use of forms; hyperlinks and query strings are used instead.

- Filtering is done using a form.

## **_Venue Listings_** Page

### Functionalities

- If I've logged in, I can always get to this page by going to **http://somedomain/admin/venues** [A25]

- If I haven't logged in, if I try and go to **http://somedomain/admin/venues**, I wind up at **http://somedomain/admin** [A26]

_The remaining functionalities assume I have logged in successfully:_

- I want to be able to log out easily; when I do, I want to wind up back on the **_Login_** Page with an empty login form. [A27]

- I want to be able to go to the **_Dashboard_** Page easily. [A28]

- I want to be able to go to the **_Member Data_** Page easily. [A29]

- I want to see the names of all venues in the database, grouped by Province. [A30]

- I want to be able to show which games are currently featured at a given venue by clicking on that venue; when I do, I see the names of the three games (or fewer) that are featured there. [A31]

- I want to easily add and remove featured games for a given venue. [A32]
  - _No more than 3 games will ever be featured at a given venue._

  - _There \***\*may\*\*** be no games featured at a venue!_

  - _Games must come from the **games** table provided to you in **/the-project-template/database/seed.sql**._

  - _This requirement does NOT add games to the provided games table; instead, you are marking pre-existing games as featured at pre-existing venues._

  - _To make your life easier, you can handle adding a featured game in \***\*one\*\*** of three ways:_
    1. _Assume that the admin will enter a valid game id in a text field, or_

    2. _Assume that the admin will enter a valid game title in a text field, or_

    3. _Use a dropdown - yes, there will be a lot of games in it!_

### Implementation Restrictions

- Adding featured games is done using a form.

- Removing featured games is done using hyperlinks.

- Addition and removal of featured games causes records to be added/removed from appropriate database tables.

# Required Database Tables & Records

_Time to dust off those COMP2521 skills._

The project uses **SQLite** - one file, no server, nothing to install beyond what the template already needs. Three files in the template's `database/` directory matter to you:

- **`/the-project-template/database/schema.sql`** - your table definitions. This is the source of truth for the shape of your database.
- **`/the-project-template/database/seed.sql`** - your data.
- **`database/build.php`** - run `php database/build.php` to rebuild `database/app.db` from those two files.

The `.db` file itself is generated and gitignored. **Never commit it.** If your tables and data exist only in your local `app.db` and not in the two `.sql` files, they don't exist as far as I'm concerned, and your project will not be marked.

You are given the **games** and **venues** tables, already defined and already populated. Your own tables go below the `YOUR TABLES` marker in `schema.sql`, and your own data below the `YOUR DATA` marker in `seed.sql`.

Two tables are nowhere near enough to fulfil the requirements. This is where you come in.

- Determine what additional tables are necessary to meet the administrative portal - AND public-facing app - requirements. The functional requirements strongly suggest some sort of members table, for instance - what fields do you suppose it needs? The analytics requirements suggest something else again, and that something else is the important one. And are there any other tables necessary because of the public-facing app requirements?...

- Add those tables to `schema.sql` and their data to `seed.sql`, then rebuild with `php database/build.php`.

  _Don't forget: you will need to tie some tables together through foreign keys! Both `build.php` and the database helper turn foreign key enforcement on, so a bad reference will fail loudly rather than quietly._

- Populate your tables with realistic data. Each table (except for the administrator table) should have **100 or more** records. Do **_not_** go crazy here - if you make a ton of records, you will run into issues; not necessarily performance issues, just PITA issues for you as a developer. For tables that track time-sensitive events like plays, make sure your data is spread across September through December, or your analytics will show you nothing useful as you move through the semester.

**Use [DB Browser for SQLite](https://sqlitebrowser.org/) to poke at `app.db`** while you're developing - it's far quicker than writing a page just to see whether a query works. Just remember that anything you change there is wiped the next time you rebuild. The `.sql` files are where changes go to last.

_Unless you're very lucky, or a database savant, chances are you will need to revisit this process multiple times over the semester. This doesn't indicate a deficiency on your part - it's simply the nature of non-trivial projects. Consider each revisit a (somewhat) good thing: you're going to the DB dojo and gaining skills....but don't revisit TOO often, because each DB change you make will almost certainly have effects on your code, which can cause you to spend your time chasing new bugs._

## Using AI for Table & Record Creation

As much as I dislike much of what current LLMs represent, I grudgingly admit that there are some situations where the tools can do grunt work that would otherwise take an onerous amount of time.

For example, I used a prompt along these lines to generate the venues data you've been given. _Naturally, I had to look over the result and draw on my experience with databases and SQL before I was happy with it._

    Create realistic data for a SQLite database holding information about 100
    Canadian venues where people can sit down and play board games. Mix board
    game cafés, game shops with play space, public libraries that lend board
    games, and community centres that host game nights. Spread them across all
    provinces, weighted roughly by population. The fields should hold an id,
    venue name, address, city, abbreviated province, postal code, latitude,
    longitude, phone number. Output it as SQLite-compatible INSERT statements.

Generating rows is a reasonable use of these tools. Designing your schema is not - that's the part you're being assessed on, and it's the part that will hurt you _later_ if you outsource it _now_.

# Additional Administrative Portal Requirements & Restrictions

### Requirements

- You have to use the directory structure provided in the starting project repository.

- All database access goes through the provided database helper's `run()` method, using bound parameters. Do not construct a `PDO` object yourself.

- Every value echoed into a view must be escaped with `e()`.

- Authorization is handled through the provided Router class.

- The **_Dashboard_**, **_Member Data_** and **_Venue Listings_** Pages must not generate any errors when validated by the [W3C Markup Validation Service](https://validator.w3.org/). (Warnings are acceptable.)
  - _You validate these by hand: view the page source in your browser, copy it, and paste it into the validator's "Validate by Direct Input" tab. Do this yourself rather than looking for a way to automate it - knowing what the validator complains about, and why, is worth more to you than a script that hides it._
  - _The Dashboard is the one most likely to have problems, because nested elements and inline style attributes are where invalid markup likes to hide._

### Restrictions

- **`www/core/Router.php` and `www/core/DatabaseHelper.php` are not modified.**

- **No dependencies.** No Composer, no `vendor/`, no npm runtime packages, no third-party JavaScript. There is one exception, covered below, for CSS.

- **Never pass a request superglobal to `view()`. The documentation for that function
  explains why.**

- **No JavaScript anywhere in the administrative portal.** This rule is deliberate: it forces you to solve sorting, filtering and analytics in PHP, which is the point of this half of the course.

- Do not use any other PHP framework (Symfony, Laravel, and so on).

_Most of the above is checked automatically - run `npm run check` before you submit anything, and fix what it reports._

# Design Expectations

## What should the pages look like?

I will be using [Google Chrome's Device Mode](https://developer.chrome.com/docs/devtools/device-mode) at Laptop L size (1440 px wide) to view your administrative portal site. There are no restrictions on the height of documents; ideally, the only pages that will require scrolling are the Venue Listings and Member Data Pages. Design accordingly.

I'm **_deliberately_** leaving the design of both sites open-ended. **You are responsible** for _interpreting_ the functional requirements, _designing_ an effective User Interface (UI) and User Experience (UX) that delivers them, and _implementing_ your design. These are crucial skills you need to develop.

**However, I am available for guidance.** If you would like me to **review** a design (e.g., wireframes or mockups) for either site, I am happy to do that. There's one catch, though: these reviews must be conducted in person. This allows you to practice presenting and discussing your design decisions - another vital skill - and is significantly more efficient than lengthy email chains. You know where to find my schedule, so when you're ready to chat, shoot me an email, and we'll set up a time to meet.

## Showing the analytics visually

Two of the four Dashboard analytics - plays by day of the week, and the top five games - must be presented **visually as well as numerically**. Seven bars and five bars, respectively.

This has to be done with **CSS only**. There is no JavaScript in the administrative portal, and that includes charting libraries, so Chart.js and friends are out. A bar is a `<div>` with a width you compute in PHP; that is the whole technique.

- The underlying number must be visible as text, not implied by the length of a bar. A coloured rectangle on its own conveys nothing to anyone using a screen reader, and nothing precise to anyone else either.

- Days with no plays still get a row, with a zero and no bar.

- How the bars actually look is up to you. Horizontal, vertical, colour-coded, whatever - I'm assessing that the data is legible, not that it matches some house style.

_Presenting a proportion by handing the browser a computed width is close to how a lot of real reporting gets built, so this isn't a toy exercise. It's also the cheapest way to make your Dashboard look like a dashboard rather than a list of numbers._

_The WK-02 milestone has worked markup and CSS to start you off, and suggests when to fit this in._

## Can I use a CSS framework?

Yes, and this is the one exception to the no-dependencies rule. A remote stylesheet brought in with `<link rel="stylesheet" href="https://…">` is fine - Bootstrap, for example.

Tailwind needs a warning. Its Play CDN is a `<script>` tag, not a stylesheet, so it is **not** permitted and `npm run check` will flag it. If you want Tailwind, build the stylesheet locally and commit the generated CSS file.

You cannot use any JavaScript-based functionality from a CSS framework, in any case. See the restrictions above.
