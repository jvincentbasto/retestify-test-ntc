# @retestify-test-ntc

**NTC (NODE - TSUP - CHANGESETS)**

Format: [Framework] - [Bundler] - [Versioning]
Only for testing purposes

## Getting started

### Installation

Install the package through any of the package managers:

```bash
# npm
npm i @retestify-test-ntc

# yarn
yarn add @retestify-test-ntc

# pnpm
pnpm add @retestify-test-ntc

# bun
bun add @retestify-test-ntc

```

### Import Package

The package can be used by type `common js` or `es modules`

```javascript
// cjs
const ntc = require("@retestify-test-ntc");

// mjs
import ntc from "@retestify-test-ntc";
```

## Versioning Documentation

**CURRENT VERSION: `changeset/cli: ^2.27.8`**

**NOTE:**
All steps indicated here are not part of a standard procedure, as this is **experimental**.

### Instructions:

- Follow the steps listed below even though they may not align with typical best practices.
- If you find areas of improvement, you are encouraged to **submit a pull request** to refine this experimental process.
  **Otherwise**, ensure that you **comply with the rules** as they are, without deviation.

### Changeset Options:

- **Patch:** Fix Release
- **Minor:** Feature Release
- **Major:** Breaking Release

### Changeset Versioning:

**Package:** `@[organization]` / `[package]`
**Default Version:** `@[major]`.`[minor]`.`[patch]`
**Pre-release Version:** `0.0.0`-`[tag]`.`[increment]`

### Pre-release Behaviors:

- **Always** increments after the **`tag`** version
- **Overrides** `main version` with the **highest** version change `(changesets)` made in `pre-release`
  - **Highest Version (HV):** ( `Major` | `Minor` | `Patch` )
  - **Format:** `[HV]`.`[HV]`.`[HV]`-`[tag]`.`[incremental]`

### Changeset Version (COMMAND) Behavior

- **Pre-relaese `[Optional]`:**
  - The **trigger** to publish a new `pre-release` version before `changeset publish` is to update the versions `changeset version`
  - **ONLY PUBLISH IF NEEDED**
- **Main Release `[NOT required]`:** If changes are made in **main tag** `(latest)`
- **Merge Tags `[Required]`:** If **merging tags** `(next)` to **main tags** `(latest)`

```bash
# [optional] if: pre-release (next)
# [required] if: merge tags (next)
# [not required] if: main tag (latest)
npm changeset version
```

### Changeset Pre-release:

#### Pre-release (Default Sequence):

**Main Version: `(0.0.0)`**

##### @Patch Release (Default Procedure)

```bash
# checkout next branch
git checkout -b next

# [required] pull / rebase changes from ( master | main )
git pull --rebase origin master

# [required] initialize pre-release tag (next)
npm changeset pre enter next

# [optional] Make changeset
npm changeset

# [optional] if: publish tag version
npm changeset version
# push changes
```

##### @Patch Release

```bash
# Make changeset (patch)
npm changeset

# Current version: 0.0.1-next.0
# Succeeding versions: 0.0.1-next.[increment]

# [optional] if: publish tag version
npm changeset version
# push changes
```

##### @Minor Release

```bash
# Make changeset (minor)
npm changeset

# Current version: 0.0.1-next.0
# Succesucceeding versions:
# 0.1.0-next.2
# 0.1.0-next.3

# [optional] if: publish tag version
npm changeset version
# push changes
```

##### @Major Release

```bash
# Make changeset (major)
npm changeset

# Current version: 0.1.0-next.3
# Succesucceeding versions:
# 1.0.0-next.5
# 1.0.0-next.6

# [optional] if: publish tag version
npm changeset version
# push changes
```

#### Pre-release Exit (Merging Sequence):

**Pre-release Version:** `1.0.0-next.6`

##### @Exit Pre-release version: (Default procedure)

```bash
# [required] checkout master
git checkout master

# merge feature branch (next)
git merge next

# [required] exit pre-release version
npm changeset pre exit

# [required] update versions
npm changeset version
# push changes
```

##### @Merge Tags: Sequence #1

```bash
# [required] update versions
npm changeset version

# Current version: 1.0.0
# push changes
```

##### @Merge Tags: Sequence #2

```bash
# next branch
git checkout next
git pull --rebase origin master

# changeset (@major)
npm changeset pre enter next
npm changeset

# Current version: 2.0.0-next.0
# Succesucceeding versions:
# 2.0.0-next.1
# 2.0.0-next.2

# [optional]
npm changeset version
# push changes
```

```bash
# master branch
git checkout master
git merge next

# update versions
npm changeset pre exit
npm changeset version

# Current version: 2.0.0
# push changes
```

##### @Merge Tags: Sequence #3

```bash
# next branch
git checkout next
git pull --rebase origin master

# changeset (@minor)
npm changeset pre enter next
npm changeset

# Current version: 2.1.0-next.0
# Succesucceeding versions:
# 2.1.0-next.1
# 2.1.0-next.2

# [optional]
npm changeset version
# push changes
```

```bash
# master branch
git checkout master
git merge next

# update versions
npm changeset pre exit
npm changeset version

# Current version: 2.1.0
# push changes
```

##### @Merge Tags: Sequence #4

```bash
# next branch
git checkout next
git pull --rebase origin master

# changeset (@patch)
npm changeset pre enter next
npm changeset

# Current version: 2.1.1-next.0
# Succesucceeding versions:
# 2.1.1-next.1
# 2.1.1-next.2

# [optional]
npm changeset version
# push changes
```

```bash
# master branch
git checkout master
git merge next

# update versions
npm changeset pre exit
npm changeset version

# Current version: 2.1.1
# push changes
```

## LICENSE

MIT. See the LICENSE file.

[Node]: https://nodejs.org/en
[Tsup]: https://www.npmjs.com/package/tsup
[Changeset]: https://www.npmjs.com/package/@changesets/cli
[Changeset/actions]: https://github.com/changesets/action
