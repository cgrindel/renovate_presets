# Renovate Presets

This reposoitory contains [shared Renovate presets](https://docs.renovatebot.com/config-presets/).

To configure a repository to use the default preset from this repository, use the following in [the
Renovate JSON file](https://docs.renovatebot.com/configuration-options/) for the target repository.

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>cgrindel/renovate_presets"]
}
```
