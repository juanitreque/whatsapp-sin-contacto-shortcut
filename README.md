# WhatsApp Without Contact 3.0 beta 4

Open a WhatsApp chat with a phone number that is not saved in Contacts. The shortcut accepts input from the Share Sheet, clipboard or manual entry and always asks for confirmation before opening WhatsApp.

## Install

**Recommended:** [Add the shortcut from iCloud](https://www.icloud.com/shortcuts/b1428c280f954816be72a4f5d0135c12).

You can also [download the signed `.shortcut` file](https://github.com/juanitreque/whatsapp-sin-contacto-shortcut/raw/refs/heads/main/release/WhatsApp-sin-contacto-3.0-beta-4.shortcut) and open it with Apple Shortcuts.

The signed build is currently named `WhatsApp sin contacto 3.0 beta 4`.

## What it handles

- Extracts one or more phone numbers from text copied from websites, emails or documents.
- Removes spaces, hyphens, dots and parentheses.
- Converts an international `00` prefix to its equivalent international format.
- Accepts Spanish numbers without a country code and adds `34`.
- Recognizes international country codes written with `+` or `00`.
- Converts common Arabic, Persian and full-width digits to ASCII digits.
- Removes explicit extensions such as `ext. 204`, `extension 204` or `annex 204`.
- Shows a list when it finds several candidates.
- Opens `https://wa.me/<number>` with digits only, as required by WhatsApp.

The shortcut **does not save contacts, send messages or download webpage content**.

## Use

1. Add the shortcut from iCloud or open the signed file with Apple Shortcuts.
2. Review its actions and choose **Add Shortcut**.
3. Select or copy a phone number in another app and run `WhatsApp sin contacto 3.0 beta 4`.
4. Check the normalized recipient before choosing **Open WhatsApp**.

## Examples

| Input | Normalized recipient |
|---|---|
| `+1 (202) 555-0123` | `+12025550123` |
| `6XX XXX XXX` | `+346XXXXXXXX` |
| `0034 (6XX) XXX-XXX` | `+346XXXXXXXX` |
| `+44 7700 900123` | `+447700900123` |
| `+١ ٢٠٢ ٥٥٥ ٠١٢٣` | `+12025550123` |
| `＋１ ２０２ ５５５ ０１２３` | `+12025550123` |
| `+1 202 555 0123 ext. 204` | `+12025550123` |

The confirmation screen displays the recipient with a leading `+`. The final `wa.me` URL removes that symbol and contains digits only.

## Known limitations

- Spain is the default country. Numbers from other countries should include `+` or `00`.
- `011 44…` and formats such as `+44 (0)20…` require manual correction because automatic conversion would not be safe for every country.
- Two foreign numbers separated only by spaces may look like one number. Separate them with `/`, a comma, a semicolon or a line break.
- A nine-digit reference beginning with 6, 7, 8 or 9 may look like a Spanish phone number. The final confirmation helps catch it before WhatsApp opens.
- Validation checks the general numbering-plan format. It cannot confirm that a number exists or has a WhatsApp account.

## Validation

- 40 parser cases executed with Apple's regular-expression engine.
- 12 complete routes executed with a diagnostic copy that omits the **Open URL** action.
- Signature, import, internal documentation and the nested-loop variable checked in the Shortcuts editor.

The anonymized results are available in [`tests/verification-summary.json`](tests/verification-summary.json).

## Internal documentation

The first actions are comments that Apple Shortcuts ignores during execution. They document the project, authors, features, limitations, version history, privacy, credits and licensing. They are only visible when the shortcut is opened in the editor.

## Privacy and security

All parsing runs on the device with native Shortcuts actions. After the user confirms the recipient, the standard build opens only `https://wa.me/<number>`. The phone number is sent to WhatsApp when that URL opens.

## Credits and licensing

This reconstruction is based on the shared shortcut **Open in WhatsApp**, attributed inside the original shortcut to `@johndoe85`.

Version 3.0 was reconstructed and is maintained by [`@juanitreque`](https://github.com/juanitreque).

General numbering rules are derived from `PhoneNumberMetadata.xml` in Google libphonenumber, distributed under the Apache License 2.0. A copy is included at [`LICENSES/libphonenumber-Apache-2.0.txt`](LICENSES/libphonenumber-Apache-2.0.txt).

No additional license is assigned to the inherited shortcut until the original author's permission is confirmed. Contributions and redistributions must preserve the existing credits. See [`COPYRIGHT.md`](COPYRIGHT.md).

