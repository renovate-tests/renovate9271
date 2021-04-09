Repro case for renovate 9271
============================

To run:
```
RENOVATE_ALLOWED_POST_UPGRADE_COMMANDS=".*" RENOVATE_TRUST_LEVEL=high renovate --log-level debug --token <token> croachrose/renovate9271
```

The post upgrade command, `touch vendor/BUILD.bazel`, should restore the empty
bazel build file after `go mod vendor` deletes it.

This example demonstrates how a post-upgrade task can undelete a file deleted by
the upgrade. This is also a problem for unmodified files. For example:

1. Vendor a library like aws-sdk-go
2. Apply a patch to the vendored library
3. Renovate updates the library but removes your patch
4. The post-upgrade task re-applies the patch
5. The modified file is restored to the original version
6. Renovate ignores the restoration
