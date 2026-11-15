# Orbit languages

Official declarative translation packs for [OrbitKanban](https://github.com/ZenPluS/OrbitKanban), supported from version 3.9.0.

English is the application's integrated source/fallback language. This repository provides Italian and welcomes additional translations. It does not contain executable code or user data.

## Use in OrbitKanban

The official reference `ZenPluS/orbit_languages` and an offline Italian snapshot are included automatically.
In **Settings > Language & translations**, press **Refresh** next to this repository to download its latest default-branch `orbit-languages.json`, then select a language and save settings.

Refresh is manual, not an automatic startup request. The last valid download is cached in the portable data folder and works offline. Invalid downloads and network failures never replace a good cache. No GitHub account or token is needed.

## Contribute a translation

1. Copy `en.template.json`. Set `code` (for example `de` or `pt-BR`), `name` (the native name shown in the selector), and `locale` (for example `de-DE`).
2. Translate values, not keys. Use plain text, not HTML. Keep placeholders such as `{0}`, guide formatting such as `**bold**` and backticks.
3. `messages` contains interface text; `terms` contains default names, demo data and guide text. `plurals` supports `zero`, `one`, `two`, `few`, `many` and the required `other` form. Keep `{0}` in counted messages.
4. Add the entire language object to the `languages` array of `orbit-languages.json` and open a pull request.

Missing or empty translations fall back to English, so partial translations are welcome. Each language code can occur only once per manifest. The English template is a source reference, not a second automatically loaded language pack.

## Publish your own repository

Create a **public** GitHub repository with `orbit-languages.json` at its default-branch root:

```json
{
  "format": "orbitkanban-languages",
  "version": 1,
  "languages": [
    {
      "format": "orbitkanban-language",
      "version": 1,
      "code": "de",
      "name": "Deutsch",
      "locale": "de-DE",
      "messages": { "Settings": "Einstellungen" },
      "terms": {},
      "plurals": {}
    }
  ]
}
```

In the app, enter `owner/repository` or its public GitHub URL and press **Add repository**.
One repository can provide several languages (up to 50). The whole manifest must be valid JSON and at most 2 MB; individual keys/values are limited to 4,000 characters. Up to 20 custom repositories can be referenced.

References apply to every organization of a portable copy. A matching code overrides the official/default translations; later custom references take precedence. Removing a reference restores defaults where available, while otherwise unavailable cached languages remain installed so saved organizations can reopen offline.

Arbitrary files in the former `data/languages` folder are no longer loaded. To migrate a previous language file, place its language object in the manifest above. Local files are left untouched.

## Maintainers

Keep the English template aligned with `languages/en.json` in the application repository. When the application adds source strings, update Italian here and ship the exact manifest as `resources/packs/orbit-languages.json`, with the publishing commit and SHA-256 recorded in the application's source lock.
