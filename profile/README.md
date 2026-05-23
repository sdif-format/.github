<p align="center">
  <img src="assets/sdif-logo-t.png" alt="SDIF Format" width="520">
</p>

<p align="center">
  <strong>Semantic Data Interchange Format</strong>
</p>

<p align="center">
  Compact, semantic and canonicalizable structured data<br>
  for AI agents, deterministic workflows and human-auditable records.
</p>

<p align="center">
  <a href="#what-is-sdif">What is SDIF?</a>
  ·
  <a href="#ecosystem">Ecosystem</a>
  ·
  <a href="#why-it-exists">Why it exists</a>
  ·
  <a href="#status">Status</a>
  ·
  <a href="#contributing">Contributing</a>
</p>

<p align="center">
  <a href="https://pypi.org/project/sdif-format/">
    <img src="https://img.shields.io/pypi/v/sdif-format.svg?style=flat-square" alt="PyPI">
  </a>
  <a href="https://pypi.org/project/sdif-format/">
    <img src="https://img.shields.io/pypi/pyversions/sdif-format.svg?style=flat-square" alt="Python versions">
  </a>
  <a href="https://github.com/sdif-format/sdif/releases/tag/v1.0.0">
    <img src="https://img.shields.io/badge/status-v1.0.0%20released-2563eb?style=flat-square" alt="Status">
  </a>
  <a href="https://github.com/sdif-format/sdif">
    <img src="https://img.shields.io/badge/design-canonicalizable-0f766e?style=flat-square" alt="Canonicalizable">
  </a>
  <a href="https://github.com/sdif-format">
    <img src="https://img.shields.io/badge/ecosystem-open%20tooling-374151?style=flat-square" alt="Open tooling">
  </a>
</p>

<br>

<p align="center">
  <code>pip install sdif-format</code>
</p>

<p align="center">
  <a href="https://pypi.org/project/sdif-format/"><strong>PyPI package</strong></a>
  ·
  <a href="https://github.com/sdif-format/sdif/releases/tag/v1.0.0"><strong>v1.0.0 release</strong></a>
  ·
  <a href="https://sdif-format.github.io/"><strong>Documentation</strong></a>
</p>

<br>

<div align="center">

<table>
  <tr>
    <td align="center" width="25%">
      <strong>Compact</strong>
      <br><br>
      Less repeated structure.<br>
      Fewer wasted tokens.
    </td>
    <td align="center" width="25%">
      <strong>Semantic</strong>
      <br><br>
      Tables, relations,<br>
      metadata and intent.
    </td>
    <td align="center" width="25%">
      <strong>Canonical</strong>
      <br><br>
      Stable output for hashing,<br>
      signing and comparison.
    </td>
    <td align="center" width="25%">
      <strong>Auditable</strong>
      <br><br>
      Designed to be read,<br>
      reviewed and trusted.
    </td>
  </tr>
</table>

</div>

<br>

---

## What is SDIF?

**SDIF — Semantic Data Interchange Format** is a compact, canonicalizable and AI-friendly data format for structured information that needs to move cleanly between humans, tools, agents and deterministic workflows.

It is designed for cases where data should be:

- small enough to be efficient in AI context windows;
- structured enough for machines;
- readable enough for humans;
- deterministic enough for hashing, signing and reproducible workflows;
- semantic enough to express tables, relations, metadata and intent.

<br>

```sdif
@sdif 1.0

kind Plan
id release.v1
title "Release readiness plan"

items[id,status,owner,evidence]:
  R1	done	build	"reports/build.md"
  R2	open	qa	"reports/tests.md"
  R3	done	security	"reports/audit.md"

rel:
  release.v1 validated_by R1
  release.v1 blocked_by R2
  release.v1 governed_by R3
```

<br>

<p align="center">
  <strong>
    Structured information closer to a document,<br>
    while still behaving like a contract.
  </strong>
</p>

<br>

---

## Ecosystem

This GitHub organization hosts the official SDIF ecosystem: the core format, reference tooling, benchmarks, examples and syntax integrations.

<div align="center">

