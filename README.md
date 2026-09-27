# Number Guessing Game

A command-line number guessing game written in Bash, backed by a PostgreSQL database that remembers every player's games and best score. Developed in a Git repository using conventional commits.

## Tech used

Bash · PostgreSQL · SQL · Git

## Files

| File | Description |
|---|---|
| `number_guess.sh` | The game script |
| `number_guess.sql` | Database dump to rebuild the database |

## How it works

1. The game picks a random number between 1 and 1000
2. The player enters a username
3. Returning players see how many games they've played and their best score
4. The player guesses, getting "higher" or "lower" hints after each try
5. Non-numeric input is caught and the player is asked to try again
6. When the number is guessed, the game is saved to the database

## Database structure

| Table | Description |
|---|---|
| `users` | Each player, with a unique username (up to 22 characters) |
| `games` | Each finished game, linked to a user, with the number of guesses |

Games played and best score are calculated with `COUNT` and `MIN` rather than stored separately.

## Example

```
Enter your username:
marija
Welcome, marija! It looks like this is your first time here.
Guess the secret number between 1 and 1000:
500
It's lower than that, guess again:
250
It's higher than that, guess again:
...
You guessed it in 9 tries. The secret number was 312. Nice job!
```

## How to run it

```bash
psql -U postgres < number_guess.sql
./number_guess.sh
```

## What I learned

- Loops, conditionals and arithmetic in Bash
- Generating random numbers with `$RANDOM`
- Input validation with regular expressions
- Storing raw data and calculating statistics with SQL
- Committing work in small, well-described steps with Git
