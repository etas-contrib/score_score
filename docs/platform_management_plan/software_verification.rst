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

.. document:: PF Software Verification Plan
   :id: doc__platform_software_verification_plan
   :status: valid
   :version: 2
   :safety: ASIL_B
   :security: YES
   :tags: platform_management
   :realizes: wp__verification_plan[version==1]


.. _software_verification_plan:

PF Software Verification Plan
=============================

Purpose
-------

The Software Verification Plan defines the software integration and verification
approach for S-CORE. It provides an overview of the applicable verification
activities, methods, responsibilities, quality objectives, and supporting
processes and references the corresponding detailed specifications and guidance.

The plan defines the objectives, approaches, and strategies used to establish
and maintain confidence in the quality of the S-CORE software platform
throughout development and release.

The primary target audiences are :need:`rl__contributor` and
:need:`rl__committer`.


Objectives and Scope
--------------------

Objectives
~~~~~~~~~~

The software integration and verification activities pursue the following
objectives:

#. **Correctness** - Verify that the software platform and its modules implement
   their specified behavior and produce the expected results.

#. **Completeness** - Verify that all applicable and valid requirements are
   implemented and appropriately verified.

#. **Reliability** - Verify that the software operates reliably under the
   specified operating conditions and handles identified error conditions
   appropriately.

#. **Performance** - Verify that applicable performance requirements, such as
   response time, resource consumption, and throughput, are satisfied.

#. **Maintainability** - Support maintainability through appropriate software
   structure, verification evidence, documentation, and automated quality
   checks.

#. **Compliance** - Verify compliance with the applicable project processes,
   development guidelines, and verification requirements.

#. **Traceability** - Ensure traceability between requirements, design elements,
   implementation, verification activities, and verification results.


Verification Scope and Constraints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The verification activities defined in this plan apply to the S-CORE software
platform and the modules developed within the project.

S-CORE performs verification at unit, component, feature-integration, and
platform-integration level as defined in this plan.

Platform-integration testing performed by S-CORE uses the project's reference
environment and, where applicable, reference hardware.

Verification and validation of the S-CORE platform as integrated into a specific
product or target system remain the responsibility of the downstream integrator
or distributor.

Verification evidence produced by S-CORE using the reference environment may be
reused as supporting evidence, subject to an assessment of its applicability to
the specific target system and configuration.

The corresponding Assumptions of Use are defined in
:need:`aou_req__platform__testing` and
:need:`aou_req__platform__test_completion`.


Risks and Mitigation
~~~~~~~~~~~~~~~~~~~~

Risks identified through software integration and verification activities are
managed according to :doc:`project_management`.

This includes the identification, assessment, tracking, and mitigation of risks
that could affect the completeness, validity, or effectiveness of verification
activities and their evidence.


Schedule and Integration Triggers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Software integration and verification are performed continuously as part of the
project's change and contribution processes.

Software changes are introduced through Change Requests and follow the
applicable Change Management process defined in
:need:`doc__platform_change_management_plan`.

A feature is considered ready for integration only when the verification
activities applicable to the corresponding integration stage have been
completed and the required verification evidence is available.

Release-specific verification activities and verification reports are completed
as part of the release process defined in
:need:`doc__platform_release_management_plan`.


Approach
--------

General
~~~~~~~

The verification objectives defined above are implemented using a Continuous
Integration (CI) approach.

Software integration and automated verification are performed continuously as
part of the project's build and integration infrastructure.

Software, build configuration, verification specifications, tests,
infrastructure configuration, and documentation are maintained as
version-controlled artifacts.

Where technically feasible, verification activities are automated and integrated
into the CI pipelines. Manual verification is used where automation is not
feasible or where the artifact under verification cannot reasonably be verified
by an executable test.

The following sections define the software integration and verification approach
in more detail.


Software Integration
~~~~~~~~~~~~~~~~~~~~

Following the Continuous Integration approach, software elements are integrated
through controlled, automated builds and verification pipelines.

The following types of changes are integrated:

#. **New software elements** are integrated according to
   :need:`doc__contr_guideline`.

#. **Defect fixes** are integrated according to the Problem Resolution process
   defined in :need:`doc__platform_problem_resolution_plan`.

#. **Changes to existing software elements** follow the Change Management
   process defined in :need:`doc__platform_change_management_plan` and the
   contribution and review process defined in
   :need:`doc__pull_request_guideline`.

