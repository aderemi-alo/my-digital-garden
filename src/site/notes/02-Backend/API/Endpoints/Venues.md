---
{"dg-publish":true,"permalink":"/02-backend/api/endpoints/venues/"}
---

### Create Venue
##### POST `/venues`
```json
{
  "name": "Grand Hall",
  "address": "123 Event Street, Lagos",
  "manager": {
    "name": "John Doe",
    "phoneNumber": "+2348011111111"
  }
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Venue created successfully",
  "data": {
    "id": "uuid",
    "name": "Grand Hall",
    "address": "123 Event Street, Lagos",
    "manager": {
      "name": "John Doe",
      "phoneNumber": "+2348011111111"
    },
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T12:00:00Z"
  }
}
```
##### Error Response
```json
{
  "success": true,
  "message": "Venue already exists",
  "data": null
}
```
##### Errors
- Venue already exists
---
### Get All Venues
##### GET `/venues`
##### Success Response
```json
{
	"success": true,
	"message": "Venues fetched successfully",
	"data": [
		{
    "id": "uuid",
    "name": "Grand Hall",
    "address": "123 Event Street, Lagos",
    "capacity": 500,
    "manager": {
      "name": "John Doe",
      "phoneNumber": "+2348011111111"
	    },
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T12:00:00Z"
		},
		{
    "id": "uuid",
    "name": "Grand Hall",
    "address": "123 Event Street, Lagos",
    "capacity": 500,
    "manager": {
      "name": "John Doe",
      "phoneNumber": "+2348011111111"
	    },
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T12:00:00Z"
		}
	]
}
```
---
### Get Venue by ID
##### GET `/venues/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Venue fetched successfully",
  "data": {
    "id": "uuid",
    "name": "Grand Hall",
    "address": "123 Event Street, Lagos",
    "capacity": 500,
    "manager": {
      "name": "John Doe",
      "phoneNumber": "+2348011111111"
    },
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T12:00:00Z"
  }
}
```
##### Error Response
```json
{
	"success": false,
	"message": "Venue does not exist",
	"data": null
}
```
##### Errors
- Venue does not exist
---
### Update Venue
##### PATCH `/venue/{id}`
##### Request Body
```json
{
  "manager": {
    "name": "Jane Smith",
    "phoneNumber": "+2348022222222"
  }
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Venue updated successfully",
  "data": {
    "id": "uuid",
    "name": "Grand Hall",
    "address": "123 Event Street, Lagos",
    "manager": {
      "name": "Jane Smith",
      "phoneNumber": "+2348022222222"
    },
    "createdAt": "2025-08-16T12:00:00Z",
    "updatedAt": "2025-08-16T14:00:00Z"
  }
}
```
##### Error Response
```json
{
	"success": false,
	"message": "Venue does not exist",
	"data": null
}
```
##### Errors
- Venue does not exist
---
### Delete Venue
##### DELETE `/venues/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Venue deleted successfully",
  "data": null
}
```
##### Error Response
```json
{
	"success": false,
	"message": "Venue does not exist",
	"data": null
}
```
##### Errors
- Venue does not exist
