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

.. document:: Platform Safety Management Plan
   :id: doc__platform_safety_management_plan
   :status: draft
   :version: 3
   :safety: ASIL_B
   :security: NO
   :realizes: wp__platform_safety_plan[version==1], wp__safety_tailoring[version==1]
   :tags: platform_management_plan


.. _platform_safety_management_plan:

PF Safety Management Plan
=========================

Purpose
-------

The purpose of the Safety Management Plan is to define the functional safety
management framework for the S-CORE platform and to ensure that the applicable
requirements of ISO 26262 are addressed according to the defined scope and
tailoring.

In particular, this plan defines:

* the functional safety management roles, responsibilities, and authorities;
* the functional safety lifecycle applicable to the S-CORE platform;
* the required functional safety activities and work products;
* the project-wide tailoring of functional safety activities and the
  corresponding rationales;
* the planning, coordination, monitoring, and reporting of functional safety
  activities;
* the management of deviations from the safety plan;
* the preparation and maintenance of the safety case and its supporting
  evidence; and
* the activities required to assess functional safety process conformance,
  including the functional safety audit.


Objectives and Scope
--------------------

Functional Safety Management Goals
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The primary functional safety management objective is to establish and maintain
conformance with the applicable requirements of ISO 26262 within the defined
S-CORE scope and tailoring.

To achieve this objective, functional safety management shall:

* plan the required functional safety activities and work products;
* assign responsibilities for their execution, verification, and approval;
* coordinate and monitor execution of the planned safety activities;
* identify and manage deviations from the Safety Plan;
* monitor completeness and maturity of the required safety work products;
* measure functional safety status using defined criteria and metrics;
* report functional safety status, risks, and unresolved issues; and
* provide the evidence required to support the safety case and functional safety
  audit.

Functional Safety Management Scope
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The functional safety management scope is aligned with the overall S-CORE
project scope.

The S-CORE platform and its components are developed and integrated for an
assumed technical system. For functional safety purposes, the platform is
developed as a Safety Element out of Context (SEooC).

Platform development follows the processes defined by S-CORE. Responsibilities
for management, requirements engineering, architecture, implementation,
integration, verification, and functional safety activities are assigned
through the applicable processes and role definitions.

The following project-wide assumptions apply:

* the highest targeted Automotive Safety Integrity Level is ASIL B;
* safety-related development activities are performed according to the
  applicable and tailored ISO 26262 requirements for ASIL B; and
* safety-related software intended to support ASIL B applications is developed
  according to the applicable S-CORE safety processes.

The software platform consists of Features that are defined by requirements and
may be developed in parallel. Features are implemented by software components
organized into Modules.

For safety-related Module development, Module-specific safety activities,
assumptions, work products, and tailoring shall be defined in the applicable
Module Safety Plan.

The template :need:`gd_temp__module_safety_plan` shall be used for this purpose.

Tailoring
~~~~~~~~~

ISO 26262 activities and work products are tailored according to the S-CORE
development scope and the assumptions associated with development of the
platform as a software SEooC.

Tailoring is defined at two levels:

* **Project-wide tailoring** applies to the S-CORE platform and is defined in
  this Safety Management Plan.
* **Module-specific tailoring** applies to an individual Module and shall be
  documented and justified in the corresponding Module Safety Plan.

Module-specific tailoring may result from characteristics of the Module, its
safety classification, applicable SEooC assumptions, or the selected
qualification approach, including qualification according to ISO 26262 Part 8,
Clause 12, where applicable.

For changes to existing safety-related Features or Modules, an impact analysis
shall determine which existing safety activities and work products are affected
and which activities need to be created, updated, or repeated.

The following ISO 26262 work products and activities are tailored out at
platform level. The rationale for each tailoring decision is documented below.


System-Level Development
^^^^^^^^^^^^^^^^^^^^^^^^

System-level development is outside the S-CORE platform development scope and
remains the responsibility of the system integrator.

Therefore, the following system-level work products are not created by S-CORE:

* :need:`std_wp__iso26262__management_751`,
  :need:`std_wp__iso26262__system_652`,
  :need:`std_wp__iso26262__system_653`,
  :need:`std_wp__iso26262__system_654`,
  :need:`std_wp__iso26262__system_655`,
  :need:`std_wp__iso26262__system_656`,
  :need:`std_wp__iso26262__system_657`,
  :need:`std_wp__iso26262__system_751`,
  :need:`std_wp__iso26262__system_752`,
  :need:`std_wp__iso26262__system_851`, and
  :need:`std_wp__iso26262__system_852`.

