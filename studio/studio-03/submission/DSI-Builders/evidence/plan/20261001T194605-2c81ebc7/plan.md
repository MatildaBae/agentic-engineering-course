1. **Define the comparison and versions**
   - Identify the exact Codex CLI release and OpenClaw release/commit to compare; record retrieval dates.
   - Treat “compaction” as context-window reduction during an active session, and distinguish it from transcript storage, session resumption, pruning, and summarization.
   - **Unknowns to resolve:** whether “OpenClaw” refers to a specific repository/product fork; whether behavior differs by model provider or configuration.

2. **Collect primary Codex CLI evidence**
   - Inspect the official Codex CLI repository, release notes, command reference, configuration documentation, and implementation/tests for context management, compaction, summarization, truncation, and session resume.
   - Record exact file paths, commits/tags, dates, and relevant code excerpts.
   - Determine:
     - Trigger conditions: token threshold, model context limit, explicit command, failure/retry, or other events.
     - What is summarized, retained verbatim, dropped, or regenerated.
     - Whether tool outputs, files, instructions, conversation turns, and working state are preserved.
     - How compacted state is serialized and whether it survives process exit or later session reopening.

3. **Collect primary OpenClaw evidence**
   - Locate the project’s canonical repository and official documentation; verify identity, version, and commit.
   - Search implementation, tests, configuration schemas, release notes, and session/state-management documentation for compaction, context pruning, summarization, memory, transcript persistence, and resume behavior.
   - Extract the same trigger, preservation, and persistence facts as for Codex CLI.
   - **Unsupported-detail check:** explicitly mark any behavior inferred only from undocumented code paths, issue discussions, logs, or third-party explanations.

4. **Verify runtime behavior where documentation is incomplete**
   - Build reproducible tests for each tool at pinned versions.
   - Use controlled conversations exceeding the context budget, explicit compaction commands if available, tool calls, file edits, and process restarts.
   - Capture API requests, local session files/databases, summaries, retained messages, and resumed-session behavior without exposing secrets.
   - Repeat across relevant models/configurations and distinguish observed behavior from implementation guarantees.

5. **Construct a comparison matrix**
   - Columns: product/version, trigger, threshold/configuration, summarized content, preserved verbatim content, discarded content, tool/file-state handling, persistence medium, restart/resume semantics, user controls, and evidence citation.
   - Separate documented guarantees, source-confirmed implementation behavior, experimentally observed behavior, and unresolved questions.

6. **Identify important unknowns**
   - List unavailable source code, undocumented thresholds, provider-dependent behavior, summary fidelity guarantees, failure recovery, backward compatibility, retention/privacy policies, and whether persisted summaries are encrypted or portable.
   - Avoid filling gaps with assumptions.

7. **Write the final cited report**
   - Use primary documentation/source citations with version or commit and publication/retrieval date.
   - Clearly distinguish compaction from persistence.
   - State limitations and unsupported details explicitly.
   - Keep the report within 400 words and include only evidence-backed conclusions.
