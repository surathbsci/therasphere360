---
sidebar_position: 2
---

# CIP GUID

To find your CIP guid, start up the frontend application and load the URL in the browser.

You should be redirected to the login page, at which point yuu should select the "Employee login" link under the Sign In button to log in with your Boston Scientific Credentials.

![Login](/cip-guid/login.png "Login")

Upon completion of the login process you should be redirected back to the frontend application's unauthorized page.

![Unauthorized](/cip-guid/unauthorized.png "Unauthorized")

Open up the developer tools in your browser and naviagte to the `application` tab, under storage expand `Session storage` select the item `http://localhost:3000`.

You will then see the data stored. Within that data you are looking for the `sub` value listed under `profile`.

![dev tools](/cip-guid/devtools.png "dev tools")

This is the value that you will need to add to the `AUTHORIZED_USERS` property in the backend .env file.