Stakeholder requirements (:need:`std_wp__iso26262__system_651`) remain within
the S-CORE scope where they are required to define assumptions, constraints, and
expected behavior of the software platform.

System- and hardware-related requirements that must be assumed by the software
SEooC are treated as assumed requirements or constraints of the platform and
are provided to platform integrators as applicable.

System-level verification remains the responsibility of the system integrator
and is therefore outside the S-CORE verification scope.

S-CORE may provide Platform Integration Tests for selected stakeholder
requirements for demonstration and integration-support purposes. These tests do
not constitute complete system-level verification.

Software integration testing of applicable Feature requirements is performed
according to the S-CORE software verification process and the applicable
requirements of ISO 26262 Part 6.

The resulting verification evidence may be reused by an integrator as supporting
evidence. The integrator remains responsible for determining whether this
evidence is sufficient for verification of the Technical Safety Requirements in
the target system.

As S-CORE provides the software platform as source code and does not perform
integration into the final target system,
:need:`std_wp__iso26262__software_1052` is tailored out.

Target Hardware Verification
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

S-CORE performs integration and verification on defined reference hardware.
Verification on the final target hardware is outside the S-CORE development
scope and remains the responsibility of the platform integrator.

Therefore, the following work products are tailored out at platform level:

* :need:`std_wp__iso26262__software_1151`
* :need:`std_wp__iso26262__software_1152`


Calibration
^^^^^^^^^^^

S-CORE platform components do not use calibration data within the defined
development scope. Configuration mechanisms are used instead.

Consequently, the following calibration-related work products are not
applicable:

* :need:`std_wp__iso26262__software_app_c_52`
* :need:`std_wp__iso26262__software_app_c_54`
* :need:`std_wp__iso26262__software_app_c_57`


Distributed Development
^^^^^^^^^^^^^^^^^^^^^^^

S-CORE development is organized as a common open-source project. Contributions
are integrated through the S-CORE development, review, and approval processes.

External open-source components and externally developed SEooCs are handled
through the applicable qualification or integration processes rather than
through the distributed development model.

Therefore, the following distributed-development-related work products and
requirements are tailored out:

* :need:`std_wp__iso26262__support_551`
* :need:`std_wp__iso26262__support_552`
* :need:`std_wp__iso26262__support_553`
* :need:`std_wp__iso26262__support_554`
* :need:`std_wp__iso26262__support_555`
* :need:`std_req__iso26262__management_64610`

Hardware Elements
^^^^^^^^^^^^^^^^^

Development and qualification of hardware elements are outside the S-CORE
platform development scope.

Therefore, the following work products and requirements are tailored out:

* :need:`std_wp__iso26262__support_1351`
* :need:`std_wp__iso26262__support_1352`
* :need:`std_wp__iso26262__support_1353`
* :need:`std_req__iso26262__management_6454`


Proven in Use
^^^^^^^^^^^^^

A proven-in-use argument is not used as a qualification approach for the S-CORE
platform.

Therefore, the following work products and requirements are tailored out:

* :need:`std_wp__iso26262__support_1451`
* :need:`std_wp__iso26262__support_1452`
* :need:`std_req__iso26262__management_6453`


Interfaces with Applications Outside the Scope of ISO 26262
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Interfacing safety-related functionality with applications outside the scope of
ISO 26262 is not part of the defined S-CORE safety lifecycle.

Therefore, :need:`std_wp__iso26262__support_1551` is tailored out.


Integration of Safety-Related Systems Developed Outside ISO 26262
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Integration of safety-related systems that have not been developed according to
ISO 26262 is not part of the defined S-CORE platform development scope.

Therefore, :need:`std_wp__iso26262__support_1651` is tailored out.

ASIL Decomposition
^^^^^^^^^^^^^^^^^^

ASIL decomposition is not applied within the S-CORE platform development scope.

Therefore, the following work products are tailored out:

* :need:`std_wp__iso26262__analysis_551`
* :need:`std_wp__iso26262__analysis_552`

Consequently, the following associated safety-analysis requirements are also
tailored out:

