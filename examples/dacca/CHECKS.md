# Local checks

Checked on 3 November 2026 with CPU JAX/JAXlib 0.12.0.1.

- 146 tests passed: the existing SMC tests, the alpha decorator tests, and
  28 IF2 and Dacca tests added on this branch.
- Ruff lint and formatting checks passed for the added Python files.
- Type checking passed for the IF2 modules, model and example.
- Both `cuthbertlib` and `cuthbert` wheels built and installed. The example ran
  from a separate directory using those installed packages.
- The default float32 example completed two IF2 iterations with 32 particles
  over 12 months. Two independent ordinary-PF evaluations were finite and above
  the density floor. Their log likelihoods were -76.691017 and -76.739929 on this
  machine. These values are a run record, not a scoring-precision assessment or
  a promise of identical values on other devices and JAX versions.

The IF2 implementation is unchanged from the saved Dacca comparison. The helper
module omits the unused optimizer interface. The Dacca model has formatting,
docstrings and local data-loading changes; its equations and data are unchanged.
The alpha-only branch and original Cuthbert filter/resampling code are unchanged.

These checks used existing local dependencies. They do not constitute a full
upstream CI run or a fresh dependency-resolution test. No completed Dacca
optimization experiment was rerun for this branch.
