---
date_published: 1980-01-31
date_modified: 1980-01-31
canonical_url: https://ike.network/ike-base-parent/index.html
---

# IKE Base Parent

[https://central.sonatype.com/artifact/network.ike/ike-base-parent](https://central.sonatype.com/artifact/network.ike/ike-base-parent)[1]

`network.ike:ike-base-parent` is the Tier 0 foundation parent POM for the IKE Network — the apex of the IKE parent inheritance forest.

## [#what-it-provides](#what-it-provides)What it provides

ike-base-parent carries the publishing-layer concerns shared by every IKE artifact, and nothing more — it is deliberately thin:

- Publishing metadata — developers, organization, license
- GPG artifact signing (Bouncy Castle signer)
- Maven Central deployment configuration (JReleaser)

Build conventions — Java version, compiler, test harness, enforcer — live in `ike-parent`, not here.

## [#the-parent-tier](#the-parent-tier)The parent tier

```
ike-base-parent              Tier 0  — this POM
   |-- ike-tooling           Tier 1
   |-- ike-docs              Tier 1
   `-- ike-platform          Tier 1
          `-- ike-parent     Tier 2  — consumer-facing parent
                 `-- consumers
```

ike-base-parent sits at the top of the release cascade and is published to Maven Central first, so every downstream POM’s parent chain resolves cleanly.

## [#coordinates](#coordinates)Coordinates

```
<parent>
    <groupId>network.ike</groupId>
    <artifactId>ike-base-parent</artifactId>
    <version>1</version>
</parent>
```

Available from Maven Central.

## [#projects-inheriting-ike-base-parent](#projects-inheriting-ike-base-parent)Projects inheriting ike-base-parent

- [ike-tooling](https://ike.network/ike-tooling/)[2] — Maven plugins and workspace tooling
- [ike-docs](https://ike.network/ike-docs/)[3] — documentation plumbing
- [ike-platform](https://ike.network/ike-platform/)[4] — consumer parent (`ike-parent`), BOM, workspace plugin
