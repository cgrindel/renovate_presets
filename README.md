# Renovate Presets

This reposoitory contains [shared Renovate presets](https://docs.renovatebot.com/config-presets/).
There are two presets:

1. [default.json](default.json): This is the original/legacy preset used for all of cgrindel's
   repositories. Renovate updates the root `MODULE.bazel` file, but does not see the `MODULE.bazel`
   files under the examples and test(s) directories.
1. [ruleset_base.json](ruleset_base.json): This preset contains the settings that are useful
   for maintaining a Bael ruleset. Renovate will ignore the root `MODULE.bazel` file, but will offer
   updates for any `MODULE.bazel` files found in sub-directories.
1. [cgrindel_default.json](cgrindel_default.json): This present contains the settings that cgrindel
   applies to their repositories (e.g. semantic commits, auto merge, rebase PRs).

## Legacy Default Preset

Add the following in [the Renovate JSON file](https://docs.renovatebot.com/configuration-options/)
for the target repository.

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>cgrindel/renovate_presets"]
}
```

## Ruleset Base Preset

To configure a repository to use the base ruleset preset from this repository, add the following in [the
Renovate JSON file](https://docs.renovatebot.com/configuration-options/) for the target repository.

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>cgrindel/renovate_presets:ruleset_base"]
}
```

This preset contains all of the presets defined in Renovate's
[config:base](https://github.com/renovatebot/renovate/blob/main/lib/config/presets/internal/config.ts),
except the `:ignoreModulesAndTests` preset. It also contains a package rule that disables Renovate
for the root `MODULE.bazel`.

The
[:ignoreModulesAndTests](https://github.com/renovatebot/renovate/blob/main/lib/config/presets/internal/default.ts#L291)
preset is excluded becuase it defines `ignorePaths` that prevent the discovery of `MODULE.bazel`
files in select sub-directories (e.g. `examples`, `test`, `tests`).

## cgrindel Base Preset

```json
{
  "$schema": "https://docs.renovatebot.com/renovate-schema.json",
  "extends": ["github>cgrindel/renovate_presets:cgrindel_default"]
}
```