Verification methods and test derivation techniques shall be selected according
to the characteristics, requirements, architecture, safety and security
classification, and identified risks of the software element under
verification.

The selected methods shall provide adequate verification from unit level through
platform-integration level.

For example:

* Resource Usage Evaluation may be selected when requirements constrain
  resource consumption or when exhaustion of resources could affect required
  behavior.
* Interface Testing is appropriate for verifying externally visible API
  behavior and interactions between software elements.
* Boundary Value Analysis is appropriate where requirements define input
  ranges, limits, buffer sizes, or other boundary conditions.

These examples are not exhaustive. Additional verification methods shall be
selected where required by the characteristics, requirements, architecture,
safety or security classification, or identified risks of the software element.
Levels of Integration and Verification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

S-CORE defines three principal verification levels:

#. **Software unit and component verification**

   Verifies individual software units, their detailed design, and the
   integration of units into components or higher-level components.

   Verification is based on:

   * detailed design,
   * component architecture, and
   * component requirements.

#. **Software feature integration verification**

   Verifies the integration of components and modules required to realize a
   feature.

   Verification is based on:

   * feature architecture, and
   * feature requirements.

#. **Software platform integration verification**

   Verifies the integration of software elements into the S-CORE software
   platform using the defined reference environment and, where applicable,
   reference hardware.

   Verification is based primarily on:

   * stakeholder requirements,
   * applicable platform integration requirements, and
   * applicable Assumptions of Use.

.. note::

   These verification levels correspond conceptually to the software
   verification and integration activities addressed by ISO 26262-6,
   Clauses 9 to 11. Their application within S-CORE is subject to the tailoring
   defined in :need:`doc__score_platform_safety_plan`.

   S-CORE does not claim to provide complete target-system integration
   verification. Complete integration and verification of S-CORE within a
   specific target system remain the responsibility of the downstream
   integrator.

   S-CORE performs platform-integration tests using its reference environment
   and, where applicable, reference hardware. The resulting verification
   evidence is documented in :need:`wp__verification_platform_ver_report` and
   may serve as supporting evidence for downstream integration.

   Consequently, platform-integration tests maintained by S-CORE are not
   intended to provide complete verification coverage of all stakeholder
   requirements for every possible target integration.

   The applicable tailoring is defined in
   :need:`gd_guidl__verification_req_tailored`.


Consistent Set of Verifications
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

S-CORE follows a multi-repository development model while delivering a
consistent software platform stack to its users. See
:need:`dec_rec__strat__consistent_stack_vs_reference`.

Verification evidence for a platform release therefore needs to represent a
consistent set of software module versions and their dependencies.

Individual S-CORE modules, including SEooCs and other dependable software
elements, may develop and release features independently. Their verification
evidence is produced within the corresponding module repository and documented
in the module verification report. See also
:need:`dec_rec__platform__feature_delivery`.

For an S-CORE software platform release, verification evidence from the
integrated modules shall additionally be considered in the context of the
specific versions that form the released platform configuration.

The ``reference_integration`` repository provides the integration context for
this purpose. It demonstrates the integration and verification activities
expected for one defined combination of:

* S-CORE software platform modules,
* operating system,
* hypervisors where applicable, and
* reference hardware where applicable.

It also provides reference evidence for activities required from downstream
users according to :need:`aou_req__platform__testing`.

A **consistent set of verification evidence** for an S-CORE software platform
release includes, as applicable:

* platform-integration test results,
* feature-integration test results,
* component-integration test results,
* structural coverage results,
* applicable unit-test results,
* static-code-analysis results, and
* the documentation build and associated inspection evidence.

The mechanism used to establish this consistent evidence set is intentionally
not prescribed by this verification plan.

Evidence may, for example, be reproduced within ``reference_integration`` or
collected from module repositories, provided that its validity for the released
configuration is demonstrated.

The selected approach shall be documented by an S-CORE decision record, for
example :need:`dec_rec__int__scope_reference_integration`.

.. _verification-methods:

Verification Methods
~~~~~~~~~~~~~~~~~~~~

Software verification uses a combination of verification methods and test
derivation techniques.

The appropriate methods depend on the verification level, the characteristics
of the software element, its requirements, architecture, safety and security
classification, and identified risks.

