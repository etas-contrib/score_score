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

.. document:: PF Project Management Plan
   :id: doc__project_mgt_plan
   :status: valid
   :version: 1
   :safety: ASIL_B
   :security: YES
   :realizes: wp__project_mgt[version==1]
   :tags: platform_management_plan

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
* the project management records and infrastructure used to provide transparency
  and traceability.


Objectives and Scope
--------------------

Project Management Goals and Definition of Done
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The project management activities are considered adequately established and
maintained when the following objectives are fulfilled:

* **Project organization is defined and maintained.**

  * The :ref:`Organization and Structure <pmp_pm_organization>` is documented
    and kept up to date.
  * Relevant organizational units, responsibilities, and interfaces are defined.

* **Communication and reporting mechanisms are established.**

  * The team structure and recurring meeting structure are documented.
  * Required communication channels are established and maintained.
  * Project meetings are scheduled in the Eclipse S-CORE calendar.
  * Relevant decisions and meeting outcomes are documented.

* **The project scope is defined and maintained.**

  * The S-CORE Handbook (:need:`doc__platform_handbook`) is available and
    maintained.
  * :ref:`Features <features>` are defined and maintained.

* **Project work is planned and tracked.**

  * The project roadmap is maintained.
  * :ref:`Milestones <pmp_pm_milestone>` and
    :ref:`Releases <pmp_pm_release>` are defined and tracked.
  * Planned work is represented by the applicable work-item hierarchy.
  * Progress and deviations from the plan are regularly monitored.

* **Escalation paths are defined.**

  * Issues that cannot be resolved within the responsible team are escalated
    through the defined project organization.

* **Required reviews are performed.**

  * Reviews are performed according to their applicable definitions.
  * The corresponding review templates and records are used and maintained.


.. _pmp_pm_organization:

Project Organization
--------------------

The S-CORE project organization consists of Steering Committees, Communities,
and Feature Teams. Together, these organizational units provide project
governance, cross-functional coordination, and responsibility for implementation.

The current organizational structure is documented in the
`S-CORE organization description
<https://github.com/orgs/eclipse-score/discussions/3472>`_.


.. _pmp_pm_steering_committees:

Steering Committees
~~~~~~~~~~~~~~~~~~~

Project-level steering is performed through the established *Lead Circles*.

The combined :term:`Project Lead Circle` coordinates strategic project decisions
and provides alignment between project management and technical direction.


.. _pmp_pm_communities:

Communities
~~~~~~~~~~~

*Communities* coordinate cross-functional topics that span multiple Feature
Teams. Typical responsibilities include:

* project-level architectural decisions;
* common development and testing infrastructure;
* engineering and project processes; and
* integration and release activities.

Each *Community* has a :term:`Community Lead` responsible for coordinating the
community's activities.


.. _pmp_pm_feature_teams:

Feature Teams
~~~~~~~~~~~~~

*Feature Teams* have end-to-end responsibility for delivering defined
functionality. Their responsibility covers the relevant development lifecycle,
from requirements and architecture through implementation and integration testing.

Feature Teams organize and track their work through the assigned *GitHub Issues*
and project infrastructure.

Each Feature Team:

* has a designated *Feature Team Lead* responsible for coordinating the team's
  activities;
* plans and tracks its work within the corresponding GitHub Project;
* maintains the work products within its scope; and
* has at least one :need:`Committer <rl__committer>` with the authority to
  approve and merge Pull Requests.


Organization Management
~~~~~~~~~~~~~~~~~~~~~~~

Changes to the project organization are decided by the responsible Lead Circle
and documented in the corresponding meeting records.

Implementation of an approved organizational change shall be tracked by a
*Task*.

Organizational changes include, in particular:

* creation of a new Community or Feature Team;
* temporary suspension of an existing Community or Feature Team; and
* dissolution of an existing Community or Feature Team.


Creation of a New Feature Team
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

When a new Feature Team is established, the following project infrastructure
shall be created or adapted as applicable:

* create the corresponding GitHub Team and assign its core members;
* create the required GitHub repository;
* define repository-specific :ref:`CODEOWNERS <pmp_pm_codeowners>`;
* create the Team GitHub Project with the required planning and tracking views;
* establish a location for meeting records;
* create the applicable organizational label;
* create the corresponding Slack channel; and
* update this Project Management Plan and other affected project documentation.


Communication
-------------

Project communication is organized to ensure transparency of project status,
decisions, responsibilities, and planned work.


External Communication
~~~~~~~~~~~~~~~~~~~~~~

External project communication is performed through the project's public
communication channels, including GitHub and other communication platforms
approved by the project.