<table>
  <tr>
    <td width="33%" valign="top">
      <p>
        <sub>CORE FORMAT</sub>
      </p>
      <h3>sdif</h3>
      <p>
        Specification, parser, canonicalizer and CLI for the Semantic Data Interchange Format.
      </p>
      <p>
        <a href="https://github.com/sdif-format/sdif"><strong>Explore sdif →</strong></a>
      </p>
    </td>
    <td width="33%" valign="top">
      <p>
        <sub>MEASUREMENT</sub>
      </p>
      <h3>sdif-benchmarks</h3>
      <p>
        Reproducible benchmark datasets and reports for comparing SDIF with existing formats.
      </p>
      <p>
        <a href="https://github.com/sdif-format/sdif-benchmarks"><strong>View benchmarks →</strong></a>
      </p>
    </td>
    <td width="33%" valign="top">
      <p>
        <sub>SYNTAX TOOLING</sub>
      </p>
      <h3>tree-sitter-sdif</h3>
      <p>
        Tree-sitter grammar foundation for syntax highlighting and editor integrations.
      </p>
      <p>
        <a href="https://github.com/sdif-format/tree-sitter-sdif"><strong>Open grammar →</strong></a>
      </p>
    </td>
  </tr>
</table>

</div>

<br>

<details>
  <summary><strong>Repository map</strong></summary>

<br>

