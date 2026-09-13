# Project Marking Scheme

**COMP3512-001**

**Fall 2026**

**Student Name:** xxxxxx

---

This project is graded using a version of something called **specifications grading**. Your submitted `submission-checklist.md` is the primary document used for marking. Each grade level is obtained by completing a "bundle" of requirements. To earn a grade, you must successfully complete **all specifications** in that grade's bundle as well as all bundles below it.

My role is to **verify the accuracy** of the items you've checked. A bundle is **satisfactory** only if you have checked all its corresponding items **and** I confirm they are functional.

**How bundles turn into a mark.** The bundle you reach is your raw Project percentage: reaching the 70-Level Bundle is a raw mark of 70%, and any additional marks are added on top of that.

Bundles are cumulative. Your mark is the highest bundle for which that bundle _and every bundle beneath it_ are satisfactory. A satisfactory 70-Level Bundle does nothing for you if the 50-Level Bundle underneath it is unsatisfactory.

I mark every bundle anyway, not just up to the first one that fails, so your feedback tells you which bundles were satisfactory and which weren't. That matters if you use your revision token: fixing the single unsatisfactory bundle promotes you to the highest level that is then unbroken.

If the 30-Level Bundle is unsatisfactory, the Project mark is zero.

Additional marks are available on top of the bundle you reach. Two of the three categories - Data Model Quality and Development History - open up as soon as your 50-Level Bundle is satisfactory, so they are live for most people. The third, UI/UX, requires the 80-Level Bundle.

Reaching the 80-Level Bundle is a raw mark of 80%, which is an A-. From there, all three categories are available, and they are what can take you to an A or an A+.

_Note: the Project mark you receive from me is capped relative to your core assessment average, as described in the course outline. That calculation happens after the final exam, so the mark you get from me in December is the **maximum** you can receive, not necessarily your final Project mark. Nothing in this document changes that; it determines your raw Project mark, which the cap is then applied to._

_One piece of strategy you should know, because it affects how you spend your time: You can estimate your own cap from about WK-06 onward - you'll have two lab tests and a midterm done by then, and you'll have an even better estimate after the JS midterm. If your estimated cap is at or below 80%, then the 80-Level Bundle alone already reaches it and the UI/UX marks are worth little or nothing to you. (Data Model Quality and Development History are a different matter - those are available from the 50-Level Bundle, so they may well be live for you even with a low cap.) Your time is far better spent preparing for the final exam, which is worth 20% of the course, is not capped, and **raises the cap itself**. Spending that valuable time polishing your CSS **for marks you likely won't receive anyway** is not a Wise Choice®._

_If you think the cap has landed unfairly on you - you build software well but test badly, and the two marks are wildly out of step - the course outline explains what to do about it. If you can see it coming, don't wait for the final grade._

---

## 🚨 [DEALBREAKER] Items

The checklist contains items marked as a **[DEALBREAKER]**. These represent the non-negotiable, foundational requirements of the project.

If I find that **any** checked [DEALBREAKER] item is actually non-functional, I will stop marking immediately.

**Dealbreakers, marking, and your token.** Two different things can go wrong with a [DEALBREAKER] item, and they don't have the same consequence:

- You **leave it unchecked**, honestly. Its bundle is Unsatisfactory. I carry on marking the rest of your bundles as normal, and your token is available for that bundle like any other.
- You **check it and it doesn't work**. I stop marking at that point. That bundle is Unsatisfactory, nothing above it is assessed, no additional marks are awarded, and under the Honesty Clause your token cannot be spent on it. Your mark is the highest bundle already established beneath it.

A dealbreaker can be repaired with your token only if you were straight with me about it in the first place.

---

## 🎟️ Revision Token

To encourage learning from mistakes, and reduce stress (at least a bit), you are granted **one "revision token"** for the Project.

Your token lets you fix **one** bundle that was marked "Unsatisfactory" and have it re-checked.

### How it works

