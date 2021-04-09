Repro case for renovate 9271
============================

To run:
```
RENOVATE_ALLOWED_POST_UPGRADE_COMMANDS=".*" RENOVATE_TRUST_LEVEL=high renovate --log-level debug --token <token> croachrose/renovate9271
```

The post-upgrade command, `git checkout .`, should revert the changes from
`go mod vendor`. The PR for aws-sdk-go continues to show the updated files
because renovate does not detect that files have been unmodified.
