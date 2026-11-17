..
   # *******************************************************************************
   # Copyright (c) 2026 Contributors to the Eclipse Foundation
   #
   # See the NOTICE file(s) distributed with this work for additional
   # information regarding copyright ownership.
   #
   # This program and the accompanying materials are made available under the
   # terms of the Apache License Version 2.0 which is available at
   # https://www.apache.org/licenses/LICENSE-2.0
   #
   # SPDX-License-Identifier: Apache-2.0
   # *******************************************************************************

.. document:: PF Software Development Plan
   :id: doc__platform_software_development_plan
   :status: valid
   :version: 2
   :safety: ASIL_B
   :security: YES
   :realizes: wp__sw_development_plan[version==1]
   :tags: platform_management

.. _sw_development:

PF Software Development Plan
============================

Purpose
-------

The Software Development Plan defines the project-wide rules, methods,
languages, guidelines, and supporting tools applicable to software development
within S-CORE.

It establishes the development framework for:

* selection and use of programming and design languages;
* software design and implementation guidelines;
* API design guidelines;
* coding guidelines and coding standards;
* software configuration principles;
* development, build, and analysis tools; and
* development-related quality, safety, and security constraints.

The plan provides a common development baseline for S-CORE software components
and supports the applicable ISO 26262 and Automotive SPICE software development
processes.


Objectives and Scope
--------------------

The objective of this plan is to establish consistent software development
policies and practices for the S-CORE platform and its modules.

The plan applies to software development activities from detailed software
design through implementation and software integration.

Detailed procedures and rules are defined by the referenced S-CORE concepts,
guidelines, process descriptions, and tool documentation.

Approach
--------

Programming and Design Languages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The selection of programming languages is derived from
:need:`stkh_req__dev_experience__prog_languages`.

Programming and design languages are evaluated with respect to the following
criteria:

* unambiguous and well-defined syntax and semantics;
* suitability for safety- and security-related software development;
* support for modularity, abstraction, and encapsulation;
* support for structured programming and design constructs;
* availability of suitable development, analysis, and verification tools; and
* suitability for the supported target platforms.


.. list-table:: Programming Language Assessment
   :header-rows: 1
   :widths: 34 33 33

   * - Criterion
     - C++
     - Rust
   * - Well-defined syntax and semantics
     - Standardized language specification with mature compiler and analysis
       tool support.
     - Well-defined language specification with strong compiler diagnostics
       and tooling.
   * - Suitability for safety-related software
     - Established safety-development ecosystem including compiler toolchains,
       coding standards, static analysis, and established verification
       practices.
     - Strong type and memory-safety mechanisms with an evolving ecosystem for
       safety-related development and qualified toolchains.
   * - Modularity, abstraction, and encapsulation
     - Classes, templates, namespaces, and access-control mechanisms.
     - Modules, crates, traits, and explicit visibility control.
   * - Structured programming
     - Supported through established language constructs and applicable coding
       rules.
     - Supported and reinforced through language constructs and applicable
       coding rules.
       
C++
^^^

C++ is an approved programming language for S-CORE.

The project language baseline is **C++17**.

Use of language features introduced after C++17 requires an explicit project
decision. Such extensions shall be assessed with respect to safety, security,
quality, compiler and analysis-tool support, coding-rule coverage, and
target-platform compatibility.

The assessment shall involve, as applicable:

* :need:`rl__safety_manager`;
* :need:`rl__security_manager`; and
* :need:`rl__quality_manager`.

The final project-level decision is taken by the Project Lead Circle
(:need:`rl__project_lead`).

The applicable C++ coding rules are defined in
:need:`doc__cpp_coding_guidelines`.


Rust
^^^^

Rust is an approved programming language for S-CORE.

The project language baseline is **Rust Edition 2021**.

For Rust code belonging to safety-related software units, the project-defined
safe Rust subset shall be used. Use of ``unsafe`` Rust requires explicit
justification and approval according to the applicable development and safety
processes.

Where ``unsafe`` Rust is not required, its use should be prevented through
compiler configuration, for example:

