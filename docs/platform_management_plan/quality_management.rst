..
   # *******************************************************************************
   # Copyright (c) 2024 Contributors to the Eclipse Foundation
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


.. document:: PF Quality Management Plan
   :id: doc__platform_quality_plan
   :status: valid
   :version: 3
   :safety: ASIL_B
   :security: YES
   :realizes: wp__qms_plan[version==1]
   :tags: platform_management_plan

PF QualityManagement Plan
=========================

Purpose
-------

The purpose of the Quality Management Plan is to define the quality management
strategy and quality assurance framework for the S-CORE platform.

The plan defines how the project provides independent and objective assurance
that:

* project processes are established and applied as defined;
* work products comply with the applicable requirements, processes, plans,
  templates, and guidelines;
* deviations and non-conformances are identified and recorded;
* identified non-conformances are resolved and their closure is verified;
* recurring quality issues are analyzed and appropriate preventive actions are
  initiated; and
* evidence of quality assurance activities is maintained.

The plan defines the applicable quality objectives, quality assurance activities,
responsibilities, cadence, reporting, and escalation mechanisms.

Quality assurance is implemented through a combination of:

* automated checks integrated into development and integration workflows;
* repository and workflow restrictions that prevent non-conforming changes;
* independent reviews and manual quality checks;
* process conformance checks and audits; and
* verification that required quality controls have been performed and have not
  been bypassed or manipulated.


Statement of Independence
-------------------------

The :need:`rl__quality_manager` provides independent quality assurance for the
S-CORE project and advises the project on quality-related improvements.

The :need:`rl__quality_manager` shall be sufficiently independent from the
development activities and delivery decisions being assessed to provide an
objective evaluation of process and work-product conformity.

The quality status and identified non-conformances are documented in the
:need:`wp__qms_report`. The quality report is reviewed and approved by the
:need:`rl__project_lead`.

.. image:: _assets/score_project_organisation.drawio.svg
   :width: 900
   :alt: Project Organization
   :align: center

S-CORE is developed collaboratively by participants representing different
organizations and stakeholder groups. Cross-organizational review provides an
additional level of independent scrutiny because contributions and their
associated work products may be reviewed by participants who were not involved
in their creation.

This collaborative review complements, but does not replace, the formally
defined quality assurance responsibilities and independence of the
:need:`rl__quality_manager`.

     - Process monitoring and improvement
     - Continuously

Additional quality assurance activities may be initiated based on identified
risks, non-conformances, audit findings, process changes, or quality trends.


Quantitative Quality Goals
~~~~~~~~~~~~~~~~~~~~~~~~~~

The following quantitative goals are used to evaluate the effectiveness and
completion of the defined quality assurance activities:

.. list-table:: Quantitative Quality Goals
   :header-rows: 1

   * - #
     - **Quality Criterion**
     - **Target**
     - **Allowed Variation**
     - **Evidence**
   * - 1
     - Platform process audit
     - 100% of required platform process audits are completed for every release
     - A delta audit may be used to complete the required audit scope
     - :need:`wf__exe_pltprocess_audit`
   * - 2
     - Feature process conformance
     - 100% of stable feature releases have a completed process conformance check
     - A feature without the required conformance evidence may only be released
       with the status ``experimental``
     - :need:`wp__qms_report`
   * - 3
     - Quality assurance of platform work products
     - 100% of work products required for a stable release satisfy their
       applicable quality criteria
     - Non-conforming work products shall not be part of a stable release
     - :need:`wp__verification_platform_ver_report`
   * - 4
     - Quality assurance of platform releases
     - 100% of stable platform releases have completed quality assurance,
       verification, and approval
     - None for stable releases
     - :need:`wp__platform_sw_release_note`,
       :need:`wf__vy_ap_modrelease`, and
       :need:`wf__vy_ap_pltrelease`
   * - 5
     - Qualification of :need:`rl__committer`
     - 100% of Committers fulfill the training and qualification criteria
       defined for the role
     - None
     - :need:`wp__training_path`
   * - 6
     - Closure of quality non-conformances
     - 100% of quality non-conformances affecting a release are resolved,
       accepted, or otherwise dispositioned before release approval
     - Open findings require an explicitly documented disposition
     - :need:`wp__issue_track_system`

The stakeholder requirements providing the basis for these objectives are
defined in :need:`stkh_req__dependability__automotive_safety` and
:doc:`../requirements/stakeholder/index`.



* required work products are available;
* required content is complete and valid;
* applicable templates, checklists, and guidelines are used;
* plans and other maintained documents reflect the current project status;
* required reviews and approvals are completed;
* identified findings are resolved or explicitly dispositioned;
* work products are traceable according to the applicable process; and
* required verification evidence is available.

Where applicable, these criteria shall be enforced through automated checks and
repository controls.

The target for mandatory work-product quality criteria is **100% compliance**
before inclusion in a stable baseline.

