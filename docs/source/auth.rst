Authentication
================================

.. _user authentication:

The user authentication is done by Laravel. As of writing, the laravel package used is laravel:breeze.

.. _login route:

/login

.. _register route:

/register

.. _logout: 

/logout of Auth::logout()


.. api tokens:

The Authorization bearer token is automatically added when the frontend makes an api call. In case the token hasn't been set, it creates and adds a token generated using an md5 hash of 120 random bytes.
