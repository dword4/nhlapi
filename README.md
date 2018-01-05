# NHL API Documentation

All of this has been compiled and tested by hand in Jan of 2018, prior to this most of the information was spread across the internet in various posts and not available in a cohesive
single place.
### Teams

`GET https://statsapi.web.nhl.com/api/v1/teams` Returns a list of data about
all teams including their id, venue details, division, conference and franchise information.

`GET https://statsapi.web.nhl.com/api/v1/teams/ID` Returns the same information as above just
for a single team instead of the entire league.
#### Modifiers
`?expand=team.roster` Shows roster of active players for the specified team

`?expand=team.schedule.next` Returns details of the upcoming game for a team

`?expand=team.schedule.previous` Same as above but for the last game played
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "teams" : [ {
    "id" : 1,
    "name" : "New Jersey Devils",
    "link" : "/api/v1/teams/1",
    "venue" : {
      "name" : "Prudential Center",
      "link" : "/api/v1/venues/null",
      "city" : "Newark",
      "timeZone" : {
        "id" : "America/New_York",
        "offset" : -5,
        "tz" : "EST"
      }
    },
    "abbreviation" : "NJD",
    "teamName" : "Devils",
    "locationName" : "New Jersey",
    "firstYearOfPlay" : "1982",
    "division" : {
      "id" : 18,
      "name" : "Metropolitan",
      "link" : "/api/v1/divisions/18"
    },
    "conference" : {
      "id" : 6,
      "name" : "Eastern",
      "link" : "/api/v1/conferences/6"
    },
    "franchise" : {
      "franchiseId" : 23,
      "teamName" : "Devils",
      "link" : "/api/v1/franchises/23"
    },
    "shortName" : "New Jersey",
    "officialSiteUrl" : "http://www.truesince82.com",
    "franchiseId" : 23,
    "active" : true
  }, {
  ```

`GET https://statsapi.web.nhl.com/api/v1/teams/ID/roster` Returns entire roster for a team
including id value, name, jersey number and position details.

```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "roster" : [ {
    "person" : {
      "id" : 8477474,
      "fullName" : "Madison Bowey",
      "link" : "/api/v1/people/8477474"
    },
    "jerseyNumber" : "22",
    "position" : {
      "code" : "D",
      "name" : "Defenseman",
      "type" : "Defenseman",
      "abbreviation" : "D"
    }
  },```
---
### Divisions
`GET https://statsapi.web.nhl.com/api/v1/divisions`  Returns full list of divisions
and associated data like which conference they belong to, id values and API links.
Does not show inactive divisions

`GET https://statsapi.web.nhl.com/api/v1/divisions/ID` Same as above but only for a
single division. This can show old inactive divisions such as 13 Patrick.
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "divisions" : [ {
    "id" : 17,
    "name" : "Atlantic",
    "link" : "/api/v1/divisions/17",
    "abbreviation" : "A",
    "conference" : {
      "id" : 6,
      "name" : "Eastern",
      "link" : "/api/v1/conferences/6"
    },
    "active" : true
  },```
---
### Conferences
`GET https://statsapi.web.nhl.com/api/v1/conferences` Returns conference details
for all current NHL conferences.

`GET https://statsapi.web.nhl.com/api/v1/conferences/ID` Same as above but for
specific conference, also can look up id 7 for World Cup of Hockey.
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "conferences" : [ {
    "id" : 6,
    "name" : "Eastern",
    "link" : "/api/v1/conferences/6",
    "abbreviation" : "E",
    "shortName" : "East",
    "active" : true
  }, {
    "id" : 5,
    "name" : "Western",
    "link" : "/api/v1/conferences/5",
    "abbreviation" : "W",
    "shortName" : "West",
    "active" : true
  } ]
}```
---
### People
`GET https://statsapi.web.nhl.com/api/v1/people/ID` Gets details for a player, must
specify the id value in order to return data.
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "people" : [ {
    "id" : 8477474,
    "fullName" : "Madison Bowey",
    "link" : "/api/v1/people/8477474",
    "firstName" : "Madison",
    "lastName" : "Bowey",
    "primaryNumber" : "22",
    "birthDate" : "1995-04-22",
    "currentAge" : 22,
    "birthCity" : "Winnipeg",
    "birthStateProvince" : "MB",
    "birthCountry" : "CAN",
    "nationality" : "CAN",
    "height" : "6' 2\"",
    "weight" : 198,
    "active" : true,
    "alternateCaptain" : false,
    "captain" : false,
    "rookie" : true,
    "shootsCatches" : "R",
    "rosterStatus" : "Y",
    "currentTeam" : {
      "id" : 15,
      "name" : "Washington Capitals",
      "link" : "/api/v1/teams/15"
    },
    "primaryPosition" : {
      "code" : "D",
      "name" : "Defenseman",
      "type" : "Defenseman",
      "abbreviation" : "D"
    }
  } ]
}```
`GET https://statsapi.web.nhl.com/api/v1/people/ID/stats` Complex endpoint with
lots of append options to change what kind of stats you wish to obtain
#### Modifiers
`?stats=statsSingleSeason&season=19801981`  Obtains single season statistics
for a player

*note - stats have changed over the years, the below sample is for Wayne Gretzky
and does not include things like evenTimeOnIce and other time related stats*
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "statsSingleSeason"
    },
    "splits" : [ {
      "season" : "19801981",
      "stat" : {
        "assists" : 109,
        "goals" : 55,
        "pim" : 28,
        "shots" : 261,
        "games" : 80,
        "powerPlayGoals" : 15,
        "powerPlayPoints" : 53,
        "penaltyMinutes" : "28",
        "shotPct" : 21.07,
        "gameWinningGoals" : 3,
        "overTimeGoals" : 0,
        "shortHandedGoals" : 4,
        "shortHandedPoints" : 7,
        "plusMinus" : 41,
        "points" : 164
      }
    } ]
  } ]
}```

*however here is Alex Ovechkin's 20162017 season stats which include time information*

```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "statsSingleSeason"
    },
    "splits" : [ {
      "season" : "20162017",
      "stat" : {
        "timeOnIce" : "1506:01",
        "assists" : 36,
        "goals" : 33,
        "pim" : 50,
        "shots" : 313,
        "games" : 82,
        "hits" : 216,
        "powerPlayGoals" : 17,
        "powerPlayPoints" : 26,
        "powerPlayTimeOnIce" : "305:21",
        "evenTimeOnIce" : "1198:26",
        "penaltyMinutes" : "50",
        "faceOffPct" : 0.0,
        "shotPct" : 10.5,
        "gameWinningGoals" : 7,
        "overTimeGoals" : 2,
        "shortHandedGoals" : 0,
        "shortHandedPoints" : 0,
        "shortHandedTimeOnIce" : "02:14",
        "blocked" : 29,
        "plusMinus" : 6,
        "points" : 69,
        "shifts" : 1737,
        "timeOnIcePerGame" : "18:21",
        "evenTimeOnIcePerGame" : "14:36",
        "shortHandedTimeOnIcePerGame" : "00:01",
        "powerPlayTimeOnIcePerGame" : "03:43"
      }
    } ]
  } ]
}```
`?stats=homeAndAway&season=20162017` Provides a split between home and away games.
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "homeAndAway"
    },
    "splits" : [ {
      "season" : "20162017",
      "stat" : {
        "timeOnIce" : "751:09",
        "assists" : 18,
        "goals" : 20,
        "pim" : 26,
        "shots" : 163,
        "games" : 41,
        "hits" : 97,
        "powerPlayGoals" : 10,
        "powerPlayPoints" : 15,
        "powerPlayTimeOnIce" : "160:21",
        "evenTimeOnIce" : "590:34",
        "penaltyMinutes" : "26",
        "shotPct" : 0.0,
        "gameWinningGoals" : 6,
        "overTimeGoals" : 2,
        "shortHandedGoals" : 0,
        "shortHandedPoints" : 0,
        "shortHandedTimeOnIce" : "00:14",
        "blocked" : 12,
        "plusMinus" : 13,
        "points" : 38,
        "shifts" : 848,
        "timeOnIcePerGame" : "18:19",
        "evenTimeOnIcePerGame" : "14:24",
        "shortHandedTimeOnIcePerGame" : "00:00",
        "powerPlayTimeOnIcePerGame" : "03:54"
      },
      "isHome" : true
    }, {
      "season" : "20162017",
      "stat" : {
        "timeOnIce" : "754:52",
        "assists" : 18,
        "goals" : 13,
        "pim" : 24,
        "shots" : 150,
        "games" : 41,
        "hits" : 119,
        "powerPlayGoals" : 7,
        "powerPlayPoints" : 11,
        "powerPlayTimeOnIce" : "145:00",
        "evenTimeOnIce" : "607:52",
        "penaltyMinutes" : "24",
        "shotPct" : 0.0,
        "gameWinningGoals" : 1,
        "overTimeGoals" : 0,
        "shortHandedGoals" : 0,
        "shortHandedPoints" : 0,
        "shortHandedTimeOnIce" : "02:00",
        "blocked" : 17,
        "plusMinus" : -7,
        "points" : 31,
        "shifts" : 889,
        "timeOnIcePerGame" : "18:24",
        "evenTimeOnIcePerGame" : "14:49",
        "shortHandedTimeOnIcePerGame" : "00:02",
        "powerPlayTimeOnIcePerGame" : "03:32"
      },
      "isHome" : false
    } ]
  } ]
}```

