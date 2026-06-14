# Privacy Notes V0.1

Food Sense handles health-adjacent personal data, including food sensitivity reports, eating records, symptoms, and possible reaction patterns.

Even in a private test, this data should be treated carefully.

## V1 Privacy Direction

V1 should use local-first storage.

This means:

- User records are stored in the browser on the user's own device.
- The product should not require an account for the first private version.
- The product should avoid collecting names, phone numbers, IDs, addresses, or contact lists.
- Users should be able to delete all local data.

## AI Recognition Caveat

Some features may require sending images or text to an AI service:

- Medical report extraction
- Ingredient list OCR and matching
- Menu or delivery screenshot understanding

Before sending data to an external AI service, the product should clearly tell the user:

- What will be uploaded
- Why it is needed
- What will be saved locally afterwards

Default preference:

- Save structured extracted data.
- Avoid long-term saving of original medical report images.

## Sensitive Data

The following should be treated as sensitive:

- Medical report photos
- Food sensitivity result values
- Symptoms
- Food logs linked with symptoms
- Pattern discovery outputs

## Product Language

The product should avoid medical diagnosis language.

Prefer:

- `可能相关`
- `建议继续观察`
- `可与医生讨论`
- `信息不足，建议补充配料或询问商家`

Avoid:

- `你对这个过敏`
- `这个一定会导致不舒服`
- `医学诊断`
- `治疗建议`

## Future Privacy Work

Before public launch, the product will need:

- Full privacy policy
- Terms of use
- Data retention policy
- Account and cloud sync security plan, if cloud storage is added
- Consent flow for sensitive personal information
- Data export and deletion flow
