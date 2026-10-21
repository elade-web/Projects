# Slide brief: replacing Appian vendor onboarding with MineOS

## Instructions for the slide agent

- **Audience:** a prospect that runs vendor onboarding on Appian and is evaluating replacing it. They want the full third-party lifecycle, from onboarding to offboarding.
- **Presenter:** MineOS solutions engineer.
- **Goal:** show that MineOS covers the vendor lifecycle with ready-made content plus configurable automation. Be honest about where the approach differs from a custom Appian build.
- **Length:** 10 to 12 slides. One idea per slide, short bullets, and diagrams where a flow is described.
- **Tone:** confident and factual. Don't criticize Appian; describe the trade-off between building and buying.
- **Do not put the "Internal only" section at the end of this file on any slide.**
- Use "Build" (delivered with Integration Builder) and "Native" (out of the box) labels consistently.

## Suggested slide outline

### 1. Title
- Third-Party Lifecycle on MineOS: from onboarding to offboarding.

### 2. How Appian onboarding works today
- Appian is a low-code platform for building process apps: workflows, data records, screens, integrations, AI and RPA.
- Vendor onboarding on Appian is an app someone built: the client's own team, a consultancy, or a partner app such as KPMG TPRM.
- The client owns the questionnaires, risk logic, vendor portal, integrations and maintenance.
- Typical pattern: intake → document collection → questionnaires and risk scoring → screening → multi-party approvals → ERP vendor master → periodic reassessment.

### 3. Build vs buy
- **Appian:** maximum flexibility, but every questionnaire, rule, screen and integration is custom code to maintain.
- **MineOS:** a third-party risk product with the content ready-made. Workflow is configured, not developed.
- Message: stop building and maintaining risk content; connect MineOS to the systems you keep.

### 4. How MineOS maps to Appian's building blocks
Use this as a table:

| Appian piece | MineOS equivalent |
|---|---|
| Forms and questionnaires | Assessment Builder: templates with conditional logic at question and section level |
| Vendor-facing portal | Collaborator view: vendor is invited by email and answers in a dedicated view |
| Process steps and routing | Rules: when an event happens and conditions match, take an action |
| Integrations to other systems | Integration Builder (embedded iPaaS): ERP, procurement, ticketing, Slack/Teams, identity |
| Data records | Vendor inventory with custom fields, owners, business units and review status |

### 5. What MineOS gives you out of the box
- **Template library:** Vendor, Third-party DPIA, DPIA, TIA, PIA, LIA, DORA ICT criticality and Register of Information, NIS2, NIST CSF, PCI DSS, HIPAA, ESG, multi-framework, Reassessment and Offboarding.
- **Vendor collaboration:** vendors answer questionnaires in their own view, with no links or extra accounts to manage.
- **AI autofill:** pre-fills vendor and assessment answers from enrichment data, trust centers and uploaded documents. Suggestions can be reviewed or auto-approved.
- **Cyber risk rating:** Panorays security rating and report covering assets, tests, dark web and cyber news.
- **Shadow-IT discovery:** finds vendors through SSO (Google, Okta, Entra), email, AWS and GCP.
- **Privacy linkage:** vendors linked to data types, processing activities (ROPA) and DPIAs.
- **Audit trail:** assessment history and versioning, plus who removed a vendor, when and why.

### 6. Onboarding flow on MineOS (diagram)
1. **Request** (Build): the request is raised in Zip, Coupa, ServiceNow or Jira. Integration Builder creates the vendor in MineOS and attaches the request.
2. **Enrich and triage** (Native): catalog enrichment, AI autofill and the Panorays rating.
3. **Assess** (Native): rules create the right assessments from the intake answers, for example a DPIA if personal data is processed or DORA for critical ICT. The vendor is invited to answer.
4. **Review and decide** (Native): any rejected assessment rejects the vendor; when all are complete the vendor moves to In evaluation. The owner gives final approval.
5. **Hand off** (Build): on approval, Integration Builder creates the supplier in the ERP, notifies the requester and opens provisioning tickets.
6. **Monitor** (Native): review dates, reminders, the Reassessment template and the ongoing cyber rating.

### 7. Offboarding flow on MineOS (diagram)
1. **Trigger** (Build or Native): a contract end in the procurement tool or ERP, or the owner moves the vendor to Trash with a justification.
2. **Offboarding assessment** (Native): data return or deletion, access removal, certificates of destruction. A rule can create it automatically.
3. **Revoke and close** (Build): Integration Builder removes the app in Okta or Entra, closes the supplier in the ERP and opens IT and finance tickets.
4. **Retain evidence** (Native): the vendor record, assessments and audit log are kept. The vendor can be restored if re-engaged.
5. **Update records** (Native): the ROPA and data map reflect the removal.

