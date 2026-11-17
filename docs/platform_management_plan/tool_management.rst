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

.. document:: PF Tool Management Plan
   :id: doc__platform_tool_management_plan
   :status: valid
   :version: 2
   :safety: ASIL_B
   :security: YES
   :tags: platform_management_plan
   :realizes: wp__tlm_plan[version==1]


PF Tool Management Plan
=======================

This document implements parts of :need:`wp__platform_mgmt`.


Purpose
-------

The purpose of the Tool Management Plan is to define how software tools used within the
S-CORE project are identified, evaluated, and, where required, qualified for safe and secure
use.

S-CORE makes extensive use of tools to support and automate the generation, verification,
and management of work products. Therefore, tools that are part of the toolchain and may
affect the generation or verification of work products shall be identified, documented,
and evaluated. Where required by the evaluation result, the tool shall additionally be
qualified.


Objectives and Scope
--------------------

Tool Management Goals
~~~~~~~~~~~~~~~~~~~~~

The Tool Management process ensures that:

* Tools are identified and documented.
* Tools are evaluated with respect to their intended use.
* Tools are qualified where required.
* Tool Verification Reports are reviewed and released.


Approach
--------

Tool Management consists of four main stages:

1. Identification
2. Evaluation
3. Qualification, where required
4. Approval

The following figure provides an overview of the Tool Management process.

.. figure:: _assets/score_tool_management_overview.drawio.svg
   :width: 100%
   :align: center
   :alt: Tool Management Overview


Tool Management Attributes
~~~~~~~~~~~~~~~~~~~~~~~~~~

The requirements defined by :need:`gd_req__tool_attr_uid` are implemented as described
in the following sections.


Identification
~~~~~~~~~~~~~~

Each tool shall be uniquely identified by its name or UID and its version, independent of
where the tool is hosted or maintained.

The main S-CORE tooling is maintained in the
`S-CORE tooling repository <https://GitHub.com/eclipse-score/tooling/>`_.
Tools may, however, also be hosted and maintained in other repositories or locations.

For each tool, :need:`gd_temp__tool_management_verif_rpt_template` shall be used to document
the information required for Tool Management.

:need:`gd_chklst__tool_cr_review` shall be used to verify that all required information has
been considered.

Tool versions and tool configurations are managed according to
:need:`doc__platform_config_mgt_plan`.

The output of the Identification stage is a
:need:`wp__tool_verification_report` with status ``identified``.


Evaluation
~~~~~~~~~~

The Tool Confidence Level (TCL) shall be determined as defined in
:need:`doc_concept__tool_process`.

The evaluation consists of the following steps:

1. Determine the Tool Impact.
2. Determine the Tool Error Detection.
3. Determine the Tool Confidence Level.

.. figure:: _assets/score_tool_management_evaluation.drawio.svg
   :width: 100%
   :align: center
   :alt: Tool Evaluation


Step 1: Determine the Tool Impact
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Based on the identified potential tool malfunctions and security threats, assess whether
a tool malfunction or threat could lead to the violation of a safety or security requirement.

If such a violation is possible, Tool Impact shall be set to ``YES``.
Otherwise, Tool Impact shall be set to ``NO``.

If Tool Impact is ``NO``, continue with Step 3.
Otherwise, continue with Step 2.


Step 2: Determine the Tool Error Detection
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For the identified potential tool malfunctions and security threats, assess whether they
can be reliably detected or prevented.

Existing or additional safety measures and security controls may be considered where they
increase the ability to prevent or detect the identified malfunction or threat.

If the identified malfunctions or threats cannot be reliably detected or prevented,
Tool Error Detection shall be set to ``NO``.

Otherwise, Tool Error Detection shall be set to ``YES``.


Step 3: Determine the Tool Confidence Level
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Tool Confidence Level shall be determined from Tool Impact and Tool Error Detection.

If Tool Impact is ``YES`` and Tool Error Detection is ``NO``, the Tool Confidence Level
shall be set to ``LOW``.

In all other cases, the Tool Confidence Level shall be set to ``HIGH``.

A Tool Confidence Level of ``LOW`` requires Tool Qualification.

The output of the Evaluation stage is a
:need:`wp__tool_verification_report` with status ``evaluated``.


Qualification
~~~~~~~~~~~~~

Where Tool Qualification is required, the method **validation of the software tool** is
applied.

The qualification shall:

* specify requirements for the intended purpose and use of the tool within S-CORE;
* analyze relevant tool malfunctions and security threats;
* define additional safety measures and security controls where required;
* define verification measures and test cases for the tool requirements;
* execute the required verification and tests;
* document the verification and test results; and
* update the Tool Verification Report with the qualification results.

The existing S-CORE processes defined in :need:`wp__platform_mgmt` shall be used for
requirements engineering, verification, and analyses.

In particular:

* Use :need:`wf__req_comp_req` to define requirements for the software tool and
  :need:`wf__monitor_verify_requirements` to verify the requirements.

* Use :need:`wf__verification_comp_int_test` to define and execute tests for the software
  tool and :need:`wf__verification_mod_ver_report` to document the verification results.

* Where applicable, use the corresponding Safety and Security Analysis workflows.
  (To be added after the Safety/Security Analysis processes have been merged.)

The output of the Qualification stage is a
:need:`wp__tool_verification_report` with status ``qualified``.


Approval
~~~~~~~~

Following evaluation and, where required, qualification, the tool shall undergo final
approval for its intended use within S-CORE.

If the tool is accepted for its intended use, the
:need:`wp__tool_verification_report` shall be set to status ``released``.

If the tool is not accepted for its intended use, the
:need:`wp__tool_verification_report` shall be set to status ``rejected``.


Tailoring
~~~~~~~~~

The following tailoring applies to the safety activities for establishing confidence in
the use of software tools.

The following ISO 26262 requirements are not applicable to S-CORE software platform
development because the corresponding methods are not used:

:need:`std_req__iso26262__support_11471`,
:need:`std_req__iso26262__support_11472`,
:need:`std_req__iso26262__support_11473`,
:need:`std_req__iso26262__support_11474`,
:need:`std_req__iso26262__support_11481`,
:need:`std_req__iso26262__support_11482`,
:need:`std_req__iso26262__support_11483`,
:need:`std_req__iso26262__management_6456`.


Tool List
~~~~~~~~~

The overview of tools managed within S-CORE is provided in :ref:`tools`.
