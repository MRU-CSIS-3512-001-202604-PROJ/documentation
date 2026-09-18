# The Project: Overview

**COMP3512-001**

**Fall 2026**

_This assignment provides an opportunity for you to demonstrate your abilities in PHP and JavaScript._

_It is quite a complex project. If it is completed successfully, it will make a strong addition to your work portfolio._

# What You'll Be Building

You will build two sites for a fictitious Canadian company called **MeepleMatchups**, which hopes to make gazillions of (Canadian) dollars by connecting board gamers with games, with venues where those games can be played, and with each other.

A **venue** is any public place where you can sit down and play a board game. In practice that means board game cafés, game shops with play space, public libraries that lend games and run game afternoons, and community centres that host game nights. You are given a hundred of them (see `database/seed.sql`), spread across the country.

The two sites share one database. That is not an incidental detail: the analytics on the administrative portal dashboard are computed from the plays that members log in the public-facing app! You design, build, seed, and read from tables in the PHP half of the semester, and read and write to them in the JavaScript half.

## Site #1: Administration Portal

The first site is an **administration portal**. Administrators can log in, view site analytics, access member data, and manage which games are featured at venues across the country - that is, which games a venue currently has available to play. You will use PHP to accomplish this.

Ideally, you should have this site complete by the end of WK-06 - the week of October 19 (the week after Reading Week), which is the last week the milestones give you for it. Technically you have until the project due date, but the second half of the semester does not leave room to still be finishing the first half.

## Site #2: Public-Facing Application

The second site is the **public-facing application**. Members can log in, keep a wishlist of games they want to play, log the plays they've had, and find other members who want to play a given game. You will use JavaScript for much of this work, though you **will** need to go back and do additional back-end work in PHP as well - every one of those features is talking to an API that you build.

## The thing most likely to go wrong

A **play** is one game, played at one venue, on one date, by several players, each of whom scored something.

Read that sentence again and ask yourself how many tables it takes to store it. Getting that answer wrong in week three is the single most common way this project goes badly, because nothing tells you that you got it wrong until week eleven, when the public-facing app tries to write a play and your schema can't hold one. By then, you'll have a full plate and will want to slam your head against a boardgaming table if you try and redesign your schema, because those changes will force you to touch the PHP code you thought you were done with while ALSO dealing with all the JS work you need to do!

So: think about what tables you will need (in addition to the ones you have been given), what fields those tables need, and how all the different tables will need to be related in order to handle the features you are being asked to implement. Ask me about it if you're unsure. This is the cheapest hour you will spend on this project.

## Naming Your Controller and View Files

There's exactly one `index.php` in this whole project: `www/public/index.php`. That's the front controller - the single entry point every request passes through before the Router sends it anywhere else. There's no need to create any more `index.php` files anywhere.

You'll be tempted to, because I've been using `index.php` as a default filename for controllers and views a lot up to now, but it's time to be more intentional with our naming: your Project will have numerous controllers and views and naming everything `index.php` is going to make it challenging to work and keep asking yourself things like, "Wait...is this `index.php` my Dashboard controller, or my login page view?".

So name your files for what they _do_ or _are_. Most of your routes make this easy - `admin/dashboard.php` for `/admin/dashboard`, `admin/members.php` for `/admin/members`, and so on. For the two that don't have a trailing word, name them for what they do instead: `admin/login.php` for `/admin`, and something like `app.php` for `/`.

A couple of habits that make this pay off later: keep your controller and its view under the same name in their respective folders, so `admin/dashboard.php` (the controller) pairs with `admin/dashboard.php` (the view) - it means you never have to guess.

## Where everything is

Eight documents make up the project specification:

1. **Overview**: this document.
1. **Suggested Milestones**: a week-by-week plan for staying on schedule.
1. **Administrative Portal Requirements**: what the PHP site has to do.
1. **Public-Facing App Requirements**: what the JavaScript app has to do.
1. **Admin Portal Authentication**: gives guidance on logon feature in the admin portal.
1. **Marking Scheme**: the way the project will be marked.
1. **Submission Checklist**: a checklist you are expected to go through and sign off on as part of the submission process.
1. **Submission Process**: how to hand it in, and what happens if you don't follow it.

_That's the order I'd read them in, it's the order the filenames are numbered in, and it's the order the repository README lists them in._

Requirements in the two requirements documents are numbered. The submission checklist you complete at the end of semester refers to those numbers directly, so a checklist item saying "[A14]" points at exactly one requirement in the Admin Portal Requirements doc you can go and re-read.

As the semester goes on I will occasionally clarify a requirement, because have you met me? Clarifications appear inline in these documents, tagged with the date they were added, like this: [2026-10-31]. I will also announce these clarifications in the Changelog on D2L, but the documents are the authority, because I might forget to update the Changelog, maybe even frequently.

## What should the sites look like?

I'm **_deliberately_** leaving the design of both sites open-ended. **You are responsible** for _interpreting_ the functional requirements, _designing_ an effective User Interface (UI) and User Experience (UX) that delivers them, and _implementing_ your design. These are crucial skills **you** need to develop.

**However, I am available for guidance.** If you would like me to **review** a design (e.g., wireframes or mockups) for either site, I am happy to do that. There's one catch, though: these reviews must be conducted **in person**. This allows you to practice presenting and discussing your design decisions - another vital skill - and is significantly more efficient than lengthy email chains. You know where to find my schedule, so when you're ready to chat, shoot me an email, and we'll set up a time to meet.

Note that the administrative portal is assessed at Laptop L size (1440 px wide) and the public-facing app at Mobile M size (375 px wide). The requirements documents say more about each.
