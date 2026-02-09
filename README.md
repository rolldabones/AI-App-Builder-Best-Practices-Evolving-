# AI-App-Builder-Best-Practices-Evolving-
Slow AI build guidelines using Origami (FRAME→DRAFT→TIGHTEN→LOCK) with risk-tiered gates to ship only tested, reviewable outputs, with versioned standards, documented taste sign-off, named human approval, monitoring, rollback, and an audit packet.

TL;DR
	•	Slow AI: visibility, tests, and evidence beat speed
	•	Origami Method: FRAME → DRAFT → TIGHTEN → LOCK with stop rules
	•	Risk-tiered gates: Low ships fast, Medium reviewed, High escalated
	•	Separation of duties: generation is not approval for Medium/High
	•	Audit packet is the product: reproduce what happened and why

Memo: AI App Builder Best Practices (Evolving)

Gold standard

𝗗𝗼𝗻𝗲 𝗶𝘀 𝘁𝗲𝘀𝘁𝗲𝗱. 𝗣𝗮𝘁𝘁𝗲𝗿𝗻𝘀 𝗮𝗿𝗲 𝘀𝘁𝗮𝗻𝗱𝗮𝗿𝗱𝘀. 𝗧𝗮𝘀𝘁𝗲 𝗶𝘀 𝘀𝗶𝗴𝗻-𝗼𝗳𝗳.

Principles
	1.	Slow AI
	•	Prefer visibility over speed.
	•	Every meaningful output must be explainable, testable, and reviewable with evidence.
	•	If the work cannot be reproduced from artifacts and logs, it is not done.
	2.	Final Liability rests with the Human
	•	Every release has a named Accountable Owner who approves residual risk.
	•	No owner, no ship.
	3.	Untrusted-by-default
	•	Treat AI outputs as untrusted until they pass explicit checks.
	•	Unknowns stay labeled “Unknown/Insufficient” until evidence is attached.

Scope

These guidelines govern how we build, review, and release AI-enabled apps and workflows so they are testable, auditable, and safe to operate.

Origami Method workflow

Each fold creates an inspectable artifact and a gate.
	1.	FRAME
	1.	Objective and ship outcome required today
	2.	Success metric in one sentence
	3.	Named Accountable Owner
	4.	Risk tier with rationale
	5.	Definition of Done: acceptance tests and required evidence
	2.	DRAFT
	1.	Structured spec v0.1
	2.	Open issues register with owners and due dates
	3.	First working slice or prototype
	3.	TIGHTEN
	1.	Identify top 3–5 critical paths
	2.	For each: failure modes and a verification method
	3.	Red-team checks for misuse, prompt injection, tool abuse
	4.	Coherence pass: one voice, one intent, one structure
	4.	LOCK
	1.	Approvals recorded for the tier
	2.	Audit packet assembled
	3.	Monitoring and rollback confirmed

Stop rule:
	•	If a critical path cannot be verified, de-scope, add evidence, or escalate. Do not ship by improvisation.

Risk tiers and required review
	1.	Low
	•	Reversible, internal, non-sensitive
	•	Peer review optional, logs required
	2.	Medium
	•	External-facing or touches customer data
	•	Peer review required, monitoring required if automated actions exist
	3.	High
	•	Safety, legal, finance, regulated, security, or irreversible impact
	•	Mandatory second reviewer plus documented risk acceptance by Accountable Owner
	•	No ship without evidence, monitoring, and rollback

Separation of duties
	1.	Generation does not equal approval for Medium/High.
	2.	Approval is a named human decision with recorded rationale.
	3.	Exceptions are allowed only if logged and signed by the Accountable Owner.

Control plane minimums for Medium/High
	1.	Data handling
	1.	Data classification and allowed inputs per tier
	2.	Redaction rules and retention policy
	2.	Secrets and environments
	1.	No secrets in prompts or logs
	2.	Separate dev/test/prod and separate webhooks and credentials by environment
	3.	Tool access boundaries
	1.	Least privilege for tools and integrations
	2.	Constraints to reduce prompt injection and tool misuse risk
	4.	Monitoring and rollback
	1.	Monitoring signals: quality, safety, drift, cost, latency
	2.	Stop rules and a freeze owner
	3.	Rollback steps: disable tools, revoke keys, revert versions

Release gate (10 minutes)

Ship only if:
	1.	Tests pass or exceptions are logged and approved.
	2.	Key claims are verified or marked Unknown/Insufficient.
	3.	Risk tier is reviewed and required approvals are recorded.
	4.	Audit trail is stored: inputs, prompts, outputs, diffs, reviewer notes, exception log.
	5.	Medium/High have monitoring and rollback in place.

Do not ship if:
	1.	High tier lacks required evidence or approvals.
	2.	Tooling can take action and there is no rollback path.
	3.	There is no named Accountable Owner.

Audit packet (must be reproducible)
	1.	Objective, risk tier, decision owner
	2.	Input packet and constraints
	3.	Workflow definition or agent charters and prompts
	4.	Outputs and diffs
	5.	Verification artifacts and exception log
	6.	Reviews and approvals
	7.	Reflection log and CAPA entries
	8.	Post-release monitoring and any incidents

Final Liability rests with the Human.
