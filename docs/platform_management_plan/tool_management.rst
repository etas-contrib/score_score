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

.. document:: PF Tool Management Plan
   :id: doc__platform_tool_management_plan
   :status: valid
   :version: 2
   :safety: ASIL_B
   :security: YES
   :tags: platform_management
   :realizes: wp__tlm_plan[version==1]

PF Tool Management Plan
=======================

This document implements the applicable parts of :need:`wp__platform_mgmt`.


Purpose
-------

The Tool Management Plan defines how software tools used within S-CORE are
identified, evaluated, and, where required, qualified and approved for their
intended use.

S-CORE uses software tools to support and automate the generation,
transformation, verification, and management of work products. Tools whose
malfunction or misuse may affect the correctness, integrity, safety, or security
of these work products shall therefore be identified, documented, and evaluated.

Where required by the evaluation result, additional qualification measures
shall be performed before the tool is approved for its intended use.


Objectives and Scope
--------------------

Tool Management Goals
~~~~~~~~~~~~~~~~~~~~~

The objectives of Tool Management are to ensure that:

* tools within the scope of Tool Management are uniquely identified and
  documented;
* each tool is evaluated with respect to its intended use and configuration;
* potential tool malfunctions and relevant security threats are assessed;
* tools are qualified where required by the evaluation result;
* required verification and qualification evidence is documented;
* Tool Verification Reports are reviewed and approved; and
* approved tool versions and configurations are controlled according to the
  Configuration Management Plan.
  
Approach
--------

Tool Management consists of four principal stages:

#. **Identification**
#. **Evaluation**
#. **Qualification**, where required
#. **Approval**

The following figure provides an overview of the Tool Management process.

.. figure:: _assets/score_tool_management_overview.drawio.svg
   :width: 100%
   :align: center
   :alt: Tool Management Overview

   Tool Management Overview


Tool Management Attributes
~~~~~~~~~~~~~~~~~~~~~~~~~~

The Tool Management requirements beginning with
:need:`gd_req__tool_attr_uid` are implemented through the information and
activities described in the following sections.


Identification
~~~~~~~~~~~~~~

Each tool shall be uniquely identified by its tool name or UID together with
the applicable version.

Where the tool behavior relevant to its intended use depends on configuration,
the applicable configuration shall also be identified.

Tool identification is independent of where the tool is developed, hosted, or
maintained.

The main S-CORE tooling is maintained in the
`S-CORE tooling repository <https://GitHub.com/eclipse-score/tooling/>`_.
Tools may also be developed, hosted, or maintained in other repositories or
external locations.

For each tool, :need:`gd_temp__tool_management_verif_rpt_template` shall be used
to document the information required for Tool Management.

:need:`gd_chklst__tool_cr_review` shall be used to verify that the required
information has been considered.

Tool versions and applicable tool configurations are managed according to
:need:`doc__platform_config_mgt_plan`.

The output of the Identification stage is a
:need:`wp__tool_verification_report` with status ``identified``.  

Evaluation
~~~~~~~~~~

The Tool Confidence Level (TCL) shall be determined according to
:need:`doc_concept__tool_process` for the identified intended use of the tool.

The evaluation consists of the following steps:

#. Determine the Tool Impact.
#. Determine the Tool Error Detection.
#. Determine the Tool Confidence Level.

.. figure:: _assets/score_tool_management_evaluation.drawio.svg
   :width: 100%
   :align: center
   :alt: Tool Evaluation

   Tool Evaluation


Step 1: Determine the Tool Impact
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Potential tool malfunctions and relevant security threats shall be identified
with respect to the intended use of the tool.

The analysis shall determine whether such a malfunction or threat could lead to
the violation of an applicable safety or security requirement or could prevent
the detection of such a violation.

If such an impact is possible, Tool Impact shall be set to ``YES``.

Otherwise, Tool Impact shall be set to ``NO``.

If Tool Impact is ``NO``, continue with Step 3.

If Tool Impact is ``YES``, continue with Step 2.

Step 2: Determine the Tool Error Detection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For each relevant tool malfunction or security threat, the available measures
for preventing or detecting the resulting erroneous tool behavior or output
shall be assessed.

