..
   # *******************************************************************************
   # Copyright (c) 2024-26 Contributors to the Eclipse Foundation
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

.. document:: PF Project Management Plan
   :id: doc__project_mgt_plan
   :status: valid
   :version: 1
   :safety: ASIL_B
   :security: YES
   :realizes: wp__project_mgt[version==1]
   :tags: platform_management

.. _pmp_pm_plan:

PF Project Management Plan
==========================

Purpose
-------

The Project Management Plan defines the organizational and management framework
for planning, coordinating, monitoring, and controlling the S-CORE project
throughout its lifecycle.

In particular, this plan defines:

* the project organization, stakeholders, roles, and responsibilities;
* the communication, coordination, and reporting mechanisms;
* the approach for planning, scheduling, and tracking project work;
* the management of milestones, releases, and dependencies;
* the mechanisms for monitoring project progress and identifying deviations;
* the escalation paths for issues that cannot be resolved within the responsible
  team or organizational unit; and
* the project-management records and infrastructure used to provide transparency
  and traceability.


Objectives and Scope
--------------------

Project Management Goals and Definition of Done
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The project-management framework is considered adequately established and
maintained when the following objectives are fulfilled:

* Project organization is defined and maintained.

  * The :ref:`Organization and Structure <pmp_pm_organization>` is documented
    and kept up to date.
  * Relevant organizational units, responsibilities, and interfaces are defined.

* Communication and reporting mechanisms are established.

  * The team structure and recurring meeting structure are documented.
  * Required communication channels are established and maintained.
  * Project meetings are scheduled in the Eclipse S-CORE calendar.
  * Relevant decisions, action items, and meeting outcomes are documented.

* The project scope is defined and maintained.

  * The S-CORE Handbook (:need:`doc__platform_handbook`) is available and
    maintained.
  * :ref:`Features <features>` are defined and maintained.

* Project work is planned and tracked.

  * The project roadmap is maintained.
  * :ref:`Milestones <pmp_pm_milestone>` and
    :ref:`Releases <pmp_pm_release>` are defined and tracked.
  * Planned work is represented by the applicable work-item hierarchy.
  * Progress, dependencies, risks to planned delivery, and deviations from the
    plan are regularly monitored.

* Escalation paths are defined.

  * Issues that cannot be resolved within the responsible organizational unit
    are escalated through the defined project organization.

* Required reviews are performed.

  * Reviews are performed according to the applicable process definitions.
  * The corresponding review criteria, templates, and records are used and
    maintained.


.. _pmp_pm_organization:

Project Organization
--------------------

The S-CORE project organization consists of Lead Circles, Communities, and
Feature Teams. Together, these organizational units provide project governance,
cross-functional coordination, and responsibility for implementation.

The current organizational structure is maintained in the S-CORE organization
description.

.. _pmp_pm_steering_committees:

Steering Committees
~~~~~~~~~~~~~~~~~~~

Project-level steering is performed through the established Lead Circles.

The combined :term:`Project Lead Circle` coordinates strategic project
decisions and provides alignment between project management and technical
direction.


.. _pmp_pm_communities:

Communities
~~~~~~~~~~~

Communities coordinate cross-functional topics that span multiple Feature
Teams.

Typical responsibilities include:

* project-level architectural decisions;
* common development, verification, and integration infrastructure;
* engineering and project processes; and
* integration and release coordination.

Each Community has a :term:`Community Lead` responsible for coordinating the
Community's activities and interfaces with the affected Feature Teams and Lead
Circles.


.. _pmp_pm_feature_teams:

Feature Teams
~~~~~~~~~~~~~

Feature Teams have end-to-end responsibility for delivering defined
functionality within their assigned scope.

Their responsibility covers the applicable development lifecycle, including
requirements, architecture, implementation, verification, and integration.

Feature Teams organize and track their work through the applicable GitHub Issues
and project-management infrastructure.

Each Feature Team:

* has a designated Feature Team Lead responsible for coordinating the team's
  activities;
* plans and tracks its work within the applicable GitHub Project;
* maintains the work products within its scope;
* coordinates dependencies with other Feature Teams and Communities; and
* has at least one :need:`Committer <rl__committer>` with the required
  repository permissions to approve and merge Pull Requests.


Organization Management
~~~~~~~~~~~~~~~~~~~~~~~

Changes to the project organization are decided by the responsible Lead Circle
and documented in the corresponding decision or meeting record.

Implementation of an approved organizational change shall be tracked using an
applicable project work item.

Organizational changes include, in particular:

* creation of a new Community or Feature Team;
* temporary suspension of an existing Community or Feature Team;
* changes to organizational responsibilities where project interfaces are
  affected; and
