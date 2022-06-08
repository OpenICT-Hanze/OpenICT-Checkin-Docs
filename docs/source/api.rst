API
===================================
.. _api:

There are 2 API versions available, until further notice only v1 is being used. It will automatically remap every API call to the default API version in case the version has been omitted. 

.. _v1:
V1
--------

/api/v1/sanctum/token:
	Functionality that checks if the user filled in the right login credentials, if that's the case, a token will be created and added to the User table.
	Requires:
		E-mail
		Password
		Device_name

/api/v1/sanctum/logout:
	Functionality that logs out an user.
	
/api/v1/user:
	Returns the current logged in user.

/api/v1/postFormApi:
	Functionality that posts the filled in Form data to the database.
	Requires:
		user_id
		form_id
		questions_array
		questions_text
		array_answers
		
/api/v1/getUserFormsRecent/{user_id}:
	Returns the latest answer sheet of a filled in form of a specific user.

/api/v1/getDailyWeekBetween/{user_id}/{from}/{to}:
	from and to need to be a date written as: yyyy-mm-dd
	Returns an answer sheet that has been submitted between the given timestamps.

/api/v1/getUserFormsMonth/{user_id}: <<<<<< Geen idee wat dit precies moet doen, returned ook geen values op postman bij mij >>>>>>>>>

/api/v1/updateAnswer:
	Allows an user to update their answer sheet.
	Requires:
		id
		question_array
		question_text
		array_answers

/api/v1/getTotalDaily/{user_id}:
	Returns the total amount of daily check-ins of a specific user.

/api/v1/getTotalWeekly/{user_id}:
	Returns the total amount of weekly check-ins of a specific user.
	
/api/v1/getTotalHoursByUser/{user_id}:
	Returns the total amount of hours filled in by a specific user.
	
/api/v1/getTotalHoursBetweenByUser/{user_id}/{from}/{to}:
	Returns the total amount of hours filled in by a specific user between two dates.

/api/v1/getVersion: 
	Returns a JSON with the used version.

/api/v1/testAdmin:
	Returns a 'works' value.
	
/api/v1/getUserAll
	Returns a JSON with all users.
	
/api/v1/getUserAdmins:
	Returns a JSON with all users who have their role set as 1.

/api/v1/getUserStudents:
	Returns a JSON with all users who have their role set as 0.
	
/api/v1/getConnectedUsers/{docent_id}:
	Returns a JSON with all users/students connected to a specific docent.

/api/v1/getAllProjectsOfMyStudents/{docent_id}:
	Returns a JSON with all projects of students connected to a specific docent.

/api/v1/getAllAnswersOfMyStudents/{docent_id}:
	Returns all answers of students connected to a specific docent.

/api/v1/getAllStudentsNotMine/{docent_id}:
	Returns all users that are not connected to a specific docent.

/api/v1/removeLinkToStudent/{student_id}:
	Allows an user to remove a student from their group/ unlink

/api/v1/connectToStudent/{docent_id}/{student_id}:
	Allows a docent to connect a student to himself.
	
/api/v1/getUser/{id}:
	Returns a JSON with the user associated with id.

POST ``/api/v1/editAccount``
	Changes the user account based on the given information. Requires all values, empty values will not be changed ``""``.
	The following example will change the email address of the user id ``1``.

	>>> class WordCounter(Document):
    ...
    ...     {
	...         "id":1,
	...         "name": "",
	...         "email": "admin@admin.admin",
	...         "password": ""
	...     }


/api/v1/addUser:
	Expects : name, email, password and role
	Example: 
		{

		    "name": "John Doe",

		    "email": "a@a.a",

		    "password": "password",

		    "role": 1

		}

/api/v1/editAnswer:
	Allows an user to edit their Answer sheet.
	Requires
		id
		question_array
		question_text
		question_answers

/api/v1/editForm:
	Allows an user to edit a form.
	Requires
		id
		title
		questions_array
		active

/api/v1/getUserForms/{user_id}:
	Returns a JSON with all answers of user user_id.
	
/api/v1/geUserFormLatest/{user_id}:
	Returns a JSON with the answers of the latest form filled in.

/api/v1/geUserDailyLatest/{user_id}:
	Returns a JSON with the answers of user user_id of the daily check-in form (form_id 1).
	
/api/v1/assignRole
	Edits the role of the provided user to the provided role. Can only be done by admins through the admin middleware.
	Expects: user_id, role
	Example: 
		{
		
		    "user_id": "13",
		    
		    "role": "1"
		    
		}

/api/v1/getFormAll:
	Returns a JSON with all forms

/api/v1/getForm/{id}:
	Returns a JSON with the form form_id and its associated questions.
	
/api/v1/getDaily:
	Returns a JSON with the daily check-in form (form_id 1).

/api/v1/getWeekly:
	Returns a JSON with the weekly check-in form (form_id 2)
	
