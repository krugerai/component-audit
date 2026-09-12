# Component Audit Example Audits

These synthetic examples show how to apply the [audit rules](rules.md). They do not define rules or replace the [canonical WCAG 2.2 Recommendation](reference/wcag-2.2.html).

Virtual paths refer to fixture files embedded in this document. Visible `NN │` gutters mark the example line locations; they are not source bytes. Finding identifiers restart at `CA-001` in each example.

Live audits use the exact H1 and H2 output levels defined in `rules.md`. These examples nest the same labels to preserve this document's hierarchy.

## Example 1: Complete RecordActions Audit

### Supplied Audit Request

- Component: `RecordActions`
- Source revision: `not applicable` — embedded fixture source
- Invocation and props: `<RecordActions onSave={fixtureOnSave} onDelete={fixtureOnDelete} />`; callback implementations are not supplied
- Intended purpose: Offer a primary Save action and a secondary Delete action for an unsaved local draft. Neither action creates a legal or financial commitment or changes persistent user-controlled data in this fixture.
- State inventory: Complete. Default, hover, keyboard focus, pointer press, and activation are supported. The component has no disabled, read-only, loading, error, success, expanded, selected, responsive, or environmental variant.
- Meaningful order: Save precedes Delete visually and programmatically to communicate primary-before-destructive action priority.

### Embedded Component Boundary

- `RecordActions.tsx`
- `RecordActions.css`
- `RecordActions.requirements.txt`
- Evidence `RA-E01` through `RA-E07`
- Limitation `RA-L01`

Default, hover, and pointer-press states share the same accessibility semantics, colors, dimensions, and labels. The audit groups them when their evidence and result match.

### Embedded Source

`RecordActions.tsx`

```text
01 │ import "./RecordActions.css";
02 │
03 │ type Props = { onSave: () => void; onDelete: () => void };
04 │
05 │ export function RecordActions({ onSave, onDelete }: Props) {
06 │   return (
07 │     <div role="group" aria-label="Record actions" className="recordActions">
08 │       <button type="button" className="recordAction saveAction" aria-label="Save record" onClick={onSave}>
09 │         <svg aria-hidden="true" focusable="false" width="16" height="16" viewBox="0 0 24 24"><path fill="currentColor" d="M5 3h12l2 2v16H5zM8 3v6h8V3zM8 14h8v5H8z" /></svg>
10 │       </button>
11 │       <button type="button" className="recordAction deleteAction" aria-label="Remove record" onClick={onDelete}>
12 │         Delete
13 │       </button>
14 │     </div>
15 │   );
16 │ }
```

`RecordActions.css`

```text
01 │ .recordActions {
02 │   display: inline-flex;
03 │   gap: 0;
04 │ }
05 │
06 │ .recordAction {
07 │   width: 20px;
08 │   height: 20px;
09 │   padding: 0;
10 │   background: #ffffff;
11 │   border: 0;
12 │ }
13 │
14 │ .saveAction { color: #b5b5b5; }
15 │ .deleteAction { color: #000000; }
16 │ .recordAction:focus { outline: none; }
```

`RecordActions.requirements.txt`

```text
01 │ The supplied specimen page contains no equivalent Save or Delete target.
02 │ The exact 20 CSS px presentation is not essential or legally required.
03 │ Component-authored CSS controls the target dimensions.
```

### Embedded Evidence

| ID | Type | Locator or environment | Observation or value | Limit |
|---|---|---|---|---|
| `RA-E01` | Accessibility tree | Rendered component | Named group “Record actions”; Save button named “Save record”; Delete button named “Remove record” | Does not prove visual presentation or interaction |
| `RA-E02` | Interaction | Keyboard and pointer observation | Tab order is Save then Delete; Enter and Space activate each button; Tab exits the group; activation occurs on pointer-up; focus alone causes no context change | Does not prove source structure, visual order, or behavior outside the component callbacks |
| `RA-E03` | Rendered | Default and keyboard-focus states | Visual order is Save then Delete; Save is an icon-only control; Delete visibly reads “Delete”; neither keyboard-focused button has a visible focus indicator; neither focused button is obscured | Does not prove source structure, zoom, reflow, or text-spacing behavior |
| `RA-E04` | Computed value | Browser-computed styles and DOM rectangles | Save icon `#b5b5b5` on `#ffffff`; Delete text `#000000` on `#ffffff` at `16 CSS px`, weight `400`; both targets are `20 × 20 CSS px`; center distance is `20 CSS px` | Values are for the supplied specimen and states only |
| `RA-E05` | Rendered | Visual meaning | Save uses a disk icon and Delete uses text; no distinction relies on color alone | Does not establish meaning outside the supplied purpose |
| `RA-E06` | Rendered | Complete target inventory for the supplied specimen page | No same-page equivalent Save or Delete target exists | Applies only to the Target Size equivalent-target exception; it does not expand the audit target beyond the component |
| `RA-E07` | Source | `RecordActions.requirements.txt:02-03` and `RecordActions.css:06-08` | The `20 CSS px` presentation is author-controlled and is not essential or legally required | Applies only to the Target Size user-agent-control and essential exceptions |

### Embedded Evidence Limitations

| ID | Missing material | Effect |
|---|---|---|
| `RA-L01` | No 200% text-resize, 320-CSS-pixel reflow, user text-spacing override, inherited host-language, or callback-effect observation was supplied | Blocks SC 1.4.4, 1.4.10, 1.4.12, 3.1.2, and 3.3.4 results |

### Component Audit

#### Audit Target

`RecordActions` in `RecordActions.tsx:05-16`, including `RecordActions.css:01-16`, `RecordActions.requirements.txt:01-03`, the complete declared state inventory, evidence `RA-E01` through `RA-E07`, and limitation `RA-L01`.

#### Evidence Reviewed

The evidence includes two source files, fixture requirements, accessibility-tree output, keyboard and pointer observations, rendered default and focus states, computed colors, font values and dimensions, visual-meaning evidence, and a complete rendered inventory of same-page targets. It does not include runtime resize, reflow, text-spacing, callback-effect, or inherited-language observations.

#### Coverage Status

`COMPLETE`

The audit reviewed all 55 criteria for applicability and evaluated every identified target and state. No criterion, target, state, or working-ledger row remains unreviewed.

#### Summary

| Measure | Count |
|---|---:|
| Required criteria | 55 |
| Evaluated criteria | 55 |
| Omitted criteria | 0 |
| Criterion `PASS` | 13 |
| Criterion `FAIL` | 4 |
| Criterion `CANNOT DETERMINE` | 5 |
| Criterion `NOT APPLICABLE` | 33 |
| Target-finding `PASS` | 13 |
| Target-finding `FAIL` | 4 |
| Target-finding `CANNOT DETERMINE` | 5 |
| Failure severity `Critical` | 0 |
| Failure severity `Major` | 3 |
| Failure severity `Minor` | 1 |

- Audit target: `RecordActions` within the boundary stated above
- Source revision: `not applicable` — embedded fixture source
- Audited invocation and props: `<RecordActions onSave={fixtureOnSave} onDelete={fixtureOnDelete} />`; callback implementations are not supplied
- Audited files: `RecordActions.tsx`, `RecordActions.css`, and `RecordActions.requirements.txt`
- Audited states and variants: default, hover, keyboard focus, pointer press, and activation; no additional variant is implemented
- Standard target: WCAG 2.2 Level AA
- Evidence limitation: runtime resize, reflow, text-spacing, callback-effect, and inherited-language observations were not supplied

#### Failed Findings

##### CA-001: Save icon lacks required non-text contrast

