# AI Standards

Purpose: engineering standards for building generative AI solutions — prompts, GPTs, and agent-based workflows.

## Engineering Mindset

- Understand the user's workflow and the decision the output supports before prompting.
- Prefer reusable, documented patterns over one-off prompts.
- Treat model output as untrusted until it has been checked, the way external input is checked elsewhere.
- Match the tool to the task; not every problem needs a model.
- Build solutions a non-author can run, understand, and trust.

## Minimal Implementation Ladder

Before building a new prompt, GPT, or agent, stop at the first rung that holds:

1. Does this solution need to exist at all? If not, do not build it.
2. Does an existing prompt, GPT, or documented pattern already do it? Reuse it.
3. Does a simpler tool (a query, a template, a built-in feature) do it without a model? Use it.
4. Does a small change to an existing asset cover the new case? Make the change.
5. Is it a single prompt? Write the one.
6. Only then build a new GPT or agent workflow.

This reduces sprawl, not rigor. Never cut evaluation, governance, or sensitive-data handling to ship faster.

## Prompt And Solution Design

- Give the model a clear role, task, and scope; remove ambiguity that could be read more than one way.
- Specify the input it will receive and the exact output shape it must return.
- Include worked examples when the desired output is specific or easy to get wrong.
- State guardrails explicitly: what the model must not do, and how it should refuse or escalate.
- Keep instructions as short as they can be while still being unambiguous.

## Reusable Assets

- Capture prompts and GPTs as named, documented patterns with a stated use case, not throwaway text.
- Version assets so changes are tracked and a working version can be restored.
- Record what each asset is for, who it serves, and what it should always do.
- Improve an existing asset before creating a near-duplicate.
- Prefer a small library of trusted patterns over many untracked one-offs.

## Evaluation And Testing

- Define what good output looks like before the prompt is written.
- Test against representative inputs, including empty, edge, and adversarial cases.
- Check for hallucination and fabricated detail; confirm claims that can be verified.
- Re-test when the prompt, the model, or the surrounding workflow changes.
- A prompt that worked once is not validated; consistent behavior across cases is.

## Governance And Documentation

- Every deployed AI solution has a named owner.
- Get the required approval before deploying a solution to users.
- Document each solution's purpose, inputs, expected output, and known limits.
- Use change control: track what changed, when, why, and by whom.
- Keep an audit trail sufficient to explain how an output was produced.
- Keep a human in the loop for consequential output; the model assists the decision, it does not own it.
- Choose models and vendors deliberately, and record the reason for the choice.

## Sensitive Data In Prompts

- Do not put PII, account data, credentials, secrets, or material non-public information into prompts or third-party tools without approval.
- Redact or use synthetic stand-ins in examples, shared assets, and documentation.
- Confirm where prompt data is sent, stored, and retained before using real data.
- Follow the firm's data handling and approval rules; when unsure, treat the data as sensitive.

## Non-Determinism And Reliability

- Expect output to vary between runs; design for variation rather than assuming repeatability.
- Set determinism and creativity settings intentionally for the task.
- Validate the shape and content of output before downstream steps depend on it.
- Define fallback behavior for when the model fails, refuses, or returns unusable output.
- Handle rate limits, timeouts, and service errors as expected states.

## Verification

Every meaningful AI change should have an appropriate verification path.

- Run the smallest relevant check first: execute the prompt on known cases and compare against expected behavior.
- Expand verification when output feeds decisions, reporting, or downstream systems.
- Confirm guardrails hold and sensitive data is not exposed.
- Document checks that could not run and why.
- Do not claim a solution is ready unless the check actually ran or was manually confirmed.
