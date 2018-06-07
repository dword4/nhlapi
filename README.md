# New Location >> https://gitlab.com/dword4/nhlapi

**I will no longer be maintaining the repo at this(github) location but it will remain up for posterity sake, the above link will contain all future work on the documentation.**

# NHL API Documentation

All of this has been compiled and tested by hand in Jan of 2018, prior to this most of the information was spread across the internet in various posts and not available in a cohesive
single place.

[OpenAPI 3.0 specification file for the NHL API](https://github.com/erunion/sport-api-specifications/tree/master/nhl) thanks to @[erunion](https://github.com/erunion)

[Teams](#teams)

[Divisions](#divisions)

[Conferences](#conferences)

[People](#people)

[Game-IDs](#game-ids)

[Schedule](#schedule)

[Standings](#standings)

[Standings Types](#standings-types)

[Stats Types](#stats-types)

[Team Stats](#team-stats)

[Draft](#draft)

[Prospects](#prospects)

[Awards](#awards)

---

### <a name="teams"></a>Teams

`GET https://statsapi.web.nhl.com/api/v1/teams` Returns a list of data about
all teams including their id, venue details, division, conference and franchise information.

`GET https://statsapi.web.nhl.com/api/v1/teams/ID` Returns the same information as above just
for a single team instead of the entire league.
#### Modifiers
`?expand=team.roster` Shows roster of active players for the specified team 

`?expand=person.names` Same as above, but gives less info.

`?expand=team.schedule.next` Returns details of the upcoming game for a team

`?expand=team.schedule.previous` Same as above but for the last game played

`?expand=team.stats` Returns the teams stats for the season

`?expand=team.roster&season=20142015` Adding the season identifier shows the roster for that season

`?teamId=4,5,29` Can string team id together to get multiple teams

`?stats=statsSingleSeasonPlayoffs` Speciy which stats to get. Not fully sure all of the values

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
  },
```
---
### <a name="divisions"></a>Divisions
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
  },
```
---
### <a name="conferences"></a>Conferences
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
}
```
---
### <a name="people"></a>People
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
}
```
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
}
```

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
}
```
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
}
```

`?stats=winLoss&season=20162017` Very similar to the previous modifier except it provides the W/L/OT split instead of Home and Away

`?stats=byMonth&season=20162017` Monthly split of stats

`?stats=byDayOfWeek&season=20162017` Split done by day of the week

`?stats=vsDivision&season=20162017` Division stats split

`?stats=vsConference&season=20162017` Conference stats split

`?stats=vsTeam&season=20162017` Conference stats split

`?stats=gameLog&season=20162017` Provides a game log showing stats for each game of a season

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
}
```

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
}
```

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
}
```

---
### <a name="game"></a>Game
`GET https://statsapi.web.nhl.com/api/v1/game/ID/feed/live` Returns all data about
a specified game id including play data with on-ice coordinates and post-game
details like first, second and third stars and any details about shootouts.  The
data returned is simply too large at often over 30k lines and is best explored
with a JSON viewer.

`GET https://statsapi.web.nhl.com/api/v1/game/ID/boxscore` Returns far less detail
than `feed/live` and is much more suitable for post-game details including goals,
shots, PIMs, blocked, takeaways, giveaways and hits.

`GET http://statsapi.web.nhl.com/api/v1/game/ID/content` Complex endpoint returning
multiple types of media relating to the game including videos of shots, goals and saves.

`GET https://statsapi.web.nhl.com/api/v1/game/ID/feed/live/diffPatch?startTimecode=yyyymmdd_hhmmss`
Returns updates (like new play events, updated stats for boxscore, etc.) for the specified game ID
since the given startTimecode. If the startTimecode param is missing, returns an empty array.

#### <a name="game-ids">Game IDs
The first 4 digits identify the season of the game (ie. 2017 for the 2017-2018 season). The next 2 digits give the type of game, where 01 = preseason, 02 = regular season, 03 = playoffs, 04 = all-star. The final 4 digits identify the specific game number. For regular season and preseason games, this ranges from 0001 to the number of games played. (1271 for seasons with 31 teams (2017 and onwards) and 1230 for seasons with 30 teams). For playoff games, the 2nd digit of the specific number gives the round of the playoffs, the 3rd digit specifies the matchup, and the 4th digit specifies the game (out of 7).

---
### <a name="schedule">Schedule

`GET https://statsapi.web.nhl.com/api/v1/schedule` Returns a list of data about the schedule for a specified date range. If no date range is specified, returns results from the current day.

#### Modifiers
`?expand=schedule.broadcasts` Shows the broadcasts of the game

`?expand=schedule.linescore` Linescore for completed games

`?expand=schedule.ticket` Provides the different places to buy tickets for the upcoming games

`?teamId=30` Limit results to a specific team. Team ids can be found through the teams endpoint

`?date=2018-01-09` Single defined date for the search

`?startDate=2018-01-09` Start date for the search

`?endDate=2018-01-12` End date for the search

`GET https://statsapi.web.nhl.com/api/v1/schedule?teamId=30` Returns Minnesota Wild games for the current day.

```
{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "totalItems" : 1,
  "totalEvents" : 0,
  "totalGames" : 1,
  "totalMatches" : 0,
  "wait" : 10,
  "dates" : [ {
    "date" : "2018-01-09",
    "totalItems" : 1,
    "totalEvents" : 0,
    "totalGames" : 1,
    "totalMatches" : 0,
    "games" : [ {
      "gamePk" : 2017020659,
      "link" : "/api/v1/game/2017020659/feed/live",
      "gameType" : "R",
      "season" : "20172018",
      "gameDate" : "2018-01-10T01:00:00Z",
      "status" : {
        "abstractGameState" : "Preview",
        "codedGameState" : "1",
        "detailedState" : "Scheduled",
        "statusCode" : "1",
        "startTimeTBD" : false
      },
      "teams" : {
        "away" : {
          "leagueRecord" : {
            "wins" : 21,
            "losses" : 16,
            "ot" : 4,
            "type" : "league"
          },
          "score" : 0,
          "team" : {
            "id" : 20,
            "name" : "Calgary Flames",
            "link" : "/api/v1/teams/20"
          }
        },
        "home" : {
          "leagueRecord" : {
            "wins" : 22,
            "losses" : 17,
            "ot" : 3,
            "type" : "league"
          },
          "score" : 0,
          "team" : {
            "id" : 30,
            "name" : "Minnesota Wild",
            "link" : "/api/v1/teams/30"
          }
        }
      },
      "venue" : {
        "name" : "Xcel Energy Center",
        "link" : "/api/v1/venues/null"
      },
      "content" : {
        "link" : "/api/v1/game/2017020659/content"
      }
    } ],
    "events" : [ ],
    "matches" : [ ]
  } ]
}
```

`GET https://statsapi.web.nhl.com/api/v1/schedule?teamId=30&startDate=2018-01-02&endDate=2018-01-02` Returns Minnesota Wild games for January 2, 2018 with attached linescores and broadcasts.

```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "totalItems" : 1,
  "totalEvents" : 0,
  "totalGames" : 1,
  "totalMatches" : 0,
  "wait" : 10,
  "dates" : [ {
    "date" : "2018-01-02",
    "totalItems" : 1,
    "totalEvents" : 0,
    "totalGames" : 1,
    "totalMatches" : 0,
    "games" : [ {
      "gamePk" : 2017020608,
      "link" : "/api/v1/game/2017020608/feed/live",
      "gameType" : "R",
      "season" : "20172018",
      "gameDate" : "2018-01-03T01:00:00Z",
      "status" : {
        "abstractGameState" : "Final",
        "codedGameState" : "7",
        "detailedState" : "Final",
        "statusCode" : "7",
        "startTimeTBD" : false
      },
      "teams" : {
        "away" : {
          "leagueRecord" : {
            "wins" : 17,
            "losses" : 17,
            "ot" : 5,
            "type" : "league"
          },
          "score" : 1,
          "team" : {
            "id" : 13,
            "name" : "Florida Panthers",
            "link" : "/api/v1/teams/13"
          }
        },
        "home" : {
          "leagueRecord" : {
            "wins" : 21,
            "losses" : 16,
            "ot" : 3,
            "type" : "league"
          },
          "score" : 5,
          "team" : {
            "id" : 30,
            "name" : "Minnesota Wild",
            "link" : "/api/v1/teams/30"
          }
        }
      },
      "linescore" : {
        "currentPeriod" : 3,
        "currentPeriodOrdinal" : "3rd",
        "currentPeriodTimeRemaining" : "Final",
        "periods" : [ {
          "periodType" : "REGULAR",
          "startTime" : "2018-01-03T01:08:44Z",
          "endTime" : "2018-01-03T01:44:06Z",
          "num" : 1,
          "ordinalNum" : "1st",
          "home" : {
            "goals" : 1,
            "shotsOnGoal" : 13,
            "rinkSide" : "right"
          },
          "away" : {
            "goals" : 0,
            "shotsOnGoal" : 9,
            "rinkSide" : "left"
          }
        }, {
          "periodType" : "REGULAR",
          "startTime" : "2018-01-03T02:03:03Z",
          "endTime" : "2018-01-03T02:48:52Z",
          "num" : 2,
          "ordinalNum" : "2nd",
          "home" : {
            "goals" : 3,
            "shotsOnGoal" : 19,
            "rinkSide" : "left"
          },
          "away" : {
            "goals" : 0,
            "shotsOnGoal" : 2,
            "rinkSide" : "right"
          }
        }, {
          "periodType" : "REGULAR",
          "startTime" : "2018-01-03T03:07:33Z",
          "endTime" : "2018-01-03T03:43:39Z",
          "num" : 3,
          "ordinalNum" : "3rd",
          "home" : {
            "goals" : 1,
            "shotsOnGoal" : 9,
            "rinkSide" : "right"
          },
          "away" : {
            "goals" : 1,
            "shotsOnGoal" : 15,
            "rinkSide" : "left"
          }
        } ],
        "shootoutInfo" : {
          "away" : {
            "scores" : 0,
            "attempts" : 0
          },
          "home" : {
            "scores" : 0,
            "attempts" : 0
          }
        },
        "teams" : {
          "home" : {
            "team" : {
              "id" : 30,
              "name" : "Minnesota Wild",
              "link" : "/api/v1/teams/30"
            },
            "goals" : 5,
            "shotsOnGoal" : 41,
            "goaliePulled" : false,
            "numSkaters" : 5,
            "powerPlay" : false
          },
          "away" : {
            "team" : {
              "id" : 13,
              "name" : "Florida Panthers",
              "link" : "/api/v1/teams/13"
            },
            "goals" : 1,
            "shotsOnGoal" : 26,
            "goaliePulled" : false,
            "numSkaters" : 5,
            "powerPlay" : false
          }
        },
        "powerPlayStrength" : "Even",
        "hasShootout" : false,
        "intermissionInfo" : {
          "intermissionTimeRemaining" : 0,
          "intermissionTimeElapsed" : 0,
          "inIntermission" : false
        },
        "powerPlayInfo" : {
          "situationTimeRemaining" : 0,
          "situationTimeElapsed" : 0,
          "inSituation" : false
        }
      },
      "venue" : {
        "name" : "Xcel Energy Center",
        "link" : "/api/v1/venues/null"
      },
      "broadcasts" : [ {
        "id" : 14,
        "name" : "FS-N",
        "type" : "home",
        "site" : "nhl",
        "language" : "en"
      }, {
        "id" : 12,
        "name" : "FS-F",
        "type" : "away",
        "site" : "nhl",
        "language" : "en"
      } ],
      "content" : {
        "link" : "/api/v1/game/2017020608/content"
      }
    } ],
    "events" : [ ],
    "matches" : [ ]
  } ]
}
```

---
### <a name="standings">Standings

`GET https://statsapi.web.nhl.com/api/v1/standings` Returns ordered standings data
for each team broken up by divisions

```
{
  "team" : {
    "id" : 52,
    "name" : "Winnipeg Jets",
    "link" : "/api/v1/teams/52"
  },
  "leagueRecord" : {
    "wins" : 37,
    "losses" : 17,
    "ot" : 9,
    "type" : "league"
  },
  "goalsAgainst" : 170,
  "goalsScored" : 213,
  "points" : 83,
  "divisionRank" : "2",
  "conferenceRank" : "3",
  "leagueRank" : "6",
  "wildCardRank" : "0",
  "row" : 35,
  "gamesPlayed" : 63,
  "streak" : {
    "streakType" : "losses",
    "streakNumber" : 1,
    "streakCode" : "L1"
  },
}
```

#### Modifiers
`?season=20032004` Standings for a specified season

`?date=2018-01-09` Standings on a specified date

`?expand=standings.record` Detailed information for each team including home and away records, record in shootouts, last ten games, and split head-to-head records against divisions and conferences

```
{
  "records" : {
    "divisionRecords" : [ {
      "wins" : 11,
      "losses" : 7,
      "ot" : 2,
      "type" : "Central"
    }, {
      "wins" : 5,
      "losses" : 3,
      "ot" : 3,
      "type" : "Atlantic"
    }, {
      "wins" : 15,
      "losses" : 4,
      "ot" : 2,
      "type" : "Pacific"
    }, {
      "wins" : 6,
      "losses" : 3,
      "ot" : 2,
      "type" : "Metropolitan"
    } ],
    "overallRecords" : [ {
      "wins" : 23,
      "losses" : 7,
      "ot" : 2,
      "type" : "home"
    }, {
      "wins" : 14,
      "losses" : 10,
      "ot" : 7,
      "type" : "away"
    }, {
      "wins" : 2,
      "losses" : 2,
      "type" : "shootOuts"
    }, {
      "wins" : 6,
      "losses" : 4,
      "ot" : 0,
      "type" : "lastTen"
    } ],
    "conferenceRecords" : [ {
      "wins" : 11,
      "losses" : 6,
      "ot" : 5,
      "type" : "Eastern"
    }, {
      "wins" : 26,
      "losses" : 11,
      "ot" : 4,
      "type" : "Western"
    } ]
  }
}
```
---

### <a name="standings-types">Standings Types

`GET https://statsapi.web.nhl.com/api/v1/standingsTypes` Returns all the standings types
to be used in order do get a specific standings

```{
[ {
  "name" : "regularSeason",
  "description" : "Regular Season Standings"
}, {
  "name" : "wildCard",
  "description" : "Wild card standings"
}, {
  "name" : "divisionLeaders",
  "description" : "Division Leader standings"
}, {
  "name" : "wildCardWithLeaders",
  "description" : "Wild card standings with Division Leaders"
}, {
  "name" : "preseason",
  "description" : "Preseason Standings"
}, {
  "name" : "postseason",
  "description" : "Postseason Standings"
}, {
  "name" : "byDivision",
  "description" : "Standings by Division"
}, {
  "name" : "byConference",
  "description" : "Standings by Conference"
}, {
  "name" : "byLeague",
  "description" : "Standings by League"
} ]
```
Ex: https://statsapi.web.nhl.com/api/v1/standings/wildCardWithLeaders?date=2018-01-16

Returns the complete wildcard (with leaders) standings on 01/16/2018.

---

### <a name="stats-types">Stats Types

`GET https://statsapi.web.nhl.com/api/v1/statTypes` Returns all the stats types
to be used in order do get a specific kind of player stats

---

### <a name="team-stats">Team Stats

`GET https://statsapi.web.nhl.com/api/v1/teams/5/stats` Returns current season stats and the current season rankings for a specific team

Ex:

```{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "stats" : [ {
    "type" : {
      "displayName" : "statsSingleSeason"
    },
    "splits" : [ {
      "stat" : {
        "gamesPlayed" : 46,
        "wins" : 24,
        "losses" : 19,
        "ot" : 3,
        "pts" : 51,
        "ptPctg" : "55.4",
        "goalsPerGame" : 2.891,
        "goalsAgainstPerGame" : 3.043,
        "evGGARatio" : 0.6602,
        "powerPlayPercentage" : "26.5",
        "powerPlayGoals" : 43.0,
        "powerPlayGoalsAgainst" : 28.0,
        "powerPlayOpportunities" : 162.0,
        "penaltyKillPercentage" : "82.6",
        "shotsPerGame" : 34.7174,
        "shotsAllowed" : 30.3043,
        "winScoreFirst" : 0.76,
        "winOppScoreFirst" : 0.238,
        "winLeadFirstPer" : 0.857,
        "winLeadSecondPer" : 1.0,
        "winOutshootOpp" : 0.6,
        "winOutshotByOpp" : 0.375,
        "faceOffsTaken" : 2889.0,
        "faceOffsWon" : 1474.0,
        "faceOffsLost" : 1415.0,
        "faceOffWinPercentage" : "51.0",
        "shootingPctg" : 8.3,
        "savePctg" : 0.9
      },
      "team" : {
        "id" : 5,
        "name" : "Pittsburgh Penguins",
        "link" : "/api/v1/teams/5"
      }
    } ]
  }, {
    "type" : {
      "displayName" : "regularSeasonStatRankings"
    },
    "splits" : [ {
      "stat" : {
        "wins" : "15th",
        "losses" : "25th",
        "ot" : "30th",
        "pts" : "17th",
        "ptPctg" : "21st",
        "goalsPerGame" : "15th",
        "goalsAgainstPerGame" : "22nd",
        "evGGARatio" : "30th",
        "powerPlayPercentage" : "1st",
        "powerPlayGoals" : "1st",
        "powerPlayGoalsAgainst" : "17th",
        "powerPlayOpportunities" : "4th",
        "penaltyKillOpportunities" : "28th",
        "penaltyKillPercentage" : "10th",
        "shotsPerGame" : "1st",
        "shotsAllowed" : "5th",
        "winScoreFirst" : "8th",
        "winOppScoreFirst" : "24th",
        "winLeadFirstPer" : "10th",
        "winLeadSecondPer" : "1st",
        "winOutshootOpp" : "6th",
        "winOutshotByOpp" : "6th",
        "faceOffsTaken" : "1st",
        "faceOffsWon" : "3rd",
        "faceOffsLost" : "24th",
        "faceOffWinPercentage" : "12th",
        "savePctRank" : "25th",
        "shootingPctRank" : "24th"
      },
      "team" : {
        "id" : 5,
        "name" : "Pittsburgh Penguins",
        "link" : "/api/v1/teams/5"
      }
    } ]
  } ]
}
```

---

### <a name="draft">Draft

`GET https://statsapi.web.nhl.com/api/v1/draft` Get round-by-round data for current year's NHL Entry Draft.

`GET https://statsapi.web.nhl.com/api/v1/draft/YEAR` Takes a YYYY format year and returns draft data

```{
  "copyright": "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "drafts": [{
    "draftYear": 2017,
    "rounds": [{
      "roundNumber": 1,
      "round": "1",
      "picks": [{
        "year": 2017,
        "round": "1",
        "pickOverall": 1,
        "pickInRound": 1,
        "team": {
          "id": 1,
          "name": "New Jersey Devils",
          "link": "/api/v1/teams/1"
        },
        "prospect": {
          "id": 65242,
          "fullName": "Nico Hischier",
          "link": "/api/v1/draft/prospects/65242"
        }
      },
```

### <a name="prospects">Prospects

`GET https://statsapi.web.nhl.com/api/v1/draft/prospects` Get all NHL Entry Draft prospects.

`GET https://statsapi.web.nhl.com/api/v1/draft/prospects/ID` Get an NHL Entry Draft prospect.

```json
{
  "copyright" : "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "prospects" : [ {
    "id" : 53727,
    "fullName" : "Zbynek Horak",
    "link" : "/api/v1/draft/prospects/53727",
    "firstName" : "Zbynek",
    "lastName" : "Horak",
    "birthDate" : "1995-03-08",
    "birthCountry" : "CZE",
    "height" : "5' 10\"",
    "weight" : 168,
    "shootsCatches" : "L",
    "primaryPosition" : {
      "code" : "L",
      "name" : "Left Wing",
      "type" : "Forward",
      "abbreviation" : "LW"
    },
    "draftStatus" : "Elig",
    "prospectCategory" : {
      "id" : 2,
      "shortName" : "Euro Skater",
      "name" : "European Skater"
    },
    "amateurTeam" : {
      "name" : "Znojmo Jr.",
      "link" : "/api/v1/teams/null"
    },
    "amateurLeague" : {
      "name" : "AUSTRIA-JR.",
      "link" : "/api/v1/league/null"
    },
    "ranks" : { }
  } ]
}
```

### <a name="awards">Awards

`GET https://statsapi.web.nhl.com/api/v1/awards` Get all NHL Awards.

`GET https://statsapi.web.nhl.com/api/v1/awards/ID` Get an NHL Award.

```json
{
  "copyright": "NHL and the NHL Shield are registered trademarks of the National Hockey League. NHL and NHL team marks are the property of the NHL and its teams. © NHL 2018. All Rights Reserved.",
  "awards": [ {
    "name": "Stanley Cup",
    "shortName": "The Cup",
    "description": "History: The Stanley Cup, the oldest trophy competed for by professional athletes in North America, was donated by Frederick Arthur, Lord Stanley of Preston and son of the Earl of Derby, in 1893. Lord Stanley purchased the trophy for 10 guineas ($50 at that time) for presentation to the amateur hockey champions of Canada. Since 1906, when Canadian teams began to pay their players openly, the Stanley Cup has been the symbol of professional hockey supremacy. It has been contested only by NHL teams since 1926-27 and has been under the exclusive control of the NHL since 1947.",
    "recipientType": "Team",
    "history": "It all started on March 18, 1892, at a dinner of the Ottawa Amateur Athletic Association. Lord Kilcoursie, a player on the Ottawa Rebels hockey club from Government House, delivered the following message on behalf of Lord Stanley, the Earl of Preston and Governor General of Canada  -- &quot;I have for some time been thinking that it would be a good thing if there were a challenge cup which should be held from year to year by the champion hockey team in the Dominion (of Canada).  There does not appear to be any such outward sign of a championship at present, and considering the general interest which matches now elicit, and the importance of having the game played fairly and under rules generally recognized, I am willing to give a cup which shall be held from year to year by the winning team.&quot; --  Shortly thereafter, Lord Stanley purchased a silver cup measuring 7.5 inches high by 11.5 inches across for the sum of 10 guineas (approximately $50); appointed two Ottawa gentlemen, Sheriff John Sweetland and Philip D. Ross, as trustees of that cup.  The first winner of the Stanley Cup was the Montreal Amateur Athletic Association (AAA) hockey club, champions of the Amateur Hockey Association of Canada for 1893. Ironically, Lord Stanley never witnessed a championship game nor attended a presentation of his trophy, having returned to his native England in the midst of the 1893 season. Nevertheless, the quest for his trophy has become one of the worlds most prestigious sporting competitions.",
    "imageUrl": "http://3.cdn.nhle.com/nhl/images/upload/2017/09/Stanley-Cup.jpg",
    "homePageUrl": "http://www.nhl.com/cup/index.html",
    "link": "/api/v1/awards/1"
  }]
}
```
