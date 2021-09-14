# ECStats_api_docs

Official documentation for Echo VR's unofficial Combat Stat Tracker.

## Summary

Echo Combat Stats (ECStats) has a public API available from their website. If a user query is `http://ecranked.ddns.net/user/Timemaster111/stats` then the API query is `http://ecranked.ddns.net/user/Timemaster111/stats.json`.

Similarly, a game/replay query is `http://ecranked.ddns.net/replay/5D833913-11FA-4A1E-8E33-4CB9A173C201` and the API is from `http://ecranked.ddns.net/replay/5D833913-11FA-4A1E-8E33-4CB9A173C201.json`.

## API Endpoints

The endpoints mirror the website, so the user endpoints are `/user/<USER>/stats.json` and the game/replay enpoints are `/replay/<REPLAY-ID>.json`.

### GET /user

#### Example Response
<pre>
{
  <a href="#average_speed">"about_string"</a>: "Developer of ECRanked",
  <a href="#average_speed">"average_speed"</a>: 1.6421,
  <a href="#average_ping">"average_ping"</a>: 64.626,
  <a href="#percent_stopped">"percent_stopped"</a>: 0.291188,
  <a href="#percent_upsidedown">"percent_upsidedown"</a>: 0.023962,
  <a href="#total_games">"total_games"</a>: 50,
  <a href="#total_deaths">"total_deaths"</a>: 344,
  <a href="#average_deaths">"average_deaths"</a>: 6.88,
  <a href="#discord_name">"discord_name"</a>: "BiffBish",
  <a href="#discord_pfp">"discord_pfp"</a>: "https://cdn.discordapp.com/avatars/301343234108424192/788a06ff1b8e6e324f879948081376e2.png",
  <a href="#loadout">"loadout"</a>: {
    "0": 0.000594,
    "1": 0.000045,
    "2": 0.0,
    ...
    "62": 0.400121,
    "63": 0.0
  },
  <a href="#top_loadout">"top_loadout"</a>: [
    [
      "33",
      0.396773
    ],
    [
      "35",
      0.291986
    ],
    [60 more...],
    [
      "62",
      0.0
    ],
    [
      "63",
      0.0
    ]
  ]
}
</pre>
#### `about_string`
The string that is used in the about me section.
- null - There is no about me string
#### `average_speed`
The average speed of the player measured in meters per second.

#### `average_ping`
The average ping of the player measured in milliseconds.

#### `percent_stopped`
The percentage of time the player is "stopped".

#### `percent_upsidedown`
The percentage of time the player is "upside-down".

#### `total_games`
The total number of games the player has played in.

#### `total_deaths`
The total number of times the player has died.

#### `average_deaths`
The average number of deaths per game.

#### `discord_name`
The discord username of the person if they have linked their discord account.
- null - The discord is not linked
#### `discord_pfp`
The discord profile picture of the person if they have linked their discord account.
- null - The discord is not linked
#### `loadout{}`
A dictionary of loadouts and percentage of frames they were in used in. The loadouts are stored via numbers in a <a href="#bitmaps"> bitmap </a>
#### `top_loadout[]`
A list of the persons top loadouts sorted from greatest to lowest
#### `top_loadout.[0]`
The loadout number in string form.
#### `top_loadout.[1]`
The percentage of time it has been used.
### GET /replay

#### Example Response