`?stats=winLoss&season=20162017` Very similar to the previous modifier except it provides the W/L/OT split instead of Home and Away

`?stats=byMonth&season=20162017` Monthly split of stats

`?stats=byDayOfWeek&season=20162017` Split done by day of the week

`?stats=vsDivision&season=20162017` Division stats split

`?stats=vsConference&season=20162017` Conference stats split

`?stats=vsTeam&season=20162017` Conference stats split

`?stats=regularSeasonStatRankings&season=20162017` Returns where someone stands vs
the rest of the league for a specific regularSeasonStatRankings
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "regularSeasonStatRankings"
    },
    "splits" : [ {
      "season" : "20162017",
      "stat" : {
        "rankPowerPlayGoals" : "1st",
        "rankBlockedShots" : "405th",
        "rankAssists" : "51st",
        "rankShotPct" : "246th",
        "rankGoals" : "13th",
        "rankHits" : "19th",
        "rankPenaltyMinutes" : "111th",
        "rankShortHandedGoals" : "133rd",
        "rankPlusMinus" : "176th",
        "rankShots" : "2nd",
        "rankPoints" : "20th",
        "rankOvertimeGoals" : "9th",
        "rankGamesPlayed" : "1st"
      }
    } ]
  } ]
}```

`?stats=goalsByGameSituation&season=20162017` Shows number on when goals for a
player happened like how many in the shootout, how many in each period, etc.

```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "goalsByGameSituation"
    },
    "splits" : [ {
      "season" : "20162017",
      "stat" : {
        "goalsInFirstPeriod" : 8,
        "goalsInSecondPeriod" : 12,
        "goalsInThirdPeriod" : 11,
        "goalsInOvertime" : 2,
        "gameWinningGoals" : 7,
        "emptyNetGoals" : 0,
        "shootOutGoals" : 0,
        "shootOutShots" : 3,
        "goalsTrailingByOne" : 3,
        "goalsTrailingByTwo" : 3,
        "goalsTrailingByThreePlus" : 1,
        "goalsWhenTied" : 14,
        "goalsLeadingByOne" : 7,
        "goalsLeadingByTwo" : 4,
        "goalsLeadingByThreePlus" : 1,
        "penaltyGoals" : 0,
        "penaltyShots" : 0
      }
    } ]
  } ]
}```

`?stats=onPaceRegularSeason&season=20172018` This only works with the current
in-progress season and shows **projected** totals based on current onPaceRegularSeason
```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "onPaceRegularSeason"
    },
    "splits" : [ {
      "season" : "20172018",
      "stat" : {
        "timeOnIce" : "1598:04",
        "assists" : 34,
        "goals" : 52,
        "pim" : 32,
        "shots" : 362,
        "games" : 82,
        "hits" : 154,
        "powerPlayGoals" : 14,
        "powerPlayPoints" : 28,
        "powerPlayTimeOnIce" : "338:16",
        "evenTimeOnIce" : "1258:48",
        "penaltyMinutes" : "32",
        "faceOffPct" : 40.0,
        "shotPct" : 14.4,
        "gameWinningGoals" : 10,
        "overTimeGoals" : 6,
        "shortHandedGoals" : 0,
        "shortHandedPoints" : 0,
        "shortHandedTimeOnIce" : "01:00",
        "blocked" : 20,
        "plusMinus" : 24,
        "points" : 86,
        "shifts" : 1676,
        "timeOnIcePerGame" : "09:44",
        "evenTimeOnIcePerGame" : "07:40",
        "powerPlayTimeOnIcePerGame" : "02:03"
      }
    } ]
  } ]
}```


---
### Game
`GET https://statsapi.web.nhl.com/api/v1/game/ID/feed/live` Returns all data about
a specified game id including play data with on-ice coordinates and post-game
details like first, second and third stars and any details about shootouts.  The
data returned is simply too large at often over 30k lines and is best explored
with a JSON viewer.

`GET https://statsapi.web.nhl.com/api/v1/game/ID/boxscore` Returns far less detail
than `feed/live` and is much more suitable for post-game details including goals,
shots, PIMs, blocked, takeaways, giveaways and hits.
