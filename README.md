# acc-workflows

ACC Workflows contains reusable workflow definitions, step schemas, and orchestration patterns for the canonical ACC™ platform.

## ACC V2 operating model

Workflows no longer assume that an agent is the top-level unit of work. They operate beneath durable project state:

```text
Project
→ Responsibility
→ Work Order
→ Workflow
→ Authorized Provider / Executor
→ Approval
→ Verification
→ Deployment / Outcome
→ Audit
```

A workflow may decompose one Work Order into multiple tasks, provider calls, human decisions, verification steps, and deployment steps while preserving the original project and work-order identifiers for traceability.

## Workflow rules

- Unknown provider identifiers must fail closed.
- Non-executable or reserved providers may be planned but must not be dispatched.
- Privileged workflow steps must preserve human approval gates.
- Schedules and triggers describe when work should be considered; they do not create authority.
- Provider-specific logic belongs in adapters, not in reusable workflow definitions.
- Completion requires verification evidence where the governing workflow requires it.

`openai-dot` is a reserved compatibility identifier only and must not be treated as an executable runtime until a supported integration exists and has been verified.

**Synchronization target:** ACC `2.0.0-alpha.1` delegation foundation. Production status remains tied to separately verified deployment evidence.
