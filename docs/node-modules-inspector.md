# Dify dependency inspector

The fork's [GitHub Pages report](https://hyoban.github.io/dify/) visualizes the
installed JavaScript dependencies across Dify's pnpm workspace, including development
dependencies. Use its report, graph, size, and duplicate-package views to explore
the dependency tree. This measures installed dependencies on Linux, not browser
bundle size or Python dependencies.

The `Node Modules Inspector` workflow on `analysis/node-modules-inspector` checks
out the latest `langgenius/dify` `main`, installs its frozen lockfile, and exports
the report with `node-modules-inspector@2.7.0`. The report title and
[`source.json`](https://hyoban.github.io/dify/source.json) identify the analyzed
upstream commit. Generated files live in a Pages artifact and are never committed.

To refresh the report, re-run all jobs of the latest
[Node Modules Inspector run](https://github.com/hyoban/dify/actions/workflows/node-modules-inspector.yml).
Every run resolves upstream `main` again. Pushing to the dedicated analysis branch
also rebuilds the report. The workflow is intentionally restricted to this fork;
its default branch and upstream application code do not need to change.

For local analysis, install dependencies at the workspace root, then run:

```sh
pnpm dlx node-modules-inspector@2.7.0
```

See the [inspector documentation](https://github.com/antfu/node-modules-inspector)
for its available views and CLI reports.
