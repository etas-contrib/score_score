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

.. document:: PF Security Management Plan
   :id: doc__platform_security_management_plan
   :status: draft
   :version: 1
   :safety: ASIL_B
   :security: YES
   :realizes: wp__platform_security_plan[version==1], wp__tailoring_work_products[version==1]
   :tags: platform_management_plan

PF Security Management Plan
===========================

Purpose
-------

The purpose of the Security Management Plan is to define the cybersecurity
management framework for the S-CORE platform and to ensure that the applicable
requirements of ISO/SAE 21434 are addressed according to the defined scope and
tailoring.

In particular, this plan defines:

* the cybersecurity management roles, responsibilities, and authorities;
* the cybersecurity lifecycle applicable to the S-CORE platform;
* the required cybersecurity activities and work products;
* the project-wide tailoring of cybersecurity activities and the corresponding
  rationales;
* the planning, coordination, monitoring, and reporting of cybersecurity
  activities;
* the management of deviations from the Security Plan;
* the preparation and maintenance of the Security Package and its supporting
  evidence; and
* the activities required to evaluate cybersecurity process conformance.

Within S-CORE, the term *security* is used synonymously with *cybersecurity* as
defined by ISO/SAE 21434, unless explicitly stated otherwise.


Objectives and Scope
--------------------

Security Management Goals
~~~~~~~~~~~~~~~~~~~~~~~~~

The primary cybersecurity management objective is to establish and maintain
conformance with the applicable requirements of ISO/SAE 21434 within the
defined S-CORE scope and tailoring.

To achieve this objective, cybersecurity management shall:

* plan the required cybersecurity activities and work products;
* assign responsibilities for their execution, verification, and approval;
* coordinate and monitor execution of the planned cybersecurity activities;
* identify and manage deviations from the Security Plan;
* monitor completeness and maturity of the required cybersecurity work products;
* measure cybersecurity status using defined criteria and metrics;
* report cybersecurity status, risks, and unresolved issues; and
* provide the evidence required to support the Security Package and applicable
  cybersecurity assurance activities.


Security Management Scope
~~~~~~~~~~~~~~~~~~~~~~~~~

The cybersecurity management scope is aligned with the overall S-CORE project
scope.

The S-CORE platform and its components are developed and integrated for an
assumed technical system. The platform and its components are therefore
developed out of the context of a specific vehicle or target system.

Platform development follows the processes defined by S-CORE. Responsibilities
for management, requirements engineering, architecture, implementation,
integration, verification, and cybersecurity activities are assigned through
the applicable processes and role definitions.

S-CORE distinguishes between software with and without cybersecurity relevance.
Where cybersecurity relevance has been identified, the applicable
cybersecurity activities, controls, verification measures, and work products
shall be planned and performed according to the defined processes.

The software platform consists of Features that are defined by requirements and
may be developed in parallel. Features are implemented by software components
organized into Modules.

For cybersecurity-relevant Module development, Module-specific security
activities, assumptions, work products, and tailoring shall be defined in the
applicable Module Security Plan.

The template :need:`gd_temp__module_security_plan` shall be used for this
purpose.

Tailoring
~~~~~~~~~

ISO/SAE 21434 activities and work products are tailored according to the S-CORE
development scope and its out-of-context development approach.

Tailoring is defined at two levels:

* **Project-wide tailoring** applies to the S-CORE platform and is defined in
  this Security Management Plan.
* **Module-specific tailoring** applies to an individual Module and shall be
  documented and justified in the corresponding Module Security Plan.

Module-specific tailoring may result from characteristics of the Module, its
cybersecurity relevance, applicable assumptions, interfaces, or its intended
usage.

For changes to existing cybersecurity-relevant Features or Modules, an impact
analysis shall determine which existing security activities and work products
are affected and which activities need to be created, updated, or repeated.

The following ISO/SAE 21434 work products and activities are tailored out at
platform level. The rationale for each tailoring decision is documented below.


Organizational and Confidentiality-Related Work Products
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

S-CORE is developed as an Eclipse Foundation open-source project. Project
development artifacts are generally maintained according to the applicable
Eclipse Foundation governance and S-CORE development processes.