Not every verification method is applicable at every verification level. The
tables below therefore specify:

* the verification levels for which each method is applicable, and
* its applicability to QM and ASIL B software.

Automated test specifications shall identify the applicable verification methods
and derivation techniques according to
:need:`gd_guidl__verification_guide`.

Where supported by the test infrastructure, the method identifiers defined
below shall be recorded using the ``TestType`` and ``DerivationTechnique``
metadata fields.

The method tables additionally contain verification activities that are not
represented by test metadata.

.. list-table:: Tool-supported test metadata
   :header-rows: 1
   :align: center

   * - Field
     - Identifier
     - Applicable test level
   * - TestType
     - interface-test
     - Unit, Component, Feature
   * - TestType
     - requirements-based
     - Component, Feature, Platform
   * - DerivationTechnique
     - requirements-analysis
     - All
   * - DerivationTechnique
     - boundary-values
     - Component, Feature, Platform
   * - DerivationTechnique
     - equivalence-classes
     - All
   * - DerivationTechnique
     - fuzz-testing
     - Unit, Component, Feature
   * - DerivationTechnique
     - error-guessing
     - All
   * - DerivationTechnique
     - explorative-testing
     - All

The fields may contain multiple comma-separated identifiers from the applicable
values above.

The test level is determined by the test's folder path. The module and
reference-integration folder structures are described in
:ref:`module_folder_structure` and
:ref:`reference_integration_folder_structure`.

Test cases shall link to requirements and design elements permitted for their
verification level:

.. list-table:: Test level and allowed requirement links
   :header-rows: 1
   :align: center

   * - Path contains
     - Test level
     - Allowed requirement links
   * - ``score/.*/tests/``
     - Component
     - ``comp``, ``comp_req``, ``comp_arc_dyn``, ``comp_arc_sta``,
       ``real_arc_int``, ``real_arc_int_op``
   * - ``score/tests/``
     - Feature
     - ``feat``, ``feat_req``, ``feat_arc_dyn``, ``feat_arc_sta``, ``mod``,
       ``mod_view_dyn``, ``mod_view_sta``, ``tool_req``
   * - ``platform_integration_tests/``
     - Platform
     - ``stkh_req``
   * - anything else
     - Unit
     - ``comp_req``, ``feat_req``

Tests outside these paths are considered unit-level tests.


.. list-table:: Software verification methods (and TestTypes)
   :header-rows: 1
   :align: center

   * - Methods (and TestTypes)
     - Identifier
     - Applicable* on level
     - Applicable* for QM / ASIL B
   * - Static Code Analysis
     - static-code-analysis
     - 1 Unit/Component
     - QM & ASIL B
   * - Structural Statement Coverage - Code coverage
     - structural-statement-coverage
     - 1 Unit/Component
     - QM & ASIL B
   * - Structural Branch Coverage - Code coverage
     - structural-branch-coverage
     - 1 Unit/Component
     - QM & ASIL B
   * - Walkthrough
     - walkthrough
     - All levels (1, 2, 3)
     - QM
   * - Inspection
     - inspection
     - 1 Unit/Component, 2 Feature Integration, -
     - ASIL B
   * - Manual verification (for non-testable artifacts)
     - manual-requirement-verification
     - All levels (1, 2, 3)
     - QM & ASIL B
   * - Interface Test
     - interface-test (TestType)
     - 1 Unit/Component, 2 Feature Integration
     - QM & ASIL B
   * - Requirements-based Test
     - requirements-based (TestType)
     - 1 Component, 2 Feature Integration, 3 Platform
     - QM & ASIL B
   * - Resource Usage Evaluation (only on reference environment)
     - resource-usage (TestType)
     - 2 Feature Integration
     - QM & ASIL B


.. note::

   *Applicable* means that the verification method shall be considered for the
   indicated safety and verification level.

   Where an indicated verification method is not used because it is not
   applicable to the specific software element, requirement, or verification
   objective, the rationale shall be documented.

For QM software, the rigor and extent of individual verification methods may be
adapted based on the applicable quality and risk considerations. Such adaptation
shall not invalidate the required verification objectives or traceability.

Static code analysis is part of :need:`wp__sw_implementation`. It is supported
by the tooling defined in
:need:`doc__platform_software_development_plan`.

