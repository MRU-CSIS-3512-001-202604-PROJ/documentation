# The Project: Submission Process

**COMP3512-001**

**Fall 2026**

**Project due date: Saturday, December 5, 2026 by the end of day**

---

# Before Submission

## Your database scripts

- [ ] `database/schema.sql` and `database/seed.sql` are both committed and pushed.
- [ ] `php database/build.php` runs cleanly **from a fresh clone** of your repository.
  - _Test this properly. Clone your own repo into a new folder, run the build, start the site. If it doesn't work there, it won't work for me either, and "it works on my machine" is not something I can mark._
- [ ] `database/app.db` is **not** committed.

**If your scripts are missing, or the build doesn't work, I will not mark your Project and it will receive a mark of zero.** Neither of us wants this to happen.

## Your data has to produce meaningful analytics

I will be marking in December. Your Dashboard needs to show real numbers, which means your seed data has to cooperate:

- [ ] Plays exist in **both November and December**, so the this-month and last-month analytics both have something to report.
  - _Put your December plays in the first week of the month. I mark on December 6th, so plays dated the 20th are real as far as your queries are concerned, but you won't be able to eyeball whether the numbers look right._
- [ ] Plays are spread across **all seven days of the week**, so the day-of-week analytic isn't mostly zeroes.
- [ ] Plays are spread across **a variety of games**, so your top-five list isn't a five-way tie at one play each.
- [ ] Both standard and premium members have logged plays, so the plays-per-member analytic can compare them.

_A Dashboard showing four zeroes is indistinguishable from a Dashboard that doesn't work. Don't make me guess which one I'm looking at._

## Your test member

I need a member I can log in as, whose data exercises every case in the public-facing app. Set this up deliberately - don't assume your generated data happens to cover it.

- [ ] The member has **2 or more connections**.
- [ ] The member has at least two games on their wishlist: one that **none** of their connections want to play, and one that **2 or more** connections want to play.
- [ ] The member has at least one wishlist game featured at one of their preferred venues, and at least one featured at **none** of them.

## Your checklist

- [ ] Your completed `submission-checklist.md` is in the root of your repository.

**If the checklist is not present, or has not been completed, I will not mark your Project and it will receive a mark of zero.**

_Read the Honesty Clause in the Marking Scheme before you fill it in. An unchecked item costs you that bundle and leaves your revision token available; a checked item that doesn't work costs you that bundle **and** your token. Honest self-assessment is genuinely in your interest here._

---

# How to Submit

Two steps. Both are required.

## 1. Push everything

Push to your project repository. Don't forget your SQL scripts and your submission checklist.

## 2. Email me

Send me an email containing:

- **Which grade bundle you think you reached.** **_I will assume that if you don't send me an email, you don't have a Project you want me to mark._**
- **The email address and cell number of the test member** I should use for your public-facing app. Include them exactly as they need to be typed - if your app wants dashes in the phone number, tell me.
- **Anything else I should know** when marking, above and beyond the known bugs you've listed on your submission checklist.

_An example email:_

> Hi, JP -
>
> I've just pushed my work to GitHub. Enjoy?
>
> I believe I've reached the 70-Level Bundle.
>
> The test member for the public-facing app has email blah@blah.com and cell 403-222-3333 (you need to add the dashes or it won't work).
>
> My Venue Listings page has a known issue with venues that have no featured games - it's on the checklist.
>
> Thank you,
>
> XXX

---

# Marking

I will begin pulling down project repositories early on **Sunday, December 6**. I can't give you an exact time, but it will be somewhere between 2 AM and 4 AM. Whatever is in your repository at that moment is what I mark. Anything pushed afterwards will not be.

_The deadline is the end of Saturday. I start pulling repositories in the small hours of Sunday, so yes, there's a gap between those two things. Don't plan your December around it. Code written at 3 AM on deadline day tends to break things that were previously working, and I have never once seen the stress be worth the marks. Whatever is in your repository when I pull is what I mark._

I mark on Sunday and Monday and send your feedback as an **Issue in your project repository** - the same way you get lab test feedback - with an email to let you know it's there. Expect that by the **end of Tuesday, December 8** at the latest.

---

# Revision Token

The full rules are in the Marking Scheme. The short version:

- You get **one** token, and it covers **one** bundle marked "Unsatisfactory."
- Email me if you want to use it, then meet me in my office and **show me the fix**. About 15 minutes. It is not a resubmission and I will not re-mark your whole project.
- The token expires at **4 PM on Wednesday, December 16**.
- It applies to bundles only. Additional marks are a single judgement call and can't be resubmitted.

_The window deliberately runs into the exam period rather than ending on the last day of classes. Your December Project mark is an estimate anyway - the cap can't be calculated until your final exam is marked - so there's no reason to cram the token into December 8th, the one day between your two cumulative lab test sittings._

_That said: if your time in the exam period is better spent studying, spend it studying. You have other courses. And our final exam is worth more than your token is, it isn't capped, and a better exam mark raises your cap. Make that trade deliberately._

---

# When You'll Get Your Marks

You will hear your **provisional** Project mark by the end of December 8th at the latest, as described above.

That mark is the **maximum** you can receive. Your actual Project mark depends on the "Hard Ceiling" cap described in the course outline, which can't be calculated until your final exam is marked and your core assessment average is known.

Final grades will be available well before the university's deadline. You will not be waiting into January to find out how you did. You know by now I'm a fast marker!
