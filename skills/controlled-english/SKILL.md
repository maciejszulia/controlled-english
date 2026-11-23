---
name: controlled-english
description: "Controlled English (CE) — controlled English that leaves every sentence exactly one meaning, with a Tractatus module that states the truth-conditions of a request and the truth table of a report. Use whenever you write, rewrite or audit English text that people or agents will act on (instructions, procedures, rules, requirements, specifications, contracts, technical reports, pull request descriptions, findings, handoffs) and whenever the user says \"write precisely\", \"unambiguous\", \"remove ambiguity\", \"check if this is unambiguous\", \"controlled English\", \"write in CE\", \"check in CE\" or \"/ce\". Not for fiction, marketing copy or casual chat. For Polish text use Polszczyzna Kontrolowana (PK)."
---

# Controlled English (CE) 0.1

CE is plain English plus a set of rules. Each rule removes one source of sentences that have more than 1 meaning.
A reader who knows the conventions reads each sentence in exactly 1 way.

English grammar leaves the reader a choice at fixed places: what a pronoun points to, where a prepositional phrase
attaches, whether "or" excludes, where a range ends, whether "may" permits or predicts. CE closes each place with a
convention. CE is the English counterpart of Polszczyzna Kontrolowana (PK). Its sentence limits follow ASD-STE100.
Module T adds two checks after Wittgenstein's *Tractatus*: the truth-conditions of a request before work starts, and
the truth table of a claim before a report says "done".

Use CE for text that someone acts on: instruction, procedure, rule, requirement, specification, contract, technical
report, pull request description, finding, handoff. Do not use CE for fiction, marketing or conversation.

## Modes

Choose the mode from the user's request.

| Mode | Request | Output |
|---|---|---|
| WRITE | "write the procedure", "write the spec" | New text in CE and a "Decisions and gaps" table. |
| REWRITE | "make this precise", "remove ambiguity" | The text in CE and a "Decisions and gaps" table. |
| CHECK | "check if this is unambiguous" | A violations table. The source text stays unchanged. |
| REPORT | "report the result", "is it done?" | The report in CE with the truth table of rule T4. |

Every mode follows 3 principles.

1. **Do not guess facts.** If a number, a boundary, an actor, an object or a date is missing, write the marker
   `[TBD: what is missing]`. A sentence with an invented number does more harm than a vague sentence, because the
   reader trusts the number.
2. **Do not choose a meaning silently.** If a source sentence has 2 meanings, record both in the "Decisions and gaps"
   table. If the choice changes an obligation, an amount, a deadline or safety, write a marker instead of choosing.
   Otherwise choose the meaning that agrees with the rest of the text and record the choice.
3. **Check the result.** After writing, do every step of the "Control" section. Count the words with the script.
   Do not replace counting with an estimate.

## Requirement keywords

Use these words in rules, requirements, specifications and contracts. They follow RFC 2119 and RFC 8174.

| Word | Meaning |
|---|---|
| MUST | A requirement without exceptions. |
| MUST NOT | A prohibition without exceptions. |
| SHOULD | A recommendation. A departure is allowed only for a valid reason and after the consequences are assessed. |
| SHOULD NOT | A discouragement. The action is allowed only for a valid reason and after the consequences are assessed. |
| MAY | A permission. The actor decides whether to act. |

- Write these words in capitals. Only the capital form has the meaning in the table. In CE, do not write "must",
  "should" or "may" in lower case.
- Do not use "will" for a requirement. "The system will log the error" is a prediction, a promise or a requirement.
  Write "The system MUST log the error" or state the fact: "The system logs the error."
- Do not write "need to", "have to", "is to be", "it is required". These forms hide the actor.
- Write a possibility as a condition: "If pump P1 runs dry, pump P1 overheats."
- Write a capability as a number: "Pump P1 delivers at most 40 L/min."
- In a step-by-step instruction, use the imperative instead of MUST.

## Rules

Every rule has an ID. Give the ID in the violations table and in the "Decisions and gaps" table.

### A. Words

**A1. One term, one meaning.** Name one concept with one term in the whole text. Do not use one term for 2 concepts.
The reader takes a new word for a new object.
- Wrong: "Close the valve. Check that the tap is tight."
- Right: "Close valve V1. Check that valve V1 is tight."