Confidential information, in particular information concerning non-disclosed
security vulnerabilities, is handled through the dedicated vulnerability
management and disclosure mechanisms rather than through public project
artifacts.

Where an ISO/SAE 21434 work product is not applicable because the corresponding
organizational responsibility is provided by the Eclipse Foundation governance
or another defined S-CORE process, this is documented as project-wide
tailoring.

The corresponding tailored work products include:

* :need:`std_wp__isosae21434__org_management_551`


System Integrator Responsibilities
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Cybersecurity activities that depend on the final vehicle, system architecture,
target environment, operational context, or integration are outside the S-CORE
platform development scope and remain the responsibility of the downstream
system integrator.

The corresponding tailored work products include:

* :need:`std_wp__isosae21434__org_management_555`
* :need:`std_wp__isosae21434__prj_management_653`
* :need:`std_wp__isosae21434__assessment_15331`
* :need:`std_wp__isosae21434__assessment_15332`
* :need:`std_wp__isosae21434__assessment_15431`
* :need:`std_wp__isosae21434__assessment_15531`

S-CORE shall provide the assumptions, constraints, interfaces, and available
security evidence required to support downstream integration where applicable.

The system integrator remains responsible for evaluating the applicability and
sufficiency of this information and evidence within the context of the target
system.


Tailoring Completeness
^^^^^^^^^^^^^^^^^^^^^^

:need:`wp__tailoring_work_products` identifies the work products that are
tailored out within the Platform Security Plan.

This provides traceability between the applicable ISO/SAE 21434 requirements,
the S-CORE development scope, and the documented tailoring decisions in
``REPLACE_external_standards``.


Approach
--------

Security Culture
~~~~~~~~~~~~~~~~

S-CORE promotes a cybersecurity culture in which contributors are encouraged
to identify risks, question assumptions, report potential security issues, and
take responsibility for the security and quality of their work.

The project supports this culture through:

* clearly defined roles and responsibilities;
* documented processes, guidelines, and templates;
* cybersecurity training appropriate to assigned responsibilities;
* open technical discussion and review where disclosure is appropriate;
* protected mechanisms for reporting potential vulnerabilities;
* independent review and verification where required;
* automated process, security, and work-product checks where appropriate; and
* continuous improvement based on findings, experience, vulnerabilities, and
  feedback.

Adherence to the defined processes is supported through automated checks,
repository controls, reviews, and manual inspections.

Cybersecurity activities are integrated into the development processes rather
than treated as separate activities. This ensures that cybersecurity is
considered throughout planning, requirements engineering, architecture,
implementation, integration, verification, release, and maintenance.

Potential vulnerabilities and other security information requiring controlled
disclosure shall be handled according to the applicable vulnerability
management process and shall not be disclosed through public project channels
until publication is permitted.

Security Management Organization
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cybersecurity management is integrated into the S-CORE project organization.

The project organization provides the roles, responsibilities, decision
mechanisms, and competence required to plan, execute, monitor, and assess
cybersecurity activities.

As an Eclipse Foundation project, S-CORE additionally operates within the
governance framework defined by the Eclipse Foundation Project Handbook.


Eclipse Roles
^^^^^^^^^^^^^

The Eclipse contribution model distinguishes between Contributors, Committers,
and the applicable Eclipse Foundation security functions.

* **Contributors** may propose changes to the project. Contributions affecting
  cybersecurity-relevant work products are subject to the same review,
  verification, and approval requirements as other security-relevant changes.
  Contributors cannot independently approve and merge their contributions.

* **Committers** may approve and integrate changes according to their repository
  permissions and the project's governance rules. Committers performing
  cybersecurity-relevant activities shall satisfy the competence requirements
  defined for their assigned responsibilities.

* The **Eclipse Foundation Security Team** provides the applicable Eclipse
  Foundation mechanisms and support for vulnerability reporting, coordination,
  and disclosure.

These Eclipse roles complement the security-specific roles defined by the S-CORE
process model.

Project Roles
^^^^^^^^^^^^^

Cybersecurity roles and their responsibilities are defined by the applicable
S-CORE processes and generic project role definitions.

The main project roles for cybersecurity management include:

* :need:`rl__project_lead`
* :need:`rl__security_manager`

Additional roles may have cybersecurity responsibilities as defined by the
applicable processes.

