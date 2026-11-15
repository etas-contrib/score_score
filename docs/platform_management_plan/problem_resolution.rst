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

.. document:: PF Problem Resolution Plan
   :id: doc__platform_problem_resolution_plan
   :status: draft
   :version: 2
   :safety: ASIL_B
   :security: YES
   :tags: platform_management
   :realizes: wp__prm_plan[version==1]

Problem Resolution Plan
=======================

This document implements parts of :need:`wp__platform_mgmt`.


Purpose
-------

The purpose of Problem Resolution is to define how project problems are reported, analyzed,
resolved, monitored, and closed.

A problem is defined as a deviation from an expected result.


Objectives and Scope
--------------------

Problem Resolution Goals
~~~~~~~~~~~~~~~~~~~~~~~~

The Problem Resolution process ensures that:

* Problems are recorded, uniquely identified, and classified.
* Problems are analyzed and assessed to determine an appropriate resolution.
* Problem resolution activities are initiated and monitored.
* Problem resolutions are verified before closure.
* Closure and relevant results are communicated to affected parties.


Approach
--------

Problem Resolution Execution
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

General contributions to the **S-CORE** project are described in
:need:`doc__contr_guideline`.

Problem Resolution is a specific type of contribution. Problems in **S-CORE** shall be
reported and managed exclusively through the Problem Resolution process described in this
document.


Problem Resolution Infrastructure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:need:`GitHub Issues (ISSUE) <doc__issue_guideline>` are used to manage Problem Reports and
their resolution. They provide the central mechanism for reporting, analyzing, planning,
tracking, and closing problems within **S-CORE**.

The following figure provides an overview of how problems are reported and managed in
**S-CORE**. A GitHub Issue is used as the Problem Report and contains the attributes required
by :need:`Problem Process Requirements <gd_req__problem_attr_uid>`.

.. figure:: _assets/score_problem_resolution_overview.drawio.svg
   :width: 100%
   :align: center
   :alt: Problem Resolution Overview

The Problem Report template :need:`gd_temp__problem_template` shall be used when creating a
Problem Report.

.. note::

   The template is automatically provided when creating an ISSUE of type **Problem Report**.
   Use this ISSUE type whenever a problem is reported in **S-CORE**.

   .. figure:: _assets/score_problem_resolution_report.drawio.svg
      :width: 100%
      :align: center
      :alt: Problem Report


Problem Resolution Attributes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Problem Resolution Process Requirements are implemented as follows.

:need:`[[title]] <gd_req__problem_attr_uid>` is represented by the ISSUE number.

:need:`[[title]] <gd_req__problem_attr_status>` is represented by the combination of the
ISSUE state and the Projects dashboard status. Where applicable, the status of linked PRs is
also considered.

.. list-table:: Problem Status
   :header-rows: 1
   :widths: 15,85,15,15

   * - Status
     - Issue status
     - Projects dashboard status
     - Linked PR status
   * - open
     - ``Open``
     - ``No Status``
     - n/a
   * - in review
     - ``Open``
     - ``Todo``
     - n/a
   * - in implementation
     - ``Open``
     - ``In Progress``
     - ``Draft`` or ``Open``
   * - closed
     - ``Closed``
     - ``Done``
     - ``Merged``
   * - rejected
     - ``Closed as not planned``
     - n/a
     - n/a

:need:`[[title]] <gd_req__problem_attr_title>` is represented by the ISSUE title.

:need:`[[title]] <gd_req__problem_attr_impact_description>` is documented in the
**Description** section of the ISSUE. This section shall describe the problem, its identified
or suspected root cause, and its impact. Where applicable, affected parties that may require
notification shall also be identified, for example the Safety Manager of an affected feature.

The **Problem notifications** section shall document whether notification is required and the
rationale for that decision, including when notification is not required. If notification is
required, the affected parties and the performed notification shall be recorded, including
who was notified, when, and through which communication mechanism.

A recipient listed without evidence of the notification does not constitute a performed
notification.

Suspected security vulnerabilities shall be handled according to the project's confidential
vulnerability reporting process.