.. code-block:: rust

   #![forbid(unsafe_code)]

The applicable Rust coding rules are defined in
:need:`doc__rust_coding_guidelines`.


C
^

C is not an approved implementation language for released S-CORE software
unless explicitly approved for a defined use.

C may be used during incubation, prototyping, or for integration with external
interfaces and toolchains where its use is technically required.

C code intended to become part of released S-CORE software shall be subject to
an explicit project decision before release. The decision shall define the
applicable coding rules, verification measures, toolchain, and safety and
security constraints.  

Detailed Design
~~~~~~~~~~~~~~~

Detailed software design is do~~mented using appropriate combinat~~ns of:

* UML or equivalent desig~~diagrams;
* textual design descri~~ions;
* traceable Sphinx-Needs ob~~cts; and
* source-code documentation where design information is closely related to the
  implementation.

The detailed design approach is defined in
:need:`doc_concept__imp_concept`.

Guidance for documenting detailed software design is provided by
:need:`gd_temp__detailed_design`.


Design Guidelines
~~~~~~~~~~~~~~~~~

The software design principles and implementation guidance applicable to
S-CORE are defined in:

* :need:`doc_concept__imp_concept`
* :need:`gd_guidl__implementation`

These definitions provide the project-wide basis for consistent software design
and implementation.


API Guidelines
~~~~~~~~~~~~~~

Public and internal software interfaces shall follow the applicable project API
design guidelines.

The applicable rules are defined in:

* :need:`doc__api_guidelines`
* :need:`doc__rust_api_design`

The guidelines address API consistency, interface usability, error handling,
naming, ownership, lifetime and resource-management concepts where applicable,
and language-specific interface design.


Coding Guidelines
~~~~~~~~~~~~~~~~~

Implementation shall comply with the coding guidelines applicable to the
selected programming language.

C++
^^^

The C++ coding guidelines are defined in:

:need:`doc__cpp_coding_guidelines`

Rust
^^^^

The Rust coding guidelines are defined in:

:need:`doc__rust_coding_guidelines`

Compliance with mandatory coding rules shall be verified through automated
analysis where supported by the applicable tooling and through review or other
verification measures where automated verification is not available.

Any permitted deviations from mandatory coding rules shall be explicitly
documented and justified according to the applicable coding guideline.     

Software Configuration
~~~~~~~~~~~~~~~~~~~~~~

Software configuration is defined through version-controlled source code,
build-system configuration, and explicitly managed configuration data.

Software behavior used for development, verification, or release shall not
depend on uncontrolled or manually maintained configuration outside the
applicable configuration-management process.

Where configurable behavior is required, the responsible software component
shall define, as applicable:

* the configuration mechanism and configuration data;
* permitted values and constraints;
* validation and error-handling behavior;
* default values, where applicable;
* compatibility and versioning rules; and
* applicable verification measures.

Software configuration items and their versions are controlled according to
:need:`doc__platform_config_mgt_plan`.

Software Development Tools
--------------------------

Development tools used within S-CORE are identified through the project tool
list:

:ref:`tools`

Tools within the scope of Tool Management shall be evaluated and, where
required, qualified and approved according to
:need:`doc__platform_tool_management_plan`.

The approved tool version, configuration, and intended use shall be controlled
according to :need:`doc__platform_config_mgt_plan`.

Verification-specific tools are additionally addressed by
:need:`doc__verification_plan`.

Static and dynamic C++ code-analysis methods and tools are described in
:need:`doc__cpp_code_analysis`.


GitHub
~~~~~~

GitHub provides the primary collaborative development environment for S-CORE.

It is used for:

* source-code and documentation version control;
* Pull Request-based contribution and review;
* ISSUE-based change and problem tracking;
* project discussions; and
* integration of automated CI workflows through GitHub Actions.

The contribution workflow is defined in:

:need:`doc__contr_guideline`

Security vulnerability reporting and the applicable vulnerability-management
process are defined in:

:need:`doc__platform_vulnerability_mgt_plan`

