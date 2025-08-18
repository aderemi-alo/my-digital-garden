---
{"dg-publish":true,"permalink":"/02-backend/api/endpoints/events/"}
---

### Create an Event
##### POST `/events`
##### Request Body
```json
{
  "name": "Wedding Reception",
  "description": "Evening lighting and effects",
  "startDate": "2025-09-10T18:00:00Z",
  "endDate": "2025-09-10T23:00:00Z",
  "venueId": "uuid-of-venue",
  "clientId": "uuid-of-client",
  "assets": [
    {
      "assetId": "uuid-of-light",
      "quantity": 20,
      "bufferDaysBefore": 1,
      "bufferDaysAfter": 1
    },
    {
      "assetId": "uuid-of-rig",
      "quantity": 5,
      "bufferDaysBefore": 0,
      "bufferDaysAfter": 2
    }
  ],
  "notes": [
	  {"text": "Leave for this event a few days before"},
	  {"text": "The client wants the lights to be pink colored"}
  ]
}
```
##### Response Example
```json
{
  "success": true,
  "message": "Event created successfully",
  "data": {
    "id": "uuid-of-event",
    "name": "Wedding Reception",
    "description": "Evening lighting and effects",
    "startDate": "2025-09-10T18:00:00Z",
    "endDate": "2025-09-10T23:00:00Z",
    "venueId": "uuid-of-venue",
    "clientId": "uuid-of-client",
    "assets": [
      {
        "assetId": "uuid-of-light",
        "quantity": 20,
        "bufferDaysBefore": 1,
        "bufferDaysAfter": 1,
        "status": "booked"
      },
      {
        "assetId": "uuid-of-rig",
        "quantity": 5,
        "bufferDaysBefore": 0,
        "bufferDaysAfter": 2,
        "status": "booked"
      }
    ],
    "notes": [
      { "text": "Leave for this event a few days before" },
      { "text": "The client wants the lights to be pink colored" }
    ]
  }
}
```
##### Error Responses
```json
{
  "success": false,
  "message": "Validation failed",
  "errors": [
    { "field": "name", "error": "Event name is required" },
    { "field": "startDate", "error": "Start date must be before end date" }
  ]
}
```
##### Possible Errors
- Validation Errors
- Venue or Client or Asset not found
- Assets not available
---
### Get Event Details
##### GET `/events/{id}`
##### Success Response
```json{
  "success": true,
  "message": "Event details retrieved successfully",
  "data": {
    "id": "uuid-of-event",
    "name": "Wedding Reception",
    "description": "Evening lighting and effects",
    "startDate": "2025-09-10T18:00:00Z",
    "endDate": "2025-09-10T23:00:00Z",
    "venueId": "uuid-of-venue",
    "clientId": "uuid-of-client",
    "assets": [
      {
        "assetId": "uuid-of-light",
        "quantity": 20,
        "bufferDaysBefore": 1,
        "bufferDaysAfter": 1,
        "status": "booked"
      },
      {
        "assetId": "uuid-of-rig",
        "quantity": 5,
        "bufferDaysBefore": 0,
        "bufferDaysAfter": 2,
        "status": "booked"
      }
    ],
    "notes": [
      { "text": "Leave for this event a few days before" },
      { "text": "The client wants the lights to be pink colored" }
    ]
  }
```
##### Possible Errors
- Event not found
---
### Update an Event
##### PATCH `/events/{id}`
##### Request Body
(same shape as create, but only include fields you want to update)
```json
{
  "name": "Updated Reception",
  "description": "Lighting + Effects",
  "notes": [
    { "text": "Bring extra cables" }
  ]
}
```
##### Success Response
```json
{
  "success": true,
  "message": "Event updated successfully",
  "data": {
    "id": "uuid-of-event",
    "name": "Updated Reception",
    "description": "Lighting + Effects",
    "startDate": "2025-09-10T18:00:00Z",
    "endDate": "2025-09-10T23:00:00Z",
    "venueId": "uuid-of-venue",
    "clientId": "uuid-of-client",
    "assets": [
      {
        "assetId": "uuid-of-light",
        "quantity": 20,
        "bufferDaysBefore": 1,
        "bufferDaysAfter": 1,
        "status": "booked"
      }
    ],
    "notes": [
      { "text": "Bring extra cables" }
    ]
  }
}
```
##### Possible Errors
- Event does not exist
- Validation Errors
- Venue or client does not exist
---
### Delete An Event
##### DELETE `/events/{id}`
##### Success Response
```json
{
  "success": true,
  "message": "Event deleted successfully",
  "data": null
}
```
##### Possible errors
- Event not found
---
### List all Events
##### GET `/events`
##### Success Response
```json
{
  "success": true,
  "message": "Events retrieved successfully",
  "data": [
    {
      "id": "uuid-of-event-1",
      "name": "Wedding Reception",
      "startDate": "2025-09-10T18:00:00Z",
      "endDate": "2025-09-10T23:00:00Z",
      "venueId": "uuid-of-venue",
      "clientId": "uuid-of-client",
      "assets": [{}],
      "notes": [
        { "text": "Leave for this event a few days before" }
      ]
    },
    {
      "id": "uuid-of-event-2",
      "name": "Birthday Party",
      "startDate": "2025-09-20T19:00:00Z",
      "endDate": "2025-09-20T23:59:00Z",
      "venueId": "uuid-of-venue",
      "clientId": "uuid-of-client",
      "assets": [{}],
      "notes": []
    }
  ]
}
```
---
### Check if Asset Overbooking Can Be Resolved
##### GET `/events/{eventId}/resolve-check`
##### Response
```json
{
  "success": true,
  "message": "Overbook status checked",
  "data": {
    "eventId": "uuid-event",
    "assets": [
      { "assetId": "uuid-light", "requested": 20, "currentlyAvailable": 20, "canResolve": true },
      { "assetId": "uuid-rig", "requested": 10, "currentlyAvailable": 5, "canResolve": false }
    ]
  }
}
```
---
### Resolve Overbooking
##### POST `/events/{eventId}/resolve-check`
##### Request Body
```json
{
  "assets": [
    { "assetId": "uuid-light", "resolve": true },
    { "assetId": "uuid-rig", "resolve": false }
  ]
}
```
##### Response
```json
{
  "success": true,
  "message": "Overbook resolved successfully",
  "data": {
    "eventId": "uuid-event",
    "resolvedAssets": [
      { "assetId": "uuid-light", "quantity": 20, "overbook": false }
    ],
    "pendingAssets": [
      { "assetId": "uuid-rig", "quantity": 10, "overbook": true }
    ],
    "overbooked": true
  }
}
```