- I will mark projects on Sunday December 6 and Monday December 7, and send your feedback as an Issue in your project repository, with an email to let you know it's there. Expect that by the **end of Tuesday, December 8** at the latest.
- If you want to use your token, email me to say so.
- You then meet me in my office and **show me the changes you've made**. Plan for about 15 minutes. This is not a resubmission, and I will not re-mark your whole project - you show me the specific things from your fixed bundle that are now working. Full stop.
- You only have **one** token, good for **one** meeting. You get **one** shot.
- Your token stays usable until **4 PM on Wednesday, December 16**. After that I need to get on with marking final exams and calculating your Project caps and getting on with other parts of my life, so it's gone.
  - _If the final exam schedule lands awkwardly against that date, I'll extend it and let you know._

### Why the window runs that long

Running the window into the exam period gives you eight days rather than December 8th - which, this year, is the single day between Part A and Part B of your cumulative lab test. That's a mercy.

_This **does** mean you could end up doing Project revisions instead of final exam study, and only you can judge whether that's a good trade. It's a fifteen-minute conversation, not an entire Project rebuild - but if your time is better spent on your final exams, or mental health days, by all means, spend it on those things! Definitely also keep in mind that our final exam is worth more than the token is, it isn't capped, and it raises your cap._

_If illness or another serious circumstance means you can't use your token in that window, come and talk to me rather than assuming you're out of luck._

---

## ✅ Honesty Clause

Your self-assessment (i.e. your submission checklist) must be accurate. A bundle will be marked **Unsatisfactory** if any single checked item is not actually complete.

Leaving an item unchecked also makes that bundle Unsatisfactory - I'm not going to pretend otherwise. The difference is what happens next:

- An **unchecked** item is an honest gap. The bundle is Unsatisfactory, and that is exactly the kind of bundle your revision token exists to repair.
- A **`B`** is an unchecked box with an explanation attached. Same effect on the bundle, and your token stays available. Use it when something half-works and you'd rather I knew that than found out by myself (which tends to make me grumpy, and you don't want the person marking your work to get grumpy).
- A **checked** item that isn't actually complete is an inaccurate submission. That bundle is Unsatisfactory **and it is not eligible for your revision token.**

So the only thing over-checking can buy you is the loss of your one repair. Check what works, leave the rest unchecked, and list anything half-finished under Known Bugs.

---

## 🏆 Grade Bundles

### 30-Level Bundle: Foundation & Integrity

This bundle covers the non-negotiable technical requirements for the project to be gradable.

- [ ] All checklist items marked **[DEALBREAKER]** under "Part 1: Underlying Code & Submission Checks → **Administrative Portal**" are checked and verified.
- [ ] `database/schema.sql` and `database/seed.sql` are both committed, and `php database/build.php` runs cleanly from a fresh clone of your repository.
- [ ] Those two scripts create and populate every table the work you are submitting actually uses, with enough data for the sites to function.
  - _You do not need 100 administrators. If you didn't reach the public-facing app, I'm not looking for its tables here._
- [ ] I believe you have made a "reasonable attempt" at completing at least the Administrative Portal. I'll use my best judgement and your Git history to help me determine this if necessary.
  - _To be plain about one case: a repository whose entire history is one or two large code dumps in the final few days is not a reasonable attempt, regardless of what the code does. Build this over the term._
- [ ] `submission-checklist.md` is submitted and accurately completed. (See Honesty Clause above.)

### 40-Level Bundle: Core Administrative Functionality

This bundle ensures the admin can log in, navigate, and view data.

- [ ] All requirements in the **30-Level Bundle** are met.
- [ ] All checklist items under "Part 2 → Administrative Portal → **Login Page**" are checked and verified.
- [ ] The Dashboard, Member Data, and Venue Listings pages are accessible at their required URLs, with clear navigation links between them.
- [ ] Member data and venue listings are displayed correctly in their initial, unfiltered and unsorted state.

### 50-Level Bundle: Dynamic Admin

This bundle adds data manipulation and reporting to the administrative portal.

- [ ] All requirements in the **40-Level Bundle** are met.
- [ ] All checklist items under "Part 2 → Administrative Portal → **Dashboard Page**" are checked and verified.
- [ ] All checklist items under "Part 2 → Administrative Portal → **Member Data Page**" are checked and verified.
- [ ] All checklist items under "Part 2 → Administrative Portal → **Venue Listings Page**" are checked and verified.
- [ ] Your plays tables can represent a play with an arbitrary number of players, each with their own score. I will test this by adding a play with five players directly to your database and confirming your Dashboard still reports correctly.
  - _None of the Dashboard analytics force this on their own, which is exactly why it's here. If your structure only works for two players, you won't discover it until WK-11, when Log a Play needs it and there's no time left to redesign._