* dissolution of an existing Community or Feature Team.


Creation of a New Feature Team
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When a new Feature Team is established, the following project infrastructure
shall be created or adapted as applicable:

* create or update the corresponding GitHub Team and assign its members;
* create or assign the required GitHub repository or repositories;
* define repository-specific :ref:`CODEOWNERS <pmp_pm_codeowners>`;
* create or configure the applicable GitHub Project with the required planning
  and tracking views;
* establish the applicable location for meeting and decision records;
* create the applicable organizational labels;
* create the corresponding communication channels; and
* update this Project Management Plan and other affected project documentation.

Communication
-------------

Project communication is organized to ensure transparency of project status,
decisions, responsibilities, dependencies, and planned work.


External Communication
~~~~~~~~~~~~~~~~~~~~~~

External project communication is performed through the project's public
communication channels, including GitHub and other communication platforms
approved by the project.

Project-wide publications and coordinated external communication are managed by
the Marketing and Communication Community where applicable.


Internal Communication
~~~~~~~~~~~~~~~~~~~~~~

Project-internal coordination is performed primarily through:

* virtual and face-to-face meetings and their documented outcomes;
* GitHub Issues for planning, discussion, and tracking of work;
* GitHub Pull Requests for reviewing and integrating changes; and
* the project-approved communication channels for direct and asynchronous
  coordination.


Meetings
~~~~~~~~

Project meetings shall be scheduled in the Eclipse S-CORE calendar where they
are relevant to the broader project community.

Unless explicitly restricted for confidentiality or another documented reason,
project meetings are open to the applicable project community.

Participants required for a decision or activity shall be identified and
invited as appropriate.

Relevant meeting outcomes, in particular decisions and action items, shall be
documented in the applicable project records.


.. _pmp_pm_repository_structure:

Repository Structure
--------------------

The S-CORE platform follows a multi-repository approach.


.. _pmp_pm_root_repository:

Root Repository
~~~~~~~~~~~~~~~

The root repository provides project-wide assets and platform-integration
information.

It contains, among other things:

* :ref:`Stakeholder Requirements <Stakeholder_Requirements>`;
* documentation of :ref:`Platform Features <features>`;
* feature requirements and architecture;
* project-wide build infrastructure, including S-CORE-specific macros and rules;
  and
* integration rules for software modules.

These artifacts follow the
:ref:`Platform Repository Folder Structure <platform_folder_structure>`.


Module Repositories
~~~~~~~~~~~~~~~~~~~

Software modules are maintained in their applicable repositories.

A module repository typically contains:

* components;
* requirements;
* architecture;
* implementation; and
* verification specifications and tests.

Module repositories follow the
:ref:`Module Folder Structure <module_folder_structure>`.


.. _pmp_pm_codeowners:

CODEOWNERS
~~~~~~~~~~

When a new repository is established, the Project Leads nominate the initial
repository CODEOWNERS.

CODEOWNERS identify technical review responsibility for defined parts of a
repository.

Candidates for CODEOWNERS should:

* have sufficient technical knowledge of the affected feature or component;
* understand the intended architecture and implementation;
* have sufficient experience to review changes within the assigned scope; and
* be :need:`Committers <rl__committer>` where repository permissions are
  required to approve and merge Pull Requests.

Being listed as a CODEOWNER does not by itself grant Committer status or merge
permissions.

CODEOWNERS definitions shall be maintained as project responsibilities evolve.

Changes to CODEOWNERS shall be performed through the normal repository change
and review process.

Planning and Tracking
---------------------

Cadence
~~~~~~~

Iteration
^^^^^^^^^

The project schedule is organized into two-week iterations.

Iterations provide the regular cadence for planning, execution, review, and
progress monitoring.


Release Frequency
^^^^^^^^^^^^^^^^^

Release planning is aligned with the project iteration and milestone structure.

The target release cadence is established through the applicable project roadmap
and milestone planning.

Release scope and timing may be adapted based on integration status,
verification readiness, dependencies, and applicable release criteria.

Each release establishes a defined baseline according to
:need:`doc__platform_release_management_plan`.


Planning and Tracking Infrastructure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

GitHub is the primary infrastructure for planning and tracking project work.

GitHub Issues represent planned, requested, or identified work.

GitHub Projects provide team-level and project-level planning and status views.

Milestones and releases provide higher-level scheduling and baseline
information.


.. _pmp_pm_issue_types:

Issue Types
~~~~~~~~~~~

The project uses defined GitHub Issue Types to distinguish the purpose and
planning level of individual work items.

.. image:: _assets/score_project_management_issue_types.drawio.svg
   :width: 900
   :alt: Issue Types
   :align: center


