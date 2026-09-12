# WhatsApp Without Contact 3.0 beta 5

Open a WhatsApp chat with a phone number that is not saved in Contacts. The shortcut accepts input from the Share Sheet, clipboard or manual entry and always asks for confirmation before opening WhatsApp.

## Install

Download [`WhatsApp-sin-contacto-3.0-beta-5.shortcut`](release/WhatsApp-sin-contacto-3.0-beta-5.shortcut) and open it with Apple Shortcuts.

The signed build is named `WhatsApp sin contacto 3.0 beta 5`.

## First-run country setup

On the first run, choose the country that should be used for national numbers without an international prefix. The searchable list contains 245 country and territory entries, with Spain shown first.

The shortcut stores the selection in `WhatsApp-sin-contacto-default-country.txt` inside the Shortcuts folder in iCloud Drive. Later runs reuse it silently. To choose another country, delete that file and run the shortcut again.

## What it handles

- Extracts one or more phone numbers from text copied from websites, emails or documents.
- Removes spaces, hyphens, dots and parentheses.
- Converts an international `00` prefix to its equivalent international format.
- Applies the chosen default country to national numbers.
- Handles common national trunk prefixes conservatively, including `0` and `8`, only when the unmodified form is invalid.
- Preserves significant leading zeroes, including Italian fixed-line numbers.
- Recognizes international country codes written with `+` or `00` and can infer a complete digit-only international number when the national interpretation is invalid.
- Converts common Arabic, Persian and full-width digits to ASCII digits.
- Removes explicit extensions such as `ext. 204`, `extension 204` or `annex 204`.
- Shows a list when it finds several candidates.
- Opens `https://wa.me/<number>` with digits only, as required by WhatsApp.

The shortcut **does not save contacts, send messages or download webpage content**.

## Use

1. Open the signed file with Apple Shortcuts and review its actions.
2. Run the shortcut and choose your default country when asked.
3. Select or copy a phone number in another app and run `WhatsApp sin contacto 3.0 beta 5`.
4. Check the normalized recipient before choosing **Open WhatsApp**.

## Examples

| Default country | Input | Normalized recipient |
|---|---|---|
| Spain (`+34`) | `612 345 678` | `+34612345678` |
| United States (`+1`) | `(786) 796-1393` | `+17867961393` |
| United Kingdom (`+44`) | `07400 123456` | `+447400123456` |
| France (`+33`) | `06 12 34 56 78` | `+33612345678` |
| Italy (`+39`) | `02 1234 5678` | `+390212345678` |
| Any | `0034 (6XX) XXX-XXX` | `+346XXXXXXXX` |
| Any | `+١ ٢٠٢ ٥٥٥ ٠١٢٣` | `+12025550123` |

The confirmation screen displays the recipient with a leading `+`. The final `wa.me` URL removes that symbol and contains digits only.

## Known limitations

- A national number is interpreted using the country selected during first-run setup. Use `+` or `00` for a number from another country.
- `011 44…` and formats such as `+44 (0)20…` require manual correction because automatic conversion would not be safe for every country.
- Two Spanish numbers separated only by spaces are split when Spain is the default country. For other countries, separate multiple numbers with `/`, a comma, a semicolon or a line break.
- A numeric reference may resemble a phone number. The final confirmation helps catch it before WhatsApp opens.
- Validation checks the general numbering-plan format. It cannot confirm that a number exists or has a WhatsApp account.

## Validation

- 22 normalization cases passed using Apple's regular-expression engine and the exact beta 5 patterns.
- All 245 country entries were parsed and validated; they map to 215 distinct calling codes.
- The signed shortcut contains 139 actions and exactly one **Open URL** action.
- A live first run saved Spain (`+34`); a second run skipped setup and did not rewrite the preference file.
- The signed build was imported and inspected in Apple Shortcuts.

The real WhatsApp recipient-opening step was not performed during automated validation. Detailed anonymized results are available in [`tests/verification-summary.json`](tests/verification-summary.json).

## Internal documentation

The first actions are comments that Apple Shortcuts ignores during execution. They document the project, authors, features, limitations, version history, privacy, credits and licensing. They are only visible when the shortcut is opened in the editor.

## Privacy and security

All parsing runs on the device with native Shortcuts actions. After the user confirms the recipient, the standard build opens only `https://wa.me/<number>`. The phone number is sent to WhatsApp when that URL opens.

## Credits and licensing

This reconstruction is based on the shared shortcut **Open in WhatsApp**, attributed inside the original shortcut to `@johndoe85`.

Version 3.0 was reconstructed and is maintained by [`@juanitreque`](https://github.com/juanitreque).

General numbering rules are derived from `PhoneNumberMetadata.xml` in Google libphonenumber, distributed under the Apache License 2.0. A copy is included at [`LICENSES/libphonenumber-Apache-2.0.txt`](LICENSES/libphonenumber-Apache-2.0.txt).

No additional license is assigned to the inherited shortcut until the original author's permission is confirmed. Contributions and redistributions must preserve the existing credits. See [`COPYRIGHT.md`](COPYRIGHT.md).