* :need:`std_req__iso26262__analysis_641`
* :need:`std_req__iso26262__analysis_642`
* :need:`std_req__iso26262__analysis_643`
* :need:`std_req__iso26262__analysis_644`


Hardware-Software Interface
^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Hardware-Software Interface (HSI) is defined by the system and hardware
integration context, which is outside the S-CORE development scope.

S-CORE defines assumptions and constraints on the hardware and execution
environment through the applicable Assumptions of Use (AoUs). Integration on
reference hardware is provided for development and verification purposes but
does not replace the platform integrator's HSI definition and verification for
the target environment.

Therefore, :need:`std_wp__iso26262__software_652` is tailored out at platform
level.


Item-Level Impact Analysis
^^^^^^^^^^^^^^^^^^^^^^^^^^

The S-CORE software platform is developed as an element rather than as an
ISO 26262 item. Item-level definition and management therefore remain outside
the S-CORE project scope.

Consequently, :need:`std_wp__iso26262__management_651` and the corresponding
item-level impact analysis are tailored out.


ASIL-Specific Requirements
^^^^^^^^^^^^^^^^^^^^^^^^^^

Requirements that are not applicable to the targeted ASIL B development scope
are tailored out:

* :need:`std_req__iso26262__system_6423`
* :need:`std_req__iso26262__system_6424`
* :need:`std_req__iso26262__system_6425`
* :need:`std_req__iso26262__support_12423`

Functional Safety Assessment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

A Functional Safety Assessment is not performed by the S-CORE project.

Therefore, the corresponding requirements are tailored out:

* :need:`std_req__iso26262__management_64121`
* :need:`std_req__iso26262__management_64122`
* :need:`std_req__iso26262__management_64123`
* :need:`std_req__iso26262__management_64124`
* :need:`std_req__iso26262__management_64125`
* :need:`std_req__iso26262__management_64126`
* :need:`std_req__iso26262__management_64127`
* :need:`std_req__iso26262__management_64128`
* :need:`std_req__iso26262__management_64129`
* :need:`std_req__iso26262__management_641210`
* :need:`std_req__iso26262__management_641211`
* :need:`std_req__iso26262__management_641212`
* :need:`std_req__iso26262__management_641213`


Confirmation Reviews
^^^^^^^^^^^^^^^^^^^^

S-CORE performs verification reviews of applicable work products through the
defined Formal Document Review process.

Confirmation reviews are not performed as a separate assurance activity within
the S-CORE scope.

Therefore, the following requirements are tailored out:

* :need:`std_req__iso26262__management_64101`
* :need:`std_req__iso26262__management_64102`
* :need:`std_req__iso26262__management_64103`
* :need:`std_req__iso26262__management_64104`
* :need:`std_req__iso26262__management_64105`


Approach
--------

Safety Culture
~~~~~~~~~~~~~~

S-CORE promotes a functional safety culture in which contributors are encouraged
to identify risks, question assumptions, report potential safety issues, and
take responsibility for the quality and safety of their work.

The project supports this culture through:

* clearly defined roles and responsibilities;
* documented processes, guidelines, and templates;
* functional safety training appropriate to assigned responsibilities;
* open technical discussion and review;
* mechanisms for reporting safety concerns and process improvements;
* independent review and verification where required;
* automated process and work-product checks where appropriate; and
* continuous improvement based on findings, experience, and feedback.

Adherence to defined processes is supported through automated checks, repository
controls, reviews, and manual inspections.

Functional safety requirements are integrated into the development processes
rather than treated as separate activities. This ensures that functional safety
is considered throughout planning, requirements engineering, architecture,
implementation, integration, verification, and release.


Cybersecurity Interface
~~~~~~~~~~~~~~~~~~~~~~~

Functional safety and cybersecurity have distinct objectives but may affect the
same platform functions, assumptions, requirements, and architectural decisions.

Safety and cybersecurity activities shall therefore be coordinated where
cybersecurity threats or controls may affect functional safety.

This includes, where applicable:

* identifying cybersecurity threats with potential safety impact;
* considering security-related assumptions and findings in safety analyses;
* aligning interacting safety and cybersecurity requirements;
* maintaining traceability between related safety and security concerns;
* coordinating reviews of architectural decisions affecting both domains; and
* communicating cybersecurity findings that may invalidate safety assumptions,
  requirements, or analyses.

