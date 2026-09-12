# Changelog

## 3.0 beta 5 — 2026-09-12

- Added a searchable first-run menu with 245 country and territory entries.
- Saved the selected default country in the Shortcuts folder in iCloud Drive and reused it silently on later runs.
- Applied the selected calling code to national numbers instead of always assuming Spain.
- Added conservative handling for national trunk prefixes while preserving significant leading zeroes such as Italian fixed-line numbers.
- Added inference for complete digit-only international numbers when the default-country interpretation is invalid.
- Expanded validation with 22 normalization cases, all 245 country entries and two live configuration runs.

## 3.0 beta 4 — 2026-09-12

- Added structured internal documentation covering the project, authors, features, limitations, version history, privacy, credits and licensing.
- Kept the normalization engine validated in beta 3 unchanged.

## 3.0 beta 3 — 2026-09-11

- Fixed the nested-loop variable that prevented some visually formatted international numbers from being processed.
- Added support for common Unicode plus signs and digits.
- Added safe removal of explicit phone extensions.
- Added a warning to reduce confusion between numeric references and phone numbers.
- Confirmed that the WhatsApp URL contains digits only.
- Expanded validation to 40 parser cases and 12 complete routes.

## 3.0 beta 2 — 2026-09-11

- First correction of the complete flow and loop-item reference.

## 3.0 beta 1 — 2026-09-11

- Initial reconstruction with multiple-number extraction, normalization and international validation.