| Repository                                                            | Purpose                                                          |
| --------------------------------------------------------------------- | ---------------------------------------------------------------- |
| [`sdif`](https://github.com/sdif-format/sdif)                         | Core format, specification, parser, canonicalization and CLI     |
| [`sdif-benchmarks`](https://github.com/sdif-format/sdif-benchmarks)   | Benchmark datasets, reports and comparison tooling               |
| [`tree-sitter-sdif`](https://github.com/sdif-format/tree-sitter-sdif) | Grammar, syntax highlighting and editor integration foundation   |
| [`.github`](https://github.com/sdif-format/.github)                   | Organization profile, shared community files and public metadata |

</details>

<br>

---

## Why it exists

Modern software workflows exchange more structured context than ever.

That context moves through APIs, files, prompts, agents, documentation systems, CI pipelines, benchmarks and human reviews. The usual formats all solve part of the problem, but none of them quite match this new middle ground.

<table>
  <tr>
    <td width="25%" valign="top">
      <strong>JSON</strong>
      <br><br>
      Universal and reliable, but noisy when repeated records dominate.
    </td>
    <td width="25%" valign="top">
      <strong>YAML</strong>
      <br><br>
      Readable, but often too permissive for deterministic workflows.
    </td>
    <td width="25%" valign="top">
      <strong>CSV</strong>
      <br><br>
      Compact, but loses structure, relations and meaning very quickly.
    </td>
    <td width="25%" valign="top">
      <strong>Markdown</strong>
      <br><br>
      Great for humans, but not enough when data must be parsed and verified.
    </td>
  </tr>
</table>

<br>

SDIF tries to sit in that gap.

Not as a replacement for every format, but as a focused layer for structured data that needs to remain compact, meaningful, reviewable and reproducible.

<br>

---

## Designed for

<table>
  <tr>
    <td width="33%" valign="top">
      <h3>AI workflows</h3>
      <ul>
        <li>Agent memory snapshots</li>
        <li>Compact context payloads</li>
        <li>AI-friendly summaries</li>
        <li>Tool-to-tool exchange</li>
        <li>Structured prompt artifacts</li>
      </ul>
    </td>
    <td width="33%" valign="top">
      <h3>Engineering</h3>
      <ul>
        <li>Project plans</li>
        <li>Roadmaps</li>
        <li>Registries</li>
        <li>Manifests</li>
        <li>Technical specifications</li>
      </ul>
    </td>
    <td width="33%" valign="top">
      <h3>Verification</h3>
      <ul>
        <li>Benchmark reports</li>
        <li>Canonical records</li>
        <li>Hashable datasets</li>
        <li>Golden files</li>
        <li>Comparison-friendly artifacts</li>
      </ul>
    </td>
  </tr>
</table>

<br>

---

## Design principles

<div align="center">

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>Compact by default</h3>
      <p>
        Repeated structure should not require repeated noise.
        SDIF aims to reduce unnecessary bytes and tokens while keeping documents understandable.
      </p>
    </td>
    <td width="50%" valign="top">
      <h3>Human-auditable</h3>
      <p>
        A good SDIF file should be inspectable in a plain text editor.
        Reviewability is part of the format, not a side effect.
      </p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>Canonicalizable</h3>
      <p>
        Equivalent data should be able to produce deterministic bytes.
        That matters for hashing, signing, reproducibility and comparison.
      </p>
    </td>
    <td width="50%" valign="top">
      <h3>Semantic</h3>
      <p>
        Data is more than rows and fields.
        SDIF treats relations, metadata, context and intent as first-class concerns.
      </p>
    </td>
  </tr>
  <tr>
    <td width="50%" valign="top">
      <h3>AI-friendly</h3>
      <p>
        Token efficiency, stable structure and low ambiguity are core design goals,
        especially for agentic and LLM-assisted workflows.
      </p>
    </td>
    <td width="50%" valign="top">
      <h3>Practical first</h3>
      <p>
        SDIF should be useful, testable and implementable.
        The format should not require heroics to parse or adopt.
      </p>
    </td>
  </tr>
</table>

</div>

<br>

---

## Status

<div align="center">

<table>
  <tr>
    <td align="center" width="33%">
      <strong>Specification</strong>
      <br><br>
      Stable<br>
      <strong>v1.0</strong>
    </td>
    <td align="center" width="33%">
      <strong>Python tooling</strong>
      <br><br>
      Parser, CLI,<br>
      canonicalization and validation
    </td>
    <td align="center" width="33%">
      <strong>Distribution</strong>
      <br><br>
      Available on PyPI as<br>
      <strong>sdif-format</strong>
    </td>
  </tr>
</table>

</div>

<br>

SDIF v1.0.0 is available as a public Python package:

```bash
pip install sdif-format
```

```python
import sdif
```

The current focus is now on adoption, documentation, conformance and ecosystem tooling:

* keep the v1.0 format contract stable;
* improve examples and documentation;
* expand conformance fixtures;
* publish reproducible benchmarks;
* improve editor and syntax tooling;
* gather feedback from real-world datasets and AI workflows.

We prefer evidence over claims. Benchmarks, golden files and reproducible examples are part of the product, not marketing decoration.

<br>

---

## What SDIF is not

SDIF is not trying to replace JSON, YAML, CSV, Markdown, XML, Parquet or Protocol Buffers.

Those formats are useful and battle-tested.

SDIF focuses on a narrower problem:

<p align="center">
  <strong>
    compact, semantic, canonicalizable structured data<br>
    that can move cleanly between humans, machines and AI systems.
  </strong>
</p>

That focus is intentional.

<br>

---

## Contributing

We are still early, so the most valuable contributions are not only code.

<table>
  <tr>
    <td width="50%" valign="top">
      <h3>Useful contributions</h3>
      <ul>
        <li>Test SDIF with real datasets</li>
        <li>Find ambiguous syntax or edge cases</li>
        <li>Compare SDIF against existing formats</li>
        <li>Improve documentation and examples</li>
        <li>Build small tools around the format</li>
      </ul>
    </td>
    <td width="50%" valign="top">
      <h3>Especially welcome</h3>
      <ul>
        <li>Reproducible benchmarks</li>
        <li>Golden files</li>
        <li>Parser feedback</li>
        <li>AI workflow experiments</li>
        <li>Constructive criticism</li>
      </ul>
    </td>
  </tr>
</table>

Good criticism is welcome.
Vague hype is less useful.

<br>

---

## Project philosophy

<p align="center">
  <img src="assets/sdif-logo-t.png" alt="SDIF symbol" width="96">
</p>

<p align="center">
  <strong>We want SDIF to be boring in the best possible way.</strong>
</p>

<div align="center">

<table>
  <tr>
    <td align="center">Clear syntax</td>
    <td align="center">Small files</td>
    <td align="center">Stable output</td>
  </tr>
  <tr>
    <td align="center">Readable examples</td>
    <td align="center">Useful errors</td>
    <td align="center">Reproducible benchmarks</td>
  </tr>
</table>

</div>

<br>

A format should not require heroics to implement.
If SDIF works, it should feel obvious after you use it.

<br>

---

## Contact

The best place to follow the project is this GitHub organization.

Useful links:

* Core repository: https://github.com/sdif-format/sdif
* Python package: https://pypi.org/project/sdif-format/
* Documentation: https://sdif-format.github.io/
* Issues and feedback: https://github.com/sdif-format/sdif/issues

Constructive criticism, real datasets, benchmark ideas and parser feedback are especially welcome