Security Resources
~~~~~~~~~~~~~~~~~~

One or more :need:`rl__security_manager` roles shall be assigned for
platform-level cybersecurity management.

For cybersecurity-relevant Module development, the responsible security
management role shall be identified in the corresponding Module Security Plan.

The :need:`rl__security_manager`, supported by the
:need:`rl__project_lead`, Feature Team Leads, and assigned security roles,
ensures that the required cybersecurity activities are planned, assigned,
monitored, and completed throughout the applicable cybersecurity lifecycle.

Required activities, resources, dependencies, and milestones shall be
represented in the project planning infrastructure according to
:doc:`project_management`.


Tools
^^^^^

GitHub provides the primary infrastructure for planning, development, review,
integration, and storage of project work products.

The following mechanisms support cybersecurity management:

* GitHub Issues for planning and tracking non-confidential security activities;
* GitHub Pull Requests for review and approval of changes;
* repository rules and ``CODEOWNERS`` for enforcing required reviews;
* CI workflows for automated verification and security-related checks; and
* GitHub Projects, milestones, and issue relationships for planning and
  monitoring cybersecurity-related work.

Security-related Issues shall use the applicable project classification,
including the ``security`` label where defined.

The applicable Issue Types and workflows are defined in
:doc:`project_management`.


Vulnerability Handling
^^^^^^^^^^^^^^^^^^^^^^

Potential vulnerabilities and other information requiring coordinated
disclosure shall not initially be recorded in public GitHub Issues or other
public project channels.

Initial vulnerability reporting shall follow the project's Security Policy and
the vulnerability management process defined in
:need:`doc__platform_vulnerability_mgt_plan`.

Reported vulnerabilities shall be handled through protected communication and
tracking mechanisms until the vulnerability has been triaged and its disclosure
status has been determined.

Information concerning a vulnerability may only be transferred to publicly
accessible project tracking once its disclosure status permits publication.

After disclosure, resulting remediation activities may be tracked through the
standard project planning infrastructure where appropriate.

The Eclipse Foundation vulnerability reporting infrastructure provides an
additional mechanism for reporting and coordinating security vulnerabilities.

Security Management Communication
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cybersecurity information is communicated through the standard project
communication mechanisms defined in :need:`doc__project_mgt_plan`.

Dedicated security coordination shall take place as required and at least
monthly while relevant cybersecurity activities are active.

Communication channels include:

* regular project and security coordination meetings;
* GitHub Issues and Pull Requests for non-confidential topics;
* applicable project messaging channels;
* email where appropriate; and
* protected communication mechanisms for confidential security and
  vulnerability information.

Ad-hoc security meetings shall be initiated where security findings,
vulnerabilities, risks, non-conformances, or implementation questions require
dedicated coordination.


Reporting
^^^^^^^^^

The :need:`rl__security_manager` regularly reports the cybersecurity status to
the applicable project steering body defined in
:need:`doc__project_mgt_plan`.

The cybersecurity status reporting shall consider, as applicable:

* completion status of planned cybersecurity activities;
* maturity and completeness of cybersecurity work products;
* verification status;
* open cybersecurity findings;
* vulnerability status at a level appropriate for the audience and current
  disclosure state;
* deviations from applicable Security Plans;
* cybersecurity-related risks and dependencies; and
* readiness for upcoming cybersecurity-related milestones or releases.

The status is derived from the applicable security plans and verification
evidence, including:

* :need:`wp__platform_security_plan`
* :need:`wp__module_security_plan`
* :need:`wp__verification_platform_ver_report`
* :need:`wp__verification_module_ver_report`

Confidential vulnerability information shall only be included in reporting where
the receiving audience is authorized to access the corresponding information.


Escalation
^^^^^^^^^^

Security issues shall be resolved at the lowest organizational level capable of
providing an appropriate resolution.

Where resolution cannot be achieved, the issue shall be escalated through the
project governance defined in :need:`doc__project_mgt_plan`.

The :need:`rl__security_manager` shall initiate or coordinate cybersecurity
escalations where applicable.

Escalation is required, for example, when:

