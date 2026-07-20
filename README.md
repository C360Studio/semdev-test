# semdev-test

Disposable target repo for exercising the semdev issue→PR flow end-to-end.

`example.com/health` classifies cpu/mem pressure. There is a known boundary bug
in `Classify` (see the open issue); its test fails until the boundary is fixed.