### 8. Business rules
- **Triggers:** an assessment is submitted, created or changes state; a vendor is approved or changes state; a custom field changes; an owner is assigned; AI autofill finishes.
- **Conditions:** template used, a specific answer, a custom field value, vendor state, vendor has no assessments.
- **Actions:** create the next assessment, send notifications, run AI autofill and approve suggestions, update the vendor's review status.
- **Example:** "When the intake assessment is submitted and personal data = Yes, create a Third-party DPIA."

### 9. Integration Builder: example flows
Present as a grid of cards (trigger → outcome):
- **Procurement intake:** new request in Zip, Coupa, Ariba, ServiceNow or Jira → vendor created in MineOS and assessments opened.
- **Approved vendor to ERP:** vendor approved → supplier created in SAP, Oracle, NetSuite or Coupa, and the requester notified.
- **Rejection loop:** vendor rejected → procurement request closed with the reason, and a Slack or Teams message sent.
- **Approvals in ticketing:** risk review triggered → security, legal and finance approval tasks in ServiceNow or Jira, with the result written back.
- **Screening:** new vendor → the client's sanctions or credit provider is checked and the result recorded.
- **Tiered reassessment:** monthly schedule → Reassessment created for vendors due for review.
- **Offboarding kickoff:** contract end → vendor moved to Trash and the Offboarding assessment created.
- **Access shutdown:** offboarding completed → app removed in Okta or Entra and the supplier blocked in the ERP.
- **Appian migration:** existing Appian vendor records loaded into MineOS. Appian can run in parallel during a phased cutover.
- Delivery model: Mine's team builds the flows with the client, and the client deploys and configures them in MineOS.

### 10. Recommended architecture
- MineOS is the system of record for third-party risk and privacy.
- The procurement tool or ERP keeps finance onboarding (banking, tax, payment terms).
- ServiceNow or Jira handles multi-level approvals where needed.
- Integration Builder connects all of them through MineOS webhooks and the public API.

### 11. Discovery questions
1. Was the Appian app custom-built, a partner app, or Appian Vendor Management? Who maintains it?
2. Walk us through one vendor from request to ERP. Which steps are risk and compliance, and which are procurement or finance?
3. How do vendors interact today: a portal with links, Appian accounts, or email only?
4. How are approvals routed (by spend, risk tier or business unit), and are there SLAs or escalations?
5. Which systems are integrated, and in which direction? For example ERP, procurement, sanctions screening, DocuSign, ServiceNow, Okta.
6. Do you screen for sanctions, KYB or credit, or collect banking and tax data, inside Appian?
7. What does offboarding look like today? Who triggers it, and what evidence do you keep?
8. Volume: vendors onboarded per year, active vendors, reassessment cadence.
9. What triggered the review: cost, maintenance, missing risk content, or vendor experience?

### 12. Next steps
- Map the client's current onboarding steps to MineOS templates, rules and Integration Builder flows.
- Agree a pilot scope: one vendor tier, end to end, including one ERP or procurement integration.
- Plan the migration of existing vendor records from Appian.

---

## Internal only (do not put on slides)

**Where Appian may be ahead. Confirm the client actually uses these before treating them as gaps:**
- A free-form process designer with parallel paths and sub-processes.
- Multi-level approval chains by spend or tier, with SLA timers and escalation. MineOS approval is one manual status change; route complex approvals through ServiceNow or Jira.
- Native ERP connections and RPA bots. MineOS has no RPA.
- Sanctions, KYB, credit, banking or tax checks. MineOS doesn't offer these; they need a custom flow or stay in the ERP or procurement tool.
- Process mining (Appian Process HQ).

**Product limits to be aware of:**
- Rule conditions are AND-only, and the action set is fixed. Rules can't set fields, call webhooks or open Jira tickets directly; use Integration Builder.
- The public API can create vendors and assessments, invite collaborators, add form submissions, fire the risk review trigger and move a vendor to Trash. It cannot write custom fields, the review status or risks.
- Outbound webhooks: `TprmTrigger` and `SystemStatusChange`.
- Rules are likely configured by Mine staff, and Integration Builder flows are built by Mine. Say "we build it with you", not "drag and drop it yourself".
- The automatic offboarding rule (create the Offboarding assessment when a vendor moves to Trash) is supported but not on by default.
- Reassessment uses per-assessment review dates and reminders. There's no recurring cadence engine; use a scheduled flow.

**Verify before promising:**
- Which Prismatic connectors exist for the client's ERP and procurement stack.
- Whether customers can use the Integration Builder designer themselves.
- Roadmap for public API writes to custom fields, review status and risks.
- Whether customers can configure rules themselves.
- How external collaborators sign in (magic link or password).

**Sources:** Appian research brief (docs.appian.com 26.x, partner pages); the MineOS codebase and internal Slack, reviewed 20 October 2026. MineOS ReadMe guides couldn't be read.
