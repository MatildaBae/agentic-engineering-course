# Studio 03 Explanation

**Team:** DSI-Builders
**Members:** Jiwon Bae (jb5234) / Michelle Lee (mjl2241)

## Patterns tried

ReAct started right away with the fixed question, and the model searched for observations. Plan version first made a 7 step plan, and it was passed into the same research loop. The plan version proposed more work than the bounded run ultimately performed. Actual Plan execution adapted to the call budget and performed 6 Tavily research.


## Runs and comparison

| Metric | Direct / ReAct | Plan-and-Execute |
|---|---|---|
| Run ID |20261001T194159-785bf717 | 20261001T194605-2c81ebc |
| Plan origin (none, model-generated, or human) | none | model-generated |
| Model calls |7 |8 |
| Bash tool calls |5 |6 |
| CLI executions |5 |6 |
| Rejected tool calls |0 |0 |
| Input / output / cached tokens |32,933 / 1,419 / 16,432 | 38,635 / 1,519 / 16,576 |
| Wall time |27.322 s | 32.166 s |

Compare what each run found, starting with factual coverage and source support. Cite specific trace events or call IDs. Then describe differences in calls, executions, token use, and wall time. Mark unavailable metrics as unknown, not zero. One pair of runs does not establish a general winner.
ReAct
OpenClaw direct extraction:
call_c5t6qt0eULET1nPmFQt7QOuC

Plan
OpenClaw direct extraction:
call_fkK82RE2X1Sgmiap6WRW2jxs

Plan
Codex compact.rs direct extraction:
call_8nfSmg6lKtFkt2Ofncqsuz5M



## Contributions

Write this section by hand. Do not use AI.

- **Member:** [contribution]
- **Member:** [contribution]