Architectural Issues
^^^^^^^^^^^^^^^^^^^^

.. _pmp_pm_feature_request:

Feature Request
"""""""""""""""

A Feature Request represents a request for new platform functionality or a
modification to the scope of existing functionality.

Feature Requests are managed according to
:need:`doc__platform_change_management_plan`.

New Features and major Feature Modifications follow the
:ref:`Feature and Enhancement Proposal (FEP) <feature_request_guideline>`
process as defined by the Change Management Plan.

The Architecture Community coordinates the architectural assessment where
required, including the applicable Shepherd review and Final Comment Period for
changes following the FEP Track.

The :term:`Project Lead Circle` performs the applicable project-level
coordination and considers accepted Feature Requests as input to roadmap,
Product Increment, milestone, and release planning.

Implementation activities resulting from an accepted Feature Request are
represented through the applicable planning work items and linked Pull Requests.

.. _pmp_pm_component_request:

Component Request
"""""""""""""""""

A Component Request represents a request for a new component or a modification
to the scope of an existing component.

Component Requests are managed according to
:need:`doc__platform_change_management_plan`.

Component Requests normally follow the standard Change Request workflow and do
not require the FEP Track unless an explicit process decision determines
otherwise.

A Component Request is owned by the responsible Feature Team and maintained in
the applicable team repository.

A Component Request may reference or be linked to other work items required to
plan and implement the requested change.

Implementation of an accepted Component Request is represented through the
applicable planning work items and linked Pull Requests.


Planning Issues
^^^^^^^^^^^^^^^

.. _pmp_pm_product_increment:

Product Increment
"""""""""""""""""

A Product Increment represents the highest level of the project planning
hierarchy for the planned development of a version of a
:ref:`Module <modules>`.

A Product Increment:

* represents a planned module increment;
* may contain multiple Epics;
* is aligned with the applicable milestones and releases; and
* is maintained as part of the overall project roadmap.

Product Increments are coordinated by the :term:`Project Lead Circle` and are
maintained in the :ref:`Root Repository <pmp_pm_root_repository>`.


.. _pmp_pm_epic:

Epic
""""

An Epic is the primary planning work package used by a Feature Team.

An Epic should be scoped so that it can normally be completed within one
S-CORE release cycle. It represents a coherent development outcome and may
contain multiple Tasks.

An Epic may exist:

* as part of a Product Increment; or
* independently when its outcome represents a self-contained improvement that
  does not require a dedicated Product Increment.

Epics are owned by the responsible Feature Team and maintained in the applicable
team repository.


.. _pmp_pm_task:

Task
""""

A Task represents the smallest standard unit of planned project work and shall
describe a concrete and assignable activity.

Tasks are normally created as children of an Epic.

A standalone Task is permitted where creation of an Epic would not provide
additional planning value.

Where several related Tasks together constitute a coherent development outcome,
an Epic should be created and the Tasks assigned to it as child work items.

Tasks are owned by the responsible team and maintained in the applicable
repository.


.. _pmp_pm_bug:

Bug
"""

A Bug represents a defect, malfunction, or unintended behavior in an existing
project work product.

Bugs requiring formal Problem Resolution shall be managed according to
:need:`doc__platform_problem_resolution_plan`.

The Bug issue type may be used as the project-planning representation of the
corresponding corrective work where applicable.

Bugs are owned by the responsible Feature Team and maintained in the applicable
team repository.

Dependencies
~~~~~~~~~~~~

Dependencies between work items shall be represented using the applicable GitHub
``blocked by`` and ``blocking`` relationships.

Dependencies that may affect other teams, Product Increments, milestones, or
releases shall be made visible in the corresponding project-planning views and
considered during progress monitoring.


.. _pmp_pm_milestone:

Milestones
~~~~~~~~~~

A Milestone represents a significant point or target in the project schedule,
such as:

* a project release;
* an integration milestone;
* a major project review; or
* a process or project audit.

GitHub Milestones are used, where applicable, to associate relevant Issues and
Pull Requests with these project-level planning targets.


.. _pmp_pm_release:

Releases
~~~~~~~~

Releases establish defined and identifiable baselines of software and associated
work products.

Release planning, verification, approval, identification, and execution shall
follow :need:`doc__platform_release_management_plan`.

Release planning shall consider the readiness of the required Product
Increments, dependencies, verification evidence, and applicable release
criteria.


.. _pmp_pm_gh_labels:

Labels
~~~~~~

GitHub Labels provide additional classification of Issues and Pull Requests.

Labels shall complement, rather than replace, dedicated GitHub properties such
as Issue Type, Status, parent-child relationships, and dependencies.