**A2. Object names.** "The filter" is ambiguous when the device has 2 filters. Give each object a unique name with an
identifier. For an object without a name, give the quantity: "each valve", "exactly 1 valve".
- Wrong: "Replace the filter." (the unit has 2 filters)
- Right: "Replace filter F2."

**A3. Pronouns.** Repeat the noun. Do not replace the noun with "it", "this", "that", "they", "them", "its" or
"their". Exception: "which", "that" or "who" directly after the noun it refers to. If a sentence names 2 people, replace
"his", "her" and "their" with the owner's name.
- Wrong: "Jan told Piotr that his pump leaks."
- Right: "Jan told Piotr that Piotr's pump leaks."

**A4. Definitions.** Use a word in its basic, common meaning. If at least 1 of these 3 cases applies, define the term
before its first use:
- the term has more than 1 meaning;
- the term has no measurable boundary;
- the term comes from a specialist language.

Pattern: `[term] means [kind] that [distinguishing feature]`. Do not use a defined term in another meaning.

**A5. Vague words.** Replace a vague word with a number and a unit, or with a condition the reader can check. The
section "Banned words" lists vague words.
- Wrong: "Check the pressure regularly."
- Right: "Check the pressure every 15 min."

**A6. Lists.** Name every element. Do not end a list with "etc.", "and so on" or "and others". If the list holds only
examples, write before it: "Examples (incomplete list):".

**A7. Abbreviations.** At first use, write the full name and give the abbreviation in parentheses.

**A8. One verb, one meaning.** Use each verb in 1 sense in the whole text: "check" means "verify", "run" means
"execute". Replace a phrasal verb whose meaning differs from its parts with a single verb: "set up" becomes "install"
or "configure", "carry out" becomes "do", "figure out" becomes "find".

**A9. "Any".** "Any" means "every" in one sentence and "at least 1" in another. Write "every" or "at least 1".
- Wrong: "If any test fails, stop the release." / "Any user can export the report."
- Right: "If at least 1 test fails, stop the release." / "Every user MAY export the report."

### B. Sentence

**B1. Actor.** Name the actor in every sentence about an action. Use the active voice. Use the passive voice only when
the actor is unknown.
- Wrong: "The valve is closed after work." (3 meanings: someone closes the valve; the valve is in the closed state;
  the reader has to close the valve)
- Right: "The operator closes valve V1 after the work ends."

**B2. Attachment.** Put a prepositional phrase next to the word it modifies. If the phrase can attach to 2 words, split
the sentence.
- Wrong: "Remove the cover with the screwdriver." (2 meanings: use the screwdriver; remove the cover that holds the
  screwdriver)
- Right: "Use screwdriver S1 to remove cover C1."

**B3. Instructions.** Write an instruction in the imperative. One sentence holds 1 command. For a repeated action, give
the interval and the duration: "Check the pressure every 15 min for 2 h."

**B4. Actions as verbs, short noun groups.** Name an action with a verb, not with a noun. Do not put more than 3 nouns in
a row.
- Wrong: "Perform validation of the input." / "the test result file path parser"
- Right: "Validate the input." / "the parser that reads the path of the test result file"

**B5. "-ing" clauses.** Do not open a sentence with an "-ing" or "-ed" clause. Such a clause hides the actor and the order
of the actions.
- Wrong: "While opening the valve, monitor the gauge." / "After opening the valve, the pressure rises."
- Right: "Open valve V1. At the same time, monitor gauge G1." / "The operator opens valve V1. Then the pressure rises."

**B6. Scope of a modifier.** Put a modifier directly next to the word it modifies. If the modifier fits 2 words, repeat
it or split the sentence.
- Wrong: "Replace old cables and wires." Right: "Replace old cables and old wires."

**B7. "Only".** Put "only" directly before the word it limits. Apply the same rule to "also" and "even".
- "Only the operator opens valve V1." (no other person opens valve V1)
- "The operator opens only valve V1." (the operator opens no other valve)

**B8. Length.** An instruction has at most 20 words. A description has at most 25 words. A paragraph has at most
6 sentences and 1 topic. A word is a string between spaces that contains at least 1 letter or digit.