Additional information can be documented in the **Supporting Information** section of the
ISSUE. In particular, information on **How to reproduce** and **Error occurrence rate**
should be provided using the dedicated sections of the Problem Report.

The **Affected Version** section identifies the version in which the problem occurs.

:need:`[[title]] <gd_req__problem_attr_affected_versions>` additionally requires the first and
last affected versions, including versions derived from a faulty version, to be documented.
If the affected versions are not yet known, they shall be recorded as ``under investigation``
and updated as part of the analysis.

Potential and selected resolutions are documented in the **Solution** section of the ISSUE.

:need:`[[title]] <gd_req__problem_attr_analysis_results>` is documented in the
**Analysis Results** section of the ISSUE. The analysis shall state whether the problem is
accepted or rejected. Where safety or security may be affected, the responsible Platform
and/or Module Safety/Security Manager shall confirm the corresponding assessment.

:need:`[[title]] <gd_req__problem_attr_stakeholder>` is represented by the ISSUE assignees.
Predefined labels may additionally be used to identify responsible Communities or Feature
Teams and their Feature Owners.

The corresponding Feature Team labeling concept is currently under discussion in
https://github.com/eclipse-score/score/issues/870.

:need:`[[title]] <gd_req__problem_attr_classification>` is documented in the
**Classification** section of the ISSUE. One of the following classifications shall be
selected:

.. list-table:: Problem Classification
   :header-rows: 1
   :widths: 15,15

   * - Classification identifier
     - Label
   * - minor
     - ``minor``
   * - major
     - ``major``
   * - critical
     - ``critical``
   * - blocker
     - ``blocker``

:need:`[[title]] <gd_req__problem_attr_safety_affected>` and
:need:`[[title]] <gd_req__problem_attr_security_affected>` are documented in the
**Category** section of the ISSUE.

Multiple categories may apply. If neither safety nor security is selected, the problem is
treated as quality-related by default.

If safety is affected, the applicable ASIL shall be documented in the **ASIL Classification**
section of the ISSUE, for example ``ASIL_B``.

:need:`[[title]] <gd_req__problem_attr_milestone>` is represented by the
**Expected Closure Version**. The ISSUE Milestone may additionally be used for planning and
tracking.


Problem Resolution Workflow
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Every Problem Resolution follows four main steps:

1. Create the Problem Report.
2. Analyze the Problem Report.
3. Initiate and monitor the Problem Resolution.
4. Verify and close the Problem Resolution.

The colors used in the following workflow figure correspond to these steps:

* grey: Problem Report creation
* blue: analysis
* yellow: implementation and monitoring
* purple: verification and closure

:need:`gd_guidl__problem_problem` provides additional guidance.


1. Create the Problem Report
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

An ISSUE of type **Problem Report** is the authoritative mechanism for reporting and tracking
a problem within **S-CORE**.

The figure below shows the basic Problem Resolution workflow.

The Problem Report is created with ISSUE type ``Bug`` and initial ISSUE state ``Open``.
The ISSUE title shall clearly identify the potential problem, and the Problem Report template
shall be completed with all information available at the time of reporting.

Planning information is captured by setting the **Expected Closure Version**. The ISSUE
Milestone may additionally be set where appropriate.

The initial Problem Resolution status ``open`` is represented by:

* ISSUE state ``Open``
* Projects status ``No Status``

To move the Problem Report to ``in review``:

* keep the ISSUE state ``Open``; and
* set the Projects status to ``Todo``.

If the reported problem is rejected:

* set the ISSUE state to ``Closed as not planned``.

.. figure:: _assets/score_problem_resolution_workflow_simple.drawio.svg
   :width: 100%
   :align: center
   :alt: Problem Resolution Simple Workflow Overview

   Problem Resolution Simple Workflow Overview


2. Analyze the Problem Report
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Problem Report is reviewed and analyzed by a
:need:`Committer <rl__committer>`. Identified findings and requested clarifications are
addressed by the :need:`Contributor <rl__contributor>` and documented in the ISSUE.

