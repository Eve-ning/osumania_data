# osu!mania data
I extracted osu!mania data from the osu! website for data analytics.

Most information about the data can be found in the following.

https://github.com/ppy/osu-api/wiki

## BEATMAPS
Only ranked & loved beatmaps are grabbed.

There are 3 entries per unique ranked beatmap.
- Half Time
- No Mod
- Double Time

You can tell them apart in the mods column.

These entries only vary in the ``difficultyrating`` from what I know.

```
"approved"             : "1",                   // 4 = loved, 3 = qualified, 2 = approved, 1 = ranked, 0 = pending, -1 = WIP, -2 = graveyard
"submit_date"          : "2013-05-15 11:32:26", // date submitted, in UTC
"approved_date"        : "2013-07-06 08:54:46", // date ranked, in UTC
"last_update"          : "2013-07-06 08:51:22", // last update date, in UTC. May be after approved_date if map was unranked and reranked.
"artist"               : "Luxion",
"beatmap_id"           : "252002",              // beatmap_id is per difficulty
"beatmapset_id"        : "93398",               // beatmapset_id groups difficulties into a set
"bpm"                  : "196",
"creator"              : "RikiH_",
"creator_id"           : "686209",
"difficultyrating"     : "5.744717597961426",   // The amount of stars the map would have ingame and on the website
"diff_aim"             : "2.7706098556518555",
"diff_speed"           : "2.9062750339508057",
"diff_size"            : "4",                   // Circle size value (CS)
"diff_overall"         : "8",                   // Overall difficulty (OD)
"diff_approach"        : "9",                   // Approach Rate (AR)
"diff_drain"           : "7",                   // Health drain (HP)
"hit_length"           : "114",                 // seconds from first note to last note not including breaks
"source"               : "BMS",
"genre_id"             : "2",                   // 0 = any, 1 = unspecified, 2 = video game, 3 = anime, 4 = rock, 5 = pop, 6 = other, 7 = novelty, 9 = hip hop, 10 = electronic, 13 = folk (note that there's no 8)
"language_id"          : "5",                   // 0 = any, 1 = other, 2 = english, 3 = japanese, 4 = chinese, 5 = instrumental, 6 = korean, 7 = french, 8 = german, 9 = swedish, 10 = spanish, 11 = italian
"title"                : "High-Priestess",      // song name
"total_length"         : "146",                 // seconds from first note to last note including breaks
"version"              : "Overkill",            // difficulty name
"file_md5"             : "c8f08438204abfcdd1a748ebfae67421",            
                                                // md5 hash of the beatmap
"mode"                 : "0",                   // game mode,
"tags"                 : "kloyd flower roxas",  // Beatmap tags separated by spaces.
"favourite_count"      : "140",                 // Number of times the beatmap was favourited. (americans: notice the ou!)
"rating"               : "9.44779",
"playcount"            : "94637",               // Number of times the beatmap was played
"passcount"            : "10599",               // Number of times the beatmap was passed, completed (the user didn't fail or retry)
"count_normal"         : "388",
"count_slider"         : "222",
"count_spinner"        : "3",
"max_combo"            : "899",                 // The maximum combo a user can reach playing this beatmap.
"storyboard"           : "0",                   // If this beatmap has a storyboard
"video"                : "0",                   // If this beatmap has a video
"download_unavailable" : "0",                   // If the download for this beatmap is unavailable (old map, etc.)
"audio_unavailable"    : "0"                    // If the audio for this beatmap is unavailable (DMCA takedown, etc.)

```

## SCORES
Only ranked & loved beatmaps are grabbed.

Only the top 100 scores are grabbed, hence note the following:
- The top 100 may not be all No Mod
- ``enabled_mods`` define the mods used
- Loved scores do not have pp

```
"score_id"         : "7654321",
"score"            : "1234567",
"username"         : "User name",
"count300"         : "300",
"count100"         : "50",
"count50"          : "10",
"countmiss"        : "1",
"maxcombo"         : "421",
"countkatu"        : "10",
"countgeki"        : "50",
"perfect"          : "0",          // 1 = maximum combo of map reached, 0 otherwise
"enabled_mods"     : "76",         // bitwise flag representation of mods used. see reference
"user_id"          : "1",
"date"             : "2013-06-22 9:11:16", // in UTC
"rank"             : "SH",
"pp"               : "1.3019",        //Float value , 4 decimals
"replay_available" : "1"              // 1 = replay is available for download, 0 = replay is unavailable
```

## SAMPLING (2500)
In every data set, there's a sampleset for 2500 randomly selected.

Hence:
- `SCORES_2500` may not have `beatmap_id` that match `BEATMAPS_2500`.
- Entries of `BEATMAPS_2500` may not include all 3 variations.
- Top 100 of a single beatmap is never guaranteed.

## MODS

Reference: https://github.com/ppy/osu-api/wiki

```
enum Mods
{
    None           = 0,
    NoFail         = 1,
    Easy           = 2,
    Hidden         = 8,
    HardRock       = 16,
    SuddenDeath    = 32,
    DoubleTime     = 64,
    HalfTime       = 256,
    Nightcore      = 512, // Only set along with DoubleTime. i.e: NC only gives 576
    Flashlight     = 1024,
    Perfect        = 16384, // Only set along with SuddenDeath. i.e: PF only gives 16416  
    FadeIn         = 1048576,
    Mirror         = 1073741824,
}
```

## ACKNOWLEDGEMENTS

API is supported here: https://github.com/ppy/osu-api/wiki


