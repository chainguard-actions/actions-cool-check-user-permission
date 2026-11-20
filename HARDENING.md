<!-- markdownlint-disable -->

# Hardening Report: actions-cool--check-user-permission/v2.3.0

> This file was generated automatically by the hardening agent.

**Policy SHA:** `374911c4be584df24e6da57af2d990570ef0f859`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **actions-cool--check-user-permission/v2.3.0** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### prior-fix (severity: high)

Carried forward from this version's previous harden, which fixed it; fix it again unless the code no longer has the problem. The previous harden changed action.yml without recording a finding for it, and this analysis reported nothing there. Re-apply its security changes unless the code no longer needs them. The previous patch:
```diff
diff --git a/action.yml b/action.yml
index d37ea7f..0947f30 100644
--- a/action.yml
+++ b/action.yml
@@ -2,12 +2,10 @@
 name: 'Check User Permission'
 description: 'A GitHub Action to check user permission of the current repository.'
 author: 'xrkffgg'
-
 # https://actions-cool.github.io/github-action-branding/
 branding:
   icon: 'user-x'
   color: 'purple'
-
 inputs:
   token:
     description: Secret GitHub API token to use for making API requests.
@@ -25,7 +23,6 @@ inputs:
   error-if-missing:
     description: Error if require or check if false
     required: false
-
 outputs:
   user-permission:
     description: User permission
@@ -33,7 +30,7 @@ outputs:
     description: The result of require
   check-result:
     description: The result of check
-
 runs:
   using: 'node20'
   main: 'dist/index.js'

```

Locations:

- `action.yml`

## Iteration Notes

### Iteration 1

**Notes:**

I made no changes. The earlier patch to action.yml only deleted four blank lines and changed nothing that affects security. The current action.yml is a node20 action with no 'uses:', no 'run:' steps, no hardcoded credentials and no shell expressions, so there was nothing to re-apply. The token input defaults to github.token, which is upstream's normal behaviour.