While the available information is insufficient to make a resolution decision, the Problem
Report remains:

* ISSUE state ``Open``
* Projects status ``Todo``
* Problem Resolution status ``in review``

Once sufficient information is available and the problem is accepted for resolution, the
Problem Report is moved to:

* ISSUE state ``Open``
* Projects status ``In Progress``
* Problem Resolution status ``in implementation``

The decision to accept or reject the problem shall be documented in the ISSUE.

Where safety or security may be affected, the responsible Platform and/or Module
Safety/Security Manager shall confirm the corresponding assessment.

:need:`gd_chklst__problem_cr_review` can be used to verify that the Problem Report contains
the information required to proceed.

If affected parties require notification, the
:need:`Project Lead <rl__project_lead>` or
:need:`Feature Team Lead <rl__delivery_team>` is responsible for ensuring that the required
notification is performed.

For platform-level problems, the Project Lead shall be added as an assignee. Depending on the
problem category, the Platform Safety Manager, Security Manager, and/or Quality Manager shall
also be assigned.

For affected Feature Teams (:ref:`pmp_pm_feature_teams`), notification and responsibility are
established by:

* adding the Feature Team Lead as an assignee;
* adding the Module Safety Manager, Security Manager, and/or Quality Manager as applicable;
* adding the corresponding Feature Team label to the ISSUE.

The **Problem notifications** section shall additionally record whether notification was
required and, where applicable, who was notified, when, and how.

If no Problem Resolution is to be initiated, the problem is rejected by setting the ISSUE
state to ``Closed as not planned``.


3. Initiate and Monitor the Problem Resolution
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The :need:`Contributor <rl__contributor>` initiates the activities required to resolve the
problem. Depending on the required changes, these activities may include Change Requests,
additional ISSUEs, planning activities, and PRs.

All ISSUEs and PRs created as part of the resolution shall be linked to the Problem Report
to provide traceability and enable monitoring of the resolution activities.

The resolution activities are tracked until all linked ISSUEs are closed and all relevant
PRs are merged or otherwise resolved.

Once all resolution activities are completed, the
:need:`Contributor <rl__contributor>` sets the Projects status to ``Done``. This triggers the
final verification by the :need:`Committer <rl__committer>`.

A Problem Resolution may also be rejected during this phase. In this case, the rationale
shall be documented and the ISSUE state shall be set to ``Closed as not planned``.


4. Verify and Close the Problem Resolution
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The :need:`Committer <rl__committer>` performs the final verification that the problem has
been completely resolved.

All linked resolution activities shall have been completed. In particular, linked ISSUEs
shall be closed and relevant PRs shall be merged or otherwise resolved.

The effectiveness of the implemented resolution measures shall be evaluated and the
corresponding rationale documented.

Where safety is affected,
:need:`[[title]] <gd_req__problem_check_safety_closure>` requires a rationale demonstrating
either:

* that an implemented safety measure is effective; or
* that the problem does not constitute an unreasonable risk.

According to :need:`[[title]] <gd_req__problem_check_safety_rationale>`, both the rationale
and its review result shall be documented.

:need:`gd_chklst__problem_cr_review` can be used to support the final completeness and closure
review.

If the closure criteria are fulfilled:

* set the Projects status to ``Done``; and
* set the ISSUE state to ``Closed``.

If the closure criteria are not fulfilled, the Projects status shall be set back to
``In Progress`` and the required resolution activities shall continue.


Problem Resolution SW Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Problem Reports constitute the Problem Resolution records published through
:need:`wp__issue_track_system`.

By default, the **S-CORE** platform and its modules use GitHub Issues, the common Problem
Report template, and the same Problem Resolution mechanism described in this document.

A module that deviates from this process, tooling, or template shall document the deviation
in its own Problem Resolution Plan.

Problem Reports for the S-CORE platform repository are identified by the ``Bug`` label:

`S-CORE Problem Reports <https://github.com/eclipse-score/score/issues?q=is%3Aissue%20state%3Aopen%20label%3Abug>`_
