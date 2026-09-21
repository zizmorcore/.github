# Security Policy

The zizmor project takes security very seriously, and welcomes security researchers
who engage in responsible disclosure.

Please make sure to read this document in full before continuing with disclosure.
See the [disclosure](#disclosure) section for concrete disclosure instructions.

## Scope

This policy covers every public repository under [zizmorcore](https://github.com/zizmorcore),
including [zizmor itself](https://github.com/zizmorcore/zizmor) and all integration repositories.

## Your responsibilities

First and formost, you **must** comply with our [AI policy](./AI_POLICy.md).

Reporting AI discovered vulnerabilities is encouraged, but you **must** be able
to explain the vulnerability report in your own words.

Beyond that, you must ensure that you understand our threat model (below)
and that your report is consistent with it. Reports that violate our threat
model will be ignored.

## Our responsibilities

We will make a good faith effort to triage all vulnerability reports within 90 days.

It is also our responsibility to ensure that all vulnerability reports are accurate
and in the best interest of our users. For example, we may decrease (or increase)
the severity of a report based on our understanding of the report's actual severity,
regardless of what metrics like CVSS indicate. We may do this unilaterally.

## Threat model

zizmor is primarily a developer tool, i.e. is expected to run in contexts
where the user is a developer and has full control over the tool's lifecycle.

That means certain theoretical classes of weaknesses are _out of scope_:

- Availability issues (causing zizmor to crash, or hang) may be considered
  bugs, but are not security issues in and of themselves.

Similarly, there are certain theoretical findings that are _usually_ out of scope
but _may_ be in scope if impact is demonstrated:

- Vulnerabilities in upstream dependencies (e.g. third-party Rust dependencies)
  are _generally_ not vulnerabilities in zizmor itself, _unless_ there is
  a demonstrable security impact on users because of how zizmor uses that dependency.

- Path traversal bugs are _generally_ not vulnerabilities in zizmor itself, since they
  don't typically result in any kind of security posture change. For example, "tricking"
  zizmor into auditing a file outside of the requested directory prefix is trivial to do,
  but does not result in a posture change.

Finally, there are things that _would_ be considered vulnerabilities in zizmor,
if found:

- Inducing zizmor to leak secrets, e.g. API tokens, via its logging or error messages.

- Inducing zizmor to execute arbitrary code, especially abitrary code from a remote source.

- Compromising any of zizmor's CI/CD processes, especially high-trust processes like release flows.

## Disclosure

Once you've read this document in full and have confirmed that your report is consistent
with it, we encourage you to disclose it to us.

To disclose, please open a new draft advisory via GitHub's private vulnerability reporting:
[link](https://github.com/zizmorcore/zizmor/security/advisories/new).
