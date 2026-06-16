# UI Rules

Purpose: design language, interaction rules, and reusable UI patterns.

If the project has no UI: not applicable.

## UI Status

- **Applies to this project:** [YES_OR_NO]
- **Primary surfaces:** [SURFACES]
- **Design source of truth:** [DESIGN_SOURCE_OR_NONE]
- **Accessibility target:** [ACCESSIBILITY_TARGET]

## Design Source

Artifacts that define the UI:

- [DESIGN_FILE_OR_REFERENCE_1]
- [DESIGN_FILE_OR_REFERENCE_2]
- [DESIGN_FILE_OR_REFERENCE_3]

Project-specific design references: [LOCATION_OR_NONE]

## Visual Language

Intended feel of the interface:

- [VISUAL_PRINCIPLE_1]
- [VISUAL_PRINCIPLE_2]
- [VISUAL_PRINCIPLE_3]

Examples: dense and operational, calm and editorial, playful and animated, technical and high-contrast, minimal and document-like.

## Layout Principles

- [LAYOUT_RULE_1]
- [LAYOUT_RULE_2]
- [LAYOUT_RULE_3]

Spacing, density, navigation, content hierarchy, responsive behavior, and layout constraints.

## Typography

| Role | Style | Usage |
| ---- | ----- | ----- |
| Primary heading | [STYLE] | [USAGE] |
| Section heading | [STYLE] | [USAGE] |
| Body text | [STYLE] | [USAGE] |
| Supporting text | [STYLE] | [USAGE] |
| Code or data text | [STYLE] | [USAGE] |

## Color And Theming

| Role | Token or value | Usage |
| ---- | -------------- | ----- |
| Background | [TOKEN_OR_VALUE] | [USAGE] |
| Surface | [TOKEN_OR_VALUE] | [USAGE] |
| Primary text | [TOKEN_OR_VALUE] | [USAGE] |
| Secondary text | [TOKEN_OR_VALUE] | [USAGE] |
| Accent | [TOKEN_OR_VALUE] | [USAGE] |
| Success | [TOKEN_OR_VALUE] | [USAGE] |
| Warning | [TOKEN_OR_VALUE] | [USAGE] |
| Error | [TOKEN_OR_VALUE] | [USAGE] |

Prefer named tokens once a design system exists. Avoid scattering raw values through implementation.

## Components And Patterns

Reusable UI patterns:

- Buttons: [RULES]
- Forms: [RULES]
- Navigation: [RULES]
- Cards or panels: [RULES]
- Tables or lists: [RULES]
- Empty states: [RULES]
- Loading states: [RULES]
- Error states: [RULES]

## Interaction Rules

- [INTERACTION_RULE_1]
- [INTERACTION_RULE_2]
- [INTERACTION_RULE_3]

Include keyboard behavior, focus management, loading feedback, destructive action confirmation, gesture rules, or command shortcuts when relevant.

## Accessibility Rules

- All interactive controls must have clear labels.
- Focus states must be visible.
- Color must not be the only way to communicate meaning.
- Text must remain readable at supported sizes and viewport widths.
- Error messages should identify the problem and suggest the next action.
- Add project-specific accessibility requirements here.

## Do Not

- Do not introduce a new visual pattern when an existing one works.
- Do not approximate provided designs when exact implementation is expected.
- Do not use decorative assets that distract from the primary task.
- Do not leave inconsistent spacing, typography, color, or interaction states unrecorded.
- Do not let UI text overlap, truncate badly, or resize containers unexpectedly.
