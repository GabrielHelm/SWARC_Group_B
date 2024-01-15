# 

**About arc42**

arc42, the template for documentation of software and system
architecture.

Template Version 8.2 EN. (based upon AsciiDoc version), January 2023

Created, maintained and © by Dr. Peter Hruschka, Dr. Gernot Starke and
contributors. See <https://arc42.org>.

<div class="note">

This version of the template contains some help and explanations. It is
used for familiarization with arc42 and the understanding of the
concepts. For documentation of your own system you use better the
*plain* version.

</div>

<div style="page-break-after: always;"></div>

# Introduction and Goals

This document describes the university management application AcademiX.
It is used to provide students, faculty and staff with the ability to manage 
their academic, administrative, and financial activities.
The application will integrate with the university's existing student 
information system and financial management system.

## Requirements Overview

<div class="formalpara-title">

**Main features ([Business Requirements Document: Section 4. Features](../materials/university%20managment/brd.md))**
- User authentication and authorization
- Dashboard with relevant information and alerts
- Course and curriculum management
- Enrollment management
- Attendance tracking and reporting
- Grading and transcript management
- Billing and payment management
- Reporting and analytics

The application must handle approximately 35.000 total and approximately 
5.000 concurrent users. The system should be able to keep track of
5-10 courses per student in the span of one semester, storing all course 
information and attendance. Furthermore, the application should enable
users to make data-driven decision through reporting and analytics.

A [use case document](../materials/university%20managment/use%20case%20document.md)
can be found in the specification of the university management project.

## Quality Goals 

The top three quality goals for the architecture whose fulfillment is of 
the highest importance to the major stakeholders can be found in the following table. 
The quality characteristics are selected in accordance with the ISO 25010 standard.

| Priority | Quality           | Motivation                                                                    |
|----------|-------------------|-------------------------------------------------------------------------------|
| *1*      | *Reliability*     | *The current system is prone to human errors, and this should be improved*    |
| *2*      | *Usability*       | *The application should make processes more efficient and save time*          |
| *3*      | *Maintainability* | *Specific requirements are expected to change during the lifetime of the app* |