Project-wide publications and coordinated external communication are managed by
the ``Marketing and Communication Community``.


Internal Communication
~~~~~~~~~~~~~~~~~~~~~~

Project-internal coordination is performed primarily through:

* virtual and face-to-face meetings and their documented outcomes;
* *GitHub Issues* for planning, discussion, and tracking of work;
* *GitHub Pull Requests* for reviewing and integrating changes; and
* Slack for direct and asynchronous project communication.


Meetings
~~~~~~~~

Project meetings shall be scheduled in the Eclipse S-CORE calendar.

Unless explicitly restricted, project meetings are open to the project
community. Members required for a particular meeting are expected to
participate.

Relevant meeting outcomes, in particular decisions and action items, shall be
documented in the applicable public project records.


.. _pmp_pm_repository_structure:

Repository Structure
--------------------

The S-CORE platform follows a multi-repository approach.


.. _pmp_pm_root_repository:

Root Repository
~~~~~~~~~~~~~~~

The root repository provides project-wide assets and integration information.

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

Each software module is maintained in its own repository.

A module repository typically contains:

* components;
* requirements;
* architecture;
* implementation; and
* tests.

Module repositories follow the
:ref:`Module Folder Structure <module_folder_structure>`.


.. _pmp_pm_codeowners:

CODEOWNERS
~~~~~~~~~~

When a new repository is established, the Project Leads nominate the initial
repository ``CODEOWNERS``.

CODEOWNERS provide technical ownership for defined parts of a repository and
participate in the review of changes within their area of responsibility.

Candidates for CODEOWNERS should:

* have sufficient technical knowledge of the affected feature or component;
* understand the intended architecture and implementation;
* preferably have substantial implementation experience in the respective area;
  and
* be :need:`Committers <rl__committer>` where merge permissions are required.

CODEOWNERS definitions shall be maintained as project responsibilities evolve.
Changes to code ownership shall be performed through the normal repository
change and review process.


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

A project release is planned after every second iteration.

A release establishes a defined project baseline according to the applicable
release management process.


Planning and Tracking Infrastructure
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

GitHub is the primary infrastructure for planning and tracking project work.

*GitHub Issues* represent planned and identified work.
*GitHub Projects* provide project-specific planning and status views.
Milestones and releases provide higher-level scheduling and baseline information.


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

A *Feature Request* represents a high-level request for new platform
functionality or a significant modification of existing functionality.

Feature Requests are governed by the
:ref:`Feature and Enhancement Proposal (FEP) <feature_request_guideline>`
process.

The ``Architecture Community`` coordinates the architectural assessment,
including the Shepherd review and Final Comment Period. The
:term:`Project Lead Circle` performs the corresponding project-level triage and
uses accepted Feature Requests as input to project roadmap planning.

Implementation activities resulting from an accepted Feature Request are tracked
using the applicable planning work items.


.. _pmp_pm_component_request:

Component Request
"""""""""""""""""

A *Component Request* represents an independent work package used to describe modifications inside a *Feature*, either adding new components or modifying existing ones.
*Component Request* work packages can be linked to other work packages, but they must not be treated as parent work packages. They shall be discussed with
``Architecture Community`` and the issues are owned by a Team and are part of the Team`s main repository.

`Component Request issue template <https://github.com/eclipse-score/.github/.github/ISSUE_TEMPLATE/1b_ComponentRequest.yml>`_


Planning Issues
^^^^^^^^^^^^^^^


.. _pmp_pm_product_increment:

Product Increment
"""""""""""""""""

A *Product Increment* represents the highest level of the project planning
hierarchy for the development of a version of a :ref:`Module <modules>`.

A Product Increment:

* represents a planned module increment;
* may contain multiple *Epics*;
* is aligned with the applicable milestones and releases; and
* is maintained as part of the overall project roadmap.

Product Increments are coordinated by the :term:`Project Lead Circle` and are
maintained in the :ref:`Root Repository <pmp_pm_root_repository>`.


.. _pmp_pm_epic:

Epic
""""

An *Epic* is the primary planning work package used by a Feature Team.

An Epic should be scoped such that it can normally be completed within one
S-CORE release cycle. It represents a coherent development outcome and may
contain multiple *Tasks*.

An Epic may exist:

* as part of a Product Increment; or
* independently when its outcome represents a self-contained improvement that
  does not require a dedicated Product Increment.

Epics are owned by the responsible Feature Team and maintained in that team's
repository.


.. _pmp_pm_task:

Task
""""

A *Task* represents the smallest standard unit of planned project work and shall
describe a concrete, assignable activity.

Tasks are normally created as children of an *Epic*. A standalone Task is
permitted where creation of an Epic would not provide additional planning value.