As an additional measure, Resource Usage Evaluation ``resource-usage`` should
also be considered for Level 3 platform-integration testing, because this level
uses the integrated platform and may also be executed on reference hardware.

This can help identify platform-level resource constraints relevant to safety
and security.

Requirements-based testing is not required to provide 100% test coverage of
stakeholder requirements where another applicable verification method is more
appropriate.

Where stakeholder requirements are verified by executable tests,
demonstrations, inspections, or other verification activities, the corresponding
traceability shall be established.

The applicable tailoring is defined in
:need:`doc__platform_safety_plan`.

The following verification methods are optional at lower safety integrity
levels but may become required depending on the applicable safety
classification, architecture, and identified risks:

#. Control Flow Analysis (``control-flow-analysis``)

   Most beneficial for verification Level 1 Unit/Component and Level 2 Feature
   Integration.

#. Data Flow Analysis (``data-flow-analysis``)

   Most beneficial for verification Level 1 Unit/Component and Level 2 Feature
   Integration.

#. Fault Injection (``fault-injection``)

   Most beneficial for verification Level 2 Feature Integration.

#. Structural Function/Call Coverage
   (``structural-function-coverage`` and ``structural-call-coverage``)

   Most beneficial for verification Level 2 Feature Integration.

Test Derivation Methods
^^^^^^^^^^^^^^^^^^^^^^^

.. list-table:: Test case derivation methods (DerivationTechnique)
   :header-rows: 1
   :align: center

   * - Derivation methods
     - Identifier
     - Applicable* on level
     - Applicable* for QM / ASIL B
   * - Analysis of Requirements
     - requirements-analysis
     - All levels (1, 2, 3)
     - QM, ASIL B
   * - Analysis of Boundary Values
     - boundary-values
     - 1 Unit/Component, 2 Feature Integration
     - ASIL B
   * - Analysis of Equivalence Classes
     - equivalence-classes
     - All levels (1, 2, 3)
     - ASIL B
   * - Fuzz Testing (security focus)
     - fuzz-testing
     - 1 Unit/Component, 2 Feature Integration
     - QM, ASIL B
   * - Audit or Assessment (for ``manual-requirement-verification``)
     - audit-assessment-inspection
     - All levels (1, 2, 3)
     - QM, ASIL B

Fuzz testing should be considered particularly for externally accessible
interfaces, parsers, protocol implementations, and other software exposed to
untrusted or highly variable input.

.. note::

   \* Applicable means that the derivation technique shall be considered for the
   indicated safety and verification level.

   Where an indicated derivation technique is not used because it is not
   applicable to the specific software element, requirement, or verification
   objective, the rationale shall be documented.

For QM software, the rigor of individual test derivation methods may be adapted
based on the applicable quality and risk considerations.

The number of boundary values tested may be adapted based on risk and relevance,
with focus on boundaries that could affect required behavior.

Similarly, Equivalence Class Analysis may focus on relevant valid and invalid
classes, including empty, null, zero, and system-limit conditions where
applicable.

Equivalence Class Analysis should be complemented by Boundary Value Analysis
where boundaries are relevant.

The following additional test derivation methods may be applied where
appropriate:

* Error Guessing, indicated by ``error-guessing``, is derived from the knowledge
  or experience of the Contributor and is applicable at all test levels.
* Explorative Testing, indicated by ``explorative-testing``, is particularly
  applicable to feature- and platform-integration use cases.


Quality Criteria
~~~~~~~~~~~~~~~~

The following quality criteria define the verification objectives to be achieved
for the applicable release baseline.

.. list-table:: Quality criteria and respective goals
   :header-rows: 1
   :align: center

   * - #
     - Criterion
     - Goal for QM
     - Goal for Safety
   * - 1
     - Structural Statement Coverage (represented by Line Coverage)
     - 85%
     - 100%
   * - 2
     - Structural Branch Coverage
     - 85%
     - 100%
   * - 3
     - Coverage of software detailed design
     - n/a
     - 100%
   * - 4
     - Coverage of software architecture design
     - 100%
     - 100%
   * - 5
     - Verification coverage of software requirements specifications
     - 100%
     - 100%
   * - 6
     - Relative amount of executed tests
     - 100%
     - 100%
   * - 7
     - Relative amount of passed tests
     - 100%
     - 100%
   * - 8
     - Freedom from static code analysis violations
     - No remaining Critical findings
     - No remaining Critical or High findings
   * - 9
     - Freedom from compiler warnings and errors
     - 100%
     - 100%