### C. Logic

**C1. "Or" and "either ... or".** "Or" means at least 1 of the parts. "Either A or B" means exactly 1 of the parts. Do not
use "and/or", a slash or "alternatively" for this role.
- "Pay by card or in cash." (one payment MAY use both)
- "Choose either slot A or slot B." (the customer chooses exactly 1 slot)

**C2. "And" with "or".** Do not combine "and" with "or" in 1 sentence. "A and B or C" has 2 meanings: "(A and B) or C" and
"A and (B or C)". Use a list from rule E2.

**C3. Conditions.** Write the condition before the action. Use only 4 patterns:

| Pattern | Meaning |
|---|---|
| "If W, D." | Condition W is enough for D to apply. |
| "When E, D." | D starts at the moment of event E. |
| "While S, D." | D applies for the whole time of state S. |
| "Only if W, D." | D is allowed only when condition W holds. |

Order of the parts: state, event, actor, keyword, action. The EARS notation is the model for this order.
- Right: "While pump P1 runs, when pressure p1 exceeds 6.0 bar, the controller MUST stop pump P1."

If the opposite case needs an action, write it in a separate sentence: "If not W, D2." Do not write "unless", "in case",
"provided that", "as long as", "assuming", "once" (2 meanings: one time; as soon as) or "where" as a condition.

**C4. Negation with "all".** Do not combine "all", "every" or "each" with a negation.
- Wrong: "All valves are not closed." (2 meanings)
- Right: "No valve is closed." or "At least 1 valve is open."

**C5. One negation.** Write positive sentences. One sentence holds at most 1 negation.
- Wrong: "Do not open the valve until the pressure drops."
- Right: "When pressure p1 falls below 0.5 bar, open valve V1."

### D. Numbers, quantities, time

**D1. Quantity.** Give the number and the unit. If the value depends on conditions, give the reference conditions.
Write numbers in digits. Put a space between the number and the unit. Use a point for the decimal mark. Group the
digits of a long number in threes with a space, not with a comma: 26 503 (the SI rule).
- Exception: the angle symbols °, ′ and ″ follow the number directly, as in "37.25°".
- Wrong: "System pressure: 2.5." Right: "The gauge pressure in the system is 2.5 bar at a water temperature of 20 °C."

**D2. Boundaries and quantities.** Use only the forms in the table.

| Form | Meaning |
|---|---|
| each | every element without exception |
| no | 0 elements |
| exactly N | x = N |
| at least N | x ≥ N |
| at most N | x ≤ N |
| more than N | x > N |
| fewer than N, less than N | x < N |
| from A to B inclusive | A ≤ x ≤ B |
| no earlier than T | moment t ≥ T |
| no later than T | moment t ≤ T |
| before T | moment t < T |
| after T | moment t > T |

- Wrong: "Children up to 3 years old enter free." (2 meanings: younger than 3 years; younger than 4 years)
- Right: "A child younger than 4 years enters free of charge."

**D3. Dates and times.** Write a date as YYYY-MM-DD (ISO 8601) or with the month name: "23 November 2026". Write a time
in the 24-hour format HH:MM with the time zone: "16:00 CET", "15:00 UTC". Do not use words whose meaning depends on the
day of reading: "today", "tomorrow", "next week", "by Friday".
- Wrong: "Send the report by Friday."
- Right: "Send the report no later than 2026-11-27, 16:00 CET."

**D4. Deadlines and frequency.** For a deadline in days, give 3 facts: the start event, the number of days and which
day is day 1. Write a frequency as "every N units" or "N times per period". In CE, "day" means a calendar day. Call a
period of 24 h a "24-hour period".
- Wrong: "File the complaint within 14 days."
- Right: "File the complaint no later than day 14. Day 1 is the day after the delivery day."

**D5. Changes and comparisons.** Give the value before, the value after and the unit. Do not write "N times less".
Distinguish a percent from a percentage point.
- Wrong: "The price rose by 25 %."
- Right: "The price rose from 40 EUR to 50 EUR, that is by 10 EUR (25 %)."

