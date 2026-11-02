# AI Agent & RAG Testing Portfolio

A sample QA portfolio for testing **agentic AI platforms**: AI agent behaviour, knowledge base / RAG, guardrails, fallback handling, and regression automation.

> All content here is written generically for learning and demonstration. It contains no confidential data from any employer or client.

## What this repo covers

| Area | What it shows |
|------|---------------|
| Adversarial and prompt-safety testing | 20 test cases: prompt injection, jailbreaks, system-prompt extraction, tenant isolation, indirect injection |
| Fallback and error handling | 18 test cases: unanswerable questions, tool failures, timeouts, handoff, recovery |
| RAG / knowledge base testing | 30 test cases: ingestion, retrieval accuracy, updates, security, performance |
| Test strategy | How manual, automation, API, and AI/LLM testing fit together |
| Defect reporting | Sample bug report and test execution summary |

## Repository structure

```
.
├── README.md
├── test-cases/
│   ├── 01-adversarial-prompts.md
│   ├── 02-fallback-scenarios.md
│   └── 03-rag-knowledge-base.md
├── test-strategy/
│   └── test-strategy.md              (scope, approach, risks)
├── automation/
│   └── robot-framework/              (sample regression suite)
├── reports/
│   ├── sample-bug-report.md
│   └── sample-execution-summary.md
```

## How AI testing differs from normal testing
- The same input can give different outputs, so each case is run several times and a **pass rate** is recorded.
- Pass/fail is judged on **safety, accuracy, and faithfulness to the source**, not exact text matching.
- Failures are logged with the exact prompt, response, agent version, and date for reproducibility.

## Tools
Robot Framework, Python, Postman (API testing), JIRA (defect tracking), Git/GitHub

## Author
**Namrata** - QA Automation Engineer