- Result: `FAIL`
- Component and state: `RecordActions`, Save, default/hover/pointer press
- Location: `RecordActions.css:14`; evidence `RA-E03`, `RA-E04`, and `RA-E05`
- Criterion: [WCAG 2.2 SC 1.4.11 — Non-text Contrast](reference/wcag-2.2.html#non-text-contrast), Level AA
- Evidence: The Save icon is the visual means of identifying the control and resolves to `#b5b5b5` on `#ffffff`.
- Evidence limit: The values apply to the supplied specimen only.
- Inputs: foreground `#b5b5b5`; background `#ffffff`
- Method: WCAG relative-luminance contrast calculation
- Observed value: unrounded `2.0504728794861493:1`; displayed `2.0505:1`
- Required threshold: `3:1`
- Units and precision: contrast ratio, displayed to four decimal places; comparison used the unrounded value
- Severity: `Major`
- Severity basis: Low-vision users may not perceive the only visible Save identifier, substantially impeding identification while the accessible name remains available through assistive technology.
- Remediation: Use an icon color that reaches at least `3:1` against the button background in every supported state.
- Recheck: Resolve the final foreground and background colors, recompute the unrounded contrast ratio, and confirm it reaches `3:1` or greater.

##### CA-002: Keyboard focus has no visible indicator

- Result: `FAIL`
- Component and state: `RecordActions`, Save and Delete, keyboard focus
- Location: `RecordActions.css:16`; evidence `RA-E02` and `RA-E03`
- Criterion: [WCAG 2.2 SC 2.4.7 — Focus Visible](reference/wcag-2.2.html#focus-visible), Level AA
- Evidence: CSS removes the focus outline, and rendered keyboard-focus evidence shows no other visible focus indicator.
- Evidence limit: The observation covers the supplied buttons and focus state only.
- Severity: `Major`
- Severity basis: Keyboard users can operate the buttons but cannot visually locate which action has focus, creating a substantial operational impediment.
- Remediation: Provide a visible focus indicator for both buttons without suppressing it unless an equivalent indicator replaces it.
- Recheck: Navigate to each button by keyboard and confirm a visible indicator identifies the focused control.

##### CA-003: Delete accessible name does not contain its visible label

- Result: `FAIL`
- Component and state: `RecordActions`, Delete, all supported states
- Location: `RecordActions.tsx:11-12`; evidence `RA-E01` and `RA-E03`
- Criterion: [WCAG 2.2 SC 2.5.3 — Label in Name](reference/wcag-2.2.html#label-in-name), Level A
- Evidence: The visible label is “Delete,” while the exposed accessible name is “Remove record”; the visible text is not contained in the accessible name.
- Evidence limit: The result applies to the supplied label and name.
- Severity: `Major`
- Severity basis: Speech-input users may invoke the visible word “Delete” without matching the control's programmatic name, substantially impeding operation while other input methods remain.
- Remediation: Use an accessible name that contains the visible label, such as “Delete record.”
- Recheck: Confirm the computed accessible name contains the exact visible text “Delete” in the same order.

##### CA-004: Adjacent pointer targets are below the minimum size and spacing

- Result: `FAIL`
- Component and state: `RecordActions`, Save and Delete, default/hover/pointer press
- Location: `RecordActions.css:01-08` and `RecordActions.requirements.txt:01-03`; evidence `RA-E04`, `RA-E06`, and `RA-E07`
- Criterion: [WCAG 2.2 SC 2.5.8 — Target Size (Minimum)](reference/wcag-2.2.html#target-size-minimum), Level AA
- Evidence: Both targets measure `20 × 20 CSS px`, have zero gap, and have centers `20 CSS px` apart. The supplied specimen has no same-page equivalent target; the controls are not inline; author CSS sets their size; and the fixture requirements establish that the presentation is not essential or legally required.
- Evidence limit: The measurements and exception evidence apply only to the supplied specimen.
- Inputs: width `20 CSS px`; height `20 CSS px`; center distance `20 CSS px`; required minimum-circle diameter `24 CSS px`
- Method: Browser `DOMRect` measurement and center-spacing comparison
- Observed value: each target is `4 CSS px` below the minimum in both dimensions; two `24 CSS px` diameter circles centered `20 CSS px` apart overlap by `4 CSS px`
- Required threshold: target size of at least `24 × 24 CSS px`, or spacing that prevents the minimum circles from intersecting
- Units and precision: CSS pixels, measured to one decimal place; comparison used unrounded browser values
- Severity: `Minor`
- Severity basis: The undersized adjacent targets create a localized motor-access barrier, while both actions remain operable through keyboard and pointer input.
- Remediation: Increase each target to at least `24 × 24 CSS px` or provide sufficient separation to satisfy the spacing condition.
- Recheck: Measure both targets and their center spacing in every supported state and confirm that size or spacing meets the canonical requirement.

#### Cannot-Determine Results

##### CA-005: Text behavior at 200% resize is unresolved

- Result: `CANNOT DETERMINE`
- Component and state: `RecordActions`, Delete, default and resized text
- Location: `RecordActions.tsx:11-12`; limitation `RA-L01`
- Criterion: [WCAG 2.2 SC 1.4.4 — Resize Text](reference/wcag-2.2.html#resize-text), Level AA
- Blocking evidence: No 200% text-resize observation was supplied.
- Evidence needed: Render the component with text resized to 200% without assistive technology and inspect content and functionality.
- Resolution check: Confirm the visible Delete label can be resized to 200% without loss of content or functionality.

##### CA-006: Reflow at the required narrow viewport is unresolved

- Result: `CANNOT DETERMINE`
- Component and state: `RecordActions`, complete component, narrow viewport
- Location: `RecordActions.css:01-16`; limitation `RA-L01`
- Criterion: [WCAG 2.2 SC 1.4.10 — Reflow](reference/wcag-2.2.html#reflow), Level AA
- Blocking evidence: No 320-CSS-pixel viewport or equivalent zoom observation was supplied.
- Evidence needed: Render the complete component at the canonical reflow condition.
- Resolution check: Inspect for lost content or functionality and for scrolling in two dimensions under the criterion's conditions and exceptions.

##### CA-007: User text-spacing overrides are unresolved

- Result: `CANNOT DETERMINE`
- Component and state: `RecordActions`, Delete, overridden text spacing
- Location: `RecordActions.tsx:11-12` and `RecordActions.css:06-15`; limitation `RA-L01`
- Criterion: [WCAG 2.2 SC 1.4.12 — Text Spacing](reference/wcag-2.2.html#text-spacing), Level AA
- Blocking evidence: No observation with the criterion's text-spacing overrides was supplied.
- Evidence needed: Apply the canonical line-height, paragraph-spacing, letter-spacing, and word-spacing overrides to the rendered specimen.
- Resolution check: Confirm no content or functionality is lost.

##### CA-008: Language of component phrases cannot be determined

- Result: `CANNOT DETERMINE`
- Component and state: `RecordActions`, group, Save, and Delete, all supported states
- Location: `RecordActions.tsx:07-12`; limitation `RA-L01`
- Criterion: [WCAG 2.2 SC 3.1.2 — Language of Parts](reference/wcag-2.2.html#language-of-parts), Level AA
- Blocking evidence: The component exposes English phrases, but no local `lang` value or inherited page-language evidence was supplied.
- Evidence needed: Supply the rendered host language and accessibility-tree language exposure for the component phrases.
- Resolution check: Confirm that the human language of each component phrase can be programmatically determined.

##### CA-009: Delete consequence and safeguard behavior cannot be determined

- Result: `CANNOT DETERMINE`
- Component and state: `RecordActions`, Delete, activation
- Location: `RecordActions.tsx:11-13`; limitation `RA-L01`
- Criterion: [WCAG 2.2 SC 3.3.4 — Error Prevention (Legal, Financial, Data)](reference/wcag-2.2.html#error-prevention-legal-financial-data), Level AA
- Blocking evidence: The component delegates Delete to `onDelete`; the callback effect and any confirmation, reversal, or verification safeguard were not supplied.
- Evidence needed: Supply the callback implementation and observed effect, including whether it creates a legal or financial commitment or modifies or deletes user-controllable stored data.
- Resolution check: If the criterion applies, verify that the action is reversible, checked for input errors with an opportunity to correct, or confirmed before finalization as the canonical provision requires.

#### Passed Findings

##### CA-010: Non-text controls have text alternatives

- Result: `PASS`
- Component and state: `RecordActions`, Save, all supported states
- Location: `RecordActions.tsx:08-09`; evidence `RA-E01`
- Criterion: [WCAG 2.2 SC 1.1.1 — Non-text Content](reference/wcag-2.2.html#non-text-content), Level A
- Evidence: The Save control exposes “Save record,” and its redundant SVG is hidden from the accessibility tree.
- Evidence limit: Accessibility-tree evidence covers the supplied component only.

##### CA-011: Visual action grouping is programmatically exposed

- Result: `PASS`
- Component and state: `RecordActions`, named action group, all supported states
- Location: `RecordActions.tsx:07-14`; evidence `RA-E01`
- Criterion: [WCAG 2.2 SC 1.3.1 — Info and Relationships](reference/wcag-2.2.html#info-and-relationships), Level A
- Evidence: The visually grouped controls are exposed as a named group, “Record actions.”
- Evidence limit: The result covers the supplied group relationship only.

##### CA-012: Meaningful action order is programmatically preserved

- Result: `PASS`
- Component and state: `RecordActions`, action order, all supported states
- Location: `RecordActions.tsx:07-14`; evidence `RA-E02` and `RA-E03`
- Criterion: [WCAG 2.2 SC 1.3.2 — Meaningful Sequence](reference/wcag-2.2.html#meaningful-sequence), Level A
- Evidence: Source order, rendered visual order, and observed Tab order are all Save then Delete.
- Evidence limit: The result covers the supplied two-action sequence.

##### CA-013: Action meaning does not rely on color alone

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, all supported states
- Location: `RecordActions.tsx:08-12`; evidence `RA-E05`
- Criterion: [WCAG 2.2 SC 1.4.1 — Use of Color](reference/wcag-2.2.html#use-of-color), Level A
- Evidence: Save uses a distinct disk shape and Delete uses visible text; color is not the only visual means of distinguishing the actions.
- Evidence limit: The result covers the supplied action identifiers.

##### CA-014: Visible Delete text meets minimum contrast

- Result: `PASS`
- Component and state: `RecordActions`, Delete, default/hover/pointer press
- Location: `RecordActions.css:10,15`; evidence `RA-E03` and `RA-E04`
- Criterion: [WCAG 2.2 SC 1.4.3 — Contrast (Minimum)](reference/wcag-2.2.html#contrast-minimum), Level AA
- Evidence: Delete text resolves to black on white.
- Evidence limit: The colors apply to the supplied states only.
- Inputs: foreground `#000000`; background `#ffffff`; font size `16 CSS px`; font weight `400`
- Method: WCAG relative-luminance contrast calculation
- Observed value: unrounded and displayed `21:1`
- Required threshold: `4.5:1` for the supplied normal-size text
- Units and precision: contrast ratio; exact endpoint colors require no rounding for comparison

##### CA-015: Both actions are keyboard operable

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, keyboard activation
- Location: `RecordActions.tsx:08-13`; evidence `RA-E02`
- Criterion: [WCAG 2.2 SC 2.1.1 — Keyboard](reference/wcag-2.2.html#keyboard), Level A
- Evidence: Tab reaches both native buttons and Enter and Space activate each one.
- Evidence limit: The observation covers the supplied component callbacks only.

##### CA-016: Keyboard focus is not trapped

- Result: `PASS`
- Component and state: `RecordActions`, action group, keyboard traversal
- Location: `RecordActions.tsx:07-14`; evidence `RA-E02` and `RA-E03`
- Criterion: [WCAG 2.2 SC 2.1.2 — No Keyboard Trap](reference/wcag-2.2.html#no-keyboard-trap), Level A
- Evidence: Tab enters, traverses, and exits the group using ordinary keyboard navigation.
- Evidence limit: The observation covers the supplied component only.

##### CA-017: Focus order matches the meaningful visual order

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, keyboard traversal
- Location: `RecordActions.tsx:07-14`; evidence `RA-E02` and `RA-E03`
- Criterion: [WCAG 2.2 SC 2.4.3 — Focus Order](reference/wcag-2.2.html#focus-order), Level A
- Evidence: Source order, rendered visual order, and observed Tab order are Save then Delete.
- Evidence limit: The result covers the supplied two-control focus sequence.

##### CA-018: Visible action labels describe their controls

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, all supported states
- Location: `RecordActions.tsx:08-12`; evidence `RA-E03` and `RA-E05`
- Criterion: [WCAG 2.2 SC 2.4.6 — Headings and Labels](reference/wcag-2.2.html#headings-and-labels), Level AA
- Evidence: The visible disk graphic identifies Save and the visible text “Delete” identifies Delete.
- Evidence limit: The group accessible name is evaluated under SC 4.1.2; SC 2.5.3 separately evaluates the mismatch between Delete's visible and accessible labels.

##### CA-019: Focused controls are not obscured

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, keyboard focus
- Location: `RecordActions.tsx:08-13`; evidence `RA-E03`
- Criterion: [WCAG 2.2 SC 2.4.11 — Focus Not Obscured (Minimum)](reference/wcag-2.2.html#focus-not-obscured-minimum), Level AA
- Evidence: Each focused button remains fully visible and is not hidden by author-created content.
- Evidence limit: This does not satisfy SC 2.4.7; visibility of the focused component and visibility of a focus indicator are separate results.

##### CA-020: Pointer activation occurs on release

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, pointer activation
- Location: `RecordActions.tsx:08-13`; evidence `RA-E02`
- Criterion: [WCAG 2.2 SC 2.5.2 — Pointer Cancellation](reference/wcag-2.2.html#pointer-cancellation), Level A
- Evidence: Neither action executes on pointer-down; activation occurs on pointer-up.
- Evidence limit: The observation covers the supplied pointer interaction.

##### CA-021: Focus does not trigger a context change

- Result: `PASS`
- Component and state: `RecordActions`, Save and Delete, keyboard focus
- Location: `RecordActions.tsx:08-13`; evidence `RA-E02`
- Criterion: [WCAG 2.2 SC 3.2.1 — On Focus](reference/wcag-2.2.html#on-focus), Level A
- Evidence: Moving focus to either button causes no context change.
- Evidence limit: Activation behavior is outside this focus-only result.

##### CA-022: Roles, names, and values are exposed

- Result: `PASS`
- Component and state: `RecordActions`, group, Save, and Delete, all supported states
- Location: `RecordActions.tsx:07-13`; evidence `RA-E01`
- Criterion: [WCAG 2.2 SC 4.1.2 — Name, Role, Value](reference/wcag-2.2.html#name-role-value), Level A
- Evidence: The accessibility tree exposes a named group and two named buttons using supported native and ARIA semantics.
- Evidence limit: SC 2.5.3 separately evaluates whether Delete's accessible name contains its visible label.

#### Criterion Ledger

| Criterion | Title | Level | Result | Targets or reason | Canonical provision |
|---|---|---|---|---|---|
| 1.1.1 | Non-text Content | A | `PASS` | Save control | [WCAG 2.2 SC 1.1.1 — Non-text Content](reference/wcag-2.2.html#non-text-content) |
| 1.2.1 | Audio-only and Video-only (Prerecorded) | A | `NOT APPLICABLE` | No prerecorded audio-only or video-only media | [WCAG 2.2 SC 1.2.1 — Audio-only and Video-only (Prerecorded)](reference/wcag-2.2.html#audio-only-and-video-only-prerecorded) |
| 1.2.2 | Captions (Prerecorded) | A | `NOT APPLICABLE` | No prerecorded synchronized media | [WCAG 2.2 SC 1.2.2 — Captions (Prerecorded)](reference/wcag-2.2.html#captions-prerecorded) |
| 1.2.3 | Audio Description or Media Alternative (Prerecorded) | A | `NOT APPLICABLE` | No prerecorded synchronized media | [WCAG 2.2 SC 1.2.3 — Audio Description or Media Alternative (Prerecorded)](reference/wcag-2.2.html#audio-description-or-media-alternative-prerecorded) |
| 1.2.4 | Captions (Live) | AA | `NOT APPLICABLE` | No live synchronized media | [WCAG 2.2 SC 1.2.4 — Captions (Live)](reference/wcag-2.2.html#captions-live) |
| 1.2.5 | Audio Description (Prerecorded) | AA | `NOT APPLICABLE` | No prerecorded video | [WCAG 2.2 SC 1.2.5 — Audio Description (Prerecorded)](reference/wcag-2.2.html#audio-description-prerecorded) |
| 1.3.1 | Info and Relationships | A | `PASS` | Named action group | [WCAG 2.2 SC 1.3.1 — Info and Relationships](reference/wcag-2.2.html#info-and-relationships) |
| 1.3.2 | Meaningful Sequence | A | `PASS` | Save-before-Delete sequence | [WCAG 2.2 SC 1.3.2 — Meaningful Sequence](reference/wcag-2.2.html#meaningful-sequence) |
| 1.3.3 | Sensory Characteristics | A | `NOT APPLICABLE` | No instruction relies on sensory characteristics | [WCAG 2.2 SC 1.3.3 — Sensory Characteristics](reference/wcag-2.2.html#sensory-characteristics) |
| 1.3.4 | Orientation | AA | `NOT APPLICABLE` | Component does not restrict display orientation | [WCAG 2.2 SC 1.3.4 — Orientation](reference/wcag-2.2.html#orientation) |
| 1.3.5 | Identify Input Purpose | AA | `NOT APPLICABLE` | No input collects information about the user | [WCAG 2.2 SC 1.3.5 — Identify Input Purpose](reference/wcag-2.2.html#identify-input-purpose) |
| 1.4.1 | Use of Color | A | `PASS` | Save shape and Delete text convey action identity | [WCAG 2.2 SC 1.4.1 — Use of Color](reference/wcag-2.2.html#use-of-color) |
| 1.4.2 | Audio Control | A | `NOT APPLICABLE` | No automatically playing audio | [WCAG 2.2 SC 1.4.2 — Audio Control](reference/wcag-2.2.html#audio-control) |
| 1.4.3 | Contrast (Minimum) | AA | `PASS` | Visible Delete text | [WCAG 2.2 SC 1.4.3 — Contrast (Minimum)](reference/wcag-2.2.html#contrast-minimum) |
| 1.4.4 | Resize Text | AA | `CANNOT DETERMINE` | No 200% text-resize observation | [WCAG 2.2 SC 1.4.4 — Resize Text](reference/wcag-2.2.html#resize-text) |
| 1.4.5 | Images of Text | AA | `NOT APPLICABLE` | No image of text | [WCAG 2.2 SC 1.4.5 — Images of Text](reference/wcag-2.2.html#images-of-text) |
| 1.4.10 | Reflow | AA | `CANNOT DETERMINE` | No required narrow-viewport observation | [WCAG 2.2 SC 1.4.10 — Reflow](reference/wcag-2.2.html#reflow) |
| 1.4.11 | Non-text Contrast | AA | `FAIL` | Save icon | [WCAG 2.2 SC 1.4.11 — Non-text Contrast](reference/wcag-2.2.html#non-text-contrast) |
| 1.4.12 | Text Spacing | AA | `CANNOT DETERMINE` | No user text-spacing override observation | [WCAG 2.2 SC 1.4.12 — Text Spacing](reference/wcag-2.2.html#text-spacing) |
| 1.4.13 | Content on Hover or Focus | AA | `NOT APPLICABLE` | No additional content appears on hover or focus | [WCAG 2.2 SC 1.4.13 — Content on Hover or Focus](reference/wcag-2.2.html#content-on-hover-or-focus) |
| 2.1.1 | Keyboard | A | `PASS` | Save and Delete controls | [WCAG 2.2 SC 2.1.1 — Keyboard](reference/wcag-2.2.html#keyboard) |
| 2.1.2 | No Keyboard Trap | A | `PASS` | Record action group | [WCAG 2.2 SC 2.1.2 — No Keyboard Trap](reference/wcag-2.2.html#no-keyboard-trap) |
| 2.1.4 | Character Key Shortcuts | A | `NOT APPLICABLE` | No character-key shortcut | [WCAG 2.2 SC 2.1.4 — Character Key Shortcuts](reference/wcag-2.2.html#character-key-shortcuts) |
| 2.2.1 | Timing Adjustable | A | `NOT APPLICABLE` | No time limit | [WCAG 2.2 SC 2.2.1 — Timing Adjustable](reference/wcag-2.2.html#timing-adjustable) |
| 2.2.2 | Pause, Stop, Hide | A | `NOT APPLICABLE` | No moving, blinking, scrolling, or auto-updating content | [WCAG 2.2 SC 2.2.2 — Pause, Stop, Hide](reference/wcag-2.2.html#pause-stop-hide) |
| 2.3.1 | Three Flashes or Below Threshold | A | `NOT APPLICABLE` | No flashing content | [WCAG 2.2 SC 2.3.1 — Three Flashes or Below Threshold](reference/wcag-2.2.html#three-flashes-or-below-threshold) |
| 2.4.1 | Bypass Blocks | A | `NOT APPLICABLE` | Component creates no repeated page block | [WCAG 2.2 SC 2.4.1 — Bypass Blocks](reference/wcag-2.2.html#bypass-blocks) |
| 2.4.2 | Page Titled | A | `NOT APPLICABLE` | Component does not control a page title | [WCAG 2.2 SC 2.4.2 — Page Titled](reference/wcag-2.2.html#page-titled) |
| 2.4.3 | Focus Order | A | `PASS` | Save-before-Delete focus order | [WCAG 2.2 SC 2.4.3 — Focus Order](reference/wcag-2.2.html#focus-order) |
| 2.4.4 | Link Purpose (In Context) | A | `NOT APPLICABLE` | No link | [WCAG 2.2 SC 2.4.4 — Link Purpose (In Context)](reference/wcag-2.2.html#link-purpose-in-context) |
| 2.4.5 | Multiple Ways | AA | `NOT APPLICABLE` | Component does not locate pages in a set | [WCAG 2.2 SC 2.4.5 — Multiple Ways](reference/wcag-2.2.html#multiple-ways) |
| 2.4.6 | Headings and Labels | AA | `PASS` | Visible Save graphic and Delete text labels | [WCAG 2.2 SC 2.4.6 — Headings and Labels](reference/wcag-2.2.html#headings-and-labels) |
| 2.4.7 | Focus Visible | AA | `FAIL` | Save and Delete focus states | [WCAG 2.2 SC 2.4.7 — Focus Visible](reference/wcag-2.2.html#focus-visible) |
| 2.4.11 | Focus Not Obscured (Minimum) | AA | `PASS` | Save and Delete focus states | [WCAG 2.2 SC 2.4.11 — Focus Not Obscured (Minimum)](reference/wcag-2.2.html#focus-not-obscured-minimum) |
| 2.5.1 | Pointer Gestures | A | `NOT APPLICABLE` | No multipoint or path-based gesture | [WCAG 2.2 SC 2.5.1 — Pointer Gestures](reference/wcag-2.2.html#pointer-gestures) |
| 2.5.2 | Pointer Cancellation | A | `PASS` | Save and Delete pointer activation | [WCAG 2.2 SC 2.5.2 — Pointer Cancellation](reference/wcag-2.2.html#pointer-cancellation) |
| 2.5.3 | Label in Name | A | `FAIL` | Delete control | [WCAG 2.2 SC 2.5.3 — Label in Name](reference/wcag-2.2.html#label-in-name) |
| 2.5.4 | Motion Actuation | A | `NOT APPLICABLE` | No device-motion or user-motion operation | [WCAG 2.2 SC 2.5.4 — Motion Actuation](reference/wcag-2.2.html#motion-actuation) |
| 2.5.7 | Dragging Movements | AA | `NOT APPLICABLE` | No dragging operation | [WCAG 2.2 SC 2.5.7 — Dragging Movements](reference/wcag-2.2.html#dragging-movements) |
| 2.5.8 | Target Size (Minimum) | AA | `FAIL` | Save and Delete pointer targets | [WCAG 2.2 SC 2.5.8 — Target Size (Minimum)](reference/wcag-2.2.html#target-size-minimum) |
| 3.1.1 | Language of Page | A | `NOT APPLICABLE` | Component does not control the page language | [WCAG 2.2 SC 3.1.1 — Language of Page](reference/wcag-2.2.html#language-of-page) |
| 3.1.2 | Language of Parts | AA | `CANNOT DETERMINE` | Component phrases lack local or inherited language evidence | [WCAG 2.2 SC 3.1.2 — Language of Parts](reference/wcag-2.2.html#language-of-parts) |
| 3.2.1 | On Focus | A | `PASS` | Save and Delete focus states | [WCAG 2.2 SC 3.2.1 — On Focus](reference/wcag-2.2.html#on-focus) |
| 3.2.2 | On Input | A | `NOT APPLICABLE` | Component has no setting-changing input | [WCAG 2.2 SC 3.2.2 — On Input](reference/wcag-2.2.html#on-input) |
| 3.2.3 | Consistent Navigation | AA | `NOT APPLICABLE` | No repeated page-navigation mechanism | [WCAG 2.2 SC 3.2.3 — Consistent Navigation](reference/wcag-2.2.html#consistent-navigation) |
| 3.2.4 | Consistent Identification | AA | `NOT APPLICABLE` | No same-function components across a set of pages | [WCAG 2.2 SC 3.2.4 — Consistent Identification](reference/wcag-2.2.html#consistent-identification) |
| 3.2.6 | Consistent Help | A | `NOT APPLICABLE` | No repeated help mechanism | [WCAG 2.2 SC 3.2.6 — Consistent Help](reference/wcag-2.2.html#consistent-help) |
| 3.3.1 | Error Identification | A | `NOT APPLICABLE` | Component detects no input error | [WCAG 2.2 SC 3.3.1 — Error Identification](reference/wcag-2.2.html#error-identification) |
| 3.3.2 | Labels or Instructions | A | `NOT APPLICABLE` | Component requires no information entry | [WCAG 2.2 SC 3.3.2 — Labels or Instructions](reference/wcag-2.2.html#labels-or-instructions) |
| 3.3.3 | Error Suggestion | AA | `NOT APPLICABLE` | No automatically detected input error | [WCAG 2.2 SC 3.3.3 — Error Suggestion](reference/wcag-2.2.html#error-suggestion) |
| 3.3.4 | Error Prevention (Legal, Financial, Data) | AA | `CANNOT DETERMINE` | Delete callback effect and safeguards were not supplied | [WCAG 2.2 SC 3.3.4 — Error Prevention (Legal, Financial, Data)](reference/wcag-2.2.html#error-prevention-legal-financial-data) |
| 3.3.7 | Redundant Entry | A | `NOT APPLICABLE` | No information-entry process | [WCAG 2.2 SC 3.3.7 — Redundant Entry](reference/wcag-2.2.html#redundant-entry) |
| 3.3.8 | Accessible Authentication (Minimum) | AA | `NOT APPLICABLE` | No authentication step | [WCAG 2.2 SC 3.3.8 — Accessible Authentication (Minimum)](reference/wcag-2.2.html#accessible-authentication-minimum) |
| 4.1.2 | Name, Role, Value | A | `PASS` | Named group and native buttons | [WCAG 2.2 SC 4.1.2 — Name, Role, Value](reference/wcag-2.2.html#name-role-value) |
| 4.1.3 | Status Messages | AA | `NOT APPLICABLE` | Component creates no status message | [WCAG 2.2 SC 4.1.3 — Status Messages](reference/wcag-2.2.html#status-messages) |

#### Evidence Limitations

- Resize Text, Reflow, Text Spacing, component-phrase language, and Delete consequence safeguards remain `CANNOT DETERMINE` because the required runtime, inherited-language, or callback evidence was not supplied.
- Results apply only to the embedded component, declared states, and evidence.
- The audit does not evaluate callback effects beyond this fixture or any page, process, website, product, legal obligation, or organization.

#### Bounded Conclusion

Coverage Status is `COMPLETE`: the audit reviewed all 55 criteria for applicability within the supplied `RecordActions` boundary and evaluated every identified target and state. The ledger contains 13 `PASS`, 4 `FAIL`, 5 `CANNOT DETERMINE`, and 33 `NOT APPLICABLE` results. Evidence confirms failures in Save icon contrast, keyboard focus visibility, Delete label-in-name consistency, and pointer-target size and spacing. Resize Text, Reflow, Text Spacing, component-phrase language, and Delete safeguards remain unresolved. This component audit does not establish formal WCAG conformance for a page, process, website, product, or organization.

## Example 2: Compact EmailField Audit

This compact example shows the full return contract for an intentionally incomplete audit. It evaluates five of 55 criteria.

### Supplied Audit Request

- Component: `EmailField`
- Source revision: `not applicable` — embedded fixture source
- Invocations and props: `<EmailField />` and `<EmailField error="Enter a valid email" />`
- Intended purpose: Collect a required work email and show a validation error.
- State inventory: Default, invalid, and error-message-visible states are declared; runtime announcement behavior was not supplied.

### Embedded Component Boundary

- `EmailField.tsx`
- `EmailField.css`
- Evidence `EF-E01` through `EF-E03`

### Embedded Source

`EmailField.tsx`

```text
01 │ export function EmailField({ error }: { error?: string }) {
02 │   return (
03 │     <div>
04 │       <label htmlFor="email">Work email</label>
05 │       <p id="email-help">Required. Use your work address.</p>
06 │       <input id="email" type="email" required aria-invalid={Boolean(error)} aria-describedby="email-help" />
07 │       {error && <p id="email-error" className="errorText">{error}</p>}
08 │     </div>
09 │   );
10 │ }
```

`EmailField.css`

```text
01 │ .errorText {
02 │   color: #aaaaaa;
03 │   background: #ffffff;
04 │ }
```

### Embedded Evidence

| ID | Type | Locator or environment | Observation or value | Limit |
|---|---|---|---|---|
| `EF-E01` | Accessibility tree | `EmailField`, default and invalid states, supported browser accessibility tree | Input role `textbox`, name “Work email,” description “Required. Use your work address.,” invalid false by default and true when error is present | Error text is not included in the input description |
| `EF-E02` | Rendered | `EmailField`, invalid state after user entry, input and error region | User-entered input displays “not-an-email”; error “Enter a valid email” appears beside it | Does not prove announcement behavior |
| `EF-E03` | Computed value | `EmailField`, invalid state, browser-computed foreground, background, font size, and weight | Label, help, and input-value text `#000000` on `#ffffff`; error `#aaaaaa` on `#ffffff`; all at `16 CSS px`, weight `400`; ratios `21:1` and `2.3231230535045992:1` | Applies to the supplied visible text only |

### Component Audit

#### Audit Target

`EmailField` in `EmailField.tsx:01-10`, including `EmailField.css:01-04`, default, invalid, and error-message-visible states, and evidence `EF-E01` through `EF-E03`.

#### Evidence Reviewed

The evidence includes component and style source, default- and invalid-state accessibility trees, rendered label, help, input-value and error text, and computed colors, background, font size, and weight. It does not include dynamic announcement behavior.

#### Coverage Status

`INCOMPLETE`

This compact audit evaluates five criteria and intentionally omits fifty.

#### Summary

| Measure | Count |
|---|---:|
| Required criteria | 55 |
| Evaluated criteria | 5 |
| Omitted criteria | 50 |
| Criterion `PASS` | 2 |
| Criterion `FAIL` | 2 |
| Criterion `CANNOT DETERMINE` | 1 |
| Criterion `NOT APPLICABLE` | 0 |
| Target-finding `PASS` | 4 |
| Target-finding `FAIL` | 2 |
| Target-finding `CANNOT DETERMINE` | 1 |
| Failure severity `Critical` | 0 |
| Failure severity `Major` | 2 |
| Failure severity `Minor` | 0 |

- Audit target: `EmailField` within the boundary stated above
- Source revision: `not applicable` — embedded fixture source
- Audited invocations and props: `<EmailField />` and `<EmailField error="Enter a valid email" />`
- Audited files: `EmailField.tsx` and `EmailField.css`
- Audited states and variants: default, invalid, and error-message-visible; no additional variant was supplied
- Standard target: WCAG 2.2 Level AA
- Evidence limitation: dynamic assistive-technology announcement behavior was not supplied, and 50 criteria were intentionally omitted

#### Failed Findings

##### CA-001: Error relationship is not programmatically exposed

- Result: `FAIL`
- Component and state: `EmailField`, invalid with visible error
- Location: `EmailField.tsx:06-07`; evidence `EF-E01` and `EF-E02`
- Criterion: [WCAG 2.2 SC 1.3.1 — Info and Relationships](reference/wcag-2.2.html#info-and-relationships), Level A
- Evidence: The error is visually adjacent, but the input references only `email-help`; no programmatic relationship points to `email-error`.
- Evidence limit: The result applies to the supplied invalid state.
- Severity: `Major`
- Severity basis: Screen-reader users receive the instruction but not the relationship between the field and its validation error, substantially impeding correction while the visible error remains available.
- Remediation: Include `email-error` in the input's `aria-describedby` references while the error is present.
- Recheck: Inspect the invalid input in the accessibility tree and confirm the description includes the error text.

##### CA-002: Error text contrast is below the minimum

- Result: `FAIL`
- Component and state: `EmailField`, error-message-visible
- Location: `EmailField.css:01-03`; evidence `EF-E02` and `EF-E03`
- Criterion: [WCAG 2.2 SC 1.4.3 — Contrast (Minimum)](reference/wcag-2.2.html#contrast-minimum), Level AA
- Evidence: The normal-size error text resolves to `#aaaaaa` on `#ffffff`.
- Evidence limit: The colors apply to the supplied error state.
- Inputs: foreground `#aaaaaa`; background `#ffffff`; font size `16 CSS px`; font weight `400`
- Method: WCAG relative-luminance contrast calculation
- Observed value: unrounded `2.3231230535045992:1`; displayed `2.3231:1`
- Required threshold: `4.5:1`
- Units and precision: contrast ratio, displayed to four decimal places; comparison used the unrounded value
- Severity: `Major`
- Severity basis: Users with low vision may be unable to perceive information needed to correct the field, creating a substantial correction barrier.
- Remediation: Use an error-text color that reaches at least `4.5:1` against the background.
- Recheck: Resolve the final colors and recompute the unrounded contrast ratio.

#### Cannot-Determine Results

##### CA-003: Dynamic error announcement cannot be determined

- Result: `CANNOT DETERMINE`
- Component and state: `EmailField`, transition into error-message-visible
- Location: `EmailField.tsx:07`; evidence `EF-E01` and `EF-E02`
- Criterion: [WCAG 2.2 SC 4.1.3 — Status Messages](reference/wcag-2.2.html#status-messages), Level AA
- Blocking evidence: Source indicates conditional insertion, but no interaction or assistive-technology announcement observation was supplied.
- Evidence needed: Observe the validation transition with the supported browser and assistive technology while focus remains on the field.
- Resolution check: Determine whether the error status is programmatically exposed without requiring focus.

#### Passed Findings

##### CA-004: Email label and instruction are programmatically associated

- Result: `PASS`
- Component and state: `EmailField`, default and invalid
- Location: `EmailField.tsx:04-06`; evidence `EF-E01`
- Criterion: [WCAG 2.2 SC 3.3.2 — Labels or Instructions](reference/wcag-2.2.html#labels-or-instructions), Level A
- Evidence: The visible label is associated through `htmlFor` and `id`; the required-format instruction is referenced by `aria-describedby`.
- Evidence limit: The result does not cover the separate error relationship.

##### CA-005: Input name, role, and invalid state are exposed

- Result: `PASS`
- Component and state: `EmailField`, default and invalid
- Location: `EmailField.tsx:04-06`; evidence `EF-E01`
- Criterion: [WCAG 2.2 SC 4.1.2 — Name, Role, Value](reference/wcag-2.2.html#name-role-value), Level A
- Evidence: The accessibility tree exposes a textbox named “Work email,” with invalid state false by default and true when the error is present.
- Evidence limit: The result does not establish error announcement behavior.

##### CA-006: Label and help relationships are programmatically exposed

- Result: `PASS`
- Component and state: `EmailField`, default and invalid
- Location: `EmailField.tsx:04-06`; evidence `EF-E01`
- Criterion: [WCAG 2.2 SC 1.3.1 — Info and Relationships](reference/wcag-2.2.html#info-and-relationships), Level A
- Evidence: `htmlFor="email"` associates the label with the input, and `aria-describedby="email-help"` associates the instruction with the input.
- Evidence limit: The separate visible error relationship fails this criterion in CA-001.

##### CA-007: Label, help, and input-value text meet minimum contrast

- Result: `PASS`
- Component and state: `EmailField`, default and invalid
- Location: `EmailField.tsx:04-06`; evidence `EF-E02` and `EF-E03`
- Criterion: [WCAG 2.2 SC 1.4.3 — Contrast (Minimum)](reference/wcag-2.2.html#contrast-minimum), Level AA
- Evidence: The normal-size label, help, and visible input-value text resolve to black on white.
- Evidence limit: The separate error text fails this criterion in CA-002.
- Inputs: foreground `#000000`; background `#ffffff`; font size `16 CSS px`; font weight `400`
- Method: WCAG relative-luminance contrast calculation
- Observed value: unrounded and displayed `21:1`
- Required threshold: `4.5:1`
- Units and precision: contrast ratio; exact endpoint colors require no rounding for comparison

#### Criterion Ledger

| Criterion | Title | Level | Result | Targets or reason | Canonical provision |
|---|---|---|---|---|---|
| 1.3.1 | Info and Relationships | A | `FAIL` | Input and visible error relationship | [WCAG 2.2 SC 1.3.1 — Info and Relationships](reference/wcag-2.2.html#info-and-relationships) |
| 1.4.3 | Contrast (Minimum) | AA | `FAIL` | Visible error text | [WCAG 2.2 SC 1.4.3 — Contrast (Minimum)](reference/wcag-2.2.html#contrast-minimum) |
| 3.3.2 | Labels or Instructions | A | `PASS` | Work email label and instruction | [WCAG 2.2 SC 3.3.2 — Labels or Instructions](reference/wcag-2.2.html#labels-or-instructions) |
| 4.1.2 | Name, Role, Value | A | `PASS` | Work email input | [WCAG 2.2 SC 4.1.2 — Name, Role, Value](reference/wcag-2.2.html#name-role-value) |
| 4.1.3 | Status Messages | AA | `CANNOT DETERMINE` | Dynamic error insertion | [WCAG 2.2 SC 4.1.3 — Status Messages](reference/wcag-2.2.html#status-messages) |

Omitted criteria: 1.1.1, 1.2.1, 1.2.2, 1.2.3, 1.2.4, 1.2.5, 1.3.2, 1.3.3, 1.3.4, 1.3.5, 1.4.1, 1.4.2, 1.4.4, 1.4.5, 1.4.10, 1.4.11, 1.4.12, 1.4.13, 2.1.1, 2.1.2, 2.1.4, 2.2.1, 2.2.2, 2.3.1, 2.4.1, 2.4.2, 2.4.3, 2.4.4, 2.4.5, 2.4.6, 2.4.7, 2.4.11, 2.5.1, 2.5.2, 2.5.3, 2.5.4, 2.5.7, 2.5.8, 3.1.1, 3.1.2, 3.2.1, 3.2.2, 3.2.3, 3.2.4, 3.2.6, 3.3.1, 3.3.3, 3.3.4, 3.3.7, 3.3.8.

Omitted targets or states within evaluated criteria: None.

#### Evidence Limitations

- No interaction or assistive-technology observation establishes whether the dynamic error is announced without focus.
- Fifty criteria were intentionally not evaluated in this compact audit.

#### No Conclusion Issued

Coverage Status is `INCOMPLETE`, so this audit issues no conclusion.

## Example 3: Compact DeleteDialog Audit

This compact example shows the full return contract for an intentionally incomplete audit. It evaluates five of 55 criteria.

### Supplied Audit Request

- Component: `DeleteDialog`
- Source revision: `not applicable` — embedded fixture source
- Invocations and props: closed and open `<DeleteDialog>` configurations with `onOpen`, `onClose`, and `onConfirm` callback interfaces; callback implementations are not supplied
- Intended purpose: Confirm or cancel deletion of a record.
- State inventory: Closed, open, keyboard focus, cancel, confirm, and close are declared; viewport-obscuration evidence was not supplied.

### Embedded Component Boundary

- `DeleteDialog.tsx`
- `DeleteDialog.css`
- Evidence `DD-E01` through `DD-E03`

### Embedded Source

`DeleteDialog.tsx`

```text
01 │ export function DeleteDialog({ open, onOpen, onClose, onConfirm }) {
02 │   return (
03 │     <>
04 │       <button type="button" onClick={onOpen}>Open delete dialog</button>
05 │       {open && (
06 │         <div className="backdrop">
07 │           <div role="dialog" aria-modal="true" aria-labelledby="delete-title" className="dialog">
08 │             <h2 id="delete-title">Delete record?</h2>
09 │             <button type="button" onClick={onClose}>Cancel</button>
10 │             <button type="button" onClick={onConfirm}>Delete</button>
11 │           </div>
12 │         </div>
13 │       )}
14 │     </>
15 │   );
16 │ }
```

`DeleteDialog.css`

```text
01 │ .backdrop { position: fixed; inset: 0; background: #000000; }
02 │ .dialog { background: #ffffff; color: #000000; }
03 │ .dialog button:focus { outline: none; }
```

### Embedded Evidence

| ID | Type | Locator or environment | Observation or value | Limit |
|---|---|---|---|---|
| `DD-E01` | Accessibility tree | `DeleteDialog`, closed and open states, supported browser accessibility tree | Opening trigger is a button named “Open delete dialog”; dialog role is named “Delete record?”; dialog buttons are named “Cancel” and “Delete” | Does not prove focus movement or visibility |
| `DD-E02` | Interaction | `DeleteDialog`, closed-to-open transition and keyboard traversal | Enter and Space activate the opening trigger and dialog buttons; after open, focus remains on the opening trigger at `DeleteDialog.tsx:04`; subsequent Tab order is Cancel then Delete | Does not prove visual obscuration, post-close focus disposition, or viewport behavior |
| `DD-E03` | Rendered | `DeleteDialog`, closed trigger focus, open retained-trigger focus, and Cancel/Delete focus | Before open, the trigger and its browser focus indicator are fully visible and not obscured; after open, the opaque backdrop entirely hides the retained-focus trigger; focused Cancel and Delete buttons show no visible focus indicator | Does not establish whether focused dialog controls are obscured at every viewport |

### Component Audit

#### Audit Target

`DeleteDialog` in `DeleteDialog.tsx:01-16`, including `DeleteDialog.css:01-03`, closed, open, keyboard-focus, cancel, confirm, and close states, and evidence `DD-E01` through `DD-E03`.

#### Evidence Reviewed

The evidence includes component and style source, closed- and open-state accessibility-tree output, keyboard activation and focus movement, and rendered trigger and dialog-button focus states. It does not include post-close focus or viewport-specific obscuration of dialog controls.

#### Coverage Status

`INCOMPLETE`

This compact audit evaluates five criteria and intentionally omits fifty.

#### Summary

| Measure | Count |
|---|---:|
| Required criteria | 55 |
| Evaluated criteria | 5 |
| Omitted criteria | 50 |
| Criterion `PASS` | 2 |
| Criterion `FAIL` | 3 |
| Criterion `CANNOT DETERMINE` | 0 |
| Criterion `NOT APPLICABLE` | 0 |
| Target-finding `PASS` | 5 |
| Target-finding `FAIL` | 4 |
| Target-finding `CANNOT DETERMINE` | 2 |
| Failure severity `Critical` | 0 |
| Failure severity `Major` | 4 |
| Failure severity `Minor` | 0 |

- Audit target: `DeleteDialog` within the boundary stated above
- Source revision: `not applicable` — embedded fixture source
- Audited invocations and props: closed and open configurations with `onOpen`, `onClose`, and `onConfirm` callback interfaces; callback implementations are not supplied
- Audited files: `DeleteDialog.tsx` and `DeleteDialog.css`
- Audited states and variants: closed, open, keyboard focus, cancel, confirm, and close; no additional variant was supplied
- Standard target: WCAG 2.2 Level AA
- Evidence limitation: post-close focus and viewport-specific obscuration for dialog controls were not supplied, and 50 criteria were intentionally omitted

#### Failed Findings

##### CA-001: Initial focus remains behind the opened dialog

- Result: `FAIL`
- Component and state: `DeleteDialog`, transition from closed to open
- Location: `DeleteDialog.tsx:04-10`; evidence `DD-E02`
- Criterion: [WCAG 2.2 SC 2.4.3 — Focus Order](reference/wcag-2.2.html#focus-order), Level A
- Evidence: Opening the modal leaves focus on the trigger behind the backdrop instead of moving it into the active dialog; the next Tab then enters the dialog at Cancel.
- Evidence limit: The result covers the observed open transition.
- Severity: `Major`
- Severity basis: Keyboard users begin interacting from content outside the active modal context, substantially impeding predictable operation while Tab can still reach the dialog.
- Remediation: Move focus to an appropriate element inside the dialog when it opens.
- Recheck: Open the dialog by keyboard and confirm focus enters the dialog in a logical position.

##### CA-002: Dialog buttons have no visible focus indicator

- Result: `FAIL`
- Component and state: `DeleteDialog`, Cancel and Delete keyboard focus
- Location: `DeleteDialog.css:03`; evidence `DD-E03`
- Criterion: [WCAG 2.2 SC 2.4.7 — Focus Visible](reference/wcag-2.2.html#focus-visible), Level AA
- Evidence: CSS removes the outline and rendered evidence shows no replacement focus indicator.
- Evidence limit: The result covers the supplied dialog buttons.
- Severity: `Major`
- Severity basis: Keyboard users can activate the controls but cannot visually identify which destructive-choice control has focus.
- Remediation: Preserve the browser focus indicator or provide an equally visible replacement.
- Recheck: Navigate between Cancel and Delete by keyboard and confirm each focused button is visibly identified.

##### CA-003: Focused opening trigger is obscured by the modal backdrop

- Result: `FAIL`
- Component and state: `DeleteDialog`, closed-to-open transition, opening trigger focus
- Location: `DeleteDialog.tsx:04` behind `DeleteDialog.css:01`; evidence `DD-E02` and `DD-E03`
- Criterion: [WCAG 2.2 SC 2.4.11 — Focus Not Obscured (Minimum)](reference/wcag-2.2.html#focus-not-obscured-minimum), Level AA
- Evidence: Interaction evidence shows focus remains on the opening trigger; rendered evidence shows the opaque fixed backdrop entirely hides that trigger.
- Evidence limit: The result covers the observed opening transition and component-owned trigger only.
- Severity: `Major`
- Severity basis: Keyboard users cannot see the currently focused trigger after the modal opens, substantially impeding orientation while Tab can still move into the dialog.
- Remediation: Move focus into the dialog when it opens so focus is not left on obscured background content.
- Recheck: Open the dialog by keyboard and confirm the focused element is visible and inside the active dialog.

##### CA-004: Opening trigger focus indicator becomes invisible behind the backdrop

- Result: `FAIL`
- Component and state: `DeleteDialog`, opening trigger, retained focus after open
- Location: `DeleteDialog.tsx:04` behind `DeleteDialog.css:01`; evidence `DD-E02` and `DD-E03`
- Criterion: [WCAG 2.2 SC 2.4.7 — Focus Visible](reference/wcag-2.2.html#focus-visible), Level AA
- Evidence: Interaction evidence shows focus remains on the opening trigger, while rendered evidence shows the opaque backdrop entirely hides its focus indicator.
- Evidence limit: The result covers the retained-focus state after opening; the pre-open focus state passes this criterion in CA-010.
- Severity: `Major`
- Severity basis: Keyboard users cannot visually locate focus after opening the dialog, substantially impeding orientation while Tab can still enter the dialog.
- Remediation: Move focus into the dialog when it opens so the active focus indicator remains visible.
- Recheck: Open the dialog by keyboard and confirm the focused element and its focus indicator remain visible.

#### Cannot-Determine Results

##### CA-005: Post-close focus disposition cannot be determined

- Result: `CANNOT DETERMINE`
- Component and state: `DeleteDialog`, cancel/confirm close transition
- Location: `DeleteDialog.tsx:09-10`; evidence `DD-E02`
- Criterion: [WCAG 2.2 SC 2.4.3 — Focus Order](reference/wcag-2.2.html#focus-order), Level A
- Blocking evidence: Cancel and Delete invoke parent callbacks, but no post-close focus observation was supplied.
- Evidence needed: Observe focus immediately after closing through both actions.
- Resolution check: Confirm focus moves to a logical location after the dialog closes.

##### CA-006: Focus obscuration inside the dialog cannot be determined

- Result: `CANNOT DETERMINE`
- Component and state: `DeleteDialog`, Cancel and Delete keyboard focus
- Location: `DeleteDialog.tsx:07-10`; evidence `DD-E03`
- Criterion: [WCAG 2.2 SC 2.4.11 — Focus Not Obscured (Minimum)](reference/wcag-2.2.html#focus-not-obscured-minimum), Level AA
- Blocking evidence: The focused controls are identifiable, but no viewport-specific obscuration observation was supplied.
- Evidence needed: Observe both focused controls at every supported viewport with all author-created overlays present.
- Resolution check: Confirm neither focused control is entirely hidden by author-created content.

#### Passed Findings

##### CA-007: Trigger, dialog, and controls expose names and roles

- Result: `PASS`
- Component and state: `DeleteDialog`, closed and open
- Location: `DeleteDialog.tsx:04,07-10`; evidence `DD-E01`
- Criterion: [WCAG 2.2 SC 4.1.2 — Name, Role, Value](reference/wcag-2.2.html#name-role-value), Level A
- Evidence: The accessibility tree exposes a trigger button named “Open delete dialog,” a dialog named “Delete record?,” and dialog buttons named “Cancel” and “Delete.”
- Evidence limit: The result covers exposed semantics only.

##### CA-008: Trigger and dialog controls are keyboard operable

- Result: `PASS`
- Component and state: `DeleteDialog`, closed and open keyboard activation
- Location: `DeleteDialog.tsx:04,09-10`; evidence `DD-E02`
- Criterion: [WCAG 2.2 SC 2.1.1 — Keyboard](reference/wcag-2.2.html#keyboard), Level A
- Evidence: Enter and Space activate the native opening trigger and both native dialog buttons.
- Evidence limit: This result does not cover focus movement or visibility.

##### CA-009: Dialog control focus order is logical

- Result: `PASS`
- Component and state: `DeleteDialog`, open keyboard traversal
- Location: `DeleteDialog.tsx:09-10`; evidence `DD-E02`
- Criterion: [WCAG 2.2 SC 2.4.3 — Focus Order](reference/wcag-2.2.html#focus-order), Level A
- Evidence: After focus enters the dialog, sequential navigation follows the source and visual order from Cancel to Delete.
- Evidence limit: The opening transition fails this criterion in CA-001, and the post-close transition remains unresolved in CA-005.

##### CA-010: Opening trigger has a visible focus indicator before open

- Result: `PASS`
- Component and state: `DeleteDialog`, opening trigger, closed keyboard-focus state
- Location: `DeleteDialog.tsx:04`; evidence `DD-E03`
- Criterion: [WCAG 2.2 SC 2.4.7 — Focus Visible](reference/wcag-2.2.html#focus-visible), Level AA
- Evidence: Before the dialog opens, the keyboard-focused trigger displays the browser's visible focus indicator.
- Evidence limit: The retained-focus state after open fails this criterion in CA-004.

##### CA-011: Opening trigger is not obscured before open

- Result: `PASS`
- Component and state: `DeleteDialog`, opening trigger, closed keyboard-focus state
- Location: `DeleteDialog.tsx:04`; evidence `DD-E03`
- Criterion: [WCAG 2.2 SC 2.4.11 — Focus Not Obscured (Minimum)](reference/wcag-2.2.html#focus-not-obscured-minimum), Level AA
- Evidence: Before the dialog opens, the focused trigger is fully visible and no author-created content obscures it.
- Evidence limit: The retained-focus state after open fails this criterion in CA-003, and dialog-control viewport states remain unresolved in CA-006.

#### Criterion Ledger

| Criterion | Title | Level | Result | Targets or reason | Canonical provision |
|---|---|---|---|---|---|
| 2.1.1 | Keyboard | A | `PASS` | Opening trigger, Cancel, and Delete controls | [WCAG 2.2 SC 2.1.1 — Keyboard](reference/wcag-2.2.html#keyboard) |
| 2.4.3 | Focus Order | A | `FAIL` | Closed-to-open focus transition | [WCAG 2.2 SC 2.4.3 — Focus Order](reference/wcag-2.2.html#focus-order) |
| 2.4.7 | Focus Visible | AA | `FAIL` | Opening trigger and dialog-button focus states | [WCAG 2.2 SC 2.4.7 — Focus Visible](reference/wcag-2.2.html#focus-visible) |
| 2.4.11 | Focus Not Obscured (Minimum) | AA | `FAIL` | Visible closed-state trigger; obscured retained-focus trigger; unresolved dialog-control viewport states | [WCAG 2.2 SC 2.4.11 — Focus Not Obscured (Minimum)](reference/wcag-2.2.html#focus-not-obscured-minimum) |
| 4.1.2 | Name, Role, Value | A | `PASS` | Opening trigger, dialog, and dialog controls | [WCAG 2.2 SC 4.1.2 — Name, Role, Value](reference/wcag-2.2.html#name-role-value) |

Omitted criteria: 1.1.1, 1.2.1, 1.2.2, 1.2.3, 1.2.4, 1.2.5, 1.3.1, 1.3.2, 1.3.3, 1.3.4, 1.3.5, 1.4.1, 1.4.2, 1.4.3, 1.4.4, 1.4.5, 1.4.10, 1.4.11, 1.4.12, 1.4.13, 2.1.2, 2.1.4, 2.2.1, 2.2.2, 2.3.1, 2.4.1, 2.4.2, 2.4.4, 2.4.5, 2.4.6, 2.5.1, 2.5.2, 2.5.3, 2.5.4, 2.5.7, 2.5.8, 3.1.1, 3.1.2, 3.2.1, 3.2.2, 3.2.3, 3.2.4, 3.2.6, 3.3.1, 3.3.2, 3.3.3, 3.3.4, 3.3.7, 3.3.8, 4.1.3.

Omitted targets or states within evaluated criteria: None.

#### Evidence Limitations

- No post-close observation establishes where focus moves after Cancel or Delete.
- No viewport-specific observation establishes whether either focused dialog control is obscured by author-created content.
- Fifty criteria were intentionally not evaluated in this compact audit.

#### No Conclusion Issued

Coverage Status is `INCOMPLETE`, so this audit issues no conclusion.
