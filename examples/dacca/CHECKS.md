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
  machine. Two evaluations do not establish scoring precision, and results may
  differ across devices or JAX versions.

The IF2 implementation is unchanged from the Dacca comparison recorded in
[`pypomp/comparisons`](https://github.com/pypomp/comparisons). Its
[numerical checks](https://github.com/pypomp/comparisons/blob/55a7f6f3407c8dc1d7a2f643ede6597682481292/reports/correctness.md)
and [optimization results](https://github.com/pypomp/comparisons/blob/55a7f6f3407c8dc1d7a2f643ede6597682481292/reports/optimization.md)
describe the full experiment, including failed checks and fits. That repository
currently requires access permission; please ask us if it is not visible to you.
The small tests in this branch can be run without access to it.

The helper module omits the unused optimizer interface. The Dacca model has
formatting, docstrings and local data-loading changes; its equations and data
are unchanged.
The original Cuthbert filter and resampling implementations are unchanged.

The checks used the existing local environment. Full upstream CI and installation
with freshly resolved dependencies have not been run. The completed Dacca
optimization experiments were not rerun for this branch.