The complete overview of quality scenarios can be found in section [Quality Scenarios](#quality-scenarios).

## Stakeholders

The following table lists all important stakeholder and their expectations
from the AcademiX project.

| Name            | Role                        | Expectations                                                                                          |
|-----------------|-----------------------------|-------------------------------------------------------------------------------------------------------|
| *John Smith*    | *University Administrator*  | *Provide an efficient and user-friendly platform for managing academic and administrative activities* |
| *Jane Doe*      | *Senior Lecturer*           | *Efficient management (schedules, notifications, etc.), one application instead of multiple systems*  |
| *Michael Lee*   | *Chief Information Officer* | *Enable data-driven decision making through reporting and analytics*                                  |
| *Emily Chen*    | *Student Representative*    | *Enhance communication and collaboration among students*                                              |
| *Sarah Johnson* | *Financial Officer*         | *Streamline billing and payment processes and guarantee security*                                     |

The stakeholders have been taken from [Business Requirements Document: Section 6. Sign-off](../materials/university%20managment/brd.md)

# Architecture Constraints

<div class="formalpara-title">

AcademiX shall be:
- platform-independent and should be accessible from all common web browsers (e.g. Chrome, Safari, Edge, Firefox and Samsung Internet), Android and iOS devices
- developed using modern web development technologies such as React, Node.js, and MongoDB
- hosted on a secure and scalable cloud infrastructure such as AWS or Azure
- integrated with the university's existing student information system and financial management system
- compiling with applicable data protection and privacy regulations
- verified by using automated tests
- operating within a predetermined monthly cloud budget
- presenting no barriers to people with physical disabilities

Taken from [Business Requirements Document: Section 5. Assumptions and Dependencies](../materials/university%20managment/brd.md)

# System Scope and Context

The following diagram shows the business and technical context of the system.
More information can be found in the section:
- [Context](#context)

![context_diagram](../materials/images/context_diagram.drawio.png)

# Context

In the following table users have been split up into students, 
faculty members and professors.

| Communication Partner         | Inputs                                                                          | Outputs                                                            | Interfaces                                 | Protocols/Formats |
|-------------------------------|---------------------------------------------------------------------------------|--------------------------------------------------------------------|--------------------------------------------|-------------------|
| Students                      | Course selections, personal data, assignment submissions, feedback and payments | Course materials, schedules, grades, billing information           | Browser, Web Server                        | HTTPS             |
| Professors                    | Course content, grades, attendance records and feedback                         | Schedule updates, administrative reports, student performance data | Faculty portal, academic databases         | HTTPS             |
| Faculty members               | Course information, financial data and timetable override information           | Enrollment reports, financial reports, timetable                   | Administrative dashboard                   | HTTPS             |
| IT Administrator              | System updates, security patches, user feedback                                 | System status reports, performance metrics                         | IT management tools                        | HTTPS, SSH        |
| External Educational Partners | Course data, enrollment information                                             | Joint program details, transfer credit information                 | Partner portals, data interchange services | API               |
| Student Information System    | Student personal information                                                    | Student personal information                                       | Standardised interface to parse data       | API               |
| Financial System              | Financial information                                                           | Financial information                                              | Standardised interface to parse data       | API               |
| Directory Server              | User data                                                                       | all object related data                                            | LDAP Interface for authentication          | LDAP              |

# Solution Strategy

| Goal/Requirements                                | Architectural Approach                       | Details |
|--------------------------------------------------|----------------------------------------------|---------|
| *Authenticate and authorize users*               | *Dedicated server (LDAP)*                    | **      |
| *Course and curriculum management*               | *Multi-tier system (Clients, REST, API, DB)* | **      |
| *Dashboard with relevant information and alerts* | *Web-app (React framework)*                  | **      |
| *Rapid scalability*                              | *Cloud Hosting (AWS)*                        | **      |
| *Data security and integrity*                    | *Secure Communication Protocols (HTTPS)*     | **      |
| *Quality assurance*                              | *Automated Testing and CI/CD*                | **      |

# 5. Building Block View

<div class="formalpara-title">
This overview visualizes the most important components and their dependencies of the application as black boxes:

<div style="margin:25px;">

![Diagram showing the Building Block View Level-1.](images\5_building_block_lvl1.png "Building Block View Level-1")

</div>

**Motivation**  
The building block overview (level 1) is based on the decomposition of the application in self-contained subsystems that are each focused on specific business functionalities. Additionally, the relationships with users (students and administrators) and external systems (student information system and financial system) are represented.  


**Contained Building Blocks**  
This table describes the black boxes from level 1:

| **Name**         | **Responsibility** |
|------------------|--------------------|
| **Web Server** |  Handling client requests and delivering content.         |
| **Core Component** |  Connecting and coordinating services.         |
| **Timetable Service** |  Management of timetables.         |
| **Course Service** |  Management of courses.         |
| **Grade Service** |  Management of grades.         |
| **Database** |  Persistent storage of data.         |
| **Directory Server** |  Storing user information and validating actions.         |      |

**Important Interfaces**  
AcademiX depends on and integrates with two external systems: the student information system and the financial system. Interactions with these systems are described by and must follow the respective specification.    

# 6. Runtime View
This section describes concrete behavior and interactions of the
system’s building blocks in form of scenarios.

## Runtime Scenario 1: Generate grade report

<div style="margin:25px;">

![Diagram showing sequence of events when student requests report.](images\6_runtime_view_report_sequence.png "Runtime View Scenario 1")

</div>

**Description**

<div style="page-break-after: always;"></div>

# 7. Deployment View

This section describes the technical infrastructure used to execute the system and the mapping of software components to those infrastructure elements.

**Infrastructure Level 1**  
This is a description of the top-level infrastructure in the system:

<div style="margin:25px;">

![Diagram showing top-level infrastructure elements.](images\7_deployment_view_lvl1.png "Deployment View Level 1")

</div>

**Motivation**  
The diagram shows the different hardware devices that execute the distributed application. This overview represents the top-level infrastructure in the system and serves as a guide to all the system's part.  

**Quality and/or Performance Features**  
The entire system utilizes virtualized devices which is enabled by the AWS Infrastructure as a Service. 

**Mapping of Building Blocks to Infrastructure**  
The following table represents a mapping of the level 1 infrastructure units to software components:

| **Node**         | **Artifact** | **Description** |
|------------------|--------------------|--------------------|
| Browser                    | None |Recent version of Chrome, Firefox, Safari, etc. |
| Web Server                 | Nginx |Handles client requests and serves content |
| Directory Server           | OpenLDAP |Stores user information and validates actions |
| App Core                   | academix-core.jar |Central application component  |
| DB Server                  | MongoDB |Persistent NoSQL storage |
| Timetable Service          | academix-timetable.jar |Microservice for timetable management |
| Course Service             | academix-course.jar |Microservice for course management |
| Grade Service              | academix-grade.jar |Microservice for grade management |
| Student Information Access | Interface to external service |Transforms incoming/outgoing data to specific format|
| Financial Access           | Interface to external service |Transforms incoming/outgoing data to specific format |

<div style="page-break-after: always;"></div>

# 8. Cross-cutting Concepts

The following section describes aspects of the application that affect multiple components and can, therefore, not be associated with individual modules.

**Concept 1: Logging**  
All components of the application must log events using the same pattern. The production environment is required to log at the level "INFO" and beyond. These logs must be managed by a monitoring system and events with serious consequences must notify relevant staff members. 


**Concept 2: Synchronization**  
The application mediates between users (students and staff) and an external information source (the student information system).  
The database is required to be consistent with the information received by the student information system and changes to relevant information received from users (e.g.: personal information change by student) must be relayed to the external system.

**Concept 3: Privacy and Compliance**  
The application must be compliant with relevant legal obligations, especially concerning privacy. This includes the General Data Protection Regulation as well as University bylaws.

<div style="page-break-after: always;"></div>

# Architecture Decisions

<div class="formalpara-title">

**Contents**

</div>

Important, expensive, large scale or risky architecture decisions
including rationales. With "decisions" we mean selecting one alternative
based on given criteria.

Please use your judgement to decide whether an architectural decision
should be documented here in this central section or whether you better
document it locally (e.g. within the white box template of one building
block).

Avoid redundancy. Refer to section 4, where you already captured the
most important decisions of your architecture.

<div class="formalpara-title">

**Motivation**

</div>

Stakeholders of your system should be able to comprehend and retrace
your decisions.

<div class="formalpara-title">

**Form**

</div>

Various options:

-   ADR ([Documenting Architecture
    Decisions](https://cognitect.com/blog/2011/11/15/documenting-architecture-decisions))
    for every important decision

-   List or table, ordered by importance and consequences or:

-   more detailed in form of separate sections per decision

See [Architecture Decisions](https://docs.arc42.org/section-9/) in the
arc42 documentation. There you will find links and examples about ADR.

<div style="page-break-after: always;"></div>

# Quality Requirements

<div class="formalpara-title">

**Content**

</div>

This section contains all quality requirements as quality tree with
scenarios. The most important ones have already been described in
section 1.2. (quality goals)

Here you can also capture quality requirements with lesser priority,
which will not create high risks when they are not fully achieved.

<div class="formalpara-title">

**Motivation**

</div>

Since quality requirements will have a lot of influence on architectural
decisions you should know for every stakeholder what is really important
to them, concrete and measurable.

See [Quality Requirements](https://docs.arc42.org/section-10/) in the
arc42 documentation.

## Quality Tree

<div class="formalpara-title">

**Content**

</div>

The quality tree (as defined in ATAM – Architecture Tradeoff Analysis
Method) with quality/evaluation scenarios as leafs.

<div class="formalpara-title">

**Motivation**

</div>

The tree structure with priorities provides an overview for a sometimes
large number of quality requirements.

<div class="formalpara-title">

**Form**

</div>

The quality tree is a high-level overview of the quality goals and
requirements:

-   tree-like refinement of the term "quality". Use "quality" or
    "usefulness" as a root

-   a mind map with quality categories as main branches

In any case the tree should include links to the scenarios of the
following section.

## Quality Scenarios

<div class="formalpara-title">

**Contents**

</div>

Concretization of (sometimes vague or implicit) quality requirements
using (quality) scenarios.

These scenarios describe what should happen when a stimulus arrives at
the system.

For architects, two kinds of scenarios are important:

-   Usage scenarios (also called application scenarios or use case
    scenarios) describe the system’s runtime reaction to a certain
    stimulus. This also includes scenarios that describe the system’s
    efficiency or performance. Example: The system reacts to a user’s
    request within one second.

-   Change scenarios describe a modification of the system or of its
    immediate environment. Example: Additional functionality is
    implemented or requirements for a quality attribute change.

<div class="formalpara-title">

**Motivation**

</div>

Scenarios make quality requirements concrete and allow to more easily
measure or decide whether they are fulfilled.

Especially when you want to assess your architecture using methods like
ATAM you need to describe your quality goals (from section 1.2) more
precisely down to a level of scenarios that can be discussed and
evaluated.

<div class="formalpara-title">

**Form**

</div>

Tabular or free form text.

<div style="page-break-after: always;"></div>

# Risks and Technical Debts

<div class="formalpara-title">

**Contents**

</div>

A list of identified technical risks or technical debts, ordered by
priority

<div class="formalpara-title">

**Motivation**

</div>

“Risk management is project management for grown-ups” (Tim Lister,
Atlantic Systems Guild.)

This should be your motto for systematic detection and evaluation of
risks and technical debts in the architecture, which will be needed by
management stakeholders (e.g. project managers, product owners) as part
of the overall risk analysis and measurement planning.

<div class="formalpara-title">

**Form**

</div>

List of risks and/or technical debts, probably including suggested
measures to minimize, mitigate or avoid risks or reduce technical debts.

See [Risks and Technical Debt](https://docs.arc42.org/section-11/) in
the arc42 documentation.

<div style="page-break-after: always;"></div>

# Glossary

<div class="formalpara-title">

**Contents**

</div>

The most important domain and technical terms that your stakeholders use
when discussing the system.

You can also see the glossary as source for translations if you work in
multi-language teams.

<div class="formalpara-title">

**Motivation**

</div>

You should clearly define your terms, so that all stakeholders

-   have an identical understanding of these terms

-   do not use synonyms and homonyms

A table with columns \<Term> and \<Definition>.

Potentially more columns in case you need translations.

See [Glossary](https://docs.arc42.org/section-12/) in the arc42
documentation.

| Term        | Definition        |
|-------------|-------------------|
| *\<Term-1>* | *\<definition-1>* |
| *\<Term-2>* | *\<definition-2>* |