The assessment may consider existing or additional safety measures, independent
verification measures, plausibility checks, review activities, security
controls, or other mechanisms that prevent or reliably detect the identified
malfunction or threat.

If the relevant malfunction or threat cannot be reliably prevented or detected,
Tool Error Detection shall be set to ``NO``.

Otherwise, Tool Error Detection shall be set to ``YES``.


Step 3: Determine the Tool Confidence Level
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Tool Confidence Level shall be determined from Tool Impact and Tool Error
Detection.

If Tool Impact is ``YES`` and Tool Error Detection is ``NO``, the Tool
Confidence Level shall be set to ``LOW``.

In all other cases, the Tool Confidence Level shall be set to ``HIGH``.

A Tool Confidence Level of ``LOW`` requires Tool Qualification.

The evaluation result, including the rationale for the determined Tool Impact,
Tool Error Detection, and Tool Confidence Level, shall be documented in the
Tool Verification Report.

The output of the Evaluation stage is a
:need:`wp__tool_verification_report` with status ``evaluated``.

Qualification
~~~~~~~~~~~~~

Where Tool Qualification is required, the method **validation of the software
tool** is applied.

Qualification shall be performed for the identified tool version,
configuration, and intended use.

The qualification shall:

* define requirements for the intended purpose and use of the tool within
  S-CORE;
* analyze relevant tool malfunctions and security threats;
* define additional safety measures, security controls, or independent
  verification measures where required;
* define verification measures and test cases for the applicable tool
  requirements;
* execute the required verification and tests;
* document the verification and test results;
* document any assumptions, constraints, or limitations applicable to the
  qualified use of the tool; and
* update the Tool Verification Report with the qualification results.

The applicable S-CORE processes shall be used for requirements engineering,
verification, testing, and analysis.

In particular:

* use :need:`wf__req_comp_req` to define requirements for the software tool and
  :need:`wf__monitor_verify_requirements` to verify the requirements;

* use :need:`wf__verification_comp_int_test` to define and execute tests for the
  software tool and :need:`wf__verification_mod_ver_report` to document the
  verification results; and

* where applicable, use the corresponding Safety and Security Analysis
  workflows.

The output of the Qualification stage is a
:need:`wp__tool_verification_report` with status ``qualified``.

Approval
~~~~~~~~

Following evaluation and, where required, qualification, the tool shall undergo
final review and approval for its identified version, configuration, and
intended use within S-CORE.

The final review shall confirm, as applicable, that:

* the tool and its applicable version and configuration are uniquely
  identified;
* the intended use is documented;
* the Tool Impact, Tool Error Detection, and Tool Confidence Level have been
  determined and justified;
* required qualification activities have been completed successfully;
* applicable assumptions, constraints, and limitations are documented;
* required verification evidence is available; and
* the applicable Tool Verification Report has been reviewed.

If the tool is approved for its intended use, the
:need:`wp__tool_verification_report` shall be set to status ``released``.

If the tool is not approved for its intended use, the
:need:`wp__tool_verification_report` shall be set to status ``rejected``.

Approval applies only to the documented version, configuration, and intended
use. A change that may affect the evaluation or qualification result shall
trigger an assessment of whether re-evaluation or re-qualification is required.

Tailoring
~~~~~~~~~

The following tailoring applies to safety activities for establishing
confidence in the use of software tools within S-CORE.

The following ISO 26262 requirements are not applicable to S-CORE software
platform development because the corresponding qualification methods are not
used:

:need:`std_req__iso26262__support_11471`,
:need:`std_req__iso26262__support_11472`,
:need:`std_req__iso26262__support_11473`,
:need:`std_req__iso26262__support_11474`,
:need:`std_req__iso26262__support_11481`,
:need:`std_req__iso26262__support_11482`,
:need:`std_req__iso26262__support_11483`,
:need:`std_req__iso26262__management_6456`.

The applicable qualification approach is the **validation of the software
tool**, as defined in the Qualification section of this plan.


Tool List
~~~~~~~~~

The overview of tools managed within S-CORE is provided in :ref:`tools`.

For each tool within the scope of Tool Management, the tool list shall enable
identification of the applicable Tool Verification Report and its current
status.



