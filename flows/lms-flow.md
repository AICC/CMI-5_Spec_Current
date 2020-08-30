## cmi5 Implementation Flow for an LMS

The chart below provide a high-level description of the execution flow for an implementing cmi5 in an LMS. Each of the shapes in the chart are further explained (below the chart).

![](./lms-flow-chart.png?raw=true)


**Import Course Structure**

  - There are 3 import scenarios:
      - ZIP file with media & manifest
      - ZIP file with manifest only (referencing media)
      - manifest only (referencing media)

  - Copy media (if present in Zip file) and read manifest (cmi5.xml) file
  - Get content metadata (URLs, Titles, launch parameters)
  - Get content hierarchy (content grouped in blocks)
  - Get course/block completion rules (called "**moveOn**" criteria)

*See Sections:*
   - [6.1 Course Structures](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#course_structures)
   - [13.0 Course Structure Data Requirements](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#course_requirements)
   - [14.0 Course Package](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#course_package)

**Assign Enrollment**

   - Create a unique registration id for each learner enrollment in the course.

*See Sections:*

   - [3.0 Definitions -- *Registration*](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#definitions)
   - [8.1 Launch Method](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#launch_method)

**Check (initial) moveOn Rules**

Upon enrollment the LMS needs to determine if any content (AU's) has a default value for moveOn or is set to "NotApplicable". This will result in

   - Individual AU's being set to "Satisfied" (moveOn rule met)
   - Entire course being set to "Satisfied" (moveOn rule met) if all AU's Satisfied

It should also be noted that course developers may unintentionally create courses with all default settings that are automatically (completely) satisfied on enrollment. (See Common Mistakes (\#4) - <http://aicc.github.io/CMI-5_Spec_Current/mistakes/> )

*See Sections:*
   - [13.1.4 AU Metadata - moveOn](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#au_meta_data)
   - [9.3.9 Satisfied](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#verbs_satisfied)

**Determine Launch Mode**

Your LMS may have business rules for the following learner scenarios:
   - Launch content initially
   - Re-entering unfinished content
   - Reviewing Content that has previously been completed
   - Previewing Content (without being evaluation)

Prior to launching content, you will need to create a "state document" specific to the launch. Based on each scenario you will need to set the launchMode (in the state document) to the correct value (Normal, Review, or Browse).

*See Sections:*
   - [10.0 xAPI State Data Model](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#xapi_state)

**Prepare for Launch**

LMS must create a state document with launch parameters. *See Section - [10.0 xAPI State Data Model](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#xapi_state)*

LMS must create an agent profile document with learner language preference specified (and may provide an audio on/off preference also). *See Section -[11.0 xAPI Agent Profile Data Model](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#xapi_agent_profile)*

LMS sends Launched Statement. *See Section [9.3.1 Launched](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#verbs_launched)*

LMS issues an abandoned statement for previously launched AU sessions that were "abnormally" terminated. *See Section - [9.3.6 Abandoned](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#verbs_abandoned)*


**Content Launch**

LMS must have a service (Fetch URL) to provide an authentication token for access to the LRS. *See Section - [8.2 Authorization Token Fetch URL](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#fetch_url).*

LMS creates a URL launch line with LRS connect string parameters (including a reference to the Fetch URL). *See Section - [8.1 Launch Method](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#launch_method).*

The LMS launches the content using one of the following methods:
   1. Redirects the Browser window to the launch URL
   2. Redirect to an iFrame to the launch URL
   3. Spawns a new window

*See Section [13.1.4 AU Metadata - launchMethod](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#au_meta_data)*

**Evaluate AU Output**



LMS Evaluates Statements from the AU session for conformance to the rules (as they are sent to the LRS)

   - Check for Initialize/Terminate
   - Validate cmi5 defined statement rules
   - Valid cmi5 allowed statement requirements
   - Check for Post terminate statements

LMS detects AU exit (e.g. return URL / Window Close)

*See Sections:*

   - [7.1.3 Types of Statements](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#type_statement_au)
   - [9.3 Verbs](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#verbs)

**AU Satisfied (verify MoveOn criteria)**

LMS checks if moveOn criteria was met for the AU (As set by the LMS in the State document).

*See Sections:*
   - [10.0 xAPI State Data Model -- moveOn](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#xapi_state)
   - [13.1.4 AU Metadata -- moveOn](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#au_meta_data)

**Block Satisfied (verify MoveOn criteria)**

LMS checks other AUs and Block within the current block to determine if the block is satisfied (per the moveOn criteria defined in the course structure).

This includes traversing the hierarchy for nested blocks.

*See Sections:*
   - [9.3.9 Satisfied](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#verbs_satisfied)
   - [13.1.2 Block Metadata](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#block_meta_data)

**Course Satisfied**

LMS verifies that all Blocks and their children are satisfied and that any AU's at the root level of the course are completed.

*See Sections:*
   - [9.3.9 Satisfied](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#verbs_satisfied)
