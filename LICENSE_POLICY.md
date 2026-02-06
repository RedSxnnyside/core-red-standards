# License Policy

This document defines how licenses are selected, applied, and enforced across all Core Red projects. License selection is a controlled decision governed by this policy.

---

## Default License

The default license for all Core Red projects is the **Core Red Custom License**, defined in [licenses/CUSTOM_LICENSE.md](licenses/CUSTOM_LICENSE.md).

All new repositories **must** use the custom license unless an explicit exception applies.

## MIT License Eligibility

A Core Red project **may** use the MIT License only when **all** of the following conditions are true:

- The project is classified as a public utility, library, or tool
- The project does not contain proprietary algorithms, trade logic, or internal infrastructure
- The project is intended for broad community adoption and external contribution
- A maintainer with repository authority has approved the license selection in writing

The canonical MIT template is defined in [licenses/MIT_LICENSE.md](licenses/MIT_LICENSE.md). No modifications to the license body are permitted.

## Custom License Applicability

The Core Red Custom License **must** be used when any of the following conditions are true:

- The project contains proprietary logic or internal tooling
- The project is private or internal-only
- The project is experimental and not designated for public distribution
- No explicit MIT exception has been granted

## Prohibited Practices

The following licensing practices are **prohibited** across all Core Red projects:

- Using a license not defined in this repository
- Modifying the legal body of any approved license template
- Omitting a LICENSE file from any repository
- Including multiple licenses in a single repository without explicit documentation of scope
- Applying a license retroactively to alter the terms of previously released versions
- Using "unlicensed", "public domain", or Creative Commons licenses for source code

## LICENSE File Requirements

Every Core Red repository **must** include a `LICENSE` file at the repository root.

The `LICENSE` file **must** contain the full text of the applicable license with all placeholder fields completed.

The license type **must** be referenced in the project README under a "License" section.

## Enforcement

License compliance is assessed as part of the standard compliance review. A repository without a valid `LICENSE` file, or with a license that contradicts this policy, is non-compliant.

Non-compliance **must** be resolved before release.