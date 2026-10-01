## Compaction in Codex CLI and OpenClaw

*Evidence date/version:* The OpenClaw documentation and Codex repository results were retrieved in June 2026. The Codex source is from the repository’s `main` branch rather than a pinned release, so behavior may differ across versions.

### Codex CLI

Codex supports automatic compaction controlled by `model_auto_compact_token_limit`; `/compact` triggers it manually. The implementation exposes a dedicated summarization prompt and summary prefix, and includes a 20,000-token maximum for the compacted user message. It also reinserts canonical initial context at a model-expected position in the replacement history. ([`compact.rs`](https://github.com/openai/codex/blob/main/codex-rs/core/src/compact.rs); [configuration issue documenting the setting](https://github.com/openai/codex/issues/14456))

The cited source confirms that Codex creates a condensed continuation context, but does not establish—at the required version level—the complete list of facts guaranteed to survive summarization. Codex also supports saved sessions and `codex resume`, but the collected primary evidence does not specify whether the compacted replacement is durably stored in the session transcript, nor its on-disk format. ([Codex CLI documentation](https://learn.chatgpt.com/docs/codex/cli))

### OpenClaw

OpenClaw automatically compacts when a session approaches its context limit and when a provider returns a context-overflow error; it then retries. `/compact` forces compaction. Proactive threshold compaction can be disabled, while overflow recovery and manual compaction remain available. ([OpenClaw compaction documentation](https://docs.openclaw.ai/concepts/compaction))

OpenClaw summarizes older conversation and preserves a recent unsummarized tail. It keeps assistant tool calls paired with matching `toolResult` entries at split boundaries. Text is supplied to the summarizer, while image pixels are omitted and represented by markers. Before compaction, it prompts the agent to save important durable notes to memory files. ([same documentation](https://docs.openclaw.ai/concepts/compaction))

Unlike pruning, OpenClaw compaction persists a summary in the session transcript; the full history remains on disk. Pruning only removes old tool results from the in-memory prompt and does not rewrite history. ([OpenClaw context documentation](https://docs.openclaw.ai/concepts/context))

### Bottom line

Both systems summarize older context to continue a long session. OpenClaw’s collected documentation explicitly distinguishes durable transcript compaction from temporary in-memory pruning. The collected Codex evidence confirms triggers and summary machinery, but does **not** support equivalent claims about transcript persistence, exact preservation guarantees, model-specific behavior, or release-pinned thresholds.