Further quality goals are defined in :doc:`quality_management`.

Structural Coverage
^^^^^^^^^^^^^^^^^^^

The structural statement and branch coverage targets defined in the table above
are represented by the Line Coverage and Branch Coverage values reported by the
applicable unit-test coverage tooling.

The applicable coverage values shall meet the targets defined in the Quality
Criteria table.

Any deviation from a required coverage target shall be documented and justified
in the applicable module verification report before an official release.

Where a coverage target cannot be achieved because code is demonstrably
unreachable or cannot reasonably be exercised through the applicable tests, the
uncovered code shall be analyzed and the rationale for the deviation shall be
reviewed and documented.


Coverage of Detailed Design
^^^^^^^^^^^^^^^^^^^^^^^^^^^

Coverage of the detailed design for safety-related software is established
through the following work product:

* :need:`wp__sw_implementation_inspection` for safety-related implementation.

Evidence of the inspection is provided by the corresponding work product and
its review.

The inspection shall cover the implementation of the applicable detailed design.

The following measures additionally support verification of the detailed design:

* structural coverage according to the defined thresholds; and
* static analysis and linting.

These measures do not count towards the coverage percentage of this goal because
they have their own defined quality objectives.

For QM software, no separate quantitative coverage calculation is required at
detailed-design level, but the applicable work products shall be created and
reviewed as required by the development process.


Coverage of Architectural Design
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Verification coverage of the architectural design is established through the
following work products, as applicable:

* :need:`wp__sw_arch_verification`, performed by walkthrough for QM elements or
  inspection for safety-related elements;
* :need:`wp__sw_component_fmea` and :need:`wp__sw_component_dfa` for
  safety-related components; and
* :need:`wp__feature_fmea` and :need:`wp__feature_dfa` for safety-related
  features.

Each applicable architectural element shall be reviewed for the availability
and completeness of the required verification evidence.


Coverage of Software Requirements Specifications
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For a release, all applicable ``valid`` software requirements shall have the
verification evidence required by their classification and applicable
verification method.

Tests suitable for requirements verification include:

* :need:`wp__verification_comp_int_test`
* :need:`wp__verification_feat_int_test`
* :need:`wp__verification_platform_int_test`
* :need:`wp__verification_sw_unit_test`

A safety-related requirement requiring complete test coverage is considered
covered when the applicable ``FullyVerified`` traceability and the required
``complete test coverage`` information are available.

Where a requirement is verified using another approved verification method,
such as inspection, analysis, or manual requirement verification, the
corresponding verification evidence and traceability shall be provided.

For QM software, the requirement attribute ``complete test coverage`` is not
required, but each applicable requirement shall have at least one corresponding
verification link.


Relative Amount of Executed and Passed Tests
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

All required tests associated with the applicable release baseline shall be
executed and shall pass before release unless an approved deviation is
documented.

The objective is to execute and successfully complete all tests linked to
applicable ``valid`` requirements for the release.

Static Code Analysis
^^^^^^^^^^^^^^^^^^^^

Static code analysis is performed to support compliance with applicable coding
standards and to identify potential quality, safety, and security issues early
in the development process.

The applicable static-analysis tools are identified in
:need:`doc__platform_software_development_plan` and managed according to
:need:`doc__platform_tool_management_plan`.

Violations identified by static-analysis tools are categorized according to
their severity or according to the classification provided by the applicable
coding standard or analysis configuration.

For QM software, no Critical static-analysis findings shall remain open at
release.

For safety-related software, no Critical or High static-analysis findings shall
remain open at release.

Remaining Medium-severity findings shall be reviewed. Where such findings are
accepted, the acceptance and corresponding rationale shall be documented.

Where an analysis tool does not provide a severity rating, the finding shall be
assessed and classified according to the applicable rule set or project
criteria before release.


