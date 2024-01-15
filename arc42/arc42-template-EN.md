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

Describes the relevant requirements and the driving forces that software
architects and development team must consider. These include

-   underlying business goals,

-   essential features,

-   essential functional requirements,

-   quality goals for the architecture and

-   relevant stakeholders and their expectations

## Requirements Overview

<div class="formalpara-title">

**Contents**

</div>

Short description of the functional requirements, driving forces,
extract (or abstract) of requirements. Link to (hopefully existing)
requirements documents (with version number and information where to
find it).

<div class="formalpara-title">

**Motivation**

</div>

From the point of view of the end users a system is created or modified
to improve support of a business activity and/or improve the quality.

<div class="formalpara-title">

**Form**

</div>

Short textual description, probably in tabular use-case format. If
requirements documents exist this overview should refer to these
documents.

Keep these excerpts as short as possible. Balance readability of this
document with potential redundancy w.r.t to requirements documents.

See [Introduction and Goals](https://docs.arc42.org/section-1/) in the
arc42 documentation.

## Quality Goals

<div class="formalpara-title">

**Contents**

</div>

The top three (max five) quality goals for the architecture whose
fulfillment is of highest importance to the major stakeholders. We
really mean quality goals for the architecture. Don’t confuse them with
project goals. They are not necessarily identical.

Consider this overview of potential topics (based upon the ISO 25010
standard):

![Categories of Quality
Requirements](images/01_2_iso-25010-topics-EN.drawio.png)

<div class="formalpara-title">

**Motivation**

</div>

You should know the quality goals of your most important stakeholders,
since they will influence fundamental architectural decisions. Make sure
to be very concrete about these qualities, avoid buzzwords. If you as an
architect do not know how the quality of your work will be judged…

<div class="formalpara-title">

**Form**

</div>

A table with quality goals and concrete scenarios, ordered by priorities

## Stakeholders

<div class="formalpara-title">

**Contents**

</div>

Explicit overview of stakeholders of the system, i.e. all person, roles
or organizations that

-   should know the architecture

-   have to be convinced of the architecture

-   have to work with the architecture or with code

-   need the documentation of the architecture for their work

-   have to come up with decisions about the system or its development

<div class="formalpara-title">

**Motivation**

</div>

You should know all parties involved in development of the system or
affected by the system. Otherwise, you may get nasty surprises later in
the development process. These stakeholders determine the extent and the
level of detail of your work and its results.

<div class="formalpara-title">

**Form**

</div>

Table with role names, person names, and their expectations with respect
to the architecture and its documentation.

| Role/Name   | Contact        | Expectations       |
|-------------|----------------|--------------------|
| *\<Role-1>* | *\<Contact-1>* | *\<Expectation-1>* |
| *\<Role-2>* | *\<Contact-2>* | *\<Expectation-2>* |

<div style="page-break-after: always;"></div>

# Architecture Constraints

<div class="formalpara-title">

**Contents**

</div>

Any requirement that constraints software architects in their freedom of
design and implementation decisions or decision about the development
process. These constraints sometimes go beyond individual systems and
are valid for whole organizations and companies.

<div class="formalpara-title">

**Motivation**

</div>

Architects should know exactly where they are free in their design
decisions and where they must adhere to constraints. Constraints must
always be dealt with; they may be negotiable, though.

<div class="formalpara-title">

**Form**

</div>

Simple tables of constraints with explanations. If needed you can
subdivide them into technical constraints, organizational and political
constraints and conventions (e.g. programming or versioning guidelines,
documentation or naming conventions)

See [Architecture Constraints](https://docs.arc42.org/section-2/) in the
arc42 documentation.

<div style="page-break-after: always;"></div>

# System Scope and Context

<div class="formalpara-title">

**Contents**

</div>

System scope and context - as the name suggests - delimits your system
(i.e. your scope) from all its communication partners (neighboring
systems and users, i.e. the context of your system). It thereby
specifies the external interfaces.

If necessary, differentiate the business context (domain specific inputs
and outputs) from the technical context (channels, protocols, hardware).

<div class="formalpara-title">

**Motivation**

</div>

The domain interfaces and technical interfaces to communication partners
are among your system’s most critical aspects. Make sure that you
completely understand them.

<div class="formalpara-title">

**Form**

</div>

Various options:

-   Context diagrams

-   Lists of communication partners and their interfaces.

See [Context and Scope](https://docs.arc42.org/section-3/) in the arc42
documentation.

## Business Context

<div class="formalpara-title">

**Contents**

</div>

Specification of **all** communication partners (users, IT-systems, …)
with explanations of domain specific inputs and outputs or interfaces.
Optionally you can add domain specific formats or communication
protocols.

<div class="formalpara-title">

**Motivation**

</div>

All stakeholders should understand which data are exchanged with the
environment of the system.

<div class="formalpara-title">

**Form**

</div>

All kinds of diagrams that show the system as a black box and specify
the domain interfaces to communication partners.

Alternatively (or additionally) you can use a table. The title of the
table is the name of your system, the three columns contain the name of
the communication partner, the inputs, and the outputs.

**\<Diagram or Table>**

**\<optionally: Explanation of external domain interfaces>**

## Technical Context

<div class="formalpara-title">

**Contents**

</div>

Technical interfaces (channels and transmission media) linking your
system to its environment. In addition a mapping of domain specific
input/output to the channels, i.e. an explanation which I/O uses which
channel.

<div class="formalpara-title">

**Motivation**

</div>

Many stakeholders make architectural decision based on the technical
interfaces between the system and its context. Especially infrastructure
or hardware designers decide these technical interfaces.

<div class="formalpara-title">

**Form**

</div>

E.g. UML deployment diagram describing channels to neighboring systems,
together with a mapping table showing the relationships between channels
and input/output.

**\<Diagram or Table>**

**\<optionally: Explanation of technical interfaces>**

**\<Mapping Input/Output to Channels>**

<div style="page-break-after: always;"></div>

# Solution Strategy

<div class="formalpara-title">

**Contents**

</div>

A short summary and explanation of the fundamental decisions and
solution strategies, that shape system architecture. It includes

-   technology decisions

-   decisions about the top-level decomposition of the system, e.g.
    usage of an architectural pattern or design pattern

-   decisions on how to achieve key quality goals

-   relevant organizational decisions, e.g. selecting a development
    process or delegating certain tasks to third parties.

<div class="formalpara-title">

**Motivation**

</div>

These decisions form the cornerstones for your architecture. They are
the foundation for many other detailed decisions or implementation
rules.

<div class="formalpara-title">

**Form**

</div>

Keep the explanations of such key decisions short.

Motivate what was decided and why it was decided that way, based upon
problem statement, quality goals and key constraints. Refer to details
in the following sections.

See [Solution Strategy](https://docs.arc42.org/section-4/) in the arc42
documentation.

<div style="page-break-after: always;"></div>

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
