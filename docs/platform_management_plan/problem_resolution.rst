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

.. document:: PF Problem Resolution Plan
   :id: doc__platform_problem_resolution_plan
   :status: draft
   :version: 2
   :safety: ASIL_B
   :security: YES
   :tags: platform_management
   :realizes: wp__prm_plan[version==1]

PF Problem Resolution Plan
==========================

This document implements the applicable parts of :need:`wp__platform_mgmt`.


Purpose
-------

The Problem Resolution Plan defines how problems are reported, analyzed,
resolved, monitored, verified, and closed within S-CORE.

A problem is defined as a deviation from an expected result.


Objectives and Scope
--------------------

Problem Resolution Goals
~~~~~~~~~~~~~~~~~~~~~~~~

The objectives of Problem Resolution are to ensure that:

* problems are recorded, uniquely identified, and classified;
* problems are analyzed to determine their impact, cause, and appropriate
  resolution;
* problem resolution activities are initiated and monitored;
* implemented resolutions are verified for completeness and effectiveness
  before closure;
* required notifications are performed and documented; and
* problems and their associated resolution activities are traceable through
  closure.


Approach
--------

Problem Resolution Execution
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

General contribution rules for S-CORE are defined in
:need:`doc__contr_guideline`.

Problem Resolution is a specific type of contribution. Problems identified
within S-CORE shall be reported and managed through the Problem Resolution
process defined in this document.


Problem Resolution Infrastructure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

:need:`GitHub Issues (ISSUE) <doc__issue_guideline>` are used to manage Problem
Reports and their resolution. They provide the central mechanism for reporting,
analyzing, planning, tracking, and closing problems within S-CORE.

A GitHub ISSUE of type **Problem Report** represents the Problem Report and
records the attributes required by the applicable Problem Resolution Process
Requirements.

The following figure provides an overview of how Problem Reports and their
resolution activities are managed in S-CORE.

.. figure:: _assets/score_problem_resolution_overview.drawio.svg
   :width: 100%
   :align: center
   :alt: Problem Resolution Overview

   Problem Resolution Overview

The Problem Report template :need:`gd_temp__problem_template` shall be used when
creating a Problem Report.

.. note::

   The template is automatically provided when creating an ISSUE of type
   **Problem Report**. This ISSUE type shall be used when reporting a problem
   in S-CORE.

   .. figure:: _assets/score_problem_resolution_report.drawio.svg
      :width: 100%
      :align: center
      :alt: Problem Report

      Problem Report


Problem Resolution Attributes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Problem Resolution Process Requirements are implemented as follows.

:need:`[[title]] <gd_req__problem_attr_uid>`
   The Problem Report identifier is the GitHub ISSUE number.

:need:`[[title]] <gd_req__problem_attr_status>`
   The Problem Resolution status is derived from the ISSUE state, the Projects
   dashboard status, and, where applicable, the status of linked PRs.

.. list-table:: Problem Status
   :header-rows: 1
   :widths: 20,25,30,25

   * - Problem Resolution Status
     - ISSUE State
     - Projects Status
     - Linked PR Status
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
     - ``Draft``, ``Open``, or ``Merged``
   * - closed
     - ``Closed``
     - ``Done``
     - ``Merged`` or n/a
   * - rejected
     - ``Closed as not planned``
     - n/a
     - n/a

:need:`[[title]] <gd_req__problem_attr_title>`
   The Problem Report title is the GitHub ISSUE title.

:need:`[[title]] <gd_req__problem_attr_impact_description>`
   The **Description** section of the ISSUE documents the problem and its
   observed impact. Identified or suspected causes may additionally be recorded
   as part of the initial description and subsequently refined during analysis.

   Where notification may be required, potentially affected parties shall also
   be identified, for example the Safety Manager responsible for an affected
   feature.

The **Problem notifications** section shall document whether notification is
required and the rationale for that decision, including when notification is
not required.

If notification is required, the affected parties and the performed
notifications shall be recorded, including who was notified, when the
notification was performed, and the communication mechanism used.

Identifying a notification recipient without recording evidence that the
notification was performed does not constitute a completed notification.

Suspected security vulnerabilities shall be handled according to the project's
confidential vulnerability reporting process.

Additional information may be documented in the **Supporting Information**
section of the ISSUE. In particular, information on **How to reproduce** and
**Error occurrence rate** should be provided using the dedicated sections of
the Problem Report.


