# The Project: Admin Portal Authentication

**COMP3512-001**

**Fall 2026**

Here's some guidance regarding the authentication portion of the Administrative Portal site.

_One note before we start, because we renamed something this term to avoid exactly this confusion: every time the word **session** appears in this document, it means a **PHP session** — the mechanism that remembers who you are between requests. It has nothing whatsoever to do with a **play**. That's why plays are called plays._

## **The Problem**

Only administrators are allowed to log in to the admin portal. They use their email and password to log in to a form and if that email/password combination belongs to a known administrator, the user is taken to the Dashboard Page; otherwise, they are redirected to the login page again.

If you were allowed to store the passwords as plain text — unencrypted — then the controller handling the form submission would look something like this:

```
// get the email from the POSTed form
// get the password from the POSTed form
// attempt to get the record from the administrator table associated with the email
// if you can't find the record
//   redirect back to the login form
// if you CAN find the record
//   if the password for that record matches the password from the form
//     write to the session to indicate the user is authorized
//     redirect to the Dashboard
//   else
//     redirect back to the login form
```

But there's a problem here: you should NEVER store passwords as plain text. **Ever**.

## **The Tools for Your Solution**

PHP provides two built-in functions that can be used to get around our issue: [password_hash()](https://www.php.net/manual/en/function.password-hash.php) and [password_verify()](https://www.php.net/manual/en/function.password-verify.php). These two functions are specifically designed to work together and to provide a way for PHP developers to safely store a [hashed password](https://auth0.com/blog/hashing-passwords-one-way-road-to-security/) (a.k.a. digest) in a database and use that digest to authenticate a user.

### Getting Hashed Passwords/Digests Into the Database

Since the Project assumes that administrators will already have their emails and hashed passwords in the administrator table, what goes into the hashed password field? The hashed password, right?

But how do you _make_ a hashed password? With password_hash()!

Let's say you wanted to have an administrator with the password PHP_makes_me_w00t. Here are the steps I'd take to generate the digest:

- You already have PHP on your machine — it's how you run the site — so you don't need any website or online tool for this. PHP will happily run a snippet straight from the command line, or from a throwaway `.php` file you delete afterwards.

- Look at Example #2 in the [password_hash() docs](https://www.php.net/manual/en/function.password-hash.php), and adjust it to use the bcrypt cost this Project requires and the password you want.
  - _No, I'm not going to give you the code — figure it out from what I've provided!_ 😁

- Copy the resulting digest string into your `seed.sql`.

**That last step matters more than it looks.** Your database is rebuilt from `/the-project-template/database/schema.sql` and `/the-project-template/database/seed.sql` every time you run `php database/build.php`, and you will run that many times between now and December. If you paste your digest straight into `app.db` using DB Browser for SQLite, it will work perfectly — right up until your next rebuild silently erases it, at which point your login stops working and nothing obvious explains why. **The digest goes in `seed.sql`.**

    Heads-up: because of how hashing works, if you run the same password through
    this process a second time, the digest will be DIFFERENT. This is confusing,
    but it's how this kind of encryption works!

    Second heads-up: a cost of 15 is deliberately expensive. Verifying a password
    will take a second or two — possibly longer on some machines. The first time
    you submit your login form and the page appears to just sit there, that's not
    a bug, that's the security doing its job!

## **Putting the Pieces Together**

Once you have the emails and associated hashed passwords in your administrator table, you're good to go. You can use the algorithm provided earlier, modified to use the password_verify() function:

```
// get the email from the POSTed form
// get the password from the POSTed form
// attempt to get the record from the administrator table associated with the email
// if you can't find the record
//   redirect back to the login form
// if you CAN find the record
//   if the password_verify() method returns true
//     write to the session to indicate the user is authorized
//     redirect to the Dashboard
//   else
//     redirect back to the login form
```

## **How the Router Fits Into This**

You are not writing the authorization check yourself — the provided Router does that part. Your job is to tell it which routes are protected, and to set the flag it looks for.

There are three pieces, and all three have to be in place or nothing works.

**1. Start the session.** Look in `www/public/index.php`. There is a `session_start()` call in there that is commented out. Uncomment it.

_If you forget, you'll get a loud exception the first time you hit a restricted route, telling you exactly this. That's intentional — without it, every visitor would silently look unauthorized and there'd be nothing to suggest why._

**2. Mark your protected routes.** `add()` returns the router, so you can chain `restrict()` onto any route that should require a login:

```php
$router->add("GET", "/admin/dashboard", "admin/dashboard.php")->restrict("???");
```

`restrict()` applies to the route immediately before it, so it goes on each protected route individually. Think about which of your admin routes should be restricted and which shouldn't — the login page itself is the obvious exception, and there's at least one other worth thinking about.

_The argument to `restrict()` is where an unauthorized visitor gets sent, and it's required rather than optional. That's deliberate. The Router has no business deciding what your login page is, and "where does someone end up when they're not allowed in" is a decision your site has to make rather than inherit. Check the requirements — they tell you exactly what the answer is for this Project._

**3. Set the flag.** When a login succeeds, the "write to the session to indicate the user is authorized" line in the algorithm above means setting `$_SESSION['authorized']`. The Router only checks whether that key exists, so what you set it _to_ is up to you — though you may find that storing something useful there saves you work elsewhere on the Dashboard.

Once those three things are true, a visitor without a session who tries to reach a restricted route gets redirected to wherever you told that route to send them, and you don't have to write a line of code to make that happen.

### Logging Out

Nothing clever here: logging out means getting rid of what you set in step 3, then sending the user back to the login page. Look up what PHP offers for this and pick whichever suits you — but do check afterwards that hitting the browser's Back button doesn't land you on a page you should no longer be able to see!

## Um…What About Validation?

Oh, right. If there was a problem with the login, you're supposed to inform the user, right? I'll give you a hint: you can use **sessions** to store a message to display on the login page. You'll need to alter your control code for the GET route, since if you arrive on the login page via a GET, you might be here because the user hasn't successfully logged in and so you will need to show a message — the message stored in the session.

_The same trick handles the other half of that requirement: remembering the email the user typed so they don't have to type it again, while pointedly not remembering the password._
