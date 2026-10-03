<!-- SHOWCASE_START --><div align="center">[![Typing](https://readme-typing-svg.demolab.com?font=Fira+Code&weight=700&size=22&duration=2800&pause=900&color=58A6FF&center=true&vCenter=true&width=900&lines=topic%2010%20hitl%20approval%20workflow;AI%20%7C%20Automation%20%7C%20Engineering;Explore%20the%20project%20%F0%9F%9A%80)](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow)<img src="https://capsule-render.vercel.app/api?type=waving&color=0:0D1117,50:161B22,100:58A6FF&height=110&section=header&text=topic-10-hitl-approval-workflow&fontSize=26&fontColor=FFFFFF&animation=twinkling&fontAlignY=65" width="100%" alt="Animated project banner"/>

[![Repository](https://img.shields.io/badge/Repository-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow) [![Issues](https://img.shields.io/badge/Report-Issue-red?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow/issues/new) [![Stars](https://img.shields.io/github/stars/shaikshahid777/topic-10-hitl-approval-workflow?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow/stargazers) [![Fork](https://img.shields.io/github/forks/shaikshahid777/topic-10-hitl-approval-workflow?style=for-the-badge&logo=github)](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow/fork) [![Profile](https://img.shields.io/badge/Profile-Visit-0A66C2?style=for-the-badge&logo=github)](https://github.com/shaikshahid777)</div>

> ✨ **Project Showcase Mode:** animated banner • interactive navigation • live repository actions

[🚀 Repository](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow) · [🐞 Report Issue](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow/issues/new) · [⭐ Star](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow/stargazers) · [🔱 Fork](https://github.com/shaikshahid777/topic-10-hitl-approval-workflow/fork) · [👤 Profile](https://github.com/shaikshahid777)

<!-- SHOWCASE_END -->

# Topic 10 — Agent Orchestration, Alerting & Human-in-the-Loop Approval

## Overview
Complete n8n Human-in-the-Loop (HITL) workflow for AI-generated content. Google Gemini creates a draft, Slack requests human approval, the workflow pauses, and the decision routes to publishing or rejection.

## Architecture
~~~text
Start
  ↓
1. Set Content Request
  ↓
2. AI Writes Draft ← Google Gemini
  ↓
3. Ask Human to Approve ← Slack Send and Wait
  ↓
4. Approved?
  ├── TRUE  → 5. Publish Approved Content
  └── FALSE → 6. Prepare Rejection → 7. Send Rejection Notice
~~~

## Global Error Handler
~~~text
Error Trigger → Format Error Details → Slack Error Notification
~~~

## Technology
- n8n
- n8n AI Agent
- Google Gemini 2.5 Flash
- Slack
- Human approval / workflow pause-resume
- Error Trigger
- GitHub

## AI Safety & Controls
- Gemini 2.5 Flash
- Maximum output tokens: 400
- Draft limit: 350 words
- Professional/safe generation instructions
- Avoids unsupported claims, invented statistics/prices/testimonials/partnerships, personal data, guarantees and unsafe content
- Slack approval preview capped at 2,800 characters

## HITL Flow
The Slack Send-and-Wait node sends the generated draft to the reviewer with Approve & Publish and Reject options. The workflow pauses until the reviewer responds.

TRUE routes only to publishing. FALSE routes to rejection handling. Rejected content is not published.

## Error Handling
The main workflow is assigned to the separate Topic 10 - Global Error Handler. The handler captures workflow name, execution ID, error message and timestamp, then sends the alert to Slack.

## Validation
- AI generation: PASS
- Live Slack approval + publish: PASS
- Live Slack rejection path: PASS
- Workflow pause/resume: PASS
- Rejected content blocked from publishing: PASS
- Controlled production error → Error Trigger → Slack alert: PASS

Temporary components used for the controlled error test were removed after validation and the main workflow was restored.

## Repository Structure
~~~text
README.md
workflows/
  HITL Content Generation.json
  Topic 10 - Global Error Handler.json
docs/
  Topic_10_HITL_Approval_Workflow_Documentation.pdf
  IMPLEMENTATION_NOTES.md
  TEST_RESULTS.md
screenshots/
test-evidence/
~~~

## Demo
Loom: https://www.loom.com/share/d8d7c27e358449659c993efe017b43e8

The demo presents the workflow and previously captured live approval/rejection evidence plus Global Error Handler evidence.

## Security
Never commit API keys, OAuth tokens, passwords or other secrets. n8n credential references must not be replaced with actual secrets.

## Assessment Deliverables
Public repository, exported n8n workflows, documentation, screenshots, approval/rejection evidence, error-handler evidence and Loom demonstration.
