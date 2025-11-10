# ClinGen SSO Specification

## Background

Over the years, ClinGen has grown to the point where it has many web
applications.
Each web app has its own solution for signup/login and user management.
If we had a single solution for signup/login and user management,
there would be several benefits:
- Users would not need to maintain multiple logins for different ClinGen
  web apps.
- A centralized user pool with an ID for each user that can be shared
  between ClinGen web apps will make it easier to integrate ClinGen web
  apps.
- We could associate roles and permissions with users in a centralized
  user pool.
  This would allow us to easily manage users across ClinGen web apps.

There are several challenges to this:
- We would like to find an "off the shelf" solution for authentication
  and (possibly) authorization.
  We would also like to make sure the solution is secure.
- Some of the solutions are more "bare bones" than others.
  For example, if we wanted a full-featured authentication and
  authorization solution, we could use Cognito,
  but it would require work on top of integrating Cognito.
- There are other solutions that do more heavy lifting for developers,
  but they aren't as well-established.

Definitions:
- Authentication (authn)
  - The process of verifying a user’s identity.
- Authorization (authz)
  - The process of determining what a user is allowed to do.
- User
  - A unique individual account in the system.
- Group
  - A set of users.
- Permission
  - Something a user or group is allowed to do.
- Single Sign On (SSO)
  - An authentication scheme that allows users to access multiple
    applications with just one set of credentials.
- Social Login
  - An authentication scheme where you are able to sign in using a
    provider account like Google, Microsoft, Apple, etc.
    (We would use OAuth to implement social login.)

## Requirements

1. Any ClinGen web application MUST be able to programmatically (1a
   create/1b read/1c update/1d delete) users.
2. Any ClinGen web application MUST be able to programmatically (2a
   create/2b read/2c update/2d delete) groups.
3. Any ClinGen web application MUST be able to programmatically (3a
   create/3b read/3c update/3d delete) permissions.
4. A user MUST be able to log into any ClinGen web application using
   email/password.
5. A user MUST be able to log into any ClinGen web application using
   Google OAuth.
6. A user MUST be able to log into any ClinGen web application using
   Microsoft OAuth.
7. ClinGen staff members MUST be able to manage (5a create/5b read/5c
   update/5d delete) users via a web interface.
8. ClinGen staff members MUST be able to manage (6a create/6b read/6c
   update/6d delete) groups via a web interface.
9. ClinGen staff members MUST be able to manage (7a create/7b read/7c
   update/7d delete) permissions via a web interface.
10. A user SHOULD be able to log into any ClinGen web application using
    ORCID.

