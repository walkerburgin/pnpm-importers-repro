# pnpm-importers-repro

Run `pnpm install`:

```console
➜  pnpm i --frozen-lockfile
Scope: all 3 workspace projects
Already up to date
Done in 14ms using pnpm v12.21.0
```

Observe that there are no entries in the lockfile for the packages in the workspace.

Run `pnpm install --fix-lockfile`: 

```console
➜  pnpm i --fix-lockfile
Scope: all 3 workspace projects
Already up to date
Done in 19ms using pnpm v12.21.0
```

Observe the diff to `pnpm-lock.yaml`: 

```diff
diff --git a/pnpm-lock.yaml b/pnpm-lock.yaml
index 10c53e8..1002301 100644
--- a/pnpm-lock.yaml
+++ b/pnpm-lock.yaml
@@ -174,3 +174,7 @@ settings:
 importers:
 
   .: {}
+
+  packages/bar-lib: {}
+
+  packages/foo-lib: {}

```
