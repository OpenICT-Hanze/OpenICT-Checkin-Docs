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

/api/v1/getHoursPerDayWeek/{user_id}/{from}/{to}
	Returns the amount of hours filled in by a specific user sorted per answersheet between two dates.
	
/api/v1/getHoursPerDay{user_id}
	returns the amount of hours filled in by a specific user per answersheet
	
/api/v1/getTotalHoursBetweenTotal/{from}/{to}
	returns total amount of hours filled in between two dates
	
/api/v1/user
	returns all users
	
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

/api/v1/getFirstAnswersOfMyStudents/{docent_id}
	returns all first answers of answersheets made by students of {docent_id}
	
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
		question_answersgetUserAnswersheets

/api/v1/getUserForms/{user_id}:
	Returns a JSON with all answers of user user_id.
	
/api/v1/getUserAnswersheets/{user_id}:
	Returns a JSON with the id's of all answersheets filled in by {user_id}

/api/v1/getUserAnswers/{user_id}:
	Returns all answers of {user_id}
	
/api/v1/getForm/{id}:
	Returns a JSON with the form form_id and its associated questions.
	
/api/v1/getDaily:
	Returns a JSON with the daily check-in form (form_id 1).

/api/v1/getWeekly:
	Returns a JSON with the weekly check-in form (form_id 2)

/api/v1/getAnswersById/{id}:
	Returns a JSON of the answers entry of answer.id {id}
	
/api/v1/getAnswersByAnswersheet/{id}:
	Returns a JSON of the answers of answersheet {id}
	
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

/api/v1/deleteAnswer/{id}:
	Deletes all answers and ansersheeets connected to answersheet {id}

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
		
//alle competentie routes zijn achterhaald en moetten opnieuw geschreven worden
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



.. _v3:

V3
--------


.. _authenticatie_autorisatie:

Authenticatie & Autorisatie
---------------------------

Om je te authenticeren voor de API, vraag je eerst een token op via ``/api/v1/sanctum/token``.
De token die je van de API krijgt, zet je in een header als ``Authorization: Bearer {token}``.

.. note::
	Je kunt de API alleen gebruiken als je voldoende rechten hebt.


.. _endpoints:

API V3 Endpoints
----------------

Hieronder een opsommingen van de API endpoints die gebruikt kunnen worden in combinatie met de geïmplementeerde :ref:`entiteiten_relaties`. 
Voor elke API call geldt de prefix /api/v3.

**GET** ``/entity``
	Vraag een collectie entiteiten op, eventueel in combinatie met zoekparameters.

	.. note:: **Voorbeeld**

		Zoek alle users met een email gelijk aan s.tudent@st.hanze.nl:

		**GET** ``/users``

		.. code-block:: json

			{
				"email": "s.tudent@st.hanze.nl"
			}


**POST** ``/entity``
	Voeg een nieuwe entiteit toe.

	.. note:: **Voorbeeld**

		Voeg een nieuwe user toe:

		**POST** ``/users``

		.. code-block:: json

			{
				"name": "Student",
				"email": "s.tudent@st.hanze.nl",
				"password": "geheimstudentenwachtwoord"
			}


**GET** ``/entity/id``
	Haal een specifieke entiteit op.

	.. note:: **Voorbeeld**

		Haal de user met id 1 op:

		**GET** ``/users/1``


**PUT** ``/entity/id``
	Pas een entiteit aan.

	.. note:: **Voorbeeld**

		Verander de email van een user naar d.ocent@pl.hanze.nl:

		**PUT** ``/users/1``

		.. code-block:: json

			{
				"email": "d.ocent@pl.hanze.nl"
			}


**DELETE** ``/entity/id``
	Verwijder een entiteit.

	.. note:: **Voorbeeld**

		Verwijder de user met id 1:

		**DELETE** ``/users/1``


**GET** ``/entity/id/relation``
	Haal de relaties van een specifiek model op, eventueel met zoekparameters.

	.. note:: **Voorbeeld**

		Bekijk de checkins van de user 1, waarvan de mood_score 5 is:

		**GET** ``/users/1/daily-checkins``

		.. code-block:: json

			{
				"mood_score": 5
			}

		Bekijk alle projecten waaraan user 1 gekoppeld is:

		**GET** ``/users/1/projects``