Rule Sets
"""""""""

The following rule sets are the minimum to be applied by every module. Modules
may add further rules or tools, for example ``clang-tidy``, but shall not remove
required rules without a documented deviation.

.. list-table:: Static code analysis rule sets and severity classification
   :header-rows: 1
   :widths: 10,30,30,30

   * - Language
     - Tool and rule set
     - Critical / High
     - Medium and below
   * - C++
     - GitHub CodeQL with the query pack
       ``codeql/misra-cpp-coding-standards`` (MISRA C++:2023, see
       :need:`doc__cpp_coding_guidelines` and
       :need:`doc__cpp_code_analysis`)
     - Violations of MISRA rules of category *Mandatory* or *Required*
     - Violations of MISRA rules of category *Advisory*
   * - C++
     - GitHub CodeQL default code scanning suite (``c-cpp``)
     - Alerts with a ``security-severity`` of 9.0 or higher (Critical) and
       7.0 to 8.9 (High)
     - All other alerts
   * - Rust
     - Clippy with the S-CORE lint profiles of ``score_rust_policies``
       (``strict`` for safety-related software, ``relaxed`` for QM software)
       and ``rustc`` warnings, see :need:`doc__rust_coding_guidelines`
     - Lints configured as ``deny`` in the applicable profile
     - Lints configured as ``warn`` and counted under "Freedom from compiler
       warnings and errors"
   * - Rust
     - GitHub CodeQL default code scanning suite (``rust``)
     - Alerts with a ``security-severity`` of 9.0 or higher (Critical) and
       7.0 to 8.9 (High)
     - All other alerts

Further improvements are foreseen to extend the checks for safety-related
software development.

The following rule sets are candidates for addition after evaluation:

* ``codeql/cpp-queries:codeql-suites/cpp-code-scanning.qls``
* ``codeql/cert-cpp-coding-standards:codeql-suites/cert-cpp-l1.qls``
* ``codeql/cert-c-coding-standards:codeql-suites/cert-c-l1.qls``

Static code analysis shall be executed for every module at least for each change
integrated into the ``main`` branch and before each release.

The analysis results in SARIF format for the release baseline shall be retained
as release evidence and summarized in the module verification report.

A finding that is not fixed shall be justified using the mechanism defined in
:need:`doc__cpp_code_analysis` and shall be listed in the module verification
report where required.


Deviation
"""""""""

Any deviation from a required verification or coverage target shall be
documented as part of the applicable module documentation.

For an official release, the deviation shall include a rationale and shall be
reviewed and approved as part of the applicable verification and release
process.


Test Development
~~~~~~~~~~~~~~~~

Verification activities and test cases are developed together with the
corresponding software implementation and verification requirements.

Where technically feasible, test execution shall be automated.

Derived test cases shall contain the metadata and traceability information
defined in :need:`gd_req__verification_link_tests`.

The applicable test-development environments are defined below.


Pre-Existing Test Cases
^^^^^^^^^^^^^^^^^^^^^^^

The recommendations defined in :need:`gd_guidl__verification_guide` apply to
pre-existing test cases.

Any pre-existing test case, for example from an OSS component, shall be reviewed
for applicability before it is credited as S-CORE verification evidence.

Where reused, the test case shall be adapted or supplemented as necessary to
comply with :need:`gd_guidl__verification_specification` and
:need:`gd_req__verification_link_tests`.


Test Execution and Result Analysis
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Automated tests are executed through the applicable build and CI pipelines.

Test results shall be evaluated against their defined expected results.
Failures, unexpected results, skipped tests, and incomplete executions shall be
analyzed and documented as required.

The :need:`rl__contributor` is responsible for addressing the results of the
verification activities associated with the contribution.


Release Test Execution
^^^^^^^^^^^^^^^^^^^^^^

Results of release test execution are recorded in the applicable module and
platform verification reports.

The release verification evidence shall provide an unambiguous ``PASSED`` or
``FAILED`` result for each required executed test case.

Skipped or non-executed required tests shall be identified in the applicable
verification report together with the corresponding rationale and disposition.


Manual Test Execution
^^^^^^^^^^^^^^^^^^^^^

The objective is to automate test execution wherever technically feasible.
Manual test execution shall be limited to cases where automation is not
reasonably feasible or appropriate.

Automated tests may be executed locally by the Contributor before changes are
pushed to the repository.

To support local test execution, applicable ``bazel test ...`` commands are
provided as part of the corresponding module and feature documentation.

When a manual test is used to verify a requirement or architectural element,
the same traceability requirements as for an automated test case apply.

The manual test specification shall use the applicable verification template
and Record Properties.

A manual test shall provide:

* the applicable traceability links;
* preconditions and required environment;
* step-by-step execution instructions;
* the expected result for the applicable steps;
* the mechanism for recording the observed result; and
* an unambiguous final result of ``PASSED`` or ``FAILED``.

The manual test specification and its execution evidence shall be part of the
test reporting and traceability and shall be reviewed as part of the applicable
verification activities.

The review shall confirm that manual execution is justified for the specific
test case.

In contrast to automated result comparison, the observed results and
confirmation of the test executor are recorded for manual tests.

The test instructions shall describe the expected result after each applicable
step. The final result shall be ``PASSED`` or ``FAILED`` based on the recorded
observations and acceptance criteria.

Manual test results shall be repeated or reconfirmed when changes to the
software, environment, requirements, or release baseline may invalidate the
previous result.

Verification of Non-Functional Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Some requirements cannot reasonably be verified through executable testing and
may therefore be verified using another applicable verification method, for
example analysis, inspection, or checklist-based assessment.

The same traceability principles as for automated and manual test cases apply.

The verification specification shall establish traceability to the verified
requirement and document:

* the applicable verification method;
* the analysis, inspection, or verification steps;
* the acceptance criteria;
* the evidence evaluated; and
* an unambiguous verification result.

The Record Properties for such verification are set to TestType
``manual-requirement-verification``.

The applicable verification specification shall describe the activities to be
performed and the evidence required to evaluate the requirement.

The verification specification and resulting evidence shall be part of the
verification reporting and traceability and shall be reviewed as part of the
applicable verification activities.

The review shall confirm that executable automated or manual testing is not
appropriate for the specific requirement and that the selected verification
method provides adequate evidence.

The final result shall be ``PASSED`` or ``FAILED`` based on the defined
acceptance criteria and recorded verification evidence.

The result shall be repeated or reconfirmed when changes to the requirement,
implementation, environment, or supporting evidence may invalidate the previous
verification result.


Test Selection and Regression Testing
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

All applicable automated regression tests shall be executed within the
continuous integration pipelines unless an explicitly defined test-selection
strategy applies.

The default S-CORE regression strategy is therefore to execute the complete
applicable automated test set rather than selecting subsets.

Manual and non-executable verification activities shall be repeated or
reconfirmed when changes may affect the validity of their existing results and
at minimum as required for the applicable release verification.

Their results shall be documented as part of the applicable verification
reports.

Committers are responsible for confirming that reused manual and non-functional
verification evidence remains applicable when reviewing the corresponding
feature or release.

Where the release baseline of a feature is intended to be reused as the basis
for a later major-version release, early assessment of the continued validity of
manual verification evidence supports subsequent platform integration and
verification.


Work Products and Traceability
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Traceability between verification-relevant work products is one of the
objectives of this plan.

An overview of the applicable verification work products and their relationships
is provided in :need:`wp__verification_plan`.

The relationship between a verification specification and the corresponding
requirement, architecture element, or design specification shall be established
using the applicable Sphinx-Needs traceability relationships.

Verification results shall be traceable to the corresponding verification
specification and the configuration for which the verification was performed.


Environments and Resources
--------------------------

Roles
~~~~~

The applicable project roles and responsibilities are defined in the S-CORE
process documentation.

The following roles are particularly relevant to this plan:

#. The :need:`rl__contributor` is responsible for performing the applicable
   software integration and verification activities and providing the required
   evidence for the contribution.

#. The :need:`rl__committer` is responsible for reviewing the contribution and
   confirming that the applicable verification requirements and acceptance
   criteria have been addressed.

Additional responsibilities are defined in
:need:`doc_concept__verification_process`.


Independence of Verification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Verification independence shall be established according to
:need:`gd_req__verification_independence`.

For component-, feature-, and platform-integration verification, the following
verification work products fall within the responsibility of the
:need:`rl__testing_community`:

* :need:`wp__verification_comp_int_test`
* :need:`wp__verification_feat_int_test`
* :need:`wp__verification_platform_int_test`

A :need:`rl__contributor` may develop verification specifications or tests for
software for which the applicable independence requirements are fulfilled,
including tests for functions the Contributor did not implement.

The :need:`rl__testing_community` supports the required independence through the
applicable review activities.

The following verification work product falls within the responsibility of the
:need:`rl__contributor`:

* :need:`wp__verification_sw_unit_test`