* a cybersecurity issue cannot be resolved at Module or Feature Team level;
* required resources for mandatory cybersecurity activities are unavailable;
* a significant deviation from an approved Security Plan cannot be resolved;
* disagreement exists regarding the disposition of a cybersecurity finding;
* a required cybersecurity activity cannot be completed as planned;
* an unresolved cybersecurity issue may affect release readiness; or
* conflicting positions between :need:`rl__project_lead`,
  :need:`rl__safety_manager`, :need:`rl__security_manager`, and
  :need:`rl__quality_manager` cannot be resolved at the responsible level.

Issues concerning vulnerability disclosure or Eclipse Foundation security
policies shall additionally be escalated through the applicable Eclipse
Foundation security mechanisms.

Significant cybersecurity-related escalations and their disposition shall be
documented and traceable, subject to the applicable confidentiality
restrictions.

Security Management Lifecycle
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The S-CORE cybersecurity lifecycle starts with project-level security planning
and is maintained throughout development, integration, verification, release,
maintenance, and subsequent changes.

The :need:`rl__security_manager`, supported by the
:need:`rl__process_community` and the responsible project roles, coordinates the
applicable cybersecurity lifecycle activities.

S-CORE applies those ISO/SAE 21434 lifecycle activities that are applicable to
the development of the platform and its Modules within the defined
out-of-context development scope.

Activities outside the S-CORE development scope are addressed through the
documented tailoring and the corresponding assumptions, constraints, and
downstream integration responsibilities.

Project governance phases defined by the Eclipse Foundation and the S-CORE
cybersecurity lifecycle serve different purposes. Eclipse project maturity or
lifecycle status does not by itself demonstrate completion of the applicable
cybersecurity activities.

Cybersecurity readiness is determined based on:

* completion of the applicable cybersecurity activities;
* availability and maturity of the required cybersecurity work products;
* completion of the required verification and review activities;
* disposition of identified cybersecurity findings and deviations; and
* availability of the cybersecurity evidence required for the corresponding
  release or baseline.

Platform-level cybersecurity activities are planned through this Security
Management Plan and the Platform Security Plan. Module-specific cybersecurity
activities are planned through the corresponding Module Security Plans.

Changes to cybersecurity-relevant Features or Modules shall trigger an impact
analysis to determine which cybersecurity activities and work products need to
be created, updated, or repeated.

Cybersecurity management continues after release through vulnerability
monitoring, vulnerability management, analysis of reported security issues,
and the corresponding remediation and disclosure activities.


Security Requirements
~~~~~~~~~~~~~~~~~~~~~

Cybersecurity requirements engineering is performed according to the applicable
S-CORE requirements engineering processes defined in
:doc:`software_development`.

Applicable ISO/SAE 21434 requirements are mapped to the corresponding S-CORE
processes, guidance, activities, and work products.

The mapping provides traceability between the applicable standard requirements
and their implementation within the S-CORE development processes.

See ``REPLACE_processes_introduction`` for the applicable mapping.


Security Schedule
~~~~~~~~~~~~~~~~~

Platform-level cybersecurity activities and milestones are defined by the
Platform Security Plan below and tracked through the project planning
infrastructure.

Module-specific cybersecurity activities and milestones shall be defined and
tracked in the corresponding Module Security Plan using
:need:`gd_temp__module_security_plan`.

Changes affecting the planned cybersecurity scope or schedule shall be reflected
in the applicable Security Plan and project planning artifacts.


Security SW Development
~~~~~~~~~~~~~~~~~~~~~~~

Software development activities applicable to cybersecurity-relevant software
are defined in :doc:`software_development`.

Cybersecurity-specific activities and controls shall be integrated into the
applicable development activities according to the cybersecurity relevance of
the affected Feature or Module.


Security Verification
~~~~~~~~~~~~~~~~~~~~~

Verification of cybersecurity-relevant software and work products is performed
according to :doc:`software_verification`.

The applicable verification activities shall be planned based on the
cybersecurity requirements, identified cybersecurity risks, and defined
verification criteria.

Verification results provide evidence for the applicable Module Security
Package and Platform Security Package.


Security Tool Management
~~~~~~~~~~~~~~~~~~~~~~~~

Tools used for cybersecurity-related development and verification activities
are managed according to :doc:`tool_management`.

