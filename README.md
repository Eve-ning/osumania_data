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

## SCORES
Only ranked & loved beatmaps are grabbed.

Only the top 100 scores are grabbed, hence note the following:
- The top 100 may not be all No Mod
- ``enabled_mods`` define the mods used
- Loved scores do not have pp

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
