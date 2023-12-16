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

- **Gist:** find all the digits in the given list of strings (in part two digits could be spelled out with letters), take first and last, combine, summarize. Solved with Regex, but in the second part Regex is tricky as it has to find overlapping "digits", e.g., `oneight3` shall become `[1, 8, 3]`.
- **Part 1:** Regex for digits only, take first and last, calculate
- **Part 2:** Regex for digits and words, convert all to digits, take first and last, calculate

[day02.livemd](day02.livemd)

- **Gist:** take into consideration the given rules and map and reduce input according to them. The solution based on lists and operations on them (`all?/2`, `reduce/3`, etc.)
- **Shared:** parse into a list of `{game_id, [sets]}` where `sets` is a list of `{n, color}`
- **Part 1:** check if game is possible – if all sets are possible; set is possible when all the items are possible (less than a max number of cuber of some color)
- **Part 2:** find a minimal set needed for each game, calculate

[day03.livemd](day03.livemd)

- **Gist:** with a given map of symbols and numbers we must find ones that stand close to others and do the calculations with them.
- **Shared:** parse into a map of all coords, plus a list of numbers per line (via Regex that returns index and length), plus a few helpers (all neighbors for a given coord, `{start_x, len}` to coordinates generator, `{start_x, len}` to an integer converter)
- **Part 1:** find all adjacent (to a non-skippable symbol) numbers, convert, reduce
- **Part 2:** find all gear positions, filter only ones that neiboring to more than one digit (it's not a guarantee that it's neighbors with different numbers!), take numbers from relative rows to the gear, check if these numbers neighboring to the gear and filter them accordingly, convert these numbers, filter only results with two integers, calculate

[day04.livemd](day04.livemd)

- **Gist:** input consists of rules to be taken into consideration with the following calculations. The 2nd part trick is not to multiply the data, but collect number of copies of data to provide the final result.
- **Shared:** parse (with regex) into a map of `%{game_id: {winning_numbers, other_numbers}}`, `winning_numbers` and `other_numbers` represented by `MapSet` (to use its `intersection/2` function in the `wins/2` function that returns numbers of overlapping numbers from the given sets)
- **Part 1:** map over the games and find number of wins in each, calculate power of 2, sum
- **Part 2:** prepare a helper map `%{game_id: 1}` (`1` is the initial number of copies), go over the games (from 1st to the last) and reduce the `cards_copies` data on each step by adding number of copies to the current ones, sum numbers of copies in the end

[day05.livemd](day05.livemd)

- **Gist:** ranges involved, as well as big numbers (which will become very long ranges)
- **Shared:** parse to return input seeds list and map of maps (maps contain information about ranges), plus two helpers – `destination/2` (finds a corresponding value in a given map) and `find_lowest_location/2` (goes over maps in the predefined order and finds a final destination by reducing source+destination)
- **Part 1:** simply maps `find_lowest_location/2` over the input seeds and finds the minimal
- **Part 2:** splits the input ranges among a number of parallel processes and finds lowest locations in each piece of data, then finds the minimal. Uses `Stream` to avoid issues with the memory; with 64 workers used ~3800s on Core i7, and ~2070s on M3 Pro.