The **Affected Version** section identifies the version in which the problem is
known to occur.

:need:`[[title]] <gd_req__problem_attr_affected_versions>`
   The first and last affected versions, including derived versions known to
   contain the problem, shall be documented.

   If the affected version range is not yet known, it shall be recorded as
   ``under investigation`` and updated as part of the problem analysis.

Potential resolutions and the selected resolution are documented in the
**Solution** section of the ISSUE.

:need:`[[title]] <gd_req__problem_attr_analysis_results>`
   The **Analysis Results** section documents the outcome of the analysis and
   the decision to accept or reject the problem for resolution.

   Where safety or security may be affected, the responsible Platform and/or
   Module Safety/Security Manager shall confirm the corresponding assessment.

:need:`[[title]] <gd_req__problem_attr_stakeholder>`
   Responsibility for the Problem Report is represented by the ISSUE assignees.
   Labels may additionally be used to identify the responsible Community or
   Feature Team.

The corresponding Feature Team labeling concept is currently under discussion
in https://github.com/eclipse-score/score/issues/870.

:need:`[[title]] <gd_req__problem_attr_classification>`
   The **Classification** section of the ISSUE records the problem
   classification. One of the following classifications shall be selected:

.. list-table:: Problem Classification
   :header-rows: 1
   :widths: 30,70

   * - Classification
     - Label
   * - minor
     - ``minor``
   * - major
     - ``major``
   * - critical
     - ``critical``
   * - blocker
     - ``blocker``

:need:`[[title]] <gd_req__problem_attr_safety_affected>`
   and

:need:`[[title]] <gd_req__problem_attr_security_affected>`
   Safety and Security relevance are documented in the **Category** section of the ISSUE.

Multiple categories may apply. If neither safety nor security relevance is
selected, the problem is treated as quality-related by default.

If safety is affected, the applicable ASIL shall be documented in the
**ASIL Classification** section of the ISSUE, for example ``ASIL_B``.

:need:`[[title]] <gd_req__problem_attr_milestone>`
   The planned target for resolving the Problem Report is recorded as the
   **Expected Closure Version**. A GitHub Milestone may additionally be assigned
   for planning and tracking.


Problem Resolution Workflow
~~~~~~~~~~~~~~~~~~~~~~~~~~~

Every Problem Resolution follows four principal steps:

#. **Create** the Problem Report.
#. **Analyze** and decide on the Problem Report.
#. **Resolve and monitor** the accepted problem.
#. **Verify and close** the Problem Report.

The colors used in the workflow figure correspond to these steps:

* grey: Problem Report creation;
* blue: analysis and decision;
* yellow: resolution and monitoring; and
* purple: verification and closure.

:need:`gd_guidl__problem_problem` provides additional guidance.


1. Create the Problem Report
^^^^^^^^^^^^^^^^^^^^^^^^^^^^

An ISSUE of type **Problem Report** is the authoritative mechanism for reporting
and tracking a problem within S-CORE.

The figure below shows the basic Problem Resolution workflow.

The Problem Report is created using the **Problem Report** ISSUE type with
initial ISSUE state ``Open``.

The ISSUE title shall clearly identify the potential problem. The Problem
Report template shall be completed with the information available at the time
of reporting.

Planning information is recorded through the **Expected Closure Version**. A
GitHub Milestone may additionally be assigned where appropriate.

The initial Problem Resolution status is ``open``:

* ISSUE state: ``Open``
* Projects status: ``No Status``

To initiate analysis, the Problem Report transitions to ``in review`` by keeping
the ISSUE state ``Open`` and setting its Projects status to ``Todo``.

If the reported problem is rejected, the decision and its rationale shall be
documented and the ISSUE shall be closed as ``Closed as not planned``.

.. figure:: _assets/score_problem_resolution_workflow_simple.drawio.svg
   :width: 100%
   :align: center
   :alt: Problem Resolution Simple Workflow Overview

   Problem Resolution Simple Workflow Overview


2. Analyze the Problem Report
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The Problem Report is reviewed and analyzed by a
:need:`Committer <rl__committer>`. Identified findings and requested
clarifications are addressed by the
:need:`Contributor <rl__contributor>` and documented in the ISSUE.

The analysis determines, as applicable:

* whether the reported deviation constitutes a problem;
* the affected versions and work products;
* the impact and classification of the problem;
* identified or suspected root causes;
* safety, security, and quality implications;
* required notifications;
* potential resolution options; and
* the selected resolution.

