---
name: Provision INRIX applications, users and groups
description: Create and administer INRIX applications, app keys, developers, users and user groups through the INRIX User Accounts System.
api: openapi/inrix-user-accounts-openapi-original.json
operations:
  - Auth_Signin
  - Application_Post
  - Application_Get
  - Application_GetAppKey
  - Application_SetStatus
  - Application_AddProperties
  - User_Post
  - UserGroup_Post
  - UserGroup_AddMembers
  - Auth_Signout
---

# Provision INRIX applications, users and groups

The INRIX User Accounts System (UAS) is the control plane behind every INRIX product. This skill
covers the administrative surface, not data access. Base host: `https://uas-api.inrix.com`.

## 1. Sign in as an administrator — `Auth_Signin`

`POST /v1/signin`. This is the *user* credential path, distinct from the application `appToken` flow
used for data calls. It returns the session token used for the operations below.

## 2. Register an application — `Application_Post`

`POST /v1/applications` creates the application. Then:

- `Application_Get` (`GET /v1/applications/{appId}`) — read it back and confirm the appId GUID.
- `Application_GetAppKey` (`GET /v1/applications/{appId}/appKey`) — retrieve the appKey. This is the
  value you hash with the appId to build the `hashToken` in the authentication skill.
- `Application_SetStatus` (`PUT /v1/applications/{appId}/status`) — enable, suspend or disable it.

Treat the appKey as a secret. It is not rotatable through a documented self-service endpoint.

## 3. Attach application metadata — `Application_AddProperties`

`POST /v1/applications/{appId}/properties` stores arbitrary key/value properties on the application.
Read them back with `Application_QueryProperty`, or a single key with
`Application_QueryPropertyByKey` (`GET /v1/applications/{appId}/properties/{key}`).
`Application_DeleteProperty` removes one.

Use this for your own deployment metadata — INRIX does not interpret these keys.

## 4. Create users — `User_Post`

`POST /v1/users`. Related flows the spec exposes:

- `User_SendVerificationEmail` then `User_VerifyEmail` / `User_ValidateEmail` — email confirmation.
- `User_InviteUser` — invite rather than directly create.
- `User_ChangePassword` and `User_ResetPassword` — credential lifecycle.
- `User_Delete` (`DELETE /v1/users/{userId}`) — removal.

## 5. Group users — `UserGroup_Post` and `UserGroup_AddMembers`

`POST /v1/usergroups` creates a group; `POST /v1/usergroups/{id}/members` adds members;
`UserGroup_GetMembers` lists them; `UserGroup_DeleteMembers`
(`DELETE /v1/usergroups/{id}/members/{memberId}`) removes one. Groups carry their own property bag
via `UserGroup_AddProperties`.

Entitlement to INRIX data products is set by INRIX per account. Group membership organizes users; it
does **not** grant API scopes — INRIX publishes no scope vocabulary.

## 6. Sign out — `Auth_Signout`

`GET /v1/signout` when the administrative session is finished.

## Rules

- **Never run this against production first.** UAS has a parallel beta host,
  `https://uas-api.beta.inrix.com`, with its own Swagger console. Tokens do not cross environments.
- Every response carries the INRIX `statusId` envelope — see `errors/inrix-error-codes.yml`.
  `statusId 7` / `19` (consumerGuid or consumerId not found) and `26` (User Authentication Failed)
  are the common administrative failures.
- Writes are **not idempotent**. Re-POSTing an application or a user will create a second one. Read
  before you write.
- The UAS spec declares no `securityDefinitions`; authorization is carried by the bearer token
  described in `authentication/inrix-authentication.yml`.