The :need:`rl__safety_manager` and the responsible security management roles
shall coordinate the treatment of identified cross-domain dependencies.

Changes to the cybersecurity context that may affect functional safety shall
trigger an evaluation of the affected safety assumptions, analyses, or work
products.

Cybersecurity management is defined in :doc:`security_management`.


Functional Safety Management Organization
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functional safety management is integrated into the S-CORE project organization.

The project organization provides the roles, responsibilities, decision
mechanisms, and competence required to plan, execute, monitor, and assess
functional safety activities.

As an Eclipse Foundation project, S-CORE additionally operates within the
governance framework defined by the `Eclipse Foundation Project Handbook
<https://www.eclipse.org/projects/handbook/>`_.


Eclipse Roles
^^^^^^^^^^^^^

The Eclipse contribution model distinguishes between Contributors, Committers,
and Project Leads.

* **Contributors** may propose changes to the project. Contributions affecting
  safety-related work products are subject to the same review, verification, and
  approval requirements as other safety-related changes. Contributors cannot
  independently approve and merge their contributions.

* **Committers** may approve and integrate changes according to their repository
  permissions and the project's governance rules. Committers performing
  safety-related activities shall satisfy the competence requirements defined
  for their assigned responsibilities.

* **Project Leads** provide project-level governance. The
  :need:`rl__project_lead` additionally fulfills the project-management
  responsibilities assigned by the S-CORE functional safety processes.


Project Roles
^^^^^^^^^^^^^

Functional safety roles and their responsibilities are defined by the applicable
S-CORE processes and generic project role definitions.

Role assignments are documented through the applicable role-assignment
mechanism.

The main project roles for functional safety management are:

* :need:`rl__project_lead`
* :need:`rl__safety_manager`
* :need:`rl__safety_engineer`

Additional roles may have functional safety responsibilities as defined by the
applicable processes.

competence, experience, and knowledge for their assigned responsibilities.

The required skills and experience for :need:`rl__project_lead`,
:need:`rl__safety_manager`, and :need:`rl__safety_engineer` are defined in the
corresponding role definitions.

Committers working on safety-related Modules shall additionally demonstrate:

* at least two years of experience in safety-related software development,
  verification, or management relevant to their assigned responsibilities,
  including appropriate knowledge of functional safety standards such as
  ISO 26262; and
* completion of the applicable S-CORE process training.

Evidence of the required competence shall be recorded through the applicable
role-assignment mechanism.

Repository ``CODEOWNERS`` are used to enforce review by authorized and
appropriately competent persons for defined safety-related areas.

Assignment of safety-related CODEOWNERS shall be reviewed by the
:need:`rl__safety_manager` and documented through the applicable role-assignment
mechanism.

Where approval authenticity is relevant, the configured GitHub identity and
signature mechanisms are used to provide traceable evidence of the person
performing the approval.


Functional Safety Resources
~~~~~~~~~~~~~~~~~~~~~~~~~~~

A :need:`rl__safety_manager` is assigned for platform-level functional safety
management. The assignment is documented in
:need:`doc__platform_safety_manager`.

For safety-related Module development, the responsible safety management role
shall be identified in the corresponding Module Safety Plan.

The :need:`rl__safety_manager`, supported by the
:need:`rl__project_lead`, Feature Team Leads, and assigned safety roles, ensures
that required functional safety activities are planned, assigned, monitored,
and completed throughout the applicable safety lifecycle.

Required activities, resources, dependencies, and milestones shall be
represented in the project planning infrastructure according to
:doc:`project_management`.


Tools
^^^^^

GitHub provides the primary infrastructure for planning, development, review,
integration, and storage of project work products.

The following mechanisms support functional safety management:

* GitHub Issues for planning and tracking safety activities and findings;
* GitHub Pull Requests for review and approval of changes;
* repository rules and CODEOWNERS for enforcing required reviews;
* CI workflows for automated verification; and
* GitHub Projects, milestones, and issue relationships for planning and
  monitoring safety-related work.

Safety-related Issues shall use the applicable project classification, including
the ``safety`` label where defined.

The applicable Issue Types and workflows are defined in
:doc:`project_management`.

The :need:`rl__safety_manager` regularly reports functional safety status to the
:term:`Project Lead Circle`.