**D6. Large numbers and approximations.** In CE, "billion" means 10^9. If the reader may use the long scale, write
10^9. Give "about" a tolerance: "50 m ± 5 m".

### E. Text structure

**E1. Steps.** One command takes 1 sentence and 1 step. If the order matters, number the steps. Write the expected
result as a fact after the step: "Result: lamp L1 is on."

**E2. Lists.** For at least 3 parts, use a vertical list. The lead-in names the logic:
- "Do every step in this order:"
- "Meet every condition:"
- "Meet at least 1 condition:"
- "Choose exactly 1 option:"

**E3. Warnings.** Put a warning before the step it applies to. Start the warning with a command or a condition, then
name the consequence.
- Right: "WARNING: Disconnect the power before you remove the cover. 230 V can kill." (here "can" names a
  consequence, not a permission; prefer "230 V causes a fatal shock" when the fact is certain)

**E4. References.** Refer by number or by name: "see step 4", "rule C1". Do not write "above", "below" or "as
mentioned".

**E5. Formulas.** Write each formula on 1 line. Below the formula, define every symbol and give its unit. In Markdown,
write formulas in LaTeX.

**E6. Legend.** A convention works only for a reader who knows it. If the reader does not know CE, add a legend at the
start. The legend lists only the conventions the text uses.

> Legend: "or" means at least 1 of the parts. "Either ... or" means exactly 1. MUST is a requirement. MUST NOT is a
> prohibition. SHOULD is a recommendation. MAY is a permission.

### F. Source of information (module for reports)

In a report, end every sentence about a fact with a source marker. The marker tells the reader how the author knows
the fact.

| Marker | Meaning |
|---|---|
| `[measurement: instrument, date, time]` | The author measured the value. |
| `[observation: date, time]` | The author saw the event or the state. |
| `[calculation: inputs]` | The author calculated the value. |
| `[source: document, page]` | The author copied the information from a document. |
| `[report: person, date]` | Another person gave the information to the author. |
| `[assumption]` | The author took the information without a check. |

Do not write "probably", "apparently", "likely", "seems" or "should work". Use a marker.
- Right: "The gauge pressure in the system is 2.5 bar `[measurement: gauge G1, 2026-11-10, 14:30 CET]`."

### T. Truth (module after Wittgenstein's *Tractatus*)

A sentence has sense when the reader knows what is the case if the sentence is true (*Tractatus* 4.024). A report is a
picture of reality; whether a picture is true cannot be seen from the picture alone (2.223, 2.224). Module T applies
this to requests, requirements and reports.

**T1. Truth-conditions of a request.** Before you write a requirement, or act on a request, list the elementary
propositions that are all true when it is fulfilled. Each proposition is observable and independent of the others
(4.21, 2.061). Done when every line can be answered yes or no by looking.
- Complex: "The app works."
- Elementary: "`npm test` exits 0 on main."

**T2. Excluded fulfilments.** List the results that satisfy the words and that the requester would still reject: the
cheap literal reading, the destructive shortcut, the right change in the wrong place, the extra scope. Turn each into a
negative condition: "and nothing outside folder X changes". When P is the set of results that satisfy the words and C
the set the requester wants, the work is safe only when P \ C is empty.

**T3. Open signs.** Mark every word of the request that signifies in 2 ways (3.323): "send", "remove", "publish",
"done", a name that matches 2 things. Settle each meaning from the context. Ask about each sign that stays open, with
1 question per sign and a proposed default.

**T4. Truth table of a claim.** Rewrite "done", "fixed", "deployed" or "sent" as the conjunction of elementary
propositions it asserts, each naming 1 observable state: "commit abc is on origin/main", "the endpoint returns 200".
Compare each proposition with reality by the check that could show it false: a command, a fetch, a read of the live
location. The plan, the diff, the author's own log and the report itself are pictures, not comparisons (5.1363).

| Proposition | T / F / ? | Evidence (command, URL, path) |
|---|---|---|

**T5. No tautologies.** A sentence that stays true whatever happens says nothing (4.461): "should work now", "handled
where possible", "improved stability". Rewrite the sentence as an elementary proposition with a check, or delete it.