New organization-wide labels shall only be introduced where a recurring
cross-project classification need exists.

The common label set shall be maintained centrally to avoid redundant or
inconsistent classifications.


Roadmap View
^^^^^^^^^^^^

Roadmap views provide a time-oriented representation of planned work and are
used to visualize Product Increments, milestones, releases, and other
time-dependent planning information.

The project roadmap shall provide sufficient visibility to identify relevant
cross-team dependencies and potential impact on planned milestones and releases.

Traceability
~~~~~~~~~~~~

Project work shall remain traceable from the originating request or planning
item through implementation.

Pull Requests shall therefore be linked to the GitHub Issues that authorize or
track the corresponding change.

Where hierarchical relationships exist, they shall be represented using the
defined parent-child relationships.

Cross-work-item dependencies shall be represented using the corresponding
GitHub dependency mechanism.

Depending on the type of change, traceability may include both a Change Request
or Problem Report and the planning work items used to organize its
implementation.

A typical planning and implementation hierarchy is:

.. code-block:: text

   Project / Release Planning
             |
             v
     Product Increment
             |
             v
            Epic
             |
             v
            Task
             |
             v
       Pull Request
             |
             v
    Changed Work Product

For controlled changes, the corresponding Change Request shall additionally be
linked to the applicable planning items and implementation Pull Requests.

For problem resolutions, the corresponding Problem Report shall additionally be
linked to the applicable resolution activities and Pull Requests.

This provides traceability between project planning, authorized or identified
work, implementation, and the resulting work products.


Planning of Work
~~~~~~~~~~~~~~~~

Planning follows a combination of bottom-up team planning and project-level
coordination.

Each Feature Team is responsible for planning the work within its scope using
its GitHub Project.

Team plans consist primarily of :ref:`Epics <pmp_pm_epic>`,
:ref:`Tasks <pmp_pm_task>`, and :ref:`Bugs <pmp_pm_bug>`.

Change Requests represented by
:ref:`Feature Requests <pmp_pm_feature_request>` and
:ref:`Component Requests <pmp_pm_component_request>` are managed according to
:need:`doc__platform_change_management_plan` and provide input to the applicable
architectural and project planning activities.

Project-level planning is coordinated by the :term:`Project Lead Circle` using
:ref:`Product Increments <pmp_pm_product_increment>`,
:ref:`Milestones <pmp_pm_milestone>`, and
:ref:`Releases <pmp_pm_release>`.

This establishes the relationship between strategic project planning,
controlled architectural evolution, team-level implementation planning, and
release planning.

.. image:: _assets/score_project_management_process_issue_overview.drawio.svg
   :width: 600
   :alt: Planning Overview
   :align: center
   
Tracking Progress
~~~~~~~~~~~~~~~~~

Progress is monitored at both team and project level.

Feature Teams regularly review the status of their planned work using their
respective GitHub Projects.

The :term:`Project Lead Circle` regularly reviews the overall project status
against upcoming Product Increments, Milestones, and Releases using the
project-wide roadmap and applicable project-planning views.

The review shall identify, where applicable:

* work that is behind plan;
* unresolved dependencies or blockers;
* Product Increments at risk;
* milestone or release deviations;
* cross-team coordination needs; and
* issues requiring escalation.

Where a significant deviation from the plan is identified, the responsible
organizational unit shall determine the required corrective action and reflect
the resulting change in the applicable planning information.


Dashboards
^^^^^^^^^^

GitHub Project insights and charts are used to provide aggregated views of
project progress and work-item status.

Dashboards complement the underlying Issues and GitHub Projects and may be used
to monitor trends, open work, completion status, dependencies, and progress
towards upcoming milestones and releases.

The authoritative status remains the status of the underlying work items and
project-planning data.


Escalation
----------

Issues shall initially be addressed within the organizational unit responsible
for the affected work.

If an issue cannot be resolved at that level, it shall be escalated through the
applicable project organization:

.. code-block:: text

   Individual / Work Item
           |
           v
      Feature Team
           |
           v
   Community / Cross-Team Coordination
           |
           v
   Project Lead Circle

Technical or architectural topics shall be escalated through the applicable
technical governance structure.

Project-planning, organizational, resource, or schedule topics shall be
escalated through the applicable project-management governance structure.

Safety, security, quality, or process topics shall additionally involve the
responsible role or Community where required by the applicable management plan.

Escalations affecting project scope, Product Increments, milestones, releases,
dependencies, or organizational responsibilities shall be documented in the
applicable project records.

Where further work or a managed change is required, it shall be represented by
the applicable GitHub Issue or Change Request.

