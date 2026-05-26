# IKE Base Parent

[![Maven Central](https://img.shields.io/maven-central/v/network.ike/ike-base-parent)](https://central.sonatype.com/artifact/network.ike/ike-base-parent)
[![License](https://img.shields.io/badge/license-Apache--2.0-blue.svg)](https://www.apache.org/licenses/LICENSE-2.0)
[![Documentation](https://img.shields.io/badge/docs-ike.network%2Fike--base--parent-blue)](https://ike.network/ike-base-parent/)
[![IKE Network](https://img.shields.io/badge/IKE-Network-green)](https://ike.network/)

`network.ike:ike-base-parent` is the Tier 0 foundation parent POM for
the IKE Network — the apex of the IKE parent inheritance forest.

## What it provides

ike-base-parent carries the publishing-layer concerns shared by every
IKE artifact, and nothing more — it is deliberately thin:

- Publishing metadata — developers, organization, license
- GPG artifact signing (Bouncy Castle signer)
- Maven Central deployment configuration (JReleaser)

Build conventions — Java version, compiler, test harness, enforcer —
live in `ike-parent`, not here.

## The parent tier

```
ike-base-parent                            Tier 0  — this POM
   ├── ike-java-support                    Tier 0  — value types
   ├── ike-workspace-extension             Tier 0  — Maven 4 ext
   ├── ike-version-management-extension    Tier 0  — Maven 4 ext
   ├── ike-tooling                         Tier 1
   ├── ike-docs                            Tier 1
   └── ike-platform                        Tier 1
          └── ike-parent                   Tier 2  — consumer-facing
                 └── consumers
```

ike-base-parent sits at the top of the release cascade and is
published to Maven Central first, so every downstream POM's parent
chain resolves cleanly.

## Coordinates

```xml
<parent>
    <groupId>network.ike</groupId>
    <artifactId>ike-base-parent</artifactId>
    <version>1</version>
</parent>
```

## Projects inheriting ike-base-parent

In dependency-direction order (upstream → downstream):

| Project | Role |
|---|---|
| [ike-java-support](https://ike.network/ike-java-support/) | Tier-0 enforced-zero-dependency value types (ConstantBackedEnum, EnumDefinition, ReleasePolicy) |
| [ike-tooling](https://ike.network/ike-tooling/) | Maven plugins and workspace tooling |
| [ike-docs](https://ike.network/ike-docs/) | Documentation plumbing |
| [ike-workspace-extension](https://ike.network/ike-workspace-extension/) | Maven 4 build extension — prunes non-existent `<subprojects>` from workspace POMs before model validation |
| [ike-version-management-extension](https://ike.network/ike-version-management-extension/) | Maven 4 build extension — implements the IKE typed-marker family (`${G__GA__A__VERSION}`, `${G__GA__A__POLICY}`) version-property convention and the release-policy validation rule |
| [ike-platform](https://ike.network/ike-platform/) | Consumer parent (`ike-parent`), BOM, workspace plugin |
| [ike-platform](https://ike.network/ike-platform/) | Consumer parent (`ike-parent`), BOM, workspace plugin |
