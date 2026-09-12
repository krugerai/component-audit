# Component Audit

## Overview

Component Audit evaluates one React UI component against WCAG 2.2 Level AA. It identifies supported passes and failures, locates each finding, cites the governing provision, and assigns severity to each failure.

Its conclusions cover only the supplied component, dependencies, states, and evidence. It does not certify a page, website, product, organization, or legal compliance.

## Usage

### 1. Add The Auditor

Add every file in this folder to one Claude Project. Preserve the filenames and `reference/` structure so each finding can link to its provision in `reference/wcag-2.2.html`.

### 2. Supply One Component

Provide:

- the component's name and purpose;
- its React entry source file;
- the exact repository commit SHA, or `not applicable` for directly supplied source;
- one concrete invocation with fixed props, or a complete prop and configuration matrix;
- all local dependencies that affect rendering or behavior, including styles, tokens, hooks, providers, utilities, and imported components; and
- all known states and variants, or a statement that the list is incomplete.

Supply the component files directly or select them from a connected GitHub repository. A repository or website URL works only when Claude can retrieve the required evidence. A live website supplies runtime evidence but cannot replace the component source, its dependencies, or its state inventory in a complete audit.

Add relevant runtime evidence when available, such as rendered screenshots or HTML, keyboard observations, accessibility-tree output, computed colors, contrast results, or element dimensions. Component Audit marks missing evidence instead of assuming a pass.

Do not include credentials, secrets, or unrelated project material.

### 3. Run The Audit

```text
Read identity.md and rules.md, then audit the supplied React component.

Component: [name]
Purpose: [intended purpose]
Entry file: [path]
Source revision: [commit SHA or not applicable]
Invocation and props: [concrete usage or complete configuration matrix]
Dependencies: [paths or missing items]
States and variants: [complete list, or say that the list is incomplete]
Additional evidence: [items with type, locator, scope, and limit, or none]
```

### 4. Read The Result

Component Audit reports `PASS`, `FAIL`, or `CANNOT DETERMINE` for each finding and `NOT APPLICABLE` for criteria that do not apply to the supplied component. Every finding includes an exact location and a citation to the included standard.

Each failure receives `Critical`, `Major`, or `Minor` severity. Coverage is reported separately as `COMPLETE` or `INCOMPLETE`; an incomplete audit identifies what was omitted and issues no conclusion. Component Audit reports counts, not a numeric compliance score.

See [audit rules](rules.md) for the exact procedure and output contract. See [example audits](examples.md) for complete and incomplete results.

## Documentation

- [Auditor identity](identity.md) - Role, scope, authority, and limits.
- [Audit rules](rules.md) - Procedure, classifications, citations, severity, and output.
- [Example audits](examples.md) - Three examples: one complete and two incomplete.
- [WCAG 2.2 Level AA index](reference/index.md) - Links to the 55 Level A and Level AA criteria.
- [WCAG 2.2 Recommendation](reference/wcag-2.2.html) - Authoritative standard.
