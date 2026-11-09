# SkillSpector Development, Testing, and Release Guide

SkillSpector is a Python 3.12+ security scanner for AI-agent skills. The README describes its purpose as detecting vulnerabilities, malicious patterns, and security risks before installation. Keep documentation and findings aligned with the current scanner implementation and test fixtures.

## Setup

```bash
git clone https://github.com/kandisaikishore/SkillSpector.git
cd SkillSpector
```

Use the project's declared dependency manager and scripts. Create an isolated Python environment and install the documented dependencies. Do not run untrusted skills merely to test the scanner.

## Scanner test matrix

Use synthetic, non-executable fixtures to test:
- Benign skills and known suspicious patterns
- Missing files, malformed metadata, and unexpected encodings
- Oversized input and deeply nested content
- Paths that attempt traversal outside the scan root
- Symlinks and platform-specific path handling where supported
- Findings with clear evidence and severity
- False-positive/false-negative regression fixtures

Treat scanned content as untrusted input. Parse safely and avoid executing discovered scripts, shell commands, or install hooks as part of scanning.

## Output and security

Each finding should identify the evidence and explain the risk without claiming certainty beyond the rule or analysis. Distinguish static indicators from proof of exploitability. Do not print secrets found in sample files unnecessarily; use fake tokens in fixtures.

## Platform and compiler prerequisites

Document OS-specific requirements for optional native extensions or compiler toolchains. If a build needs a C/C++ compiler, state how to verify its availability and provide supported installation guidance rather than implying every environment includes it.

## Pull-request checklist

- [ ] Run Python tests, lint, and type checks declared by the project.
- [ ] Add a fixture for each scanner behavior changed.
- [ ] Verify the scanner never executes scanned content.
- [ ] Record supported Python/OS requirements and unavailable checks.
- [ ] Keep security claims tied to reproducible evidence.