Reporting shall consider, as applicable:

* completion status of planned safety activities;
* maturity and completeness of safety work products;
* verification status;
* open safety anomalies and findings;
* deviations from applicable Safety Plans;
* safety-related risks and dependencies; and
* readiness for upcoming safety-related milestones or releases.

The status is derived from the applicable safety plans and verification
evidence, including:

* :need:`wp__platform_safety_plan`
* :need:`wp__module_safety_plan`
* :need:`wp__verification_platform_ver_report`
* :need:`wp__verification_module_ver_report`


Escalation
^^^^^^^^^^

Safety issues shall be resolved at the lowest organizational level capable of
providing an appropriate resolution.

Where resolution cannot be achieved, the issue shall be escalated according to
the following path:

.. code-block:: text

   Module / Feature Team
            |
            v
      Safety Manager
            |
            v
       Project Lead
            |
            v
   Project Lead Circle
            |
            v
    Eclipse Foundation
     (where applicable)

The :term:`Project Lead Circle` is the highest project-level escalation body
within S-CORE. Applicable Eclipse Foundation governance remains authoritative
for matters within its scope.

Escalation is required, for example, when:

* a safety issue cannot be resolved at Module or Feature Team level;
* required resources for mandatory safety activities are unavailable;
* a significant deviation from an approved Safety Plan cannot be resolved;
* disagreement exists regarding the disposition of a safety anomaly;
* a required safety activity cannot be completed as planned; or
* an unresolved safety issue may affect release readiness.

Significant safety-related escalations and their disposition shall be documented
and traceable.

S-CORE applies those ISO 26262 lifecycle activities that are applicable to the
development of the software platform as a SEooC. Activities outside the S-CORE
development scope are addressed through the documented tailoring and the
corresponding SEooC assumptions.

Project governance phases defined by the Eclipse Foundation and the S-CORE
functional safety lifecycle serve different purposes. Eclipse project maturity
or lifecycle status does not by itself demonstrate completion of the applicable
functional safety activities.

Functional safety readiness is determined from completion and adequacy of the
applicable safety activities and work products, their verification, and the
results of the defined functional safety assurance activities.

Platform-level safety activities are planned through this Safety Management
Plan and the Platform Safety Plan. Module-specific safety activities are planned
through the corresponding Module Safety Plans.

Changes to safety-related Features or Modules shall trigger an impact analysis
to determine which safety activities and work products need to be created,
updated, or repeated.


Functional Safety Requirements
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Functional safety requirements engineering is performed according to the
applicable S-CORE requirements engineering processes.

Applicable ISO 26262 requirements are mapped to the corresponding S-CORE
processes, guidance, activities, and work products. See, for example,
:need:`gd_req__safety_doc_status`.


Functional Safety Schedule
~~~~~~~~~~~~~~~~~~~~~~~~~~

Platform-level safety activities and milestones are defined by the Platform
Safety Plan below and tracked through the project planning infrastructure.

Module-specific safety activities and milestones shall be defined in the
corresponding Module Safety Plan using
:need:`gd_temp__module_safety_plan`.


Functional Safety Development
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Software development activities applicable to safety-related software are
defined in :doc:`software_development`.


Functional Safety Verification
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Verification of safety-related software and work products is performed according
to :doc:`software_verification`.


Functional Safety Tool Management
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Tools used for safety-related development activities are managed according to
:doc:`tool_management`.


Functional Safety Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Project-wide functional safety work products are defined by this Safety
Management Plan, the Platform Safety Plan, and the applicable processes.

Module-specific functional safety work products shall be identified and planned
in the corresponding Module Safety Plan using
:need:`gd_temp__module_safety_plan`.


Functional Safety Quality Criteria
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Quality management and the general quality criteria applicable to safety-related
work products are defined in :doc:`quality_management`.


Platform Safety Plan / Package
------------------------------

The Platform Safety Plan defines and tracks the project-wide functional safety
work products required for the planned S-CORE platform release.

The Platform Safety Package collects the resulting safety evidence and provides
the basis for evaluating the functional safety status of the corresponding
platform baseline.

The tables below provide the current status of the applicable project-wide work
products.

.. _sw_platform_wp_list:

