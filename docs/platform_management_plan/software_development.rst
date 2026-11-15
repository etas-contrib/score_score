..
   # *******************************************************************************
   # Copyright (c) 2025 Contributors to the Eclipse Foundation
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

The Software Development Plan defines the rules, methods, languages, guidelines,
and supporting tools to be applied during software development within S-CORE.

It establishes the project-wide development framework for:

* selection and use of programming and design languages,
* software design and implementation guidelines,
* API design guidelines,
* coding guidelines and coding standards,
* software configuration principles,
* development and analysis tools, and
* development-related quality and safety constraints.

The plan provides a common development baseline for software components and
supports compliance with the applicable ISO 26262 and Automotive SPICE
development processes.


Objectives and Scope
--------------------

The objective of this plan is to define consistent software development policies
and practices for the S-CORE platform.

The plan applies to the complete S-CORE software platform and covers the
development activities from software design through implementation and
integration.

Detailed procedures and rules are defined in the referenced S-CORE concepts,
guidelines, process descriptions, and tool documentation.


Approach
--------

Programming and Design Languages
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The selection of programming languages is derived from
:need:`stkh_req__dev_experience__prog_languages`.

Programming and design languages are evaluated according to the following
criteria:

* unambiguous and well-defined syntax and semantics,
* suitability for safety-related software development,
* support for modularity, abstraction, and encapsulation,
* support for structured programming and design constructs,
* availability of suitable development and verification tools, and
* suitability for the targeted software platform.


.. list-table:: Programming language assessment
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
     - Established safety-development ecosystem including qualified compilers,
       coding standards, static analysis, and traceability practices.
     - Strong type and memory-safety mechanisms with an emerging ecosystem for
       safety-related development and qualified toolchains.
   * - Modularity, abstraction, and encapsulation
     - Classes, templates, namespaces, modules, and access control.
     - Modules, crates, traits, and explicit visibility control.
   * - Structured programming
     - Fully supported.
     - Fully supported and reinforced by language constructs.


C++
^^^

C++ is an approved programming language for S-CORE.

The project baseline is **C++17**.

Use of language features introduced after C++17 requires an explicit project
decision. Such extensions shall be assessed with respect to safety, security,
quality, compiler support, and target-platform compatibility.

The assessment involves:

* :need:`rl__safety_manager`
* :need:`rl__security_manager`
* :need:`rl__quality_manager`

The final project-level decision is taken by the Project Lead Circle
(:need:`rl__project_lead`).

The applicable C++ coding rules are defined in
:need:`doc__cpp_coding_guidelines`.


Rust
^^^^

Rust is an approved programming language for S-CORE.

The current project baseline is **Rust Edition 2021**.

For Rust code belonging to safety-related units, the project-defined safe Rust
subset shall be used. Unless explicitly justified and approved, unsafe Rust is
prohibited.

Where applicable, this restriction shall be enforced by compiler configuration,
for example:

.. code-block:: rust

   #![forbid(unsafe_code)]

The applicable Rust coding rules are defined in
:need:`doc__rust_coding_guidelines`.


C
^

C is not an approved programming language for released S-CORE software.

C may temporarily be used during incubation or prototyping, provided that the
code can be processed by the selected project toolchain.

C code shall not be part of a released S-CORE software unit unless its use has
been explicitly approved and incorporated into the Software Development Plan.


Detailed Design
~~~~~~~~~~~~~~~

Detailed software design is documented using a combination of:

* UML diagrams,
* textual design descriptions,
* traceable Sphinx-Needs objects, and
* Doxygen-style source-code documentation where design information is closely
  related to the implementation.

The detailed design approach is defined in
:need:`doc_concept__imp_concept`.

Guidance for creating detailed designs is provided by
:need:`gd_temp__detailed_design`.


Design Guidelines
~~~~~~~~~~~~~~~~~

The software design principles and implementation guidance applicable to
S-CORE are defined in:

* :need:`doc_concept__imp_concept`
* :need:`gd_guidl__implementation`

These guidelines provide the project-wide basis for consistent software
architecture and component design.


API Guidelines
~~~~~~~~~~~~~~

Public and internal APIs shall follow the project API design guidelines.

The applicable rules are defined in:

* :need:`doc__api_guidelines`
* :need:`doc__rust_api_design`

The guidelines cover topics such as API consistency, interface usability,
error handling, naming, ownership, and language-specific API design.


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

Compliance with applicable mandatory coding rules shall be verified through
automated analysis where suitable and through review where automated
verification is not possible.


Software Configuration
~~~~~~~~~~~~~~~~~~~~~~

Software configuration is primarily expressed through version-controlled source
code and build-system configuration.