<pre>
{
  <a href="#frames">"frames"</a>: 19029,
  <a href="#start_time">"start_time"</a>: "2021-09-12 20:20:19.02",
  <a href="#end_time">"end_time"</a>: "2021-09-12 20:24:57.34",
  <a href="#match_length">"match_length"</a>: 278,
  <a href="#framerate">"framerate"</a>: 68.44964028776978,
  <a href="#map">"map"</a>: "surge",
  <a href="#players">"players"</a>: [
    {
      <a href="#playersteam">"team"</a>: 0,
      <a href="#playersplayerid">"playerid"</a>: 0,
      <a href="#playersname">"name"</a>: "GE0-_",
      <a href="#playersuserid">"userid"</a>: 2719646711436186,
      <a href="#playersnumber">"number"</a>: 22,
      <a href="#playerslevel">"level"</a>: 9,
      <a href="#playersstartFrame">"startFrame"</a>: 0,
      <a href="#playersstats">"stats"</a>: {
        <a href="#playersstatstotal_frames">"total_frames"</a>: 19029,
        <a href="#playersstatstotal_ping">"total_ping"</a>: 1797145,
        <a href="#playersstatstotal_speed">"total_speed"</a>: 42329.234783699496,
        <a href="#playersstatsframes_speed">"frames_speed"</a>: 15530,
        <a href="#playersstatstotal_upsidedown">"total_upsidedown"</a>: 10640,
        <a href="#playersstatsframes_upsidedown">"frames_upsidedown"</a>: 15530,
        <a href="#playersstatstotal_stopped">"total_stopped"</a>: 5289,
        <a href="#playersstatsframes_stopped">"frames_stopped"</a>: 15530,
        <a href="#playersstatstotal_deaths">"total_deaths"</a>: 3,
        <a href="#playersstatstotal_deaths">"loadout"</a>: {
          "0": 1012,
          "1": 18017,
          ...
          "62": 0,
          "63": 0
        },
        "frames_loadout": 19029
      }
    },
  [players.....]
  ]
}
</pre>

#### `frames`

Total number of frames the bot recorded from the game.

#### `start_time`

The time the bot started recording in GMT/UTC in ISO format.

#### `end_time`

The time the bot stopped recording in GMT/UTC in ISO format.

#### `match_length`

Number of seconds the match was recorded for.

#### `framerate`

The frames per second the bot recorded at.

#### `map`

The map the game was played on.

#### `players`

Players that were in the game.

#### `players{}.team`

Team the player was on.

- 0 - Team Blue(?)
- 1 - Team Orange(?)
- 2 - Spectator

#### `players[].playerid`

The player ID of the player.
- unique per game

#### `players[].name`
The name of the player.

#### `players[].userid`
The Oculus ID of the player.
#### `players[].number`
The number of the player.
- not unique


#### `players[].level`
The combat level of the player.

#### `players[].startFrame`
The frame the player joined the match.


#### `players[].stats`
Dictionary of statistics for the player for that game


#### `players[].stats{}.total_frames`
Total number of frames the player was in the game.

#### `players[].stats{}.total_ping`
Players ping added up for all total frames.

#### `players[].stats{}.total_speed`
Players speed (m/s) added up for tracked frames.

#### `players[].stats{}.frames_speed`
Number of frames the player is not in the spawn room and not traveling under 1m/s.


#### `players[].stats{}.total_upsidedown`
Number of frames the players head is flipped upside-down while tracked 

#### `players[].stats{}.frames_upsidedown`
Number of frames the player is not in the spawn room

#### `players[].stats{}.total_stopped`
Number of frames the player is traveling under 1m/s while tracked

#### `players[].stats{}.frames_stopped`
Number of frames the player is not in the spawn room

#### `players[].stats{}.total_deaths`
Number of deaths of the player


#### `players[].stats{}.loadout`
A dictionary of loadouts and how many frames they were in use. The loadouts are stored via numbers in a <a href="#bitmaps"> bitmap </a>





## Responses

### Success

On a success the API will return a JSON with the data.

### Fail

On a fail the API will return an error message along with a 404 status code. The error message is `There is no user with that username` for /user and `session id not found` for /replay

## Concepts

### Bitmaps

The loadouts are stored as bitmaps.

A bitmap is a set of bits where each bit or section of bits represents a value.

In the case of this API, the bitmap translates as follows:

| X              | 00     | 00             | 00             |
| -------------- | ------ | -------------- | -------------- |
| representation | weapon | ordnance       | tac mod        |
| 00             | Pulsar | Detonator      | Repair Matrix  |
| 01             | Nova   | Stun Field     | Threat Scanner |
| 10             | Comet  | Arc Mine       | Energy Barrier |
| 11             | Meteor | Instant Repair | Phase Shift    |

So a code of 010011 would be a Nova, Detonator and Phase Shift.

### Total and Frames

Total*\* refers to the total number of frames in which the stat (\*) has been tracked, and Frames*\* is the number of frames this stat is true for.
