# ECStats_api_docs

Official documentation for Echo VR's unofficial Combat Stat Tracker.

## Summary

Echo Combat Stats (ECStats) has a public API available from their website. If a user query is `http://ecranked.ddns.net/user/Timemaster111/stats` then the API query is `http://ecranked.ddns.net/user/Timemaster111/stats.json`.

Similarly, a game/replay query is `http://ecranked.ddns.net/replay/5D833913-11FA-4A1E-8E33-4CB9A173C201` and the API is from `http://ecranked.ddns.net/replay/5D833913-11FA-4A1E-8E33-4CB9A173C201.json`.

## API Endpoints

The endpoints mirror the website, so the user endpoints are `/user/<USER>/stats.json` and the game/replay enpoints are `/replay/<REPLAY-ID>.json`.

### GET /user

#### Example Response

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
  <a href="#players">"players"</a>: {
    "GE0-_": {
      <a href="#team">"team"</a>: 0,
      <a href="#playerid">"playerid"</a>: 0,
      <a href="#name">"name"</a>: "GE0-_",
      <a href="#userid">"userid"</a>: 2719646711436186,
      <a href="#number">"number"</a>: 22,
      <a href="#level">"level"</a>: 9,
      <a href="#startFrame">"startFrame"</a>: 0,
      <a href="#stats">"stats"</a>: {
        <a href="#total_frames">"total_frames"</a>: 19029,
        "total_ping": 1797145,
        "total_speed": 42329.234783699496,
        "frames_speed": 15530,
        "total_upsidedown": 10640,
        "frames_upsidedown": 15530,
        "total_stopped": 5289,
        "frames_stopped": 15530,
        "total_deaths": 3,
        "loadout": {
          "0": 0,
          "1": 0,
          "2": 0,
          "3": 0,
          "4": 0,
          "5": 0,
          "6": 0,
          "7": 19029,
          "8": 0,
          "9": 0,
          "10": 0,
          "11": 0,
          "12": 0,
          "13": 0,
          "14": 0,
          "15": 0,
          "16": 0,
          "17": 0,
          "18": 0,
          "19": 0,
          "20": 0,
          "21": 0,
          "22": 0,
          "23": 0,
          "24": 0,
          "25": 0,
          "26": 0,
          "27": 0,
          "28": 0,
          "29": 0,
          "30": 0,
          "31": 0,
          "32": 0,
          "33": 0,
          "34": 0,
          "35": 0,
          "36": 0,
          "37": 0,
          "38": 0,
          "39": 0,
          "40": 0,
          "41": 0,
          "42": 0,
          "43": 0,
          "44": 0,
          "45": 0,
          "46": 0,
          "47": 0,
          "48": 0,
          "49": 0,
          "50": 0,
          "51": 0,
          "52": 0,
          "53": 0,
          "54": 0,
          "55": 0,
          "56": 0,
          "57": 0,
          "58": 0,
          "59": 0,
          "60": 0,
          "61": 0,
          "62": 0,
          "63": 0
        },
        "frames_loadout": 19029
      }
    },
[players.....]
}
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

## Responses

### Success

On a success the API will return a JSON with the data.

### Fail

On a fail the API will return an error message. This is `There is no user with that username` for /user and `session id not found` for /replay

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
