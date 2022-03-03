Database
===================================

.. tables:
Check-in
--------
check_in_questions: 
	Here are all the questions are are going to be asked in a check-in. With the `active` column it possible to have a question in the table but not asked in a check-in

check_in
	This is the collection point for the check-in.
	This is linked to a user to see who the check-in belongs to and a Date so that it is known on what date the check-in was made.

check_in_answer
	Here are the answers to the questions.
	The questions themselves are also saved. Because in the possibility that the questions are modified, you want to know to what wording the users answered to.

User
----
user
	Here is the user data saved. THe saved user data is: A name to login with, The email, the role of the user and the password.

role
	The roles available to link to a user


Contents
--------

.. toctree::

	Check-in
	User
