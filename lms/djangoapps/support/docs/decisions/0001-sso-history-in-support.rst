1. Registering SSO History Model in Support
================================================

Status
------

Accepted

Context
-------

SSO History was one of the feature requested by support that provides the 
historical data of any particular SSO record (based off UserSocialAuth)
in frontend-app-support-tools via support API.

Decision
--------

We have introduced the simple_django_history registeration for 
UserSocialAuth model in the Support app for LMS instead of the 
third_party_auth in Common. 

The primary reason were the failing migration tests in CMS with the 
current configurations in the studio. We tried to add the third_party_auth
as an installed app on Studio but later found out that Studio is not 
configured for third_party_auth and probably is a little complex to 
configure. Consequently, there was over 6 hours of pipeline outage on
stage and we had to revert the changes made in the system.

Consequences
------------

The most optimum method to introduce the feature was to register the model
in support app and get the data via support API.