- [ ] Every table your Project uses has at least 100 records, the administrator table excepted.
- [ ] Your seed data produces meaningful, non-zero Dashboard analytics for both November and December, as described under Part 1 → Test Data for Marking.

_Completing this bundle means your PHP site is done. By the end of Reading Week you should have everything in it except the Login Page and the authorization work - that is, the Dashboard, Member Data and Venue Listings pages all working against your database. WK-06 adds login, authorization and the previous-login feature, and finishes the bundle._

### 60-Level Bundle: Reduced Public App Core

This bundle establishes that the public-facing app runs, authenticates, and reads from your API.

- [ ] All requirements in the **50-Level Bundle** are met.
- [ ] All checklist items marked **[DEALBREAKER]** under "Part 1: Underlying Code & Submission Checks → **Public-Facing App**" are checked and verified.
- [ ] All checklist items under "Part 2 → Public-Facing App → **Login Page**" are checked and verified.
- [ ] All checklist items under "Part 2 → Public-Facing App → **Personal Dashboard Page (Reduced)**" are checked and verified.
- [ ] Your scripts create and populate the additional tables the public-facing app requires - wishlists, preferred venues, and connections between members - with at least 100 records each.
- [ ] The test member described under Part 1 → Test Data for Marking exists, and I have their email and cell number from your submission email.

### 70-Level Bundle: Public App Core

This bundle establishes the full read-and-modify functionality of the public app.

- [ ] All requirements in the **60-Level Bundle** are met.
- [ ] All checklist items under "Part 2 → Public-Facing App → **Personal Dashboard Page (Full)**" are checked and verified.
- [ ] All checklist items under "Part 2 → Public-Facing App → **Find a Player Page**" are checked and verified.
- [ ] Your test member's data exercises every case described under Part 1 → Test Data for Marking: two or more connections, a wishlist game no connection wants and one that two or more do, and a wishlist game featured at a preferred venue and one featured at none.

### 80-Level Bundle: Full-Featured Application & Professional Polish

This bundle represents a complete project that meets all requirements.

- [ ] All requirements in the **70-Level Bundle** are met.
- [ ] All checklist items under "Part 2 → Public-Facing App → **Log a Play**" are checked and verified.
- [ ] All non-dealbreaker items in "Part 1" of the checklist are checked and verified.

_Log a Play sits at the top deliberately. It is the hardest thing in the Project: a `<dialog>` built from scratch, a write that spans more than one table and has to stay consistent, and a result computed from the data you just captured rather than stored. It is also the feature the whole system exists for - everything the administrative portal reports on comes from plays logged here._

---

## 🌟 Additional Marks

There are three categories of additional marks, worth up to **20%** in total. They do not all become available at the same point.

| Category            | Worth | Available from  |
| ------------------- | ----- | --------------- |
| Data Model Quality  | 4%    | 50-Level Bundle |
| Development History | 6%    | 50-Level Bundle |
| UI/UX               | 10%   | 80-Level Bundle |

_The reasoning, since you're entitled to it: the first two categories are about how you built the thing, and a student who designed a sound schema and worked steadily over the term deserves credit for that whether or not they finished every feature. UI/UX is different - polish only really means anything on a finished application, so it stays at the top._

_The bundles are 10 points apart and the first two categories total 10, so this can never push you past a student who earned a higher bundle. At most it draws you level with one who earned no additional marks at all._

_If a **checked** [DEALBREAKER] item fails, I stop marking, which means no additional marks either._

_I realize that a lot of these marks are subjective and/or the requirements or point allocations are vague. This is partly by intent and partly because that's the nature of this work._

### Data Model Quality (up to 4%)

_Available from the 50-Level Bundle._

The bundles above only ever check that your pages produce the right output. This category is about _how_ your database is put together underneath, because a schema that produces correct results today can still be one you'd regret the moment anything changed.

I will read `database/schema.sql` with these questions in mind: is anything stored that should be derived? Are foreign keys declared where relationships exist? Can the plays tables actually represent a game played by five people with five different scores, or do they only work because your test data never has more than a couple?

