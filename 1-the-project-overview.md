# The Project: Overview

**COMP3512-001**

**Fall 2026**

_This assignment provides an opportunity for you to demonstrate your abilities in PHP and JavaScript._

_It is quite a complex project. If it is completed successfully, it will make a strong addition to your work portfolio._

# What You'll Be Building

You will build two sites for a fictitious Canadian company called **MeepleUp**, which hopes to make oodles and oodles of money by connecting board gamers with games, with venues that stock them, and with each other.

- The first site is an **administration portal**. Administrators can log in, view site analytics, access member data, and manage which games are featured at venues across the country. You will use PHP to accomplish this. Ideally you should have this site complete by the end of Reading Week; technically you have until the project due date, but the second half of the term does not leave room to still be finishing the first half.

- The second site is the **public-facing application**. Members can log in, keep a wishlist of games they want to play, log the plays they've had, and find other members who want to play a given game. You will use JavaScript for much of this work, though you **will** need to go back and do additional back-end work in PHP as well — every one of those features is talking to an API that **you** build.

The two sites share one database. That is not an incidental detail: the analytics on the administrative portal dashboard are computed from the plays that members log in the public-facing app. You build (and seed) the tables in the PHP half of the term and write to them in the JavaScript half.

## The thing most likely to go wrong

A **play** is one game, played at one venue, on one date, by several players, each of whom scored something.

Read that sentence again and ask yourself how many tables it takes to store it. Getting that answer wrong in week three is the single most common way this project goes badly, because nothing tells you that you got it wrong until week eleven, when the public-facing app tries to write a play and your schema can't hold one. By then, attempts to redsign your schema will drive you bonkers and devour valuable time.

So: sketch the ERD first. Ask me about it if you're unsure. This is the cheapest hour you will spend on this project.

## Where everything is

Five documents make up the project specification:

- **Overview** — this document.
- **Administrative Portal Requirements** — what the PHP site has to do.
- **Public-Facing App Requirements** — what the JavaScript app has to do.
- **Suggested Milestones** — a week-by-week plan for staying on schedule.
- **Submission Process** — how to hand it in, and what happens if you don't follow it.

Requirements in the two requirements documents are numbered. The submission checklist you complete at the end of term refers to those numbers directly, so a checklist item saying "[14]" points at exactly one requirement you can go and re-read.

As the term goes on I will occasionally clarify a requirement. Clarifications appear inline in these documents, tagged with the date they were added, like this: [2026-10-19]. I will also make every to announce them, but because I am a squishy human with a squishy
human brain, the documents are the authority!

## What should the sites look like?

I'm **_deliberately_** leaving the design of both sites open-ended. **You are responsible** for _interpreting_ the functional requirements, _designing_ an effective User Interface (UI) and User Experience (UX) that delivers them, and _implementing_ your design. These are crucial skills you need to develop.

**However, I am available for guidance.** If you would like me to **review** a design (e.g., wireframes or mockups) for either site, I am happy to do that. There's one catch, though: these reviews must be conducted in person. This allows you to practice presenting and discussing your design decisions — another vital skill — and is significantly more efficient than lengthy email chains. You know where to find my schedule, so when you're ready to chat, shoot me an email, and we'll set up a time to meet.

Note that the administrative portal is assessed at Laptop L size (1440 px wide) and the public-facing app at Mobile M size (375 px wide). The requirements documents say more about each.