Where several related Tasks together constitute a coherent development outcome,
an Epic should be created and the Tasks assigned to it as child work items.

Tasks are owned by the responsible team and maintained in the applicable
repository.


.. _pmp_pm_bug:

Bug
"""

A *Bug* represents a defect, malfunction, or unintended behavior in an existing
project work product.

Bugs are planned and tracked similarly to development work packages but focus on
restoring or correcting existing functionality rather than introducing new
functionality.

Bugs are owned by the responsible Feature Team and maintained in the applicable
team repository.


Dependencies
~~~~~~~~~~~~

Dependencies between work items shall be represented using the GitHub
``blocked by`` and ``blocking`` relationships.

Dependencies that can affect milestones, releases, or other teams shall be made
visible in the corresponding project planning views.


.. _pmp_pm_milestone:

Milestones
~~~~~~~~~~

A *Milestone* represents a significant point in the project schedule, such as:

* a project release;
* an integration milestone;
* a major project review; or
* a process or project audit.

GitHub Milestones are used to associate relevant Issues and Pull Requests with
these project-level planning points.


.. _pmp_pm_release:

Releases
~~~~~~~~

*Releases* are project milestones that establish defined baselines of the
development activities and their resulting work products.

Release planning and execution shall follow the applicable S-CORE release
management process.


.. _pmp_pm_gh_labels:

Labels
~~~~~~

GitHub Labels provide additional classification of Issues and Pull Requests.

Labels shall complement, rather than replace, dedicated GitHub properties such
as Issue Type, Status, parent-child relationships, and dependencies.

New organization-wide labels shall only be introduced where a recurring
cross-project classification need exists. The common label set is maintained
centrally to avoid redundant or inconsistent classifications.
Roadmap View
^^^^^^^^^^^^

Roadmap views provide a time-oriented representation of planned work and are
used to visualize Product Increments, milestones, releases, and other
time-dependent planning information.


Traceability
~~~~~~~~~~~~

Project work shall remain traceable from planning through implementation.

Pull Requests shall therefore be linked to the GitHub Issues that authorize or
track the corresponding change.

Where hierarchical relationships exist, they shall be represented using the
defined parent-child relationships. Cross-work-item dependencies shall be
represented using the corresponding GitHub dependency mechanism.

This provides traceability between:

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


Planning of Work
~~~~~~~~~~~~~~~~

Planning follows a combination of bottom-up team planning and project-level
coordination.

Each Feature Team is responsible for planning the work within its scope using
its ``GitHub Project``. Team plans consist primarily of
:ref:`Epics <pmp_pm_epic>`, :ref:`Tasks <pmp_pm_task>`, and
:ref:`Bugs <pmp_pm_bug>`.

Architectural change requests, represented by
:ref:`Feature Requests <pmp_pm_feature_request>` and
:ref:`Component Requests <pmp_pm_component_request>`, are coordinated by the
``Architecture Community``.

Project-level planning is coordinated by the :term:`Project Lead Circle` using
:ref:`Product Increments <pmp_pm_product_increment>`,
:ref:`Milestones <pmp_pm_milestone>`, and
:ref:`Releases <pmp_pm_release>`.

This establishes the relationship between strategic project planning,
architectural evolution, and team-level implementation planning.

.. image:: _assets/score_project_management_process_issue_overview.drawio.svg
   :width: 600
   :alt: Planning Overview
   :align: center

Tracking Progress
~~~~~~~~~~~~~~~~~

Progress is monitored at both team and project level.

Feature Teams regularly review the status of their planned work using their
respective ``GitHub Project``.

The :term:`Project Lead Circle` regularly reviews the overall project status
against upcoming Product Increments, Milestones, and Releases using the
project-wide roadmap.

The review shall identify, where applicable:

* work that is behind plan;
* unresolved dependencies or blockers;
* Product Increments at risk;
* milestone or release deviations; and
* issues requiring escalation.


Dashboards
^^^^^^^^^^

GitHub Project insights and charts are used to provide aggregated views of
project progress and work-item status.

Dashboards complement the underlying Issues and GitHub Projects and may be used
to monitor trends, open work, completion status, and progress towards upcoming
milestones and releases.


Escalation
----------

Issues shall initially be resolved within the organizational unit responsible
for the affected work.

If an issue cannot be resolved at that level, it shall be escalated according
to the project organization:

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

Project planning, organizational, resource, or schedule topics shall be
escalated through the applicable project management governance structure.

Escalations that affect project scope, milestones, releases, or organizational
responsibilities shall be documented in the corresponding project records and,
where further work is required, represented by an appropriate GitHub Issue.
