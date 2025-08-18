---
{"dg-publish":true,"permalink":"/02-backend/api/endpoints/clients/"}
---

### Create Client
##### POST `/clients`
##### Request Body
```json
{
  "name": "Glow Events",
  "type": "organization",
  "phoneNumber": "+2348012345678",
  "socialMedia": {
    "instagram": "glowevents",
    "facebook": "gloweventsng"
  }
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Client created successfully",
  "data": {
    "id": "uuid",
    "name": "Glow Events",
    "type": "organization",
    "phoneNumber": "+2348012345678",
    "socialMedia": {
      "instagram": "glowevents",
      "facebook": "gloweventsng"
    }
  }
}
```
##### Error Response
```json
{
  "success": "false",
  "message": "This name is already taken",
  "data": null
}
```
##### Errors
- Client already exists
---
### Get Clients
##### GET `/clients`
##### Success Response
```json
{
  "success": true,
  "message": "Clients retrieved successfully",
  "data": [
    {
      "id": "uuid",
      "name": "Glow Events",
      "type": "organization",
      "phoneNumber": "+2348012345678",
      "socialMedia": {
        "instagram": "glowevents",
        "facebook": "gloweventsng"
      }
    },
    {
      "id": "uuid2",
      "name": "John Doe",
      "type": "individual",
      "phoneNumber": "+2348098765432",
      "socialMedia": {
        "instagram": "johndoe"
      }
    }
  ]
}
```
---
### Get Client by ID
##### GET `/clients/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Client retrieved successfully",
  "data": {
    "id": "uuid",
    "name": "Glow Events",
    "type": "organization",
    "phoneNumber": "+2348012345678",
    "socialMedia": {
      "instagram": "glowevents",
      "facebook": "gloweventsng"
    }
  }
}
```
##### Error Response
```json
{
	"success": false,
	"message": "Client does not exist",
	"data": null
}
```
##### Errors
- Client does not exist
---
### Update Client
##### PATCH `/clients/{id}`
##### Request Body
```json
{
  "name": "New Event Planner Ltd",
  "phoneNumber": "+2348012345678",
  "socialMedia": {
    "instagram": "newplanner",
    "facebook": "newplannerfb"
  }
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Client updated successfully",
  "data": {
    "id": "uuid",
    "name": "New Event Planner Ltd",
    "type": "organisation",
    "phoneNumber": "+2348012345678",
    "socialMedia": {
      "instagram": "newplanner",
      "facebook": "newplannerfb"
    },
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T14:30:00Z"
  }
}
```
##### Error Response
```json
{
	"success": false,
	"message": "Client does not exist",
	"data": null
}
```
##### Errors
- Client does not exist
---
### Delete Client
##### DELETE `/clients/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Client deleted successfully",
  "data": null
}
```
##### Error Response
```json
{
	"success": false,
	"message": "Client does not exist",
	"data": null
}
```
##### Errors
- Client does not exist