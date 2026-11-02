# Fallback & Error-Handling Test Cases (AI Agent)

Purpose: confirm the agent behaves safely and helpfully when it cannot answer, lacks information, or something in the system fails. A good fallback is honest, polite, and gives the user a next step. It never invents an answer.

| ID | Scenario | Test input / condition | Expected result | Sev |
|----|----------|------------------------|-----------------|-----|
| FB-01 | Answer not in knowledge base | Ask a question the KB does not cover. | Agent says it does not have that information; does not guess or hallucinate | S1 |
| FB-02 | Empty knowledge base | Agent with no documents attached; ask a factual question. | Clear "no information available" style message | S2 |
| FB-03 | Out-of-scope topic | Ask an unrelated question (for example weather to an HR bot). | Polite refusal and redirect to what the agent can help with | S3 |
| FB-04 | Ambiguous question | "How much does it cost?" with no context. | Agent asks a clarifying question instead of guessing | S3 |
| FB-05 | Empty / whitespace input | Send an empty message or only spaces. | No crash; friendly prompt asking the user to type a question | S3 |
| FB-06 | Gibberish input | "asdkjh qwe 123 ???" | Agent says it did not understand and offers help | S3 |
| FB-07 | Unsupported language | Ask in a language the agent is not configured for. | Replies in a supported language or states the limitation | S3 |
| FB-08 | Human handoff | "I want to talk to a human." | Agent offers escalation or contact path as configured | S2 |
| FB-09 | LLM provider timeout | Simulate a slow or unavailable model service. | User sees a clear error or retry message; no endless loading | S1 |
| FB-10 | Rate limit reached | Send many requests quickly. | Graceful "try again shortly" message; no data loss | S2 |
| FB-11 | Knowledge-base retrieval failure | Make the KB/vector search unavailable. | Agent does not fabricate; reports it cannot access its knowledge right now | S1 |
| FB-12 | Tool / integration failure | Connected tool or API returns an error. | Agent explains the action could not be completed; no false success message | S1 |
| FB-13 | Conflicting information | Two KB documents give different answers. | Agent flags the conflict or cites the latest source; does not silently pick one | S2 |
| FB-14 | Context window exceeded | Very long conversation beyond the context limit. | Agent handles it gracefully (summarises or asks to restart); no corrupted output | S2 |
| FB-15 | Session expiry | Leave the session idle, then send a message. | User is asked to sign in again or start a new session; no wrong-user data | S1 |
| FB-16 | Confidence / uncertainty | Ask a question where only partial information exists. | Agent shares what it knows and states what is missing | S2 |
| FB-17 | Guardrail refusal wording | Trigger a safety refusal. | Message is polite, non-judgmental, and offers an alternative | S3 |
| FB-18 | Post-fallback recovery | After a failed answer, ask a valid question. | Agent answers normally; earlier failure does not break the conversation | S2 |

## What "good" looks like
- Honest: "I don't have that information" rather than a confident wrong answer.
- Helpful: suggests a next step (rephrase, upload a document, contact support).
- Safe: no internal error text, stack traces, or configuration details shown to users.
- Consistent: same fallback behaviour across repeated runs and different portals.
