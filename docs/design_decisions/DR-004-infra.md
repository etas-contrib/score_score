<!--
Copyright (c) 2025 Contributors to the Eclipse Foundation

See the NOTICE file(s) distributed with this work for additional
information regarding copyright ownership.

This program and the accompanying materials are made available under the
terms of the Apache License Version 2.0 which is available at
https://www.apache.org/licenses/LICENSE-2.0

SPDX-License-Identifier: Apache-2.0
-->

# DR-004-Infra: Integrating External Development Tools into Pipelines

* **Status:** Draft
* **Owner:** Infrastructure Community
* **Date:** 2025-09-23

---
## Executive Summary

Within [../DR-001-Infra](DR-001-infra.md) we established a strategy for integrating external development tools (linters, formatters, static analyzers, code generators, license/SBOM and security scanners, doc builders) into S-CORE.

Regarding "normal tools" and pipelines the decision was:
- **Devcontainer** is the primary distribution for all tools, ensuring consistency and ease of onboarding.
- The same devcontainer (possibly stripped down) is used in CI for reproducibility.
- For small/fast CI jobs, **native installs** are preferred due to speed, especially when version pinning is less critical.

So as you can see that decision was rather high-level and still allows multiple ways to implement pipelines that run these tools in a consistent way (compared to local CLI, and IDE/editor integrations).

## Case Studies

Instead of a generic approach, this DR starts with very concrete examples of pipelines that run external tools. The goal is to identify common patterns and then generalize them into a reusable framework.

### Copyright Check

Within S-CORE we have a custom script to verify that all source files contain the correct copyright header. This is a simple Python script that reads all source files and checks the header.

Todays workflow is, and bare with me:

* Tooling repo
  * provides `cr_checker.py`
  * that script is wrapped into a bazel `py_library` named `cr_checker_lib`
  * Which is used by a bazel macro named `copyright_checker`, which creates two `py_binaries` based on that.
  * All of that is wrapped into the bazel module `score_tooling`.
* Module repo
  * Needs to depend on `score_tooling`
  * One of the BUILD files needs to call `copyright_checker` and therefore define a local `copyright` target.
    * Note that providing a correct list of source files is a manual task and extremely error-prone.
  * Has a workflow named `copyright.yml` which runs on pull_request. It calls `cicd-workflows/copyright.yml` and passes the exact name of the local `copyright` target.
* `cicd-workflows` repo
  * Provides the reusable workflow `copyright.yml`
  * Which clones the module repository
  * Installs bazel
  * Runs that local `copyright` target.

Is this too complicated? Let's disect the relevant requirements:

- **Version Pinning**: The script is pinned via bazel, so we have version pinning.
- **Performance**: The script is fast, but bazel increases the CI runtime to two minutes.
- **Low Friction** & **Maintenance Effort**: The local `copyright` target is very error-prone, Seems things could be simplified.

Alternatives: should we discuss that here, or later after some examples?

### License Check (Dash)

* Eclipse
  * Provides a backend service and a frontend in the form of `org.eclipse.dash.licenses-1.1.0.jar`
* Tooling repo
  * Format Converter
    * Provides a python script `dash_format_converter.bzl` to convert lock files of various package managers into the format dash understands.
    * Wraps that script into a bazel `py_library` named `dash_format_converter_lib` and a `py_binary` named `dash_format_converter`.
    * Provides a bazel rule `dash_format_converter` to run that binary.
  * License Checker
    * Provides a bazel `java_import` named `jar` around that jar file.
    * Provides a bazel macro `dash_license_checker`, which defines a `java_binary` named `license-check` which depend on calling `dash_format_converter` rule.
  * All of that is wrapped into the bazel module `score_tooling`.
* Module repo
  * Needs to depend on `score_tooling`
  * One of the BUILD files needs to call `dash_license_checker` and therefore define a local `license-check` target. It passes the local lock files as a parameter.
  * Has a workflow named `license_check.yml` which runs on pull_request_target. It calls `cicd-workflows/license-check.yml` and passes the exact name of the local `license-check` target and the DASH token (org secret).
* `cicd-workflows` repo
  * Provides the reusable workflow `license-check.yml`
  * Which clones the module repository
  * Installs bazel
  * Runs that local `license-check` target.
  * Evaluates the output and fails if there are any unknown licenses.
  * It provides detailed feedback in the PR

Let's again disect the relevant requirements:

- **Version Pinning**: The jar file and all scripts are pinned via bazel, so we have version pinning.
- **Performance**: The tool itself runs about 15 seconds, and bazel increases the CI runtime to 1-2 minutes.
- **Low Friction** & **Maintenance Effort**: Seems it could be simplified.
