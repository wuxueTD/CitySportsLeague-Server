**This documentation is automatically generated.**

**Output schemas only represent `data` and not the full output; see output examples and the JSend specification.**

# /api/auth/playerlogin/?

    Content-Type: application/json

## POST


**Input Schema**
```json
{
    "properties": {
        "password": {
            "type": "string"
        },
        "username": {
            "type": "string"
        }
    },
    "required": [
        "username",
        "password"
    ],
    "type": "object"
}
```



**Output Schema**
```json
{
    "properties": {
        "username": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Notes**

POST the required credentials to get back a cookie

* `username`: Username
* `password`: Password



## GET


**Input Schema**
```json
null
```



**Output Schema**
```json
{
    "type": "string"
}
```



**Notes**

GET to check if authenticated.

Should be obvious from status code (403 vs. 200).



<br>
<br>

# /api/game/dateandloc/?

    Content-Type: application/json

## POST


**Input Schema**
```json
{
    "properties": {
        "date": {
            "type": "string"
        },
        "id": {
            "type": "number"
        },
        "location": {
            "type": "string"
        }
    },
    "required": [
        "date",
        "location",
        "id"
    ],
    "type": "object"
}
```



**Output Schema**
```json
{
    "properties": {
        "date": {
            "type": "string"
        },
        "id": {
            "type": "number"
        },
        "location": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Notes**

(Game host only) Update date and location of game

* `date`: Must be in YYYY-MM-DD format
* `location`
* `id`: ID of game to change



<br>
<br>

# /api/game/finish/?

    Content-Type: application/json

## POST


**Input Schema**
```json
{
    "properties": {
        "final_score": {
            "type": "object"
        },
        "id": {
            "type": "number"
        }
    },
    "type": "object"
}
```


**Input Example**
```json
{
    "final_score": {
        "Blue": 3,
        "Red": 5
    },
    "id": 1
}
```


**Output Schema**
```json
{
    "type": "string"
}
```



**Notes**

(Game host only) POST to finalize game



<br>
<br>

# /api/game/game/\(?P\<game\_id\>\[a\-zA\-Z0\-9\_\]\+\)/?$

    Content-Type: application/json

## GET


**Input Schema**
```json
null
```



**Output Schema**
```json
{
    "properties": {
        "accepted_players": {
            "type": "array"
        },
        "cancelled": {
            "type": "boolean"
        },
        "date": {
            "type": "string"
        },
        "final_score": {
            "type": "string"
        },
        "host": {
            "type": "string"
        },
        "id": {
            "type": "number"
        },
        "location": {
            "type": "string"
        },
        "teams": {
            "type": "array"
        }
    },
    "type": "object"
}
```



**Notes**

GET game with game_id



<br>
<br>

# /api/game/inviterespond/?

    Content-Type: application/json

## POST


**Input Schema**
```json
{
    "properties": {
        "decision": {
            "enum": [
                "Accept",
                "Decline"
            ]
        },
        "id": {
            "type": "number"
        }
    },
    "type": "object"
}
```



**Output Schema**
```json
{
    "type": "string"
}
```



**Notes**

Decline or accept invite

* `id`: ID of game you want to respond to invite for
* `decision`: Either "Accept" or "Decline"



<br>
<br>

# /api/player/invitations/?

    Content-Type: application/json

## GET


**Input Schema**
```json
null
```



**Output Schema**
```json
{
    "type": "array"
}
```



**Notes**

GET array of IDs for open game invitations for self



<br>
<br>

# /api/player/me/?

    Content-Type: application/json

## GET


**Input Schema**
```json
null
```



**Output Schema**
```json
{
    "properties": {
        "accepted_games": {
            "type": "array"
        },
        "bio": {
            "type": "string"
        },
        "birthday": {
            "type": "string"
        },
        "city": {
            "type": "string"
        },
        "country": {
            "type": "string"
        },
        "first": {
            "type": "string"
        },
        "games_hosted": {
            "type": "array"
        },
        "gender": {
            "type": "string"
        },
        "last": {
            "type": "string"
        },
        "teams": {
            "type": "array"
        },
        "username": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Notes**

(Player only) GET to retrieve player info

* `games`: Array of game IDs that player has accepted
* `teams`: Array of team names



<br>
<br>

# /api/player/player/?

    Content-Type: application/json

## PUT


**Input Schema**
```json
{
    "properties": {
        "bio": {
            "type": "string"
        },
        "birthday": {
            "type": "string"
        },
        "city": {
            "type": "string"
        },
        "country": {
            "type": "string"
        },
        "first": {
            "type": "string"
        },
        "gender": {
            "enum": [
                "M",
                "F"
            ]
        },
        "last": {
            "type": "string"
        },
        "password": {
            "type": "string"
        },
        "username": {
            "type": "string"
        }
    },
    "required": [
        "username",
        "first",
        "last",
        "password",
        "birthday",
        "city",
        "country"
    ],
    "type": "object"
}
```



**Output Schema**
```json
{
    "properties": {
        "username": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Notes**

PUT the required parameters to permanently register a new player

* `username`
* `first`: First name
* `last`: Last name
* `password`: Password for future logins
* `gender`: M/F
* `birthday`: e.g., "1993-05-16"
* `city`
* `country`
* `bio`



<br>
<br>

# /api/player/search/?

    Content-Type: application/json

## POST


**Input Schema**
```json
{
    "properties": {
        "query": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Output Schema**
```json
{
    "type": "array"
}
```



**Notes**

Search for players whose name starts with query



<br>
<br>

# /api/team/matchmake/?

    Content-Type: application/json

## POST


**Input Schema**
```json
{
    "properties": {
        "team_name": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Output Schema**
```json
{
    "properties": {
        "game_id": {
            "type": "number"
        }
    },
    "type": "object"
}
```



**Notes**

Does matchmaking by finding a rival team for the provided `team_name`,
creates a new game with the two teams and returns the game_id
for that game



<br>
<br>

# /api/team/team/\(?P\<name\>\[a\-zA\-Z0\-9\_\]\+\)/?$

    Content-Type: application/json

## PUT


**Input Schema**
```json
{
    "properties": {
        "name": {
            "type": "string"
        },
        "sport": {
            "enum": [
                "Basketball",
                "Soccer"
            ]
        },
        "usernames": {
            "type": "array"
        }
    },
    "required": [
        "usernames",
        "name",
        "sport"
    ],
    "type": "object"
}
```



**Output Schema**
```json
{
    "properties": {
        "name": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Notes**

PUT to create a team

* `name`
* `usernames`: list of players in team (INCLUDING YOURSELF!!)
* `sport`: One of "Basketball" or "Soccer"



## GET


**Input Schema**
```json
null
```



**Output Schema**
```json
{
    "properties": {
        "games": {
            "type": "array"
        },
        "losses": {
            "type": "number"
        },
        "name": {
            "type": "string"
        },
        "points_ratio": {
            "type": "number"
        },
        "sport": {
            "enum": [
                "Basketball",
                "Soccer"
            ]
        },
        "ties": {
            "type": "number"
        },
        "usernames": {
            "type": "array"
        },
        "wins": {
            "type": "number"
        }
    },
    "type": "object"
}
```



**Notes**

Get team with `name`



<br>
<br>

# /api/team/team/?

    Content-Type: application/json

## PUT


**Input Schema**
```json
{
    "properties": {
        "name": {
            "type": "string"
        },
        "sport": {
            "enum": [
                "Basketball",
                "Soccer"
            ]
        },
        "usernames": {
            "type": "array"
        }
    },
    "required": [
        "usernames",
        "name",
        "sport"
    ],
    "type": "object"
}
```



**Output Schema**
```json
{
    "properties": {
        "name": {
            "type": "string"
        }
    },
    "type": "object"
}
```



**Notes**

PUT to create a team

* `name`
* `usernames`: list of players in team (INCLUDING YOURSELF!!)
* `sport`: One of "Basketball" or "Soccer"



## GET


**Input Schema**
```json
null
```



**Output Schema**
```json
{
    "properties": {
        "games": {
            "type": "array"
        },
        "losses": {
            "type": "number"
        },
        "name": {
            "type": "string"
        },
        "points_ratio": {
            "type": "number"
        },
        "sport": {
            "enum": [
                "Basketball",
                "Soccer"
            ]
        },
        "ties": {
            "type": "number"
        },
        "usernames": {
            "type": "array"
        },
        "wins": {
            "type": "number"
        }
    },
    "type": "object"
}
```



**Notes**

Get team with `name`


