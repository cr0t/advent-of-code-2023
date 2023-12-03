# Advent of Code 2023


Use [Livebook](https://livebook.dev/) server to run these `.livemd` files.

```console
$ livebook server
[Livebook] Application running at http://localhost:8080/?token=***
```

Open the given link and then `.livemd` file you want.

Input can be found in the similarly-named files.

## Solutions' Notes

[day01.livemd](day01.livemd)

- Part 1: Regex for digits only, take first and last, calculate
- Part 2: Regex for digits and words, convert all to digits, take first and last, calculate

[day02.livemd](day02.livemd)

- Shared: parse into a list of `{game_id, [sets]}` where `sets` is a list of `{n, color}`
- Part 1: check if game is possible – if all sets are possible; set is possible when all the items are possible (less than a max number of cuber of some color)
- Part 2: find a minimal set needed for each game, calculate

[day03.livemd](day03.livemd)

- Shared:
- Part 1:
- Part 2:
