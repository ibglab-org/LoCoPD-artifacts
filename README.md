# LoCoPD public artifacts

This repository contains approved supporting artifacts for the LoCoPD proposal.
The proposal document remains in the private project workspace. This is a
publication companion, not the LoCoPD source repository and not a software
distribution.

## Contents

- [`examples/revised_seed34_v5/transcript.json`](examples/revised_seed34_v5/transcript.json)
  is the frozen 16-session conversation used for the proposal-stage diagnostic
  example.
- [`examples/revised_seed34_v5/evidence_plan.json`](examples/revised_seed34_v5/evidence_plan.json)
  records the example's provenance, episode coverage, and simulator/authored
  state used to design the comparisons.
- [`examples/revised_seed34_v5/results_summary.json`](examples/revised_seed34_v5/results_summary.json)
  contains the compact reported model results.
- [`examples/revised_seed34_v5/validation.json`](examples/revised_seed34_v5/validation.json)
  records the pre-publication transcript checks for the example.

The example is a development diagnostic for the proposal. It does not establish
a memory-architecture advantage, causal medical conclusions, a validated
difficulty ladder, or a general benchmark result. Simulator truth and
transcript-supported evidence are kept separate in the supporting artifact.

The generation and evaluation implementation, private prompts, provider
requests, credentials, internal run logs, and unrelated state-layer work remain
in the private LoCoPD repository.

## Provenance

The revised seed-34 example is adapted from an existing sampled trajectory. The
conversation preserves the frozen transcript used in the diagnostic comparison;
the longitudinal relationship is not stated in the dialogue. The supporting
state plan is included so readers can distinguish design truth from what the
conversation itself says.

## Citation and contact

Please cite the associated LoCoPD proposal when using these materials. Questions
about the artifacts should be directed to the LoCoPD laboratory team.