A deviation from a mandatory criterion shall be explicitly identified,
documented, assessed, and dispositioned according to the applicable process.
A deviation shall therefore not be implicitly treated as successful quality
assurance.

Training material and training evidence shall be maintained through
:need:`wp__training_path`.

Quality-related findings and improvement actions shall be managed through the
applicable issue tracking mechanism.


Quality Management Scope
~~~~~~~~~~~~~~~~~~~~~~~~

The Quality Management Plan applies to the project scope defined in
:need:`doc__project_mgt_plan`.

The S-CORE platform and its components are developed and integrated for an
assumed technical system. For functional-safety-related development, applicable
elements are developed according to the defined Safety Element out of Context
(SEooC) assumptions.

Platform development shall follow the defined S-CORE processes. Responsibilities
for management, development, implementation, integration, verification, safety,
security, and quality assurance are assigned through the applicable process
roles.

The platform consists of Features and Modules that may be developed in parallel.
Quality assurance shall therefore cover both:

* project-wide processes and work products; and
* Feature- and Module-specific application of the processes.


Tailoring of Quality Assurance Activities
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Quality-related tailoring is divided into:

* project-wide tailoring; and
* Feature- or Module-specific tailoring.

Project-wide Automotive SPICE tailoring is documented in the
`S-CORE Automotive SPICE 4.0 mapping
<https://eclipse-score.github.io/process_description/main/standards/aspice_40/aspice.html>`_.

Feature- or Module-specific tailoring shall be documented where the standard
project processes or work products are not fully applicable.

Tailoring shall not silently remove applicable quality requirements. Any
deviation from a mandatory project requirement shall be justified, documented,
and approved according to the applicable process.

The :need:`rl__quality_manager`, supported by the :need:`rl__project_lead` and
the responsible project stakeholders, ensures that quality assurance activities
are planned and performed throughout the project lifecycle.

Required quality activities, resources, dependencies, and milestones shall be
represented in the project planning infrastructure according to
:need:`doc__project_mgt_plan`.


Tools and Infrastructure
~~~~~~~~~~~~~~~~~~~~~~~~

GitHub provides the primary infrastructure for development, planning, review,
integration, and storage of project work products.

Quality controls shall be automated where technically and economically
appropriate.

The following mechanisms are used:

* GitHub Issues for planning and tracking quality activities and findings;
* GitHub Pull Requests for review and approval of changes;
* repository rules and branch protection for enforcing required controls;
* CI workflows for automated verification;
* issue relationships for tracking findings and corrective actions; and
* quality-related labels and project views for reporting and monitoring.

Quality-related issues shall use the applicable project classification,
including the ``quality`` label where defined.


Quality Management Communication
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Quality-relevant information shall be communicated through the standard S-CORE
project communication mechanisms defined in :need:`doc__project_mgt_plan`.

Depending on the purpose and required evidence, communication may include:

* regular project and team meetings;
* GitHub Issues and Pull Requests;
* Slack or other project communication channels;
* email; and
* dedicated quality meetings.

Ad-hoc quality meetings may be initiated where findings, risks, or
non-conformances require immediate coordination.


Quality Reporting
~~~~~~~~~~~~~~~~~

The project-level quality status is documented in
:need:`wp__qms_report`.

The quality report shall provide sufficient information to determine, as
applicable:

* the status of planned quality activities;
* the status and outcome of audits and conformance checks;
* identified non-conformances;
* unresolved quality findings;
* corrective and preventive actions;
* release-relevant quality risks; and
* the overall quality status relevant to the upcoming release.

Quality reporting shall provide input to project monitoring and release
readiness decisions.

Escalation
~~~~~~~~~~

Quality issues shall be resolved at the lowest organizational level capable of
providing an effective resolution.

Where an issue cannot be resolved, or where the required independence would be
compromised, it shall be escalated according to the following path:

.. code-block:: text

   Feature Team / Responsible Contributor
                 |
                 v
          Quality Manager
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

Escalation to the Eclipse Foundation is applicable where the issue concerns
Eclipse Foundation governance, policies, or obligations that cannot be resolved
within the S-CORE project governance structure.

Examples of conditions requiring escalation include:

* disagreement between :need:`rl__quality_manager` and
  :need:`rl__committer` regarding the disposition of a quality finding;
* a quality issue that cannot be resolved within the responsible Feature Team;
* insufficient resources to perform a mandatory quality assurance activity;
* unresolved disagreement between :need:`rl__project_lead`,
  :need:`rl__safety_manager`, :need:`rl__security_manager`, and
  :need:`rl__quality_manager`;
* repeated or systematic process non-conformance;
* attempts to bypass or manipulate defined quality controls; and
* unresolved quality findings that may affect release readiness.

Significant escalations and their disposition shall be documented in the
applicable project records.


Quality Management Specifics
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

No additional project-specific quality management provisions are currently
defined beyond those described in this plan and the referenced processes.


Quality-Relevant Work Products
------------------------------

The quality-related work products defined in this section apply to the platform
independently of the safety or security classification of individual Features
or Modules.

