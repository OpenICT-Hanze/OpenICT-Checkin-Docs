API
===================================
.. _api:

There are 2 API versions available, until further notice only v1 is being used. It will automatically remap every API call to the default API version in case the version has been omitted. 

.. _v1:
V1
--------

/api/v1/getVersion: 
	Returns a JSON with the used version.

/api/v1/getDailyAll:
	Returns a JSON with the used version.

/api/v1/getDailyID/{id}: 
	expects: ID number of a daily
	on fail: Returns 404 page
	Returns a JSON with the daily of the corresponding id.

/api/v1/getDaily/{username}:
	expects: Exact username
	on fail: Returns 404 page
	Returns a JSON with all the users daily check ins.

/api/v1/getDailyUserLatest/{username}:
	expects: Exact username
	on fail: Returns 404 page
	Returns a JSON with the latest daily post.

POST /api/v1/dailyCheckin:
	Expects a JSON request with the following fields:
	
		username STRING
		
		feeling_score INT
		
		feeling_text STRING (not required)
		
		hours_worked_yesterday INT
		
		problems BOOL
		
		problems_text STRING (not required)
	
	Example:
	
		{
		
			"username":"Ro",
			
			"feeling_score": 4,
			
			"feeling_text": "slecht geslapen",
			
			"hours_worked_yesterday":3,
			
			"problems":true,
			
			"problems_text": "moe"
			
		}		


/api/v1/putDaily: 
	Expects: nothing
	Creates a random daily check in
	Returns a JSON with status OK, and the data created.

.. _v2:
V2
--------
/api/v2/getVersion: 
	Returns a JSON with the used version.
	
/api/v2/getForm/{id}:
	Returns a JSON with the form and questions associated with that form. Eg.
		[
			[
				{"id":1,"title":"daily","questions_array":"{1, 2, 3, 4, 5,}","active":1,"protected":1,"changed":0,"created_at":"2022-03-09T08:04:20.000000Z","updated_at":"2022-03-09T08:04:20.000000Z"}
			],
			[
				{"id":1,"form_id":1,"type":"text","data":"Question 0","active":1,"deleted":0,"changed":0,"created_at":"2022-03-09T08:04:20.000000Z","updated_at":"2022-03-09T08:04:20.000000Z"},
				
				{"id":2,"form_id":1,"type":"text","data":"Question 1","active":1,"deleted":0,"changed":0,"created_at":"2022-03-09T08:04:20.000000Z","updated_at":"2022-03-09T08:04:20.000000Z"},
				
				{"id":3,"form_id":1,"type":"text","data":"Question 2","active":1,"deleted":0,"changed":0,"created_at":"2022-03-09T08:04:20.000000Z","updated_at":"2022-03-09T08:04:20.000000Z"},
				
				{"id":4,"form_id":1,"type":"text","data":"Question 3","active":1,"deleted":0,"changed":0,"created_at":"2022-03-09T08:04:20.000000Z","updated_at":"2022-03-09T08:04:20.000000Z"},
				
				{"id":5,"form_id":1,"type":"text","data":"Question 4","active":1,"deleted":0,"changed":0,"created_at":"2022-03-09T08:04:20.000000Z","updated_at":"2022-03-09T08:04:20.000000Z"}
			]
		]

/api/v2/getAnswers/{id}:
	Returns a JSON with answers with the associated id
	
/api/v2/getFormAll
	Returns a JSON with all forms
	
/api/v2/getUserForms/{user_id}
	Returns a JSON with all answers of user user_id
	
/api/v2/geUserFormLatest/{user_id}
	Returns a JSON with latest Form filled in

/api/v2/saveFormAnswers
	Saves the answers, Expects: user_id, form_id, Answers in a array
	Example:
		{
			"Het ging goed",
			"5",
			"-",
			"Ik heb veel geleerd"
		}