Functional Safety/Security Management SW Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table:: SW Platform work products
    :header-rows: 1

    * - work product Id
      - Process status
      - Link to WP
      - WP status

    * - :need:`wp__policies`
      - n/a (comes from outside the project)
      - `Eclipse Foundation Project Handbook: <https://www.eclipse.org/projects/handbook/>`_
      - RELEASED

    * - :need:`wp__qms_plan`
      - :ndf:`copy('status', need_id='wf__cr_mt_qlm_plan')`
      - :need:`doc__platform_quality_plan`
      - :ndf:`copy('status', need_id='doc__platform_quality_plan')`

    * - :need:`wp__issue_track_system`
      - :ndf:`copy('status', need_id='wf__platform_mr_im_platform_mgmt_plan')`
      - `Project issues <https://github.com/eclipse-score/score/issues>`_
      - established

    * - :need:`wp__platform_mgmt`
      - :ndf:`copy('status', need_id='wf__platform_cr_mt_platform_mgmt_plan')`
      - :doc:`index`
      - :ndf:`copy('status', need_id='doc__platform_mgt_plan')`

    * - :need:`wp__process_description`
      - :ndf:`copy('status', need_id='wf__def_app_process_description')`
      - `Process description <https://eclipse-score.github.io/process_description/main/index.html>`_
      - Maturity Level 1-2

    * - :need:`wp__process_impr_report`
      - :ndf:`copy('status', need_id='wf__mon_imp_process_description')`
      - `Process issues <https://github.com/eclipse-score/process_description/issues>`_
      - see issues

    * - :need:`wp__process_strategy`
      - :ndf:`copy('status', need_id='wf__cr_mt_process_mgt_strategy')`
      - `Process development community planning <https://github.com/orgs/eclipse-score/projects/21>`_
      - see planning board

    * - :need:`wp__platform_handbook`
      - :ndf:`copy('status', need_id='wf__rel_platform_handbook')`
      - :need:`doc__platform_handbook`
      - :ndf:`copy('status', need_id='doc__platform_handbook')`

    * - :need:`wp__platform_sw_release_note`
      - :ndf:`copy('status', need_id='wf__rel_platform_rel_note')`
      - `Release Note <https://eclipse-score.github.io/reference_integration/main>`_
      - see reference integration

    * - :need:`wp__verification_platform_ver_report`
      - :ndf:`copy('status', need_id='wf__verification_platform_ver_report')`
      - `Verification Report <https://eclipse-score.github.io/reference_integration/main>`_
      - see reference integration

    * - :need:`wp__requirements_stkh`
      - :ndf:`copy('status', need_id='wf__req_stkh_req')`
      - :need:`doc__stakeholder_requirements`
      - :ndf:`copy('status', need_id='doc__stakeholder_requirements')`

    * - :need:`wp__requirements_sw_platform_aou`
      - :ndf:`copy('status', need_id='wf__req_stkh_req')`
      - :need:`doc__platform_assumptions`
      - :ndf:`copy('status', need_id='doc__platform_assumptions')`

    * - :need:`wp__sw_development_plan`
      - :ndf:`copy('status', need_id='wf__sw_development_plan')`
      - :need:`doc__platform_software_development_plan`
      - :ndf:`copy('status', need_id='doc__platform_software_development_plan')`

    * - :need:`wp__verification_plan`
      - :ndf:`copy('status', need_id='wf__verification_plan')`
      - :need:`doc__platform_software_verification_plan`
      - :ndf:`copy('status', need_id='doc__platform_software_verification_plan')`

    * - :need:`wp__tool_verification_report`
      - :ndf:`copy('status', need_id='wf__tool_create_tool_verification_report')`
      - :need:`doc__tool_evaluation_list`
      - :ndf:`copy('status', need_id='doc__tool_evaluation_list')`


Functional Safety Specific SW Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

