Repro case for renovate 9271
============================

To run:
```
RENOVATE_ALLOWED_POST_UPGRADE_COMMANDS=".*" RENOVATE_TRUST_LEVEL=high renovate --log-level debug --token <token> croachrose/renovate9271
```

The post upgrade command, `touch vendor/BUILD.bazel`, should restore the empty
bazel build file after `go mod vendor` deletes it.