While the available information is insufficient to make a resolution decision,
the Problem Report remains ``in review``:

* ISSUE state: ``Open``
* Projects status: ``Todo``

The decision to accept or reject the problem for resolution shall be documented
in the ISSUE.

Where safety or security may be affected, the responsible Platform and/or
Module Safety/Security Manager shall confirm the corresponding assessment.

:need:`gd_chklst__problem_cr_review` provides the applicable review criteria.

If affected parties require notification, the
:need:`Project Lead <rl__project_lead>` or the responsible Feature Team Lead
shall ensure that the required notification is performed.

For platform-level problems, the Project Lead shall be added as an assignee.
Depending on the problem category, the Platform Safety Manager, Security
Manager, and/or Quality Manager shall also be assigned as applicable.

For affected Feature Teams (:ref:`pmp_pm_feature_teams`), notification and
responsibility are established by:

* assigning the responsible Feature Team Lead;
* assigning the Module Safety Manager, Security Manager, and/or Quality Manager
  as applicable; and
* applying the corresponding Feature Team label to the ISSUE.

The **Problem notifications** section shall record whether notification was
required and, where applicable, who was notified, when the notification was
performed, and the communication mechanism used.

An accepted Problem Report transitions to ``in implementation`` by keeping the
ISSUE state ``Open`` and setting its Projects status to ``In Progress``.

If the problem is rejected, the rationale shall be documented and the ISSUE
shall be closed as ``Closed as not planned``.


3. Resolve and Monitor the Problem
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

For an accepted Problem Report, the
:need:`Contributor <rl__contributor>` initiates the activities required to
resolve and verify the problem.

Depending on the required resolution, these activities may include a Change
Request, additional ISSUEs, planning activities, and one or more PRs.

Where the resolution requires a controlled change to the scope of an existing
feature or component, or the introduction of a new feature or component, the
applicable Change Request shall be created and managed according to
:need:`doc__platform_change_management_plan`.

All ISSUEs, Change Requests, and PRs created as part of the resolution shall be
linked to the Problem Report to maintain traceability and enable monitoring of
the resolution activities.

Resolution activities are monitored until all required activities have been
completed and the associated ISSUEs and PRs have been closed or merged, as
applicable.

Once implementation and verification activities are complete, the
:need:`Contributor <rl__contributor>` sets the Projects status to ``Done`` to
initiate the final closure review by the
:need:`Committer <rl__committer>`.

If resolution of an accepted problem is discontinued, the decision and its
rationale shall be documented before the Problem Report is closed using the
applicable closure state.



4. Verify and Close the Problem Report
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

The :need:`Committer <rl__committer>` performs the final review to confirm that
the accepted problem has been completely resolved and that the implemented
resolution is effective.

The final review confirms, as applicable, that:

* required resolution activities have been completed;
* associated ISSUEs are closed;
* required PRs are merged;
* affected work products have been updated;
* required verification activities have been completed successfully;
* the effectiveness of the implemented resolution has been evaluated;
* required notifications have been completed and documented; and
* required traceability is complete.

The effectiveness of the implemented resolution shall be evaluated and the
corresponding evidence or rationale documented.

Where safety is affected,
:need:`[[title]] <gd_req__problem_check_safety_closure>`
requires a rationale demonstrating either:

* that the implemented safety measure is effective; or
* that the problem does not constitute an unreasonable risk.

According to
:need:`[[title]] <gd_req__problem_check_safety_rationale>`,
both the rationale and its review result shall be documented.

:need:`gd_chklst__problem_cr_review` provides additional completeness and
closure criteria.

If all closure criteria are fulfilled:

* the Projects status is set to ``Done``; and
* the ISSUE is set to ``Closed``.

If further resolution or verification activities are required, the ISSUE
remains open and the Projects status is returned to ``In Progress``.


Problem Resolution SW Platform Work Products
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Problem Reports constitute the Problem Resolution records managed through
:need:`wp__issue_track_system`.

By default, the S-CORE platform and its modules use GitHub Issues, the common
Problem Report template, and the Problem Resolution process defined in this
document.

A module that deviates from this process, tooling, or template shall document
the deviation in its own Problem Resolution Plan.

Problem Reports for the S-CORE platform repository can be identified using the
``bug`` label:

`S-CORE Problem Reports <https://github.com/eclipse-score/score/issues?q=is%3Aissue%20state%3Aopen%20label%3Abug>`_
