# Project 2 - Input/Output Sanitization

Time spent: **8** hours spent in total

## User Stories

The following **required** functionality is completed:

1\. [x]  Required: Import the Starting Database

2\. [x]  Required: Set Up the Starting Code

3\. [x]  Required: Review code for Staff CMS for Users

4\. [x]  Required: Complete Staff CMS for Salespeople
  * [x]  Required: index.php
  * [x]  Required: show.php
  * [x]  Required: new.php
  * [x]  Required: edit.php

5\. [x]  Required: Complete Staff CMS for States
  * [x]  Required: index.php
  * [x]  Required: show.php
  * [x]  Required: new.php
  * [x]  Required: edit.php

6\. [x]  Required: Complete Staff CMS for Territories
  * [x]  Required: index.php
  * [x]  Required: show.php
  * [x]  Required: new.php
  * [x]  Required: edit.php

7\. [x]  Required: Add Data Validations
  * [x]  Required: Validate that no values are left blank.
  * [x]  Required: Validate that all string values are less than 255 characters.
  * [x]  Required: Validate that usernames contain only the whitelisted characters.
  * [x]  Required: Validate that phone numbers contain only the whitelisted characters.
  * [x]  Required: Validate that email addresses contain only whitelisted characters.
  * [x]  Required: Add *at least 5* other validations of your choosing.

8\. [x]  Required: Sanitization
  * [x]  Required: All input and dynamic output should be sanitized.
  * [x]  Required: Sanitize dynamic data for URLs
  * [x]  Required: Sanitize dynamic data for HTML
  * [x]  Required: Sanitize dynamic data for SQL

9\. [x]  Required: Penetration Testing
  * [x]  Required: Verify form inputs are not vulnerable to SQLI attacks.
  * [x]  Required: Verify query strings are not vulnerable to SQLI attacks.
  * [x]  Required: Verify form inputs are not vulnerable to XSS attacks.
  * [x]  Required: Verify query strings are not vulnerable to XSS attacks.
  * [x]  Required: Listed other bugs or security vulnerabilities


The following advanced user stories are optional:

- [ ]  Bonus: On "public/staff/territories/show.php", display the name of the state.

- [ ]  Bonus: Validate the uniqueness of `users.username`.

- [ ]  Bonus: Add a page for "public/staff/users/delete.php".

- [ ]  Bonus: Add a Staff CMS for countries.

- [ ]  Advanced: Nest the CMS for states inside of the Staff CMS for countries


## Video Walkthrough

Here's a walkthrough of implemented user stories:

<img src='http://i.imgur.com/YdeRdfp.gif' title='Video Walkthrough' width='400px' alt='Video Walkthrough' />

GIF created with [LiceCap](http://www.cockos.com/licecap/).

## Notes

Describe any challenges encountered while building the app.

- I wish I could have figured out a better way to structure sanitization so that
I didn't have to change anything in each page.
- I figured out that the best place to sanitize an object was in the db_fetch_assoc.
This would have prevented a lot of work if I started with this approach.
- I had a misunderstanding of how to use mysqli_real_escape_string, and used it on my
entire sql query string, instead of each variable input
- I missed some query data where I needed to use db_escape. I wanted to figure out an
alternate way to structure the sql sanitization so that I don't have to type it so often
and rely on not forgetting to sanitize some inputs.

Bugs / Vulnerabilities Found:

- Putting an html tag in a name input will cause the page to not display correctly
because the POST data is not sanitized before being redisplayed. (Fixed)
- My obj_o sanitization function wasn't properly sanitizing html tags, because the
for each loop was not directly referencing key values (Fixed)
- Attempting to inject html tags can result in a successful db entry because the
sanitization will strip them before checking format. This could be changed, but I'm not sure if it should
be considered a great enough issue to restructure. A normal userbase should not be trying
to type html tags in inputs.
- Some sql queries were not properly sanitized because I missed them when adding db_escape calls. (Fixed)

## License

    Copyright [2017] [William Brooks Van Buren]

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
    WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
    See the License for the specific language governing permissions and
    limitations under the License.
