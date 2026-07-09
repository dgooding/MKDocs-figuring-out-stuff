---
title: Advanced feature showcase
description: Full Material for MkDocs feature demo — diagrams, tabs, annotations, cards, admonitions, and more
tags:
  - guide
  - showcase
  - mkdocs
  - advanced
---

# Advanced feature showcase

<div class="showcase-hero" markdown>

:material-star-four-points: **Bells and whistles mode**

This page is the advanced Material for MkDocs demo linked from the **four-point star** icon in the header (next to search and the theme toggle). It demonstrates patterns used on high-end docs sites: [Material for MkDocs reference](https://squidfunk.github.io/mkdocs-material/reference/), diagrams, tabs, annotations, cards, and more.

[Open convert-to-Markdown guide](convert-files-to-markdown.md){ .md-button }
[Back to home](../index.md){ .md-button .md-button--primary }

</div>

---

## Theme chrome (look at the header)

| Control | What it does |
|---------|----------------|
| :material-magnify: **Search** | Full-text search with suggestions (`search.suggest`) and shareable results |
| :material-weather-night: / :material-weather-sunny: / :material-brightness-auto: **Palette** | Light, dark, or system preference |
| :material-star-four-points: **This page** | Custom header action (theme override) |
| :fontawesome-brands-github: **Repo** | Jump to GitHub source |
| Sticky **tabs** | Top-level sections stay available while scrolling |

---

## Admonitions (callouts)

Use these to make policies and SOPs scannable under pressure.

!!! note "Note"
    Neutral context that supports the main procedure.

!!! abstract "Summary / TL;DR"
    Collapse the whole article into one tight takeaway.

!!! info "Info"
    Background or system behavior the reader should know.

!!! tip "Tip"
    Faster path or power-user shortcut.

!!! success "Success"
    Expected healthy outcome after the steps.

!!! question "Question"
    Common agent or end-user FAQ.

!!! warning "Warning"
    Easy to get wrong — pause before continuing.

!!! failure "Failure"
    Known bad state or failed validation.

!!! danger "Danger"
    Security, data loss, or major-incident risk.

!!! bug "Bug"
    Known defect or vendor limitation.

!!! example "Example"
    Concrete ticket wording or sample payload.

!!! quote "Quote"
    Policy excerpt or external standard.

### Collapsible blocks

??? tip "Expand for the long version"
    Extra detail lives here so the default view stays short. Perfect for edge cases, vendor IDs, and deep troubleshooting trees.

???+ warning "Open by default"
    Use `???+` when the warning must be visible immediately but can still collapse after read.

---

## Content tabs

Group OS-specific or tool-specific steps without duplicating whole pages.

=== "Windows"

    ```powershell
    cd ~\MKDocs-figuring-out-stuff
    .\.venv\Scripts\Activate.ps1
    mkdocs serve
    ```

    Then open [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

=== "macOS / Linux"

    ```bash
    cd ~/MKDocs-figuring-out-stuff
    source .venv/bin/activate
    mkdocs serve
    ```

=== "Docker (idea)"

    ```bash
    docker run --rm -it -p 8000:8000 -v ${PWD}:/docs squidfunk/mkdocs-material
    ```

Nested tabs also work for API examples:

=== "cURL"

    ```bash
    curl -sS -X POST https://api.contoso.example/v1/tickets \
      -H "Authorization: Bearer $TOKEN" \
      -H "Content-Type: application/json" \
      -d '{"title":"VPN down","severity":2}'
    ```

=== "PowerShell"

    ```powershell
    Invoke-RestMethod -Method Post `
      -Uri "https://api.contoso.example/v1/tickets" `
      -Headers @{ Authorization = "Bearer $TOKEN" } `
      -ContentType "application/json" `
      -Body (@{ title = "VPN down"; severity = 2 } | ConvertTo-Json)
    ```

=== "Python"

    ```python
    import os, requests

    r = requests.post(
        "https://api.contoso.example/v1/tickets",
        headers={"Authorization": f"Bearer {os.environ['TOKEN']}"},
        json={"title": "VPN down", "severity": 2},
        timeout=30,
    )
    r.raise_for_status()
    print(r.json())
    ```

---

## Code blocks with line numbers, copy, and annotations

Hover a code block to copy. Numbers and annotations help walk an agent through a script.

```python title="triage_ticket.py" linenums="1" hl_lines="6-8"
from enum import Enum

class Severity(Enum):
    SEV1 = 1
    SEV2 = 2
    SEV3 = 3
    SEV4 = 4

def choose_severity(users_impacted: int, workaround: bool) -> Severity:
    if users_impacted >= 50:
        return Severity.SEV1  # (1)
    if users_impacted >= 5 and not workaround:
        return Severity.SEV2  # (2)
    if users_impacted >= 1:
        return Severity.SEV3  # (3)
    return Severity.SEV4
```

1.  Company-wide or large cohort outages start at **Sev 1**.
2.  Multi-user impact with no workaround is **Sev 2**.
3.  Single-user / small group with business still moving is **Sev 3**.

Inline code and keys: press ++ctrl+k++ or ++slash++ to search; config lives in `mkdocs.yml`.

Mark text with ==highlights==, ^^insertions^^, and ~~strike~~ when comparing revisions.

---

## Keyboard keys, abbreviations, and tooltips

Hover the abbreviations after they are defined:

The service desk uses the SLA for Sev 1 and may open a MIR with CSIRT when security is involved.

*[SLA]: Service Level Agreement — contractual response and restore targets
*[MIR]: Major Incident Review / major incident response bridge
*[CSIRT]: Computer Security Incident Response Team

Tooltips on links work with Material’s `content.tooltips` feature:

[Password reset procedure](../how-to/password-reset.md "Agent + self-service steps")

---

## Buttons and icons

[Primary action](../getting-started/overview.md){ .md-button .md-button--primary }
[Secondary action](../policies/incident-severity.md){ .md-button }
[With icon :material-rocket-launch:](https://squidfunk.github.io/mkdocs-material/){ .md-button }

Icon + emoji soup for scannable lists:

- :material-shield-lock: Security first response  
- :material-vpn: Remote access  
- :material-email-fast: Messaging  
- :fontawesome-solid-headset: Live agent support  
- :octicons-dependabot-16: Automation candidates  

---

## Task lists and definition lists

### Onboarding checklist

- [x] Create identity from HR ticket  
- [x] Assign license bundle  
- [ ] Confirm MFA enrollment  
- [ ] Close ticket after user confirmation  

### Definitions

Service request
:   A planned ask (access, hardware, software) — not an unplanned outage.

Incident
:   Unplanned interruption or degradation of an IT service.

Problem
:   Root cause of one or more incidents; tracked separately from the break/fix ticket.

---

## Tables (status + data)

| Severity | Initial response | Example | Status |
|----------|------------------|---------|--------|
| Sev 1 | 15 minutes | Email down company-wide | :material-circle:{ .red } Critical |
| Sev 2 | 1 hour | Regional VPN outage | :material-circle:{ .orange } Major |
| Sev 3 | 4 hours | Single laptop print fail | :material-circle:{ .blue } Normal |
| Sev 4 | 1 business day | Cosmetic desktop issue | :material-circle:{ .green } Low |

Grid of cards for navigation-style layouts:

<div class="grid cards" markdown>

-   :material-book-open-variant:{ .lg .middle } **Authoring**

    ---

    Standards for clear, searchable articles

    [:octicons-arrow-right-24: KB guidelines](../reference/kb-authoring.md)

-   :material-file-replace:{ .lg .middle } **Import pipeline**

    ---

    Convert Word/PDF libraries into Markdown

    [:octicons-arrow-right-24: Conversion guide](convert-files-to-markdown.md)

-   :material-graph:{ .lg .middle } **Diagrams**

    ---

    Mermaid flow, sequence, and ER charts below

    [:octicons-arrow-right-24: Jump to diagrams](#mermaid-diagrams)

-   :material-palette-swatch:{ .lg .middle } **Theming**

    ---

    Custom CSS, fonts, header actions, dark mode

    [:octicons-arrow-right-24: Material docs](https://squidfunk.github.io/mkdocs-material/)

</div>

---

## Mermaid diagrams

Native Mermaid support (via `pymdownx.superfences` custom fence) — colors follow the theme.

### Service desk intake flowchart

``` mermaid
graph TD
  A[User reports issue] --> B{Self-service KB hit?}
  B -->|Yes| C[Resolve without ticket]
  B -->|No| D[Open ticket in portal]
  D --> E{Security related?}
  E -->|Yes| F[Tag Security + page CSIRT]
  E -->|No| G[Tier 1 triage]
  G --> H{Known fix?}
  H -->|Yes| I[Apply fix / close]
  H -->|No| J[Escalate Tier 2]
  F --> K[Incident bridge]
  J --> L[Resolve + knowledge article?]
  I --> L
  K --> L
```

### Password reset sequence

``` mermaid
sequenceDiagram
  autonumber
  actor User
  participant Portal as Self-service portal
  participant MFA as Authenticator
  participant Desk as Service Desk
  participant IdP as Identity platform

  User->>Portal: Request password reset
  Portal->>MFA: Challenge
  MFA-->>User: Approve prompt
  User->>Portal: Set new password
  alt Self-service succeeds
    Portal->>IdP: Commit password change
    IdP-->>User: Success
  else Self-service fails
    User->>Desk: Open ticket
    Desk->>User: Verify identity
    Desk->>IdP: Admin reset + force change
    IdP-->>User: Temporary password (secure channel)
  end
```

### Entity relationship (simplified CMDB)

``` mermaid
erDiagram
  EMPLOYEE ||--o{ DEVICE : is-assigned
  EMPLOYEE ||--o{ TICKET : opens
  DEVICE ||--o{ TICKET : mentioned-in
  TICKET }o--|| SERVICE : impacts
  TICKET }o--o| CHANGE : linked-to
  SERVICE ||--o{ SLA : governed-by
```

### State machine — major incident

``` mermaid
stateDiagram-v2
  [*] --> Detected
  Detected --> Triaged
  Triaged --> Mitigating
  Mitigating --> Monitoring
  Monitoring --> Resolved
  Resolved --> Postmortem
  Postmortem --> [*]
  Triaged --> MajorBridge: Sev1 / wide Sev2
  MajorBridge --> Mitigating
```

---

## Math (when you need formulas)

Inline: the availability target \( A = \frac{\text{uptime}}{\text{uptime}+\text{downtime}} \).

Block:

\[
\text{SLA credit} = \max\left(0,\; R - \frac{\text{actual uptime}}{\text{month minutes}}\right) \times C
\]

---

## Footnotes and citations

Agents should cite the source procedure in the ticket[^kb]. For security events, attach the timeline to the CSIRT handoff[^sec].

[^kb]: Knowledge articles are living documents — link the page URL, not a screenshot alone.
[^sec]: See the [security incident quick reference](../reference/security-incident.md).

---

## Nested formatting playground

> **Blockquote** for policy callouts from leadership.
>
> > Nested quote for “exact wording from the standard.”

1. Ordered step one  
   - Nested bullet  
   - Nested bullet  
2. Ordered step two with `inline code` and **bold** / *italic* / ***both***  
3. Step with a footnote marker[^kb]

---

## What powers this page (config map)

| Capability | Enabled via |
|------------|-------------|
| Material theme + dark mode | `theme.name`, `theme.palette` |
| Instant nav + sticky tabs | `navigation.*` features |
| Search suggest / highlight / share | `search.*` features + search plugin |
| Code copy + annotate | `content.code.copy`, `content.code.annotate` |
| Tabs, task lists, critic marks | `pymdownx.tabbed`, `tasklist`, `mark`, `tilde`, `caret` |
| Mermaid diagrams | `pymdownx.superfences` → `custom_fences: mermaid` |
| Icons / emoji | `pymdownx.emoji` + Material icon sets |
| Admonitions + details | `admonition`, `pymdownx.details` |
| Math | `pymdownx.arithmatex` (+ MathJax if you add JS) |
| Header star icon | `overrides/partials/header.html` |
| Brand CSS | `docs/stylesheets/extra.css` |

!!! success "Show this to your team"
    This page is intentionally loud. Production SOPs can stay quieter — reuse only the patterns that improve scan-speed for agents.

## Related

- [Convert a file library to Markdown](convert-files-to-markdown.md)
- [KB authoring guidelines](../reference/kb-authoring.md)
- [Official Material reference](https://squidfunk.github.io/mkdocs-material/reference/)