Runtime behavior shall not depend on unmanaged or manually maintained external
configuration files.

Where configurable behavior is required, the configuration mechanism,
configuration data, validation rules, and applicable verification measures
shall be explicitly defined by the affected software component.


Software Development Tools
--------------------------

Development tools used by S-CORE are managed through the project tool list:

:ref:`tools`

The tool list provides the basis for identifying tools that require assessment,
evaluation, or qualification according to the project's safety and quality
processes.

Verification-specific tools are additionally addressed by
:need:`doc__verification_plan`.

Static and dynamic code-analysis methods and tools are described in
:need:`doc__cpp_code_analysis`.


GitHub
~~~~~~

GitHub provides the primary collaborative development environment for S-CORE.

It is used for:

* source-code and documentation version control,
* pull-request based contribution and review,
* issue and defect tracking,
* security vulnerability reporting,
* project discussions, and
* continuous integration through GitHub Actions.

The contribution workflow is defined in:

:need:`doc__contr_guideline`

Security-related repository functionality and vulnerability-management
measures are addressed in:

:need:`doc__platform_vulnerability_mgt_plan`

S-CORE uses available GitHub security capabilities including:

* **Dependabot** for dependency vulnerability detection and dependency-update
  pull requests,
* **code scanning** for automated detection of relevant software weaknesses,
* **secret scanning** for detection of accidentally committed credentials or
  secrets, and
* **CodeQL** where applicable for static security analysis.


Sphinx
~~~~~~

Sphinx is used to generate the project software documentation from
reStructuredText sources.

Documentation sources are maintained under version control and are processed
as part of the project's Docs-as-Code workflow.


Sphinx-Needs
~~~~~~~~~~~~

Sphinx-Needs is used to manage structured engineering information within the
Docs-as-Code environment described in:

:need:`doc_tool__doc_as_code`

Sphinx-Needs objects are used for requirements, architecture elements,
development documentation, traceability, and other structured engineering
artefacts.

The objects are stored together with the documentation sources and processed by
the Sphinx documentation build.


PlantUML
~~~~~~~~

PlantUML is used for version-controlled textual UML diagrams.

It is primarily used for static and dynamic software-design and architecture
views where textual diagram definitions provide appropriate maintainability
and traceability.


Draw.io
~~~~~~~

Draw.io is used for graphical diagrams for which a textual PlantUML
representation is not suitable or would significantly reduce readability.

Typical applications include process descriptions, concept illustrations, and
complex graphical overviews.


C++ Host Compiler
~~~~~~~~~~~~~~~~~

GCC is used as the host C++ compiler and linker.

It supports development and verification activities including:

* compilation and linking,
* compiler diagnostics,
* sanitizer-based analysis,
* unit-test builds, and
* creation of binaries used for software integration testing.


C++ Target Compiler
~~~~~~~~~~~~~~~~~~~

The QNX C/C++ toolchain (QCC) is planned as the target compilation and linking
environment for the QNX-based target platform.

Its use in safety-related development is subject to the applicable tool
evaluation and qualification process.


Clang-Tidy
~~~~~~~~~~

Clang-Tidy is used for automated static analysis of C++ source code.

The applicable checks and project configuration shall be defined centrally to
ensure reproducible analysis across the project.


GitHub CodeQL
~~~~~~~~~~~~~

CodeQL is used where applicable as part of the project's automated static
security analysis.

CodeQL analysis is integrated into CI workflows to detect relevant security
weaknesses and programming defects before changes are integrated.

The centrally maintained analysis configuration defines the queries and rule
sets applicable to S-CORE.

Project-specific queries may be added where generic CodeQL analysis does not
sufficiently cover project-specific security requirements or programming
constraints.


Rust Host Compiler
~~~~~~~~~~~~~~~~~~

The Rust host-development toolchain shall use the project-defined Rust compiler
version corresponding to the approved Rust edition.

The concrete compiler version shall be centrally defined and reproducible
through the project toolchain/build configuration.

.. note::

   The exact Rust host compiler baseline is currently an open project decision
   and shall be fixed before the corresponding development baseline is released.


Rust Target Compiler
~~~~~~~~~~~~~~~~~~~~

Ferrocene is planned as the Rust compiler toolchain for safety-related target
software.

The concrete Ferrocene version and qualification scope shall be defined by the
applicable S-CORE tool evaluation and qualification activities.


Bazel
~~~~~

Bazel is the primary build system for S-CORE.

It is used to build:

* software components,
* generated documentation,
* unit and integration tests, and
* other automated development and verification artefacts.

The Bazel configuration together with the project's version-controlled
dependencies and toolchain definitions provides the basis for reproducible
project builds.
