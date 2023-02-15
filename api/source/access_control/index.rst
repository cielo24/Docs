Access Control
==============

All parameters are expected to be safely quoted as is customary for GET query strings.
Unless otherwise noted, all actions will accept either a GET or a POST request.
For each session, you will be given an api access token.
This token identifies the session, and all additional accesses are made using it.
Api tokens expire after the user has been inactive for more than one hour.

.. toctree::
   :maxdepth: 2

   login
   logout
   update_password
   update_setting
   generate_api_key
   remove_api_key
   sandbox_access