Additional safety- and security-specific work products are defined in:

* :doc:`safety_management`;
* :doc:`security_management`;
* :need:`gd_temp__module_safety_plan`; and
* :need:`gd_temp__module_security_plan`.


Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~

Platform-level quality work products are created and maintained once at platform
level unless the responsible process defines a different lifecycle or cadence.

They provide the project-level evidence required to:

* plan quality assurance activities;
* demonstrate process conformance;
* record audit and assessment results;
* monitor quality status;
* track non-conformances and corrective actions; and
* support release readiness and approval.

.. list-table:: Quality relevant platform work products
        :header-rows: 1

        * - Workproduct Id
          - Link to WP

        * - :need:`wp__policies`
          - `Eclipse Foundation Project Handbook <https://www.eclipse.org/projects/handbook/>`_

        * - :need:`wp__platform_mgmt`
          - :ref:`project_documents_list`

        * - :need:`wp__project_mgt`
          - :ref:`project_documents_list`

        * - :need:`wp__qms_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__qms_report`
          - :ref:`project_documents_list`

        * - :need:`wp__process_impr_report`
          - :ref:`project_documents_list`

        * - :need:`wp__training_path`
          - :ref:`project_documents_list`

        * - :need:`wp__process_strategy`
          - :need:`wp__process_strategy`

        * - :need:`wp__process_description`
          - :need:`wp__process_description`

        * - :need:`wp__requirements_proc_tool`
          - :need:`wp__process_description`

        * - :need:`wp__tailoring_work_products`
          - :ref:`project_documents_list`

        * - :need:`wp__chm_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__config_mgt_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__document_mgt_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__prm_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__tlm_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__tool_verification_report`
          - :ref:`project_documents_list`

        * - :need:`wp__sw_development_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__verification_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__issue_track_system`
          - :ref:`project_documents_list`

        * - :need:`wp__platform_handbook`
          - :ref:`project_documents_list`

        * - :need:`wp__platform_sw_release_plan`
          - :ref:`project_documents_list`

        * - :need:`wp__platform_sw_release_note`
          - :ref:`project_documents_list`

        * - :need:`wp__requirements_stkh`
          - :ref:`project_documents_list`

        * - :need:`wp__platform_arch`
          - :ref:`project_documents_list`

        * - :need:`wp__verification_platform_int_test`
          - :ref:`project_documents_list`

        * - :need:`wp__verification_platform_ver_report`
          - :ref:`project_documents_list`

        * - :need:`wp__sw_platform_sbom`
          - :ref:`project_documents_list`

Feature Work Products
^^^^^^^^^^^^^^^^^^^^^
Needed for each feature.

.. list-table:: Quality relevant feature work products
        :header-rows: 1

        * - Workproduct Id
          - Link to WP

        * - :need:`wp__feat_request`
          - :ref:`documents_docs_features`

        * - :need:`wp__requirements_feat`
          - :ref:`documents_docs_features`

        * - :need:`wp__requirements_inspect`
          - :ref:`documents_docs_features`

        * - :need:`wp__feature_arch`
          - :ref:`documents_docs_features`

        * - :need:`wp__verification_feat_int_test`
          - :ref:`documents_docs_features`

Module Work Products
^^^^^^^^^^^^^^^^^^^^
Needed for each module.

.. list-table:: Quality relevant module work products
        :header-rows: 1

        * - Workproduct Id
          - Link to WP

        * - :need:`wp__module_sw_release_plan`
          - :ref:`documents_docs_modules`

        * - :need:`wp__module_sw_release_note`
          - :ref:`documents_docs_modules`

        * - :need:`wp__verification_module_ver_report`
          - :ref:`documents_docs_modules`

        * - :need:`wp__sw_module_sbom`
          - :ref:`documents_docs_modules`

Component Work Products
^^^^^^^^^^^^^^^^^^^^^^^
Needed for each component of a module.

.. list-table:: Quality relevant component work products
        :header-rows: 1

        * - Workproduct Id
          - Link to WP

        * - :need:`wp__cmpt_request`
          - :ref:`documents_docs_modules`

        * - :need:`wp__requirements_comp`
          - :ref:`documents_docs_modules`

        * - :need:`wp__requirements_inspect`
          - :ref:`documents_docs_modules`

        * - :need:`wp__component_arch`
          - :ref:`documents_docs_modules`

        * - :need:`wp__sw_arch_verification`
          - :ref:`documents_docs_modules`

        * - :need:`wp__sw_implementation`
          - :ref:`documents_docs_modules`

        * - :need:`wp__sw_implementation_inspection`
          - :ref:`documents_docs_modules`

        * - :need:`wp__verification_sw_unit_test`
          - :ref:`documents_docs_modules`

        * - :need:`wp__verification_comp_int_test`
          - :ref:`documents_docs_modules`

        * - :need:`wp__sw_component_class`
          - :ref:`documents_docs_modules`