.. list-table:: SW Platform safety work products
    :header-rows: 1

    * - work product Id
      - Process status
      - Link to WP
      - WP status

    * - :need:`wp__platform_safety_plan`
      - :ndf:`copy('status', need_id='wf__cr_mt_safety_plan')`
      - this document
      - see above

    * - :need:`wp__platform_safety_package`
      - :ndf:`copy('status', need_id='wf__cr_mt_safety_package')`
      - this document
      - see above

    * - :need:`wp__fdr_reports` (platform Safety Plan)
      - :ndf:`copy('status', need_id='wf__p_formal_rv')`
      - :need:`doc__score_platform_safety_plan_fdr`
      - :ndf:`copy('status', need_id='doc__score_platform_safety_plan_fdr')`

    * - :need:`wp__fdr_reports` (platform Safety Package)
      - :ndf:`copy('status', need_id='wf__p_formal_rv')`
      - :need:`doc__score_platform_safety_package_fdr`
      - :ndf:`copy('status', need_id='doc__score_platform_safety_package_fdr')`

    * - :need:`wp__fdr_reports` (feature's Safety Analyses & DFA)
      - :ndf:`copy('status', need_id='wf__p_formal_rv')`
      - :need:`doc__score_platform_safety_analysis_fdr`
      - :ndf:`copy('status', need_id='doc__score_platform_safety_analysis_fdr')`

    * - :need:`wp__audit_report`
      - performed by external experts
      - `Audit findings <https://github.com/eclipse-score/process_description/issues/518>`_
      - intermediate

    * - :need:`wp__platform_dfa`
      - :ndf:`copy('status', need_id='wf__analyse_platform_featarch')`
      - :need:`doc__score_platform_dfa`
      - :ndf:`copy('status', need_id='doc__score_platform_dfa')`

    * - :need:`wp__platform_safety_manual`
      - :ndf:`copy('status', need_id='wf__cr_mt_safety_manual')`
      - :need:`doc__score_platform_safety_manual`
      - :ndf:`copy('status', need_id='doc__score_platform_safety_manual')`

    * - :need:`wp__safety_tailoring` (generic)
      - :ndf:`copy('status', need_id='wf__def_app_process_description')`
      - :need:`wp__tailoring_work_products` & :need:`doc__platform_safety_management_plan`
      - :ndf:`copy('status', need_id='wp__tailoring_work_products')`

The **Process Status** represents the status of the workflow responsible for
producing or maintaining the corresponding work product. It is derived from the
status of the process documentation and guidance associated with that workflow.

Platform-level safety work for the applicable release is planned and tracked
through the corresponding project planning issue.

Feature and Module Safety Planning
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Safety-related work products for individual Features and Modules are defined by
their respective safety planning.

The currently available safety planning includes:

* `Baselibs Safety Planning <https://eclipse-score.github.io/baselibs/main/features/safety_planning/index.html>`_
* :need:`doc__com_ipc_safety_wp`
* `Lifecycle Safety Planning <https://eclipse-score.github.io/lifecycle/main/features/lifecycle/safety_planning/index.html>`_
* `Logging Safety Planning <https://eclipse-score.github.io/logging/main/features/logging/safety_planning/index.html>`_
  for Freedom from Interference (FFI) capability
* `Persistency Safety Planning <https://eclipse-score.github.io/persistency/main/features/persistency/safety_planning/index.html>`_

The planned Feature scope is defined by :ref:`releases`.

A Feature that is part of the planned release scope but is not represented by
applicable safety planning shall not be considered safety-planned.

.. note::

   Freedom from Interference (FFI) means in this context that the functionality
   of the respective Feature may itself be developed as QM, while the interfaces
   and resources provided by the Feature are designed and constrained such that
   their use by an ASIL component does not adversely affect the safety-related
   behavior of that component.



Platform Management Plan - Documents Status Chart
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See :ref:`doc_platform_management_plan`.


Deviations from the Platform Safety Plan
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Deviations from the approved Platform Safety Plan shall be identified,
documented, assessed, and dispositioned as part of the Platform Safety Package.

A deviation may relate to:

* a planned safety activity that was not performed or was performed differently
  from the approved plan;
* a required work product that is incomplete or deviates from its defined
  quality criteria;
* a planned verification or review activity that could not be completed;
* a change in assumptions, dependencies, or scope affecting the Safety Plan; or
* another deviation from the planned functional safety lifecycle.

For each deviation, the following information shall be documented:

* description of the deviation;
* affected activity, requirement, or work product;
* impact on functional safety;
* applicable mitigation or rationale;
* responsible role;
* planned resolution, where required; and
* status of the deviation.

Software defects and safety anomalies are not treated as Safety Plan deviations
unless they also represent a deviation from the planned safety activities or
processes. They shall be tracked through the applicable problem-resolution
process and reported in the corresponding release documentation where required.
