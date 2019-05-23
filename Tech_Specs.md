# Self-Replicating Repository

This repository contains the Python code that forks itself into the user's GitHub profile.

## Overview

1. User clicks on the link of the deployed application. For this example, [https://self-replicating-repository-1.herokuapp.com/](https://self-replicating-repository-1.herokuapp.com/)
2. User is redirected to GitHub site to allow access to his/her public profile for the application.
3. Application forks its own repository into User's GitHub profile.

## How It's Done
This Python application is hosted on [Heroku](https://www.heroku.com), a cloud application platform.
It utilizes two packages, Flask and requests-oauthlib. [Flask](http://flask.pocoo.org) is a web development
microframework, allowing a program to create web pages and redirect the program to certain URLs.
[requests-oauthlib](https://requests-oauthlib.readthedocs.io/en/latest/) helps us create an OAuth2 client,
allowing a user to provide a GitHub access token for the program to use. <br><br>
In this application, the flask app provides the framework for the code to step through the following web pages:
<ol><li>Authorization
<ul>Redirects the user to GitHub authentication URL using OAuth2Session from the requests_oauthlib package.
At this step, the user is asked to grant permission to the base repo owner for public repositories only.</ul></li>
<li>Callback
<ul>The page the user is redirected to after GitHub authentication. This page retrieves the user's token, which
will be used in the final step, replication. This page redirects the user to the replication web page.</ul></li>
<li>Replication
<ul>This is where all of the information has been gathered, and the application is ready to replicate the repository.
The OAuth2Session module is used to fork the base repository into the authenticated user's personal repository.</ul>
</li>
</ol>