/api/v1/postForm:
	Adds a new entry to the forms and questions table
	Expects: form title as title, questions in a json array as questions.(the name of the question itself is inconsequential)
	Example:
		{
		
		    "title": "bah",
		    
		    "questions":{
		    
			"q1": {
			
			    "type": "text",
			
			    "data": "text",
			    
			    "title": "Hoe was je dag vandaag?"
			    
			},
			
			"q2": {
			
			    "type": "radio",
			
			    "data": "1-5",
			    
			    "title": "Rate je dag."
			    
			}
			
		    }
		    
		}

/api/v1/getAnswerAll:
	Returns a JSON with all answers written.
	
/api/v1/getAnswerById/{id}:
	Returns a JSON of all answers by id.
	
/api/v1/getFormAnswers/{form_id}:
	Returns a JSON with the answers in the row form_id.
	
/api/v1/getAnswersByFormUser/{form_id}/{user_id}:
	Returns a JSON of the answers on basis of form_id and user_id
	
/api/v1/saveFormAnswers:
	Saves the answers in the database.
	Expects:
		user_id -> The id of the user who answered the form.
		form_id -> The id of the form that is filled in.
		array_answers -> An array of the answers in JSON format. 
			Example:
				{
				
    					"user_id": "1",
					
    					"form_id": "1",
					
    					"array_answers" : {"boe": "hallo"}
					
				}

/api/v1/getQuestionAll:
	Returns a JSON with all questions.

/api/v1/getQuestion/{id}:
	Returns a JSON with Question id.
	
/api/v1/deleteAnswer/{id}:
	Allows an user to delete an answer.

/api/v1/putDaily:
	Functionality that creates fake answer data.
	
/api/v1/getAnswersQuestionOne:
	Returns a JSON with answers of question one of the daily-checkin

/api/v1/getAllAnswersQuestionOne/{user_id}:
	Returns a JSON with all answers of question one per user
	
/api/v1/getDailyCreatedAtLo:
	Returns a JSON with the created_at date lower than provided date.
	
/api/v1/getDailyCreatedAtHi:
	Returns a JSON with the created_at date higher than provided date.

/api/v1/getDailyCreatedAtBetweenUser/{from}/{to}/{user_id}
	Returns a JSON with the created_at date that's between two provided dates by a specific user.
	
	Example :
	In postman create a request, get the following raw data in JSON format :
	{"user_id" : "1",
    "form_id" : "1",
    "date1" : "2022-03-14 10:22:00",
    "date2" : "2022-03-14 10:37:13"}
    
 /api/v1/getTotalUsers:
 	Returns a JSON with all users.
    
 /api/v1/editQuestion:
	Allows the user to edit a question title in the questions table of database. Only allowed by admin user.
	Expects:
		id > The id of the question.
		title > Title of the question.
		data > Data of the question.
		

		Example: 
		{

		    "id": "2",

		    "title": "Question 2 test",

		    "data": "1-5",

		}
	
/api/v1/createQuestion
	Allows the user to create a new question in the database. Only allowed by admin user.
	expects:
		form-id -> The id of the form (Daily or weekly)
		qdata -> Data of question
		title -> Title of the question
		type -> Type of the question (Text, radio or slider)
	

		Example: 
		{

		    "form_id": "1",

		    "qdata": "test data",

		    "title": "test title",

		    "type": "text"

		}
		
/api/v1/editCompetentieNiveau:
	Allows an user to edit a competentie niveau.
	Requires:
		user_id
		competentie_id
		niveau

/api/v1/editCompetentieDoel:
	Allows an user to edit their competentie doel.
	Requires:
		user_id
		competentie_id
		doel


	Creates a new competentie, Only allowed by admin.
	expects:
		name: the name of the competentie
		
	Example: 
	
		{

			"name": "backend developer"

		}
		
/api/v1/editCompetentie
	Edits an existing competentie, Only allowed by admin.
	expects:
		name: the new name of the competentie
		id: of the competentie
	Example:
	
		{
		
			"id": 1,
			
			"name": "backend deloper"
			
		}
		
/api/v1/delCompetentie
	Removes an existing competentie, Only allowed by admin.
	expects:
		id: of the competentie
	Example:
	
		{

			"id": 1

		}
		
/api/v1/getAllCompetenties
	Returns all competenties
	
/api/v1/getCompetentieById/{competentie_id}
	Returns the specific competentie

/api/v1/addCompetentieToUser
	Adds a competentie to a User, Only allowed by admin user.
	Expects:
		user_id,
		competentie_id
		
	Example:
	
		{

			"user_id": 1,

			"competentie_id": 3

		}

/api/v1/delCompetentieToUser
	Removes a competentie from a user, Only allowed by admin user.
	Expects:
		id
	
	Example:
	
		{

			"id": 1

		}