**T6. Independent conjuncts.** From one elementary proposition no other follows (5.134). A green build does not make the
deploy healthy. A state measured at 14:00 is not a state at 15:00 (5.1361). Give each proposition its own check and its
own time.

**T7. Silence about the unchecked.** Mark a proposition that you could not compare with `?` and give the reason. Keep
it out of every "done" (7). The report says "done" only when every row of the truth table is T. Otherwise the report
names the F rows and the ? rows.

## Banned words

| Do not write | Reason | Write |
|---|---|---|
| appropriate, suitable, proper, adequate, sufficient | no criterion | a condition the reader can check |
| promptly, soon, quickly, ASAP, in due course | no time | "in less than N" or a date with a time |
| regularly, periodically, often, rarely, usually | no frequency | "every N units" |
| several, a few, many, most, numerous, some | no number | a number |
| large, small, high, low, long, short, fast, slow | no measure | a number with a unit |
| about, approximately, around, roughly, nearly | no tolerance | value ± tolerance |
| up to, over, under, between, within, until, max, min (as a boundary) | boundary included or excluded | a form from rule D2 |
| today, tomorrow, yesterday, currently, recently, next, previous | depends on the day of reading | a date |
| last | 2 meanings: final; most recent | "final" or a name with a date |
| and/or, slash, alternatively | 2 meanings | "or" or "either ... or" |
| unless, in case, provided that, as long as, assuming, once | more than 1 word for 1 relation | a pattern from rule C3 |
| need to, have to, is to be, it is required, will (as a requirement) | no actor or no force | an actor and a keyword |
| must, should, may (lower case) | 2 meanings | a keyword or a condition |
| can (as permission) | permission or ability | MAY, or a number for ability |
| etc., and so on, and others | open list | a full list or "Examples (incomplete list):" |
| any, certain, various, some | no quantity | "every", "exactly 1", "at least 1" |
| probably, apparently, likely, seems, should work | no source | a marker from module F |
| it, this, that, they, them, its, their (instead of a name) | refers to 2 objects | the object's name |
| an opening "-ing" or "-ed" clause | hidden actor and order | a full sentence |
| set up, carry out, figure out, deal with (phrasal verbs) | meaning differs from the parts | a single verb |

## Glossary of CE terms

| Term | Definition |
|---|---|
| part | A piece of a sentence that the conjunction "and", "or" or "either ... or" joins to another piece. |
| actor | The person, agent or device that performs the action. |
| object | The thing a sentence talks about. |
| term | A word or phrase that has 1 defined meaning in the text. |
| meaning | One way to read a sentence. |
| instruction | A sentence that tells the reader to act. |
| description | A sentence that states a fact or a requirement. |
| vague word | A word without a measurable boundary. |
| elementary proposition | A sentence that names 1 observable state and that a check can show false. |

If a text has at least 3 terms, add a "Glossary" section before the content. The section has 3 columns: term,
definition, banned words for the concept.

## Control

After writing, do every step in this order:

1. Count the words of every sentence. Fix every sentence over the limit of rule B8.
2. Search the text for every word of the section "Banned words".
3. Name the actor of every sentence about an action.
4. Check every number: unit, reference conditions, boundary form from rule D2.
5. Check every date and every time: format of rule D3, time zone.
6. Check every term: 1 name in the whole text and a definition in the "Glossary" section.
7. Do the 2-meaning test. For every sentence, look for a second meaning. Rewrite every sentence that has one.
8. In a report, build the truth table of rule T4. Write "done" only when every row is T.

If you have a tool that runs code, count the words with a script. Counting from memory gives errors.

```python
import re, sys

for line in sys.stdin:
    for s in re.split(r"(?<=[.!?])\s+", line.strip()):
        n = sum(1 for w in s.split() if re.search(r"\w", w))
        if n > 20:
            print(n, s)
```

The script prints every sentence with more than 20 words. A description with 21 to 25 words inclusive meets rule B8.
An abbreviation with a point splits a sentence in the wrong place ("e.g.", "i.e."). Count such a sentence by hand.

## Output format

WRITE and REWRITE return 3 parts in this order:

1. The "Glossary" section. If the text has fewer than 3 terms, leave it out.
2. The text in CE.
3. A "Decisions and gaps" table with the columns: No., Fragment, Rule, Meanings or gap, Choice.

