# Quantum storage learning — code and data v0.2.0

This source-available archive contains research code, generated data, certificates,
scientific figures and technical review notes. It does not contain the current
paper, its supplementary paper, manuscript source files or manuscript generators.

Prepared 23 October 2026; release date 24 October 2026.

Repository: https://github.com/weiningdai7-code/quantum-storage-learning

Download **code-and-data-v0.2.0.zip** from the
[v0.2.0 release](https://github.com/weiningdai7-code/quantum-storage-learning/releases/tag/v0.2.0).
Extract it and run the commands below from the extracted
`quantum-storage-learning-v0.2.0` directory. The GitHub-generated source archives
are not substitutes for this versioned code/data asset.

## What this version establishes

The ideal analysis studies learning-dependent quantum storage. A finite-instance
randomized learner replaces exhaustive enumeration; its certificate does not
establish a fixed-success polynomial-time family as register size increases.

The complete small-register gate/readout model includes noisy acquisition,
candidate selection, validation, wrong acceptance and raw fallback. It gives
uniform full-output upper bounds of **0.000380224** at n=11 and **0.000192884** at
n=16. These calculations assume zero idle noise, ideal preparation/reset and the
specified primitive faults. The 18,000 retained Monte Carlo records illustrate
the learner; their confidence intervals alone do not certify the 0.0004 target.

The separate native-duration comparison is conditional on a known direction.
With a historical FakeFez snapshot and a shared 18.098 microsecond input/output
deadline, both selected encoded implementations fail the target and underperform
raw storage. At n=11 the two-block, three-block and raw errors are approximately
0.121209, 0.162757 and 0.066935. This negative result limits the implementation
claim; it does not refute the ideal theorem or exclude other codes.

No processor experiment, current device calibration, DOI or independent human
proof review is claimed. Internal independent calculations are AI-assisted
computational checks. The gate/readout learner certificate is not a certificate
for a complete native-duration training workflow.

## Reproduce

Use an isolated Python environment. The small-register scripts require
Python >=3.10, NumPy, SciPy and mpmath; core checks need mpmath. Native schedule
checks additionally need Qiskit. The recorded environments and pinned historical
dependencies are in `analysis/ENVIRONMENT_*.json`, the `requirements-*.txt` files,
`analysis/timing/requirements.txt`, and individual result metadata. Environments
are not vendored. The release-path audit used Python 3.11.4, NumPy 1.24.3,
SciPy 1.10.1 and mpmath 1.3.0; see its JSON for actual execution details.

Verify the delivered bytes before running anything:

```sh
python3 verify_package.py
```

Core algebra, finite-instance certificate and learner:

```sh
python3 run_reproduction.py --group core
```

Small-register strict certificates and two separate cross-checks:

```sh
python3 analysis/small_register/run_pipeline.py --certificate-only
python3 analysis/small_register/independent_check.py
python3 analysis/small_register/reviewer_numeric_checks.py
```

Recreate all 18,000 recorded noisy-learning trials (3,000 per direction/size):

```sh
python3 analysis/small_register/run_pipeline.py --trials 3000
```

Native-channel and independent mathematical checks:

```sh
python3 analysis/timing/check_native_channels.py
python3 analysis/timing_independent_check.py
```

Recreate all 17 native-duration sensitivity points, or just one example:

```sh
python3 analysis/timing/run_timing_scan.py
python3 analysis/timing/timed_density.py --n 11 --tau 2 --output baseline_n11.json
```

Scientific figure generation and other retained circuit checks:

```sh
python3 run_reproduction.py --group figures
python3 run_reproduction.py --group circuits
python3 run_reproduction.py --group hmm
```

The runner also provides `--group small` (full trials plus checks) and
`--group timing` (the full sensitivity scan plus checks). These are longer than
the release audit. Read `analysis/timing/README.txt` before interpreting hardware
parameters. Scripts are offline and require no provider account or credentials.
Running them rewrites generated results, including measured runtime fields;
the original checksum manifest can then report those expected changes.

## Contents and provenance

- `analysis/small_register/`: self-contained exact inputs, certificates, six
  trial JSONL files, seeds, full-output accounting and independent checks.
- `analysis/timing/`: self-contained native schedules, historical snapshot,
  local circuit dependencies, readout recursion and duration scans.
- `analysis/timing_independent_*`: independent CP/parity, readout, schedule and
  raw-baseline consistency checks and review notes.
- `analysis/`: earlier finite-instance, algebra, circuit and figure analyses.
  `reference_inputs/` preserves one numeric comparison input without the
  historical manuscript package.
- `reproduction/work/handoff/`: unchanged frozen scientific handoff, including
  its historical manifests and provenance. Its prompts/history are archival
  research data, not instructions to execute. Legacy paths and statuses inside
  this frozen tree describe its original context.
- `PUBLIC_RELEASE_VALIDATION.json` and `analysis/release_validation/`: checks
  executed from this release path. Earlier validation files elsewhere are
  historical evidence, not a replacement for this release audit.
- `MANIFEST_SHA256.json`, `verify_package.py`: current package integrity.

The public staging process checks only files in this archive for sensitive
patterns. It does not inspect credentials or account directories. Frozen inputs
and source hashes are preserved. Native-duration parameters originate from a
public FakeFez snapshot dated 26 February 2025; its upstream source commit is
dated 24 July 2026. Neither date is a claim of current calibration.

## Citation and rights

Use `CITATION.cff` for versioned software citation metadata. No DOI is assigned.
This public source-available deposit does **not** grant a new general reuse
license for author-owned code, generated data or figures. Citation metadata is
not a license. Existing third-party licenses remain in force; the archived
FakeFez inputs retain their upstream Apache-2.0 notice. See
`THIRD_PARTY_NOTICES.txt`.