/api/v1/getAllCompetentiesOfAllUsers
	Returns arrays of competenties connected to users, Only allowed by admin user.
	Example:
		{
		
		    "1": [
		    
			{
			
			    "id": 3,
			    
			    "competentie_id": 3,
			    
			    "user_id": 1,
			    
			    "created_at": "2022-03-17T11:26:41.000000Z",
			    
			    "updated_at": "2022-03-17T11:26:41.000000Z",
			    
			    "name": "backend developer"
			    
			},
			
			{
			
			    "id": 2,
			    
			    "competentie_id": 2,
			    
			    "user_id": 1,
			    
			    "created_at": "2022-03-17T11:09:51.000000Z",
			    
			    "updated_at": "2022-03-17T11:09:51.000000Z",
			    
			    "name": "frontend developer"
			    
			}
			
		    ],
		    
		    "186": [
		    
			{
			
			    "id": 3,
			    
			    "competentie_id": 3,
			    
			    "user_id": 186,
			    
			    "created_at": "2022-03-17T11:26:41.000000Z",
			    
			    "updated_at": "2022-03-17T11:26:41.000000Z",
			    
			    "name": "backend developer"
			    
			},
			
			{
			
			    "id": 2,
			    
			    "competentie_id": 2,
			    
			    "user_id": 186,
			    
			    "created_at": "2022-03-17T11:09:51.000000Z",
			    
			    "updated_at": "2022-03-17T11:09:51.000000Z",
			    
			    "name": "frontend developer"
			    
			}
			
		    ]
		    
		}

/api/v1/getCompetentiesByUser/{comp_id}/{user_id}:
	returns a list of competenties that are connected to the user

/api/v1/getAllCompetentieByUser/{comp_id}/{user_id}:
	returns all competenties by user.

/api/v1/editUserData
	Allows an admin user to edit/update the data collumn of the user table.
	Example:
		{
			
			    "id": 2,
			    
			    "data": "Test 3.0",
			
			    
			}	

/api/v1/checkFilledIn/{user_id}/{form_id}
	Checks the database if a daily check-in has been filled in already or not. The 'ProfileController' handles this API 	and returns a warning message if the check-in has been filled in.

/api/v1/getProjectsByUser/{user_id}
	Returns a list of projects connected to a specific user.

/api/v1/newProject
	Allows an admin user to create a new Project.
	Requires:
		name: the name of the project.
		description: a small description of the project.
		
	Example: 
	
		{

			"name": "Check-In Website & Applicatie",
			"description": "Hier komt een algemene beschrijving"

		}
		
/api/v1/newUserProject
	Allows an admin user to connect an user to an existing project.
	Requires:
		project_id: The id of the project
		user_id: The id of the user
	
/api/v1/editProject
	Allows an admin user to edit an existing project name and description.
	Requires:
		name: the name of the project.
		description: a small description of the project.
		id: the id of the project you want to edit.

/api/v1/getProjectByID/{id}
	Returns an array of the values of the relevant project.
	
/api/v1/getProjectIdByUserId/{user_id}
	Returns an array of information of the project connected to a specific user.
	
	Example: If admin is connected to project 1 (Check-In) this function will return this project.

/api/v1/getAllProjects
	Returns array values of all present projects.
	
/api/v1/deleteProject/{id}
	Allows an admin user to delete a certain project, which is selected by ID.
	
/api/v1/getAllJobroles
	Returns an array of all existing jobroles

/api/v1/getJobRolesByUser/{user_id}
	Returns an array value of all jobroles connected to a specific user.

/api/v1/deleteUser/{id}
	Allows an user to COMPLETELY delete an existing user from the database. 
	
/api/v1/deleteJobRole/{id}
	Allows an user to delete a specific Jobrole from the database.

/api/v1/addJobrole
	Allows an user to connect an user to a jobrole
	Requires:
		user_id: ID of the user u want to add the jobrole to.
		jobrole_id: the ID of the specific jobrole you want to add to the user.
		
/api/v1/newNotification
	Allows the application to create a new notification.
	Requires:
		user_id: ID of the user.
		type: Type of notification
		data: Data/description of the notification
		
/api/v1/getAllNotifications
	Returns an array of values of all existing notifications.
	
/api/v1/getNotificationDetails/{id}
	Returns an array of details of a specific notification.
	Requires:
		ID: ID of the specific notification.
		
/api/v1/getNotificationType/{id}
	Returns an array with the 'type' value of a specific notification.
	Requires:
		ID: ID of the specific notification.
		
/api/v1/getAmountOfNotifications
	Returns the total amount of existing notifications.

/api/v1/delNotification/{id}
	Allows an user to delete an existing notification.
	
/api/v1/getJobRolesByUser/{user_id}
	Returns an array of all jobroles connected to a specific user.
	Requires:
		user_id: ID of the specific user.


.. _v2:
V2
--------
/api/v2/getVersion: 
	Returns a JSON with the used version.
	
