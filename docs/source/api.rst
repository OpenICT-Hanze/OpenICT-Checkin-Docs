API
===================================
.. _api:

There are 2 API versions available, until further notice only v1 is being used. It will automatically remap every API call to the default API version in case the version has been omitted. 

.. _v1:
V1
--------

/api/v1/getVersion: 
	Returns a JSON with the used version.

/api/v1/getUserAll
	Returns a JSON with all users.
	
/api/v1/getUserAdmins:
	Returns a JSON with all users who have their role set as 1.

/api/v1/getUserStudents:
	Returns a JSON with all users who have their role set as 0.
	
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
	
/api/v1/postForm:
	Adds a new entry to the forms and questions table
	Expects: form title as title, questions in a json array as questions.(the name of the question itself is inconsequential)
	Example:
		{
		
		    "title": "bah",
		    
		    "questions":{
		    
			"q1": {
			
			    "type": "text",
			    
			    "title": "Hoe was je dag vandaag?"
			    
			},
			
			"q2": {
			
			    "type": "text",
			    
			    "title": "Hoeveel heb je geleerd?"
			    
			}
			
		    }
		    
		}

/api/v1/getAnswerAll:
	Returns a JSON with all answres written.
	
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
	
/api/v1/editQuestion/{id}:
	Functiionality not written.
	
/api/v1/getAnswersQuestionOne:
	Returns a JSON with answers of question one of the daily-checkin

/api/v1/getAllAnswersQuestionOne:
	Returns a JSON with all answers of question one per user
	
/api/v1/getDailyCreatedAtLo:
	Returns a JSON with the created_at date lower than provided date.
	
/api/v1/getDailyCreatedAtHi:
	Returns a JSON with the created_at date higher than provided date.

/api/v1/getDailyCreatedAtBet:
	Returns a JSON with the created_at date that's between two provided dates.
	
	Example :
	In postman create a request, get the following raw data in JSON format :
	{"user_id" : "1",
    "form_id" : "1",
    "date1" : "2022-03-14 10:22:00",
    "date2" : "2022-03-14 10:37:13"}
    
    
	
.. _v2:
V2
--------
/api/v2/getVersion: 
	Returns a JSON with the used version.
	
