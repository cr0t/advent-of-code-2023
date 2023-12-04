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

- **Part 1:** Regex for digits only, take first and last, calculate
- **Part 2:** Regex for digits and words, convert all to digits, take first and last, calculate

[day02.livemd](day02.livemd)

- **Shared:** parse into a list of `{game_id, [sets]}` where `sets` is a list of `{n, color}`
- **Part 1:** check if game is possible – if all sets are possible; set is possible when all the items are possible (less than a max number of cuber of some color)
- **Part 2:** find a minimal set needed for each game, calculate

[day03.livemd](day03.livemd)

- **Shared:** parse into a map of all coords, plus a list of numbers per line (via Regex that returns index and length), plus a few helpers (all neighbors for a given coord, `{start_x, len}` to coordinates generator, `{start_x, len}` to an integer converter)
- **Part 1:** find all adjacent (to a non-skippable symbol) numbers, convert, reduce
- **Part 2:** find all gear positions, filter only ones that neiboring to more than one digit (it's not a guarantee that it's neighbors with different numbers!), take numbers from relative rows to the gear, check if these numbers neighboring to the gear and filter them accordingly, convert these numbers, filter only results with two integers, calculate

[day04.livemd](day04.livemd)

- **Shared:** parse (with regex) into a map of `%{game_id: {winning_numbers, other_numbers}}`, `winning_numbers` and `other_numbers` represented by `MapSet` (to use its `intersection/2` function in the `wins/2` function that returns numbers of overlapping numbers from the given sets)
- **Part 1:** map over the games and find number of wins in each, calculate power of 2, sum
- **Part 2:** prepare a helper map `%{game_id: 1}` (`1` is the initial number of copies), go over the games (from 1st to the last) and reduce the `cards_copies` data on each step by adding number of copies to the current ones, sum numbers of copies in the end
