# Controlled English (CE)

A rule set and a Claude skill for English text that people or agents act on: every sentence has exactly 1 meaning,
and every report says which of its claims were checked. CE is the English counterpart of
[Polszczyzna Kontrolowana (PK)](https://github.com/maciejszulia/polszczyzna-kontrolowana).

Version 0.2. Author: Maciej Szulia. Full standard: [`SKILL.md`](skills/controlled-english/SKILL.md).

## Why

English leaves the reader a choice at fixed places: what a pronoun points to, where a prepositional phrase attaches,
whether "or" excludes, where a range ends, whether "may" permits or predicts. CE closes each place with a convention.

| Sentence in plain English | Meanings | Sentence in CE |
|---|---|---|
| "Children up to 3 years old enter free." | younger than 3 years; younger than 4 years | "A child younger than 4 years enters free of charge." |
| "The valve is closed after work." | someone closes it; it is in the closed state; the reader has to close it | "The operator closes valve V1 after the work ends." |
| "Remove the cover with the screwdriver." | use the screwdriver; remove the cover that holds it | "Use screwdriver S1 to remove cover C1." |
| "If any test fails, stop. Any user can export." | at least 1; every | "If at least 1 test fails, stop. Every user MAY export." |
| "The fix should work now." | says nothing that a check could show false | a truth table: each claim with T, F or ? and its evidence |

## What the standard contains

- **Requirement keywords:** MUST, MUST NOT, SHOULD, SHOULD NOT, MAY, after RFC 2119 and RFC 8174.
- **Numbered rules in 5 groups:** A. Words, B. Sentence, C. Logic, D. Numbers, quantities, time, E. Text structure.
- **Module F for reports:** a source marker after every fact (`[measurement: ...]`, `[assumption]`).
- **Module T after Wittgenstein's *Tractatus*:** the truth-conditions of a request before work starts and the truth
  table of a claim before a report says "done". It folds in the skills `tractatus-sense` and `tractatus-verify` from
  [tractatus-skills](https://github.com/maciejszulia/tractatus-skills).
- **Module S for busy repositories:** patterns for claims, findings, test reports ("Tested `<head>` merged with `main`
  at `<sha>`"), pull request descriptions and review comments. Every statement about code names its commit, because
  `main` can change between 2 reads.
- **Banned words** with the reason and the replacement, for example "up to", "any", "unless", "and/or", "should work".
- **Control:** 8 steps after writing, including a word count script and the 2-meaning test.
- **Gap rule:** a missing number, date or actor is never guessed. The text keeps the marker `[TBD: what is missing]`.

## Use as a Claude skill

Copy `skills/controlled-english` into `~/.claude/skills/` (Claude Code) or upload it as a skill in claude.ai. The skill
starts when you ask to write, rewrite or check text "in CE", "precisely" or "without ambiguity", or type `/ce`.

## Limits

CE does not judge legal effects: a contract in CE still needs a lawyer. CE is not plain language (ISO 24495-1): plain
language serves easy understanding, CE serves a single meaning. Module T shows which claims were compared with reality;
it does not prove a claim true.

## License and author

MIT. Maciej Szulia.
