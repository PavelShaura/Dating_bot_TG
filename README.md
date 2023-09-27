🤖 Telegram online dating bot (aiogram, Gino, PostgresQL)
=========================================

!!!Note!!!

1. When you start the bot, all database tables are zeroed and created. The first admin is entered in the Admin database.
Only he will be able to add, delete, etc. admins.
2. admins will be able to add and delete, etc. moderators and users.
3. Moderators will be able to add and delete etc. users.
4. From the commands only /start for everyone.
The /start command will, depending on the user's role, open a keyboard with possible commands
5. When clicking on start everyone will be checked for username 

1 Description

The system has three roles:
- users;
- moderators (check users, block/unblock users);
- administrators.
Bot users view cards with other users and give a "Sympathy" or "Skip". If two 
users give each other "Sympathy", a "Pair" is formed. Once a pair is formed, users have access to each other's 
each other's contacts (username in Telegram). 
Each user must be moderated, the moderator in his control panel sees all users, waiting for the 
verification. Administrator sees all users in general and can set moderation for each of them passed or not passed. 
not passed.

2 Basic functionality

2.1 Users

2.1.1 Creating a profile on the site. 

When entering the bot for the first time, the following fields are specified:
- name;
- age;
- gender;
- biography (text);
- from 1 to 10 photos;
- looking for m or w;
- looking for age from and to;
- search location;
- search radius.
- 
The user must have username set in Telegram to work with the bot, otherwise registration is not started and a message with the corresponding text is displayed. 
a message with the corresponding text is displayed. All of the above fields are mandatory and can be changed later in the settings. 
to change in the settings.

2.1.2 View user cards by specified search criteria.

Using the search parameters specified in the settings (looking for m or w, looking for age from and to, location and radius) users 
browse one person at a time using InlineKeyboard. Once a user clicks on "Like" or "Skip" they cannot cancel the action. 
action cannot be undone. It is also possible to send a complaint to a user's card with a reason (either from the list 
specified by the administrator or by its own text).

2.1.3 The "They Like Me" page with a list of users who have given this user a "Sympathy". 

For each of these profiles there is an opportunity to leave a mutual "Like" (a "Couple" is formed) or "Skip" 
(the user is removed from the "They Like Me" page).

2.1.4 "My Couples" page with a list of profiles. Unviewed profiles are marked (conventionally with an asterisk).
When you enter the card of a user with whom a "Couple" has been formed, the user's information + his username for contact is displayed 
(contact). Search among your "Couples" by name, filter by age.

2.1.5 "My Settings" page. Editing of all information specified at the registration stage.

2.1.6 "People Nearby" page with sorting of users by distance from the location specified by the current user. 
user.

2.2 Moderators

Moderator has all the functionality of the User inclusive.

2.2.1 Page with users waiting for moderation. Ability to confirm or reject moderation.

2.2.1 Page with users complained about. Ability to block an account (temporarily or permanently). 
In the database the blocking is fixed for a certain moderator, so that it is clear who made the decision to block.

2.3 Administrators

An Administrator has all the functionality of a Moderator inclusive.

2.3.1 A page with all users (N entries per page, set in the settings). For each user you can 
perform the following actions for each user:

- blocking (temporary or permanent) or unblocking; in case of blocking, a specified message is sent to the user;
- confirm or reject moderation;
- change the information entered by the user during registration.
- send a message on behalf of the bot.
- 
2.3.2 Mailing to all users.
  
3 Technical part

3.1 Programming language: Python.

3.2 DBMS: PostgreSQL. Library for working with PostgreSQL from Python - Gino.

3.3 Bot development library: aiogram.

3.4 Pages with several homogeneous objects should have pagination set in bot settings before launching.

3.5 All settings should be placed in a configuration file or corresponding database records.

3.6 Logging.