Where enabled for the applicable repositories, GitHub security capabilities may
include:

* **Dependabot** for dependency vulnerability detection and dependency-update
  Pull Requests;
* **code scanning** for automated detection of selected software weaknesses;
* **secret scanning** for detection of accidentally committed credentials or
  secrets; and
* **CodeQL** for supported static security analysis.


Sphinx
~~~~~~

Sphinx is used to generate project documentation from reStructuredText
sources.

Documentation sources are maintained under version control and processed as
part of the S-CORE Docs-as-Code workflow.


Sphinx-Needs
~~~~~~~~~~~~

Sphinx-Needs is used to manage structured engineering information within the
Docs-as-Code environment described in:

:need:`doc_tool__doc_as_code`

Sphinx-Needs objects represent requirements, architecture elements, work
products, traceability relationships, and other structured engineering
information.

The objects are maintained together with the documentation sources and
processed as part of the Sphinx documentation build.


PlantUML
~~~~~~~~

PlantUML is used for version-controlled textual diagrams.

It is primarily used for software-design and architecture views where a textual
diagram definition provides appropriate maintainability, reviewability, and
traceability.


Draw.io
~~~~~~~

Draw.io is used for graphical diagrams where a textual representation would not
provide sufficient readability or maintainability.

Typical applications include process descriptions, concept illustrations, and
complex graphical overviews.

C++ Host Compiler
~~~~~~~~~~~~~~~~~

The project-defined GCC toolchain is used as the host C++ compilation and
linking environment.

It supports development and verification activities including:

* compilation and linking;
* compiler diagnostics;
* sanitizer-enabled builds;
* unit-test builds; and
* creation of binaries used for software integration testing.

The applicable compiler version and configuration shall be defined by the
project toolchain configuration and managed according to the Tool Management
and Configuration Management Plans.


C++ Target Compiler
~~~~~~~~~~~~~~~~~~~

The QNX C/C++ toolchain (Q~~) is the planned target compilati~~ and linking
environment for the ~~X-based target platform.

Its use~~or safety-related software is sub~~ct to the applicable tool
evaluat~~n, qualification, and approval pr~~ess.

The applicable version, con~~guration, qualification scope, and intended use
shall be documented through Tool Management.


Clang-Tidy
~~~~~~~~~~

Clang-Tidy is used for automated static analysis of C++ source code.

The applicable version, checks, and project configuration shall be centrally
defined and version-controlled to provide consistent analysis across the
project.


GitHub CodeQL
~~~~~~~~~~~~~

CodeQL may be used as part of the project's automated static security analysis.

Where applied, CodeQL analysis is integrated into CI workflows to detect
supported classes of security weaknesses and programming defects before
changes are integrated.

The applicable analysis configuration defines the query suites and
project-specific queries used by S-CORE.

Project-specific queries may be added where the standard query suites do not
sufficiently address project-specific security requirements or programming
constraints.


Rust Host Compiler
~~~~~~~~~~~~~~~~~~

The Rust host-development toolchain shall use the project-defined Rust compiler
version compatible with the approved Rust edition.

The applicable compiler version shall be centrally defined and controlled
through the project toolchain and build configuration.

.. note::

   The Rust host compiler version shall be defined and evaluated before Rust
   software using that toolchain is included in an applicable release baseline.


Rust Target Compiler
~~~~~~~~~~~~~~~~~~~~

Ferrocene is planned as the Rust compiler toolchain for safety-related target
software.

The applicable Ferrocene version, configuration, intended use, and qualification
scope shall be established through the S-CORE Tool Management process before
use for released safety-related software.


Bazel
~~~~~

Bazel is the primary build system for S-CORE.

It is used to build, as applicable:

* software components;
* generated documentation;
* unit and integration tests; and
* other automated development and verification artifacts.

The version-controlled Bazel configuration, dependency definitions, and
toolchain definitions establish the controlled build configuration for S-CORE.

Together with the identified source, tools, and dependencies, this configuration
provides the basis for reproducible project builds.