**POST** ``/entity/id/relation``
	Voeg een nieuwe relatie toe aan een entiteit.

	.. note:: **Voorbeeld**

		Maak een nieuwe daily checkin aan voor user 1:

		**POST** ``/users/1/daily-checkins``

		.. code-block:: json

				{
					"mood_score": 5,
					"mood_description": "Toppie",
					"hours_worked": 6,
					"comment": "Heb je een scooter?"
				}

	.. warning:: 
		Deze API call werkt enkel voor ``hasMany`` relaties (:ref:`entiteiten_relaties`)


**GET** ``/entity/id/relation/id``
	Haal een specifieke relatie bij een entiteit op.

	.. note:: **Voorbeeld**

		Haal het project met id 1 op, als deze bij user 1 hoort:

		**GET** ``/users/1/projects/1``


**PUT** ``/entity/id/relation/id``
	Koppel twee entiteiten aan elkaar.

	.. note:: **Voorbeeld**

		Koppel project 1 aan user 1:

		**PUT** ``/users/1/projects/1``

	.. warning:: 
		Deze API call werkt enkel voor ``belongsToMany`` relaties (:ref:`entiteiten_relaties`)


**DELETE** ``/entity/id/relation/id``
	Verwijder een relatie of koppel twee entiteiten los.

	.. note:: **Voorbeeld**

		Verwijder de daily checkin met id 1 van user 1:

		**DELETE** ``/users/1/daily-checkins/1``

		Koppel project 1 los van user 1:

		**DELETE** ``/users/1/projects/1``


.. _response_codes:

API responses
-------------

De API geeft voor elke client request een response terug. 
Hieronder staat aangegeven in welke situatie welke response van de API verwacht kan worden.

``HTTP 200``
``HTTP 201``
``HTTP 204``
	Bij een succesvolle request zal een 200, 201 of 204 response terug worden gegeven. 

``HTTP 404``
	Als een bepaalde resource wordt opgevraagd die niet bestaat, zal een 404 response worden teruggegeven.

	.. note:: **Voorbeeld**

		``/users/1``, waarbij geen user met id 1 bestaat.

		``/users/1/daily-checkins/1``, waarbij geen user **en/of** daily checkin met id 1 bestaat, **of** dat beide wel bestaan, maar de daily checkin bij een andere user hoort.

		``/users/1/projects/1``, waarbij geen user **en/of** project met id 1 bestaat, **of** dat beide wel bestaan, maar het project niet aan de user is gekoppeld.

``HTTP 403``
	Als de gebruiker een token meestuurt, maar de token incorrect is of de gebruiker onvoldoende rechten heeft, zal een 403 response terug worden gegeven.

``HTTP 401``
	Als de gebruiker de API probeert te gebruiken zonder een token mee te sturen, kan een 401 response verwacht worden.

``HTTP 400``
	Bij een API call in combinatie met een request body met onvoldoende of ongeldige parameters, zal een 400 response worden teruggestuurd.


.. _entiteiten_relaties:

Entiteiten & Relaties
---------------------

Op dit moment geeft de API V3 toegang tot de volgende entiteiten en relaties.

* **users**

	* ``hasMany`` cubes
	* ``hasMany`` daily-checkins
	* ``hasMany`` weekly-checkins
	* ``belongsToMany`` jobroles
	* ``hasMany`` notifications
	* ``belongsToMany`` projects
	* ``hasMany`` portfolio-elements

* **projects**

	* ``belongsToMany`` users

* **groups**

	* ``belongsToMany`` users

* **jobroles**

	* ``belongsToMany`` users
	* ``hasMany`` descriptions

* **cubes**

	* ``hasMany`` matrix-fields

* **matrix-field**

	* ``belongsToMany`` portfolio-elements

* **portfolio-elements**
* **activities**
* **architectures**
* **levels**
