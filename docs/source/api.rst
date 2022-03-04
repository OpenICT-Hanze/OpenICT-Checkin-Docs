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
	.. code-block:: none	
		username STRING
		feeling_score INT
		feeling_text STRING (not required)
		hours_worked_yesterday INT
		problems BOOL
		problems_text STRING (not required)
	
	Example:
	.. code-block: json
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