Where the use or malfunction of a tool may affect cybersecurity-related work
products or evidence, the applicable tool-management activities shall be
performed according to the defined process.


Security Work Products
~~~~~~~~~~~~~~~~~~~~~~

Project-wide cybersecurity work products are defined by this Security Management
Plan, the Platform Security Plan, and the applicable S-CORE processes.

Module-specific cybersecurity work products shall be identified and planned in
the corresponding Module Security Plan using
:need:`gd_temp__module_security_plan`.

The status and maturity of the required cybersecurity work products shall be
monitored as part of cybersecurity management and considered when determining
release readiness.


Security Quality Criteria
~~~~~~~~~~~~~~~~~~~~~~~~~

Quality management and the general quality criteria applicable to
cybersecurity-related work products are defined in
:doc:`quality_management`.

Cybersecurity work products shall additionally satisfy the cybersecurity-specific
criteria defined by the process responsible for their creation, verification,
review, and approval.

A cybersecurity-relevant work product that does not satisfy its mandatory
quality criteria shall not be considered complete without an explicitly
documented and approved deviation.

Platform Security Plan
----------------------

The Platform Security Plan defines and tracks the project-wide cybersecurity
activities and work products required for the planned S-CORE platform release.

The Platform Security Plan provides the basis for:

* planning the required cybersecurity activities;
* assigning responsibilities for their execution and verification;
* planning the required cybersecurity work products;
* tracking cybersecurity activities and work-product maturity;
* identifying dependencies and deviations; and
* determining the cybersecurity-related readiness of the planned platform
  release.

Module-specific cybersecurity activities and work products are defined in the
applicable Module Security Plans.


Functional Safety/Security Management SW Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

See :ref:`sw_platform_wp_list`.


Security Specific SW Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following work products provide the project-wide cybersecurity planning,
assurance, and release evidence for the S-CORE platform.

.. list-table:: SW Platform security work products
   :header-rows: 1

   * - Work Product ID
     - Process Status
     - Link to WP
     - WP Status

   * - :need:`wp__platform_security_plan`
     - :ndf:`copy('status', need_id='wf__cr_mt_security_plan')`
     - this document
     - see above

   * - :need:`wp__platform_security_package`
     - :ndf:`copy('status', need_id='wf__cr_mt_security_package')`
     - <Link to WP>
     - <automated>

   * - :need:`wp__fdr_reports_security` (Platform Security Plan)
     - :ndf:`copy('status', need_id='wf__p_formal_security_rv')`
     - <Link to WP>
     - <automated>

   * - :need:`wp__fdr_reports_security` (Platform Security Package)
     - :ndf:`copy('status', need_id='wf__p_formal_security_rv')`
     - <Link to WP>
     - <automated>

   * - :need:`wp__fdr_reports_security` (Feature Security Analyses)
     - <Process Status>
     - <Link to WP>
     - <automated>

   * - :need:`wp__audit_report_security`
     - performed by external experts
     - n/a
     - currently tailored out

   * - :need:`wp__platform_security_manual`
     - :ndf:`copy('status', need_id='wf__cr_mt_security_manual')`
     - <Link to WP>
     - <automated>

   * - :need:`wp__tailoring_work_products` (generic)
     - :ndf:`copy('status', need_id='wf__def_app_process_description')`
     - :need:`doc__platform_security_plan`
     - :ndf:`copy('status', need_id='doc__platform_security_plan')`

   * - :need:`wp__sw_platform_sbom`
     - :ndf:`copy('status', need_id='wf__cr_mt_security_sbom')`
     - <Link to WP>
     - <automated>


The **Process Status** represents the status of the workflow responsible for
producing or maintaining the corresponding work product. It is derived from the
status of the process documentation and guidance associated with that workflow.


Security Management Feature Specific Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Feature- and Module-specific cybersecurity work products are defined by the
applicable security planning documents.

The corresponding documents are created using
``doc__feature_example_security_planning_wp`` provided by the Module Template.

<Link to security planning document for every applicable Feature or Module>


Security Work Products Status Charts
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The following table provides the status of the applicable platform management
documents.

.. needtable::
   :style: table
   :columns: title;id;status;realizes
   :colwidths: 25,25,25,25
   :sort: title

   results = []

   for need in needs.filter_types(["document"]):
       if need and "platform_management" in need["tags"]:
           results.append(need)


