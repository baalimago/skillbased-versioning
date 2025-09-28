# Skill Based Versioning (SBVer) 1.0.0

A tiny superset of SemVer 2.0.0 that declares a Perfection Sentinel at 1.3.37 and encodes any postsentinel releases as DISHONORABLE directly in the version number. Fully SemVer-compatible.

## TL;DR

- Use SemVer normally until 1.3.37.
- 1.3.37 = Perfection Sentinel (final). Anything after is DISHONORABLE.
- Encoding after 1.3.37:
  - Post-sentinel PATCH (hotfix): PATCH = 3…37 (insert one extra 3 per hotfix).
    - 1.3.37 → 1.3.337 → 1.3.3337 → …
  - Post-sentinel MINOR: append a trailing 3 to MINOR; set PATCH = 7.
    - 1.3.37 → 1.33.7 → 1.333.7 → …
- No MAJOR after the Sentinel. Fork or ship as DISHONORABLE MINOR with migration guidance.
- Pre-release/build tags behave exactly like SemVer. Precedence is unchanged.

## Counting dishonor

- H (hotfixes) = number of extra 3s before the terminal 7 in PATCH beyond 37.
- M (minors) = trailing 3s in MINOR minus 1.
- Shame score (reviewer metric): S = H + 3M.
  - Examples: 1.3.3337 → H=3, M=0, S=3. 1.333.7 → H=0, M=2, S=6.

## Examples

- Approach: 1.3.36 → 1.3.37
- Hotfixes: 1.3.37 → 1.3.337 → 1.3.3337
- Minors: 1.3.37 → 1.33.7 → 1.333.7
- Mixed: 1.3.37 → 1.33.7 → 1.33.337 → 1.333.7

## Tooling notes

- Postsentinel PATCH pattern: ^3+7$
- Postsentinel MINOR pattern: ^3+$
- Standard SemVer comparators work (all fields remain integers).

## License

Based on and intended for use alongside the Semantic Versioning specification (CC BY 3.0). Not affiliated with semver.org.