- [ ] 4: A sound schema. Sensibly normalised, foreign keys where they belong, and the plays tables genuinely model a play rather than approximating one.
- [ ] 2: Works, but with a design flaw that would cause real trouble as soon as the application grew - a repeated column that should be a join, a missing foreign key, a table doing two jobs.
- [ ] 0: Works largely by accident. Heavily denormalised, no declared relationships, or a plays structure that can't represent a play with an arbitrary number of players.

_This is the category most affected by what you do in WK-03, and the one you can most easily protect by showing me your ERD before you build anything. I will happily look at a sketch. It costs you one conversation and can save you the whole 4%._

### Development History (up to 6%)

_Available from the 50-Level Bundle._

There is no development journal this year. Instead, I will look at your repository's commit history, which tells me the same thing with less work for both of us.

What I'm looking for is evidence that this project was built steadily over the term, rather than assembled in a panic at the end. Incremental commits with messages that describe what changed. Work spread across weeks. A history that looks like someone building software.

- [ ] 6: Commits spread across 7 or more distinct weeks, with meaningful messages throughout.
- [ ] 4: Commits spread across 5 or 6 distinct weeks.
- [ ] 2: Commits spread across 3 or 4 distinct weeks, or a history with large unexplained code dumps.
- [ ] 0: Fewer than 3 distinct weeks of activity.

_For calibration: there are eleven working weeks on this Project, and several of them contain a lab test or a midterm. Seven weeks of activity out of eleven is a steady pace, not a demanding one._

_To be explicit about what this is not: I am not counting commits, and there is no minimum number. Ten thoughtful commits across ten weeks beats two hundred across three days. Nor am I asking you to commit on a schedule - weeks where you were busy with lab tests and didn't touch the Project are entirely expected._

### UI/UX (up to 10%, 5% for the Administrative Portal and 5% for the App)

_Available from the 80-Level Bundle only._

This is a development course, not a design course...but a certain amount of design care must be taken, especially in consideration of the amount of assistance developers these days can obtain through careful AI use.

I will mark UI/UX with these questions in mind:

- Do pages on a site have a unified visual "feel"?
- Is it made clear to the user visually that sorting, adding, or deletion has occurred?
- Are icons used to make pages less text heavy?
- Are the Dashboard analytics actually legible? Four numbers in a row is not a dashboard; neither is a bar chart with no numbers on it.
- Do pages contain examples of design that are simply "phoned in" - that is, no effort whatsoever was taken with the visual design?
  - 'Phoned in' work is characterized by a lack of effort, such as using unstyled, default HTML elements or creating layouts that are misaligned and ignore the specified viewport widths.
- Is it reasonably obvious how to use the site - even to someone not familiar with The Project?
- Are there any truly broken things going on? (Things like freezing, links that go to incorrect or non-existent pages, buttons that seem to do nothing, and other such shenanigans.)

#### Administrative Portal UI/UX @ Laptop L (up to 5%)

- [ ] 5: I'm honestly impressed.
- [ ] 4: Minor issues only present.
- [ ] 3: One or two "phoned it in" examples present.
- [ ] 1: Three or more "phoned it in" examples present.
- [ ] 0: No discernible design effort anywhere on the site - unstyled default elements throughout.

#### Public-Facing App UI/UX @ Mobile M (up to 5%)

- [ ] 5: I'm honestly impressed.
- [ ] 4: Minor issues only present.
- [ ] 3: One or two "phoned it in" examples present.
- [ ] 1: Three or more "phoned it in" examples present.
- [ ] 0: No discernible design effort anywhere on the site - unstyled default elements throughout.

---

## Summary

| Bundle | What it establishes                                                             |
| ------ | ------------------------------------------------------------------------------- |
| 30     | It builds, it's submitted honestly, a real attempt was made                     |
| 40     | Admin login and navigation work; data displays                                  |
| 50     | Admin portal complete - analytics, filtering, sorting, featured games           |
| 60     | Public app runs, authenticates, reads from your API                             |
| 70     | Public app wishlist management and Find a Player work                           |
| 80     | Log a Play works; everything else in Part 1 is clean                            |
| +10%   | Data model quality and development history - available from the 50-Level Bundle |
| +10%   | UI/UX - available from the 80-Level Bundle                                      |