Platform Security Package
-------------------------

The Platform Security Package consolidates the cybersecurity evidence resulting
from execution of the Platform Security Plan for a defined platform baseline.

The Platform Security Package shall provide sufficient evidence to determine:

* completion of the planned cybersecurity activities;
* availability and maturity of the required cybersecurity work products;
* completion and results of the required cybersecurity verification activities;
* status and disposition of identified cybersecurity findings;
* status of known vulnerabilities relevant to the baseline, subject to the
  applicable confidentiality and disclosure restrictions;
* deviations from the Platform Security Plan and their disposition;
* applicable cybersecurity assumptions and integration constraints; and
* the overall cybersecurity status of the platform baseline.

The Platform Security Package provides evidence for a defined platform baseline.
It does not replace the continuous vulnerability management activities defined
in :need:`doc__platform_vulnerability_mgt_plan`.

Cybersecurity findings discovered after creation of a Platform Security Package
shall be handled according to the applicable vulnerability and change management
processes and shall trigger an impact analysis where they may affect an existing
cybersecurity assessment, assumption, work product, or released baseline.


Deviations from the Platform Security Plan
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Deviations from the approved Platform Security Plan shall be identified,
documented, assessed, and dispositioned as part of the Platform Security
Package.

A deviation may relate to:

* a planned cybersecurity activity that was not performed or was performed
  differently from the approved plan;
* a required cybersecurity work product that is incomplete or does not satisfy
  its defined quality criteria;
* a planned verification or review activity that could not be completed;
* a change in assumptions, dependencies, or scope affecting the Security Plan;
  or
* another deviation from the planned cybersecurity lifecycle.

For each deviation, the following information shall be documented:

* description of the deviation;
* affected activity, requirement, or work product;
* potential cybersecurity impact;
* applicable mitigation or rationale;
* responsible role;
* planned resolution, where required; and
* status of the deviation.

Security weaknesses and vulnerabilities are not considered deviations from the
Security Plan solely because they exist.

They shall be managed according to
:need:`doc__platform_vulnerability_mgt_plan`.

A weakness or vulnerability shall additionally be treated as a Security Plan
deviation where it demonstrates that a planned cybersecurity activity, required
control, verification activity, or process was not performed or was not
effective as planned.


Security Release Readiness
~~~~~~~~~~~~~~~~~~~~~~~~~~

A platform release shall only be considered ready from a cybersecurity
management perspective when:

* all mandatory cybersecurity activities planned for the release are completed;
* the required cybersecurity work products are available at the required
  maturity;
* required verification and review activities are completed;
* identified deviations have been assessed and dispositioned;
* known cybersecurity findings relevant to the release have been assessed;
* known vulnerabilities relevant to the release have been dispositioned
  according to the applicable vulnerability management process;
* applicable cybersecurity assumptions, constraints, and integration
  responsibilities are documented and available to downstream integrators;
* the applicable Software Bill of Materials
  (:need:`wp__sw_platform_sbom`) is available; and
* the resulting cybersecurity evidence is consolidated in the Platform Security
  Package.

Open cybersecurity findings do not automatically prevent a release. However,
each open release-relevant finding shall have a documented cybersecurity impact
assessment, disposition, and responsible role before release.

Confidential vulnerability information shall not be exposed through public
release documentation unless its disclosure has been authorized according to
the applicable vulnerability management process.


Post-Release Cybersecurity Management
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Cybersecurity management continues after release.

Reported vulnerabilities, newly identified weaknesses, changes in the threat
landscape, and relevant changes to dependencies shall be evaluated for their
potential impact on supported S-CORE releases.

Where an identified issue may affect the cybersecurity properties of an
existing release, an impact analysis shall determine the required actions.

Depending on the result, these actions may include:

* remediation of the affected software or work product;
* update of cybersecurity requirements or analyses;
* update of assumptions or integration constraints;
* update of the Platform Security Package;
* creation of a corrective or security release; and
* coordinated vulnerability disclosure according to
  :need:`doc__platform_vulnerability_mgt_plan`.

Relevant findings shall provide input to subsequent cybersecurity planning and
continuous improvement activities.