Unit tests may be developed by the same :need:`rl__contributor` who implemented
the corresponding software unit.

The applicable degree of independence is provided through the review process,
which requires review by a :need:`rl__committer` other than the author of the
Pull Request.

The applicable independence requirements are defined in
:need:`gd_req__verification_independence`.

Contributions and reviews are performed transparently within the S-CORE project
infrastructure, allowing additional review by project participants where
appropriate.

Tools
~~~~~

The tools listed in this section represent the principal tools used for test
execution and verification reporting. They do not constitute the complete
S-CORE Tool List.

The complete Tool List, including the controlled tool versions,
configurations, intended uses, and applicable Tool Verification Reports, is
managed according to :need:`doc__platform_tool_management_plan` and
:need:`doc__platform_config_mgt_plan`.

The purpose of the following overview is to describe the principal tooling used
to implement the software verification strategy.


.. rubric:: Bazel

Bazel is the primary build and test orchestration environment used to build
software components, documentation, and automated tests.


.. rubric:: GoogleTest (gtest)

GoogleTest is used for unit testing of S-CORE software components implemented in
C++ where applicable.


.. rubric:: Code Coverage (llvm-cov/llvm-profdata)

For C++ software, structural coverage achieved through unit testing is evaluated
using the applicable ``llvm-cov`` and ``llvm-profdata`` toolchain.

The C++ unit-test tooling supports the following coverage metrics:

* ``line`` - used in S-CORE to represent the
  ``structural-statement-coverage`` method.
* ``branch`` - used in S-CORE to represent the
  ``structural-branch-coverage`` method.
* ``function`` - used in S-CORE as additional supporting information for
  ``structural-function-coverage``.

Rust structural-coverage evidence is generated using the applicable approved
Rust toolchain and coverage configuration.

``llvm-cov`` and ``llvm-profdata`` may be used in dedicated host-based LLVM
workflows but are not assumed to be the default Rust coverage-reporting
mechanism.


.. rubric:: Integration Testing Framework (ITF)

The Integration Testing Framework (ITF) is used for applicable integration
verification activities.

It supports the definition and execution of tests using pytest-based test
execution.


.. rubric:: Rust

The S-CORE platform supports Rust as a programming language. Rust software uses
the applicable Rust test and verification tooling defined by the project
toolchain.


Verification Setups and Variants
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Different test frameworks are used to verify individual software elements and
their integration into the software platform.

The principal test setups are:

#. GoogleTest
#. Rust test and verification tooling
#. Integration Testing Framework (ITF)

The applicable setups are used to execute automated tests within the
corresponding continuous integration pipelines.


Test Execution Environment and Reference Hardware
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

S-CORE primarily provides middleware functionality above the operating-system
and hardware-abstraction layers. The platform is therefore not inherently bound
to one physical hardware implementation.

S-CORE integrates with POSIX operating systems that provide the applicable
abstraction from the underlying physical hardware.

The S-CORE reference environments use supported combinations of operating
systems and processor architectures representative of the intended integration
context.

Applicable configurations may include Linux and QNX environments on
``x86_64`` and ``aarch64`` architectures.

To support reuse and execution of verification activities across different
environments, unit and integration tests are executed, where applicable, for
the supported operating-system and hardware-architecture combinations provided
by the reference integration.

Integration, verification, and validation of the S-CORE platform on a specific
target device remain the responsibility of the downstream integrator or
distributor.

Platform-integration tests executed using S-CORE reference hardware may be used
as a starting point and as supporting evidence for downstream target
integration, subject to an assessment of their applicability.

See also the corresponding Assumptions of Use:

* :need:`aou_req__platform__testing`
* :need:`aou_req__platform__test_completion`


Reference Hardware Interaction with Infrastructure
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Where reference hardware is used, the applicable verification environment shall
define:

* the reference-hardware type and configuration;
* relevant hardware and firmware versions;
* the operating-system and software configuration;
* integration with the CI infrastructure;
* physical and remote access controls;
* physical maintenance responsibilities; and
* the mechanism used to establish an identifiable and controlled verification
  environment.

The applicable reference-hardware configuration shall be identified before
verification evidence dependent on that hardware is credited for an official
release.

Changes to the reference-hardware configuration that may affect existing
verification evidence shall trigger an assessment of whether the affected
verification activities need to be repeated.