CHECK returns a violations table with the columns: No., Fragment, Rule, Problem, Fix. In the "Problem" column, write
both meanings of the fragment. Below the table, give the number of violations for each rule.

REPORT returns the report in CE, the truth table of rule T4 and 1 sentence: "done" only when every row is T; otherwise
the F rows and the ? rows by name.

## Example

Context from the user: the unit has 1 valve (V1) and 1 filter (F1).

Source text: "The valve should be closed after work. The filter needs to be cleaned regularly. Send the log by Friday."

Text in CE:

- After the work ends, close valve V1.
- Clean filter F1 every `[TBD: interval between cleanings]`.
- Send the log to `[TBD: recipient]` no later than `[TBD: date and time]`.

Decisions and gaps:

| No. | Fragment | Rule | Meanings or gap | Choice |
|---|---|---|---|---|
| 1 | "should be closed", "needs to be cleaned" | B1, keywords | No actor; "should" in lower case. | The reader is the actor. Imperative. |
| 2 | "regularly" | A5 | No frequency. | `[TBD]` |
| 3 | "by Friday" | D2, D3 | 2 meanings: the deadline includes Friday; the deadline ends before Friday. No date. | `[TBD]` |
| 4 | "Send" | B1 | No recipient. | `[TBD]` |

Report example (mode REPORT) for the claim "the fix is deployed":

| Proposition | T / F / ? | Evidence |
|---|---|---|
| Commit `abc1234` is on `origin/main`. | T | `git branch -r --contains abc1234` |
| The deploy job for `abc1234` succeeded. | T | CI job 123: `success` |
| `GET /api/health` returns 200. | T | `curl -s -o /dev/null -w '%{http_code}' https://example.org/api/health` at 15:02 CET |
| The error no longer appears in the log. | ? | No access to the production log. |

Not done: the log row is ?, because the author has no access to the production log.

## Limits of the standard

- CE does not change spelling or punctuation. Use one spelling variant (British or American) in the whole text.
- A quotation, a proper name and a user-interface label stay unchanged. Put such a fragment in quotation marks.
- The user's instruction has priority over a CE rule. Record the departure in the "Decisions and gaps" table.
- If 2 rules conflict, a single meaning wins over length. Split the sentence.
- A contract in CE still needs a lawyer. CE removes language ambiguity and does not judge legal effects.
- CE is a different standard from plain language. Plain language serves easy understanding (ISO 24495-1). CE serves a
  single meaning. An author MAY apply both standards in 1 text.
- Module T does not prove a claim true. Module T shows which parts of the claim were compared with reality.

## Sources

- Keywords: [RFC 2119](https://www.rfc-editor.org/rfc/rfc2119) (S. Bradner, 1997) and [RFC 8174](https://www.rfc-editor.org/info/rfc8174).
- B1, B3, B4, B8, A8, E3: modelled on [ASD-STE100 Simplified Technical English](https://www.asd-ste100.org/), Issue 9 (2025).
- C3: A. Mavin et al., [Easy Approach to Requirements Syntax (EARS)](https://alistairmavin.com/ears/), 2009.
- D1: BIPM, [The International System of Units (SI) brochure](https://www.bipm.org/en/publications/si-brochure), section 5.4 (writing numbers and units).
- D3: [ISO 8601](https://www.iso.org/iso-8601-date-and-time-format.html).
- D6: MathWorld, ["Billion"](https://mathworld.wolfram.com/Billion.html) (short and long scale).
- Module T: L. Wittgenstein, *Tractatus Logico-Philosophicus* (1921), propositions 2.061, 2.223, 2.224, 3.323, 4.024,
  4.21, 4.461, 5.134, 5.1361, 5.1363 and 7; the skills `tractatus-sense` and `tractatus-verify`
  ([tractatus-skills](https://github.com/maciejszulia/tractatus-skills)).
- Polish counterpart: [Polszczyzna Kontrolowana (PK)](https://github.com/maciejszulia/polszczyzna-kontrolowana).
- Plain language: [ISO 24495-1:2023](https://www.iplfederation.org/iso-standard/).
