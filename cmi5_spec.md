  
<p>
<p align=center><img src="https://cloud.githubusercontent.com/assets/1656316/9965238/bc9deb2c-5de9-11e5-9954-63aa03873f88.png" align=center></p>

# cmi5 Specification Profile for xAPI


---

## Table of Contents

[__Revision History__](#revhistory)

[__Contributors__](#contributors)

* [__1.0 Overview__](#overview)
  * [1.1 Scope](#scope)
* [__2.0 References__](#references)
* [__3.0 Definitions__](#definitions)
  * [3.1 Abbreviations and Acronyms](#acronyms)
* [__4.0 Conformance__](#conformance)
  * [4.1 Assignable Unit (AU)](#au_conformance)
  * [4.2 Learning Management Systems (LMS)](#lms_conformance)
  * [4.3 Optional JSON Values](#json_conformance)
  * [4.4 Courses](#course_conformance)
* [__5.0 Conceptual Model: Informative__](#concept)
* [__6.0 LMS Requirements__](#lms_requirements)
  * [6.1 Course Handling Requirements](#course_structures)
  * [6.2 LMS State API Requirements](#lms_state_api_requirements)
  * [6.3 LMS Statement API Requirements](#lms_statement_api_requirements)
* [__7.0 AU Requirements__](#au_requirements)
  * [7.1 AU Statement API Requirements](#au_statement_api_requirements)
      * [7.1.1 First Statement API Call](#first_statement_au)
      * [7.1.2 Last Statement Call](#last_statement_au)
      * [7.1.3 Types of Statements](#type_statement_au)
* [__8.0 Content Launch Mechanisms__](#content_launch)
  * [8.1 Launch Method](#launch_method)
  * [8.2 Authorization Token Fetch URL](#fetch_url)
      * [8.2.1 Overview](#fetch_url_overview)
      * [8.2.2 Definition: auth-token](#definition_auth_token)
      * [8.2.3 Errors](#fetch_url_errors)
          * [8.2.3.1 Duplicate call to fetch URL](#duplicate_call_to_fetch_url)
          * [8.2.3.2 Error Values](#fetch_url_error_values)
  * [8.3 Other Launch Environments](#other_environment)
* [__9.0 xAPI Statement Data Model__](#xapi_data_model)
  * [9.1 Statement ID](#statement_id)
  * [9.2 Actor](#actor)
  * [9.3 Verbs](#verbs)
      * [9.3.1 Launched](#verbs_launched)
      * [9.3.2 Initialized](#verbs_initialized)
      * [9.3.3 Completed](#verbs_completed)
      * [9.3.4 Passed](#verbs_passed)
      * [9.3.5 Failed](#verbs_failed)
      * [9.3.6 Abandoned](#verbs_abandoned)
      * [9.3.7 Waived](#verbs_waived)
      * [9.3.8 Terminated](#verbs_terminated)
      * [9.3.9 Satisfied](#verbs_satisfied)
  * [9.4 Object](#object)
  * [9.5 Result](#result)
      * [9.5.1 Score](#score)
      * [9.5.2 Success](#success)
      * [9.5.3 Completion](#completion)
      * [9.5.4 Duration](#duration)
          * [9.5.4.1 AU statements that include duration](#au_statements_that_include_duration)
          * [9.5.4.2 LMS statements that include duration](#lms_statements_that_include_duration)
      * [9.5.5 Extensions](#result_extensions)
          * [9.5.5.1 progress](#result_extensions_progress)
          * [9.5.5.2 reason](#result_extensions_reason)
  * [9.6 Context](#context)
      * [9.6.1 Registration](#registration)
      * [9.6.2 ContextActivities](#context_activities)
          * [9.6.2.1 cmi5 Category Activity](#context_activities_category_cmi5)
          * [9.6.2.2 moveOn Category Activity](#context_activities_category_moveon)
          * [9.6.2.3 Publisher ID Grouping Activity](#context_activities_grouping_publisherid)
      * [9.6.3 Extensions](#extensions)
          * [9.6.3.1 session ID](#context_extensions_session_id)
          * [9.6.3.2 masteryScore](#context_extensions_masteryScore)
          * [9.6.3.3 launchMode](#context_extensions_launchMode)
          * [9.6.3.4 launchURL](#context_extensions_launchURL)
          * [9.6.3.5 publisherId](#context_extensions_publisherid)
          * [9.6.3.6 moveOn](#context_extensions_moveOn)
          * [9.6.3.7 launchParameters](#context_extensions_launchParameters)
  * [9.7 Timestamp](#timestamp)
* [__10.0 xAPI State Data Model__](#xapi_state)
* [__11.0 xAPI Agent Profile Data Model__](#xapi_agent_profile)
  * [11.1 languagePreference](#language_preference)
  * [11.2 audioPreference](#audio_preference)
* [__12.0 xAPI Activity Profile Data Model__](#xapi_activity_profile)
* [__13.0 Course Structure Data Requirements__](#course_requirements)
  * [13.1 Course Structure Data Model](#course_structure_data_model)
    * [13.1.1 Course Level Metadata](#course_level_meta_data)
    * [13.1.2 Block Metadata](#block_meta_data)
    * [13.1.3 Objective Metadata](#objective_meta_data)
    * [13.1.4 AU Metadata](#au_meta_data)
    * [13.1.5 Vendor Specific Metadata (Extensions)](#vendor_meta_data)
  * [13.2 Course Structure XSD](#course_structure_xsd)
* [__14.0 Course Package__](#course_package)
  * [14.1 Course Packages in ZIP Format](#course_packages_in_zip_format)
  * [14.2 Course Structure XML Without a ZIP File Package](#course_structure_xml_without_a_zip_file_package)
* [__15.0 Course Structure Examples__](#course_structure_examples)
  * [15.1 Simple](#course_structure_examples_simple)
  * [15.2 Complex](#course_structure_examples_complex)
  * [15.3 Extension](#course_structure_examples_extension)

[__License Agreement__](#license_agreement)

------

<a name="revhistory"></a>
## Revision History

Versioning in the cmi5 specification is managed in the following manner:
 * _Major Version_ – Stones (Sandstone, Quartz, etc.) – Major changes in functionality
 * _Minor Version_ – Editions (1st edition, 2nd edition, etc.) – Minor changes in functionality.
 * _Errata_ – Minor corrections that do not affect functionality are not versioned.  (See GitHub repository for specific revision history)

The versions of this specifcation are as follows:

__Quartz - 1st Edition (June 1, 2016)__

__Sandstone - 1st Edition (May 15, 2015):__

* Developer release

__Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__

* Converted existing working draft to markdown format from Microsoft Word. All previous work from 2012 discarded.


<a name="contributors"></a> 
## Contributors

| Name:                | Organization:                          |
|----------------------|----------------------------------------|
| Ed Cohen             | AICC Infrastructure Subcommittee Chair |
| Aaron Silvers        | ADL                                    |
| Jonathan Poltrack    | ADL                                    |
| Andy Johnson         | ADL                                    |
| Tom Creighton        | ADL                                    |
| Nik Hruska           | ADL                                    |
| Avron Barr           | The LETSI Foundation                   |
| Mike Rustici         | Rustici Software                       |
| Ben Clark            | Rustici Software                       |
| Megan Bowe           | Rustici Software                       |
| Andrew Downes        | Rustici Software                       |
| Brian J. Miller      | Rustici Software                       |
| Jacques Talvard      | Airbus                                 |
| Bill McDonald        | Boeing                                 |
| Ray Lowery           | Pratt &amp; Whitney                    |
| Dennis Hall          | Learning Templates                     |
| John Kleeman         | Questionmark                           |
| Kris Rockwell        | Hybrid Learning Systems                |
| Paul Roberts         | Questionmark                           |
| Christopher Reynolds | Pelesys                                |
| Mingrui Zheng        | Pelesys                                |
| Chris Sawwa          | Meridian Knowledge Systems             |
| Michael Roberts      | VTraining Room                         |
| Thomas Person        | (Formerly of Adobe)                    |
| Art Werkenthin       | RISC,Inc                               |
| Severin Neumann      | die eLearning AG                       |
| Chris Amyot          | ICOM Productions, Inc.                 |
| David Pesce          | Exputo Inc.                            |
| Henry Ryng           | inXsol                                 |
| Chris Handorf        | Pearson                                |
| Jamie Burns          | Virtual College                        |
| Pankaj Agrawal       | Next Software Solutions                |

<a name="overview"></a>  
# 1.0 Overview


This specification describes interoperable runtime communication between Learning Management Systems
(LMS) and Assignable Units (AU).

<a name="scope"></a>  
## 1.1 Scope

The scope of this specification is limited to the following:

* Launch by an LMS of AUs.
* Launch and runtime environment used by LMS and AUs.
* Runtime communication data and data transport between the LMS and AUs. 
* LMS course definition as it pertains to runtime data used by AUs.
* LMS Course Structure Import/Export.
* Reporting requirements for the LMS.

This specification references how to use the xAPI specification within this scope.

Other uses of the xAPI specification are outside of this scope.

Uses of activities not explicitly defined above are outside of the scope of this specification.


<a name="references"></a> 
# 2.0  References

The following referenced documents are indispensable for the application of this specification. 

* Internationalized Resource Identifiers (IRIs): IRI Syntax January 2005<br>
https://www.ietf.org/rfc/rfc3987.txt
* "Experience API", version 1.0.x (subject to change just prior to release), ADL<br>
https://github.com/adlnet/xAPI-Spec/blob/xAPI-1.0.2/xAPI.md
* cmi5 Course Structure, Sandstone 1st Edition (merged into this document)<br>
* MIME Types<br>
http://www.iana.org/assignments/media-types/index.html
* Extensible Markup Language (XML)<br>
http://www.w3.org/XML
* The JSON Data Interchange Format<br>
http://json.org/
* ISO/IEC 21320-1:2015(en) Information technology — Document Container File — Part 1: Core (Commonly called ZIP file format):<br>https://www.iso.org/obp/ui/#iso:std:iso-iec:21320:-1:ed-1:v1:en

<a name="definitions"></a>   
# 3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user who manages the LMS and related systems. This user performs tasks such as learner enrollment, course structure definition, and report management.

* __Activity__: In this specification it is representative of an AU or the Object of a statement with objectType of “Activity”. Thus the granularity can be anything from a single AU course down to a specific interaction.

* __Assignable Unit (AU)__:  A learning content presentation launched from an LMS. The AU is the unit of tracking and management. The AU collects data on the learner and sends it to the LMS.

* __Block__: A grouping of AU's and other Blocks (nesting).

* __Course__: A collection of assignable units, in a logical grouping, of learning content. A course is typically an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied sequence, representing a course.  

* __Experience API (xAPI)__: A runtime data communication specification for learning content (AU) to send and receive data to a Learning Record Store (LRS).  The xAPI specification referenced by this document is used to define the data transport and the data model.

* __Internationalized Resource Identifier (IRI)__: A unique identifier according to RFC 3987. The IRI may be an IRL. IRLs SHOULD be defined within a domain controlled by the person creating the IRL. Note that IRI’s in this spec MUST be fully qualified and not IRI References.

* __Internationalized Resource Locator (IRL)__: According to the xAPI specification, an IRL is an IRI that, when translated into a URI (according to the IRI to URI rules), is a URL.

* __Learner__: The end user viewing/using the learning content (AUs).

* __Learning Management System (LMS)__: A computer system that may include the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners' progress. LMS launching, reporting, and tracking roles are the focus of the cmi5 specification. The LMS is integrated with an LRS. In the remainder of this document the term “LMS” refers to an integrated entity of LMS and LRS.

* __Learning Records Store (LRS)__: As defined in the xAPI specification.

* __Registration__: An enrollment instance of a learner in a course. (a registration ID uniquely identifies this). The registration ID persists throughout the course progress to completion and during review of a completed course. A new registration is created for new enrollment instances (such as recurrent courses or re-taking courses).

* __Session__: A period of time marked by the launch of an AU until its termination (or abandonment).

<a name="acronyms"></a> 
## 3.1 Abbreviations and Acronyms
<br>
__ADL__: Advanced Distributed Learning<br>
__AICC__: Aviation Industry Computer-Based Training Committee<br>
__API__: Application Programming Interface<br>
__CMI__: Computer Managed Instruction<br>
__JSON__: JavaScript Object Notation<br>
__IRI__: Internationalized Resource Identifier<br>
__IRL__: Internationalized Resource Locator<br>
__LMS__: Learning Management System<br>
__LRS__: Learning Record Store<br>
__PII__: Personally Identifiable Information<br>
__URI__: Uniform Resource Identifier<br>
__URL__: Uniform Resource Locator<br>
__URN__: Uniform Resource Name<br>
__xAPI__: Experience API<br>
__XML__: Extensible Markup Language<br>
__XSD__: XML Schema Definition<br>
<br>


<a name="conformance"></a>  
# 4.0  Conformance

Conformance to this specification is defined in this section. 

In this specification:
* "MUST" is to be interpreted as a requirement on an implementation.
* "MUST NOT" is to be interpreted as a prohibition.
* "SHOULD" is to be interpreted as a recommendation for implementation.
* "SHOULD NOT" is to be interpreted as the converse of "SHOULD".
* "MAY" is to be interpreted as a course of action that is permissible within the limits of the specification.
* "NEED NOT" is to be interpreted as a course of action that is not required.

Uses of the xAPI specification outside of the scope of this specification do not affect conformance with this specification.

<a name="au_conformance"></a> 
## 4.1 Assignable Unit (AU)

See Section 7 – AU Requirements. An Assignable Unit MUST conform to all requirements as specified in the xAPI specification (see References).

<a name="lms_conformance"></a> 
## 4.2 Learning Management Systems (LMS)

See Section 6 – LMS Requirements. The LMS MUST conform to all LRS requirements as specified in the xAPI specification (see References).

The LMS MUST have an account which is able to retrieve all Resource data (from the Statement API, etc, including attachments and extensions) about another distinct user across multiple sessions for that user.

<a name="json_conformance"></a> 
## 4.3 Optional JSON Values

If JSON properties are indicated as "optional", you MAY leave such properties out of the JSON structure being described.

<a name="course_conformance"></a>
## 4.4 Courses

A course MUST be bundled with course structure data that conform to all requirements listed in Section 13 and Section 14.
  
Course structure data MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  


<a name="concept"></a> 
# 5.0 Conceptual Model: Informative  

Synopsis of the cmi5 model:
* An LMS imports a course structure which contains at least one AU.  Optionally, the course structure may include one or more blocks, which consist of 1 or more AUs or nested blocks.
* An LMS administrative user assigns a course to a learner.
* A learner authenticates with an LMS or a related system.
* A learner launches an AU from the LMS or an associated launching system, using an interface.
* The LMS writes launch data to the integrated LRS.
* The AU sends a message to the LMS requesting launch parameters and previous state information.
* The learner views the AU content and performs the learning. During this time, the AU MAY request data from, and store data to, the LMS.
* The learner exits the AU.
* The AU reports the final tracking data to the LMS and issues a "terminate" statement.
* Administrative users create and view reports of the tracking data recorded by the AUs for individual learners.

Responsibilities of the Assignable Unit:
* Parse the parameters from the launching environment to determine where the LMS location is and initiate communication with the LMS.
* Acting as a "client", send and receive messages using the defined transport mechanism(s) and associated commands as prescribed in this specification.
* Format all data according to the defined data types and vocabularies that are defined in this specification.
* Send a "terminate" statement prior to terminating the AU's execution.

Responsibilities of the LMS:
* Create and maintain course structures.
* Acting as a "server", receive and reply to messages using the defined transport mechanism(s) and associated commands as prescribed in this specification.
* Format all data according to the defined data types and vocabularies that are defined in this specification.
* Launch the specified AU contained in the courses within the defined environment(s).

<a name="lms_requirements"></a>  
# 6.0 LMS Requirements

The LMS MUST:

* Implement an LRS as defined in the xAPI specification.
* Implement additional "State API" requirements to initialize the AU state as defined in Section 10.
* Implement the runtime launch interface as defined in Section 8.0.
* Implement additional xAPI "Statement API" requirements as defined in Section 9.
* Implement additional xAPI "Agent Profile API" requirements as defined in Section 11.
* Implement course handling as defined in Section 6.1.

<a name="course_structures"></a>  
## 6.1 Course Handling Requirements

* The LMS SHOULD implement a means to create, edit, and maintain course structures.
* The LMS MUST implement the import of the Course Structure defined in Section 13 and the Course Package defined in Section 14.
* The LMS SHOULD implement the export of the course data structure defined in Section 13 and the Course Package defined in Section 14.
* The LMS SHOULD provide a user interface to the LMS administrative users to create and edit course structures internally.
* The LMS MUST support course structures containing more than 1000 AUs.
* The LMS MUST support course structures conforming to the XSD schema defined in Section 13.2.


<a name="lms_state_api_requirements"></a>  
## 6.2 LMS State API Requirements
The LMS MUST implement the State API Requirements as defined in Section 10.

<a name="lms_statement_api_requirements"></a>  
## 6.3 LMS Statement API Requirements

The LMS MUST NOT provide permissions/credentials which allow the AU to issue voiding Statements.

The LMS SHOULD reject statements that conflict with the "Statement API" requirements as defined in Section 9.

The LMS MUST Void statements that are NOT rejected AND conflict with the "Statement API" requirements as defined in Section 9.

<a name="au_requirements"></a>  
# 7.0 AU Requirements

An AU MUST:

* Implement the runtime launch interface as defined in Section 8.
* Implement runtime communication as defined in the xAPI Specification.
* Implement State API requirements in this specification as defined in Section 10.
* Implement Profile API requirements in this specification as defined in Section 11.
* Implement Statement API requirements as defined in Section 7.1.

<a name="au_statement_api_requirements"></a>  
## 7.1 AU Statement API Requirements

<a name="first_statement_au"></a> 
### 7.1.1 First Statement API Call
The AU MUST issue a statement to the LRS after being launched, initialized, and ready for learner interaction using the Initialized verb as described in Section 9.3.2.

<a name="last_statement_au"></a>  
### 7.1.2 Last Statement Call
The AU MUST issue a Terminated statement to the LRS as described in Section 9.3.8 as the last statement in a session.
 
Once the AU has determined that the session will end (e.g. by user action or some other means) the AU SHOULD issue a Terminated statement.
 
 Circumstances under which the AU may determine that the session is ending could include:
 
* Monitoring for browser window or application close events
* An AU defined user action for closing the AU session
* Other AU defined events such as a timeout from user inactivity


<a name="type_statement_au"></a>  
### 7.1.3 Types of Statements
The statements issued within an AU session could fall within the following categories:

* "cmi5 defined" - Statements using cmi5 defined verbs, category id as defined in section 9.6.2.1, and context template.
* "cmi5 allowed" - Statements using any verb and cmi5 context template (but NOT including cmi5 category id as defined in section 9.6.2.1).
* "cmi5 not-allowed" - Any statements not conforming with the cmi5 specification.

"cmi5 allowed" statements posted by the AU MUST occur between cmi5 statements using the "Initialized" verb and the "Terminated" verb. "cmi5 allowed" statements are not considered in cmi5 defined session management and completion rules.

<a name="content_launch"></a>  
# 8.0 Content Launch Mechanisms

<a name="launch_method"></a>  
## 8.1 Launch Method

The AU MUST be launched by the LMS using one of the following methods, depending on the launchMethod in the Course Structure (Section 13.1.4 AU Meta Data, URL):

When the launchMethod is "OwnWindow", the LMS MUST use one of the following:
* Spawning a new browser window for the AU.
* Re-directing the existing browser window to the AU.

When the launchMethod is "AnyWindow", the LMS MUST choose the window context of the AU.  All browser window options are acceptable - Frameset, New window, browser redirect, etc.

Regardless of the launchMethod the AU MUST be launched by the LMS with a URL having query string launch parameters as defined in this section. The launch parameters MUST be name/value pairs in a query string appended to the URL that launches the AU.

If the AU's URL requires a query string for other purposes, then the names MUST NOT collide with named parameters defined below.

The AU MUST have the ability to process the query string launch parameters in any order.

Each value for the associated names MUST be URL-encoded. 

The format of the launching URL is as follows:  

```
<URL to AU>
?endpoint=<URL to LMS Listener>
&fetch=<Fetch URL for the Authorization Token>
&actor=<Actor>
&registration=<Registration ID>
&activityId=<AU activity ID>
```

Example:

```
http://www.example.com/LA1/Start.html
?endpoint=http://lrs.example.com/lrslistener/
&fetch=http://lms.example.com/tokenGen.htm?k=2390289x0
&actor={"objectType": "Agent","account": 
{"homePage": "http://www.example.com","name": "1625378"}}
&registration=760e3480-ba55-4991-94b0-01820dbd23a2
&activityId=http://www.example.com/LA1/001/intro
```

(For readability the above example is not URL encoded.)

The values for the URL launch parameters are described below: 

<table>
  <tr><th colspan=2 align="left">endpoint</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>A URL to the LMS listener location for xAPI requests to be sent to.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>endpoint</em></strong> in the query string.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>endpoint</em></strong> value from the query string. The AU MUST use the <strong><em>endpoint </em></strong>value as the Base Endpoint for xAPI requests.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A URL-encoded URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>https://example.com/my-cmi5-listener/</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">fetch</th></tr>
  <tr><th align="right">Description:</th><td>The <strong><em>fetch</em></strong> URL is used by the AU to obtain an authorization token created and managed by the LMS. The authorization token is used by the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>fetch</em></strong> in the Launch URL.<br>The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses SHOULD generate an error as defined in section 8.2. The authorization token returned by the <strong><em>fetch</em></strong> URL MUST be limited to the duration of a specific user session. </td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>fetch</em></strong> value from the query string. The AU MUST make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve the authorization token as defined in section 8.2. The AU MUST place the authorization token in the Authorization headers of all HTTP requests made to the endpoint using the xAPI.  The AU SHOULD NOT make more than one post to the <strong><em>fetch</em></strong> URL.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A URL-encoded URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>http://lms.example.com/tokenGen.htm?k=2390289x0</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">actor</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>A JSON object of objectType "Agent" (as defined in the xAPI specification) that identifies the learner launching the AU so the AU will be able to include it in xAPI requests.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST populate the <strong><em>actor</em></strong>  parameter in the query string based on the authenticated learner's identity conforming to Section 9.2. The LMS SHOULD create this parameter with an object that is specific to the LMS instance that does NOT include sensitive PII of the learner.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>actor</em></strong> value from the query string. The AU MUST use the <strong><em>actor</em></strong> value in xAPI requests that require an "actor" property.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A JSON object (as defined in Section 9.2)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>{"objectType": "Agent","account": {"homePage": "http://www.example.com","name": "1625378"}}</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">registration</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>A Registration ID corresponding to the learner's enrollment for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>registration</em></strong> in the query string based on the authenticated learner's corresponding    enrollment for the Course that the AU being launched is a member of.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>registration</em></strong> value from the query string. The AU MUST use the <strong><em>registration</em></strong> value in xAPI requests that require a "registration".</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>UUID (as defined in the xAPI specification)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td></td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">activityId</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The Activity ID of the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST generate a unique activityId for the AU. The LMS MUST place its value in the query string. The activityId generated MUST NOT match the AU's id (publisher id) from the course structure (See Section 13.1.4 - AU Metadata). The LMS MUST use the same generated activityId on all subsequent launches (for the same AU) within the same registration. The LMS SHOULD use the same generated activityId (for the same AU) for all registrations.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>activityId</em></strong> value from the query string. The AU MUST use the <strong><em>activityId</em></strong> value as the id property of the Object in all "cmi5 defined" statements.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>IRI</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td></td></tr>
</table>

<br>

<a name="fetch_url"></a>
## 8.2 Authorization Token Fetch URL

<a name="fetch_url_overview"></a>
### 8.2.1 Overview
The LMS MUST include the <strong><em>fetch</em></strong> name/value pair in the launch URL.  The AU MUST make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve an authorization token.  Note than an HTTP GET is not allowed in order to prevent caching of the request.

The <strong><em>fetch</em></strong> URL MUST return a JSON structure using a Content-Type of "application/json". An example JSON structure is shown below:
```javascript
{
  "auth-token": "QWxhZGRpbjpvcGVuIHNlc2FtZQ=="
}
```
The AU MUST place the <strong><em>auth-token</em></strong> in the HTTP header, as defined in <a href='http://tools.ietf.org/html/rfc1945#section-11'>RFC 1945 - 11.1 Basic Authentication Scheme</a>, in all subsequent xAPI communications with the LMS.  The authorization token returned by the <strong><em>fetch</em></strong> URL MUST be limited to the duration of the session.

The AU SHOULD NOT attempt to retrieve the authorization token more than once.  The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses SHOULD generate an error (see Section 8.2.3). 

<a name="definition_auth_token"></a>  
### 8.2.2 Definition: auth-token
<table>
  <tr><th colspan=2 align="left">auth-token</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>An authorization token used in all xAPI communications with the LMS.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>auth-token</em></strong> in a JSON structure, as shown in Section 8.2.1, in its response to a <strong><em>fetch</em></strong> URL request. The response MUST have a Content-Type of "application/json". The HTTP status code MUST be "200" for a valid request (including one that generates error as described in section 8.2.3).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>auth-token</em></strong> value using an HTTP POST to the <strong><em>fetch</em></strong> URL. The AU MUST then place the authorization token in the Authorization headers of all HTTP requests made to the endpoint using the xAPI.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>QWxhZGRpbjpvcGVuIHNlc2FtZQ==</td></tr>
</table>

<a name="fetch_url_errors"></a>  
### 8.2.3 Errors

<a name="duplicate_call_to_fetch_url"></a>  
#### 8.2.3.1 Duplicate call to fetch URL
The <strong><em>fetch</em></strong> URL is a "one-time use" URL and only the first request SHOULD return the <strong><em>auth-token</em></strong>. Subsequent requests made to the <strong><em>fetch</em></strong> URL during the session SHOULD generate an error.  The error SHOULD be returned in the form of a JSON structure using Content-Type "application/json".  An example JSON structure is shown below:
```javascript
{
  "error-code": "1",
  "error-text": "The authorization token has already been returned."
}
```
<a name="fetch_url_error_values"></a>
#### 8.2.3.2 Error Values
The following <strong><em>error-code</em></strong> values are allowed.
<table>
<tr><td><strong>Code</strong></td><td><strong>Meaning</strong></td></tr>
<tr><td>1</td><td><strong>Already in Use or Expired</strong> - Token has been used before or the AU session has expired</td></tr>
<tr><td>2</td><td><strong>General Security Error</strong> - All other security issues including invalid tokens</td></tr>
<tr><td>3</td><td><strong>General Application Error</strong> - Application or environment failures</td></tr>
</table>

The values for <strong><em>error-text</em></strong> are defined by the LMS.

<br>

<a name="other_environment"></a>  
## 8.3 Other Launch Environments

Other launch environments are not currently implemented in this specification. cmi5 implementations for LMS's and AU's in these other environments will use the same REST communication interface as specified in xAPI specification.  The xAPI specification does not specify launch mechanisms.

<a name="xapi_data_model"></a>  
# 9.0 xAPI Statement Data Model  

<a name="statement_id" ></a>
## 9.1 Statement ID
The AU MUST assign a statement id property in UUID format (as defined in the xAPI specification) for all statements it issues.
  
<a name="actor" ></a>
## 9.2 Actor
The Actor property will be defined by the LMS. The Actor property for all "cmi5 defined" statements MUST be of objectType "Agent". The Actor property MUST contain an "account" IFI as defined in the xAPI specification.

<a name="verbs" ></a> 
## 9.3 Verbs  

The following xAPI verbs are defined in this specification.

Note that "cmi5 allowed" statements are NOT subject to the usage rules in this section. 

All statements in this section refer to "cmi5 defined" statements unless otherwise noted.

AUs MUST use the below verbs that are indicated as mandatory in other sections of this specification.

For all requirements listed below including language involving order, the order is determined by the value of the timestamp property.

AU Verb Ordering Rules within an AU session are as follows:
* Verbs MUST NOT be duplicated (in cmi5 defined statements).
* More than one of the set of {"Passed","Failed"} verbs MUST NOT be used (in cmi5 defined statements).
* The "Initialized" verb MUST be the first statement (cmi5 allowed or defined).
* The "Terminated" verb MUST be the last statement (cmi5 allowed or defined).

AU Verb Ordering Rules within a Registration (per AU) are as follows:
* Exactly zero or one "Completed" cmi5 defined statement MUST be used per registration.
* Exactly zero or one "Passed" cmi5 defined statement MUST be used per registration.
* A "Failed" statement MUST NOT follow a "Passed" statement (in cmi5 defined statements) per registration.

AUs may use additional verbs not listed in this specification.

The LMS MUST record and provide reporting for all statements regardless of the verbs used in statements sent by AUs. 

LMS verb ordering rules are as follows:
* LMS may issue multiple satisfied statements (in a session).
* LMS SHOULD NOT issue multiple satisfied statements (in a registration).
* LMS MUST NOT issue more than one abandoned statement for a session.
* LMS MUST NOT issue more than one waived statement per session and MUST not issue more than one waived statement per registration per AU.


<a name="verbs_launched"></a>
### 9.3.1 Launched
<table>
<tr><th align="left">Verb</th><td>Launched</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/launched</td></tr>
<tr><th align="left">Description</th><td>The verb "Launched" indicates that the AU was launched by the LMS.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS before launching an AU.  (See Statement API, Section 10) The LMS MUST NOT issue multiple statements with "Launched" for the same AU within a given AU session.</td></tr>
<tr><th align="left">Usage</th><td>A "Launched" statement is used to indicate that the LMS has launched the AU. </td></tr>
</table>

<a name="verbs_initialized"></a>
### 9.3.2 Initialized
<table>
<tr><th align="left">Verb</th><td>Initialized</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/initialized</td></tr>
<tr><th align="left">Description</th><td>An "Initialized" statement is used by the AU to indicate that it has been fully initialized. The "Initialized" statement MUST follow, within a reasonable period of time, the "Launched" statement created by the LMS.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST use "Initialized" in the first statement (of any kind) in the AU session.  The AU MUST NOT issue multiple statements with "Initialized" for the same AU within a given AU session.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>None</td></tr>
<tr><th align="left">Usage</th><td>An "Initialized" statement is used by the AU to indicate that it has been fully initialized.</td></tr>
</table>

<a name="verbs_completed"></a>
### 9.3.3 Completed
<table>
<tr><th align="left">Verb</th><td>Completed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/completed</td></tr>
<tr><th align="left">Description</th><td>The verb "Completed" indicates the learner viewed or did all of the relevant activities in an AU presentation.  The use of the Completed verb indicates progress of 100%.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a statement containing the "Completed" verb when the learner has experienced all relevant material in an AU. The AU MUST NOT issue multiple statements with "Completed" for the same AU within a given course registration for a given learner.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use "Completed" statements based on the "moveOn" criteria for the AU as provided in the LMS Launch Data. (See xAPI State Data Model, Section 10.0 - moveOn).</td></tr>
<tr><th align="left">Usage</th><td>The criterion for "Completed" is determined by the course designer.</td></tr>
</table>

<a name="verbs_passed"></a>
### 9.3.4 Passed
<table>
<tr><th align="left">Verb</th><td>Passed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/passed</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and succeeded in a judged activity in the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a statement containing the "Passed" verb when the learner has attempted and passed the AU. If the "Passed" statement contains a (scaled) score, the (scaled) score MUST be equal to or greater than the "masteryScore" indicated in the LMS Launch Data. (See xAPI State Data Model, Section 10.0 - masteryScore). The AU MUST NOT issue multiple statements with "Passed" for the same AU within a given course registration for a given learner.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use "Passed" statements based on the "moveOn" criteria for the AU as provided in the LMS Launch Data. (See xAPI State Data Model, Section 10.0 - moveOn).</td></tr>
<tr><th align="left">Usage</th><td>The criterion for "Passed" is determined by the course designer.</td></tr>
</table>

<a name="verbs_failed"></a>
### 9.3.5 Failed
<table>
<tr><th align="left">Verb</th><td>Failed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/failed</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and failed in a judged activity in the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a statement containing the "Failed" verb when the learner has attempted and failed the AU.  If the "Failed" statement contains a (scaled) score, the (scaled) score MUST be less than the "masteryScore" indicated in the LMS Launch Data. (See xAPI State Data Model, Section 10.0 - masteryScore).</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>None.</td></tr>
<tr><th align="left">Usage</th><td>The criterion for "Failed" is determined by the course designer.</td></tr>
</table>

<a name="verbs_abandoned"></a>
### 9.3.6 Abandoned
<table>
<tr><th align="left">Verb</th><td>Abandoned</td></tr>
<tr><th align="left">ID</th><td>https://w3id.org/xapi/adl/verbs/abandoned</td></tr>
<tr><th align="left">Description</th><td>The verb "Abandoned" indicates that the AU session was abnormally terminated by a learner's action (or due to a system failure).</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>In the absence of a "Terminated" statement, the LMS MUST make the determination if an AU abnormally terminated a session by monitoring new statement or state API requests made for the same learner/course registration for a different AU.  The LMS MUST record an "Abandoned" statement on behalf of the AU indicating an abnormal session termination.  The LMS MUST NOT allow any statements to be recorded for a session after recording an "Abandoned" statement.</td></tr>
<tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>

<a name="verbs_waived"></a>
### 9.3.7 Waived
<table>
<tr><th align="left">Verb</th><td>Waived</td></tr>
<tr><th align="left">ID</th><td>https://w3id.org/xapi/adl/verbs/waived</td></tr>
<tr><th align="left">Description</th><td>The verb "Waived" indicates that the LMS has determined that the AU requirements were met by means other than satisfying the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS when it determines that the AU may be waived. A statement containing a "Waived" verb MUST include a "reason" in the extension property of the Statement Result. (See Section 9.5.5.2) The LMS MUST generate a unique session id for the statement containing a "Waived" verb and MUST NOT issue any other statements (except for statements with the "Satisfied" verb) using that session id. The LMS MUST NOT issue multiple statements with "Waived" for the same AU within a course registration. </td></tr>
<tr><th align="left">Usage</th><td>A "Waived" statement is used by the LMS to indicate that the AU may be skipped by the learner.</td></tr>
</table>

<a name="verbs_terminated"></a>
### 9.3.8 Terminated

<table>
<tr><th align="left">Verb</th><td>Terminated</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/terminated</td></tr>
<tr><th align="left">Description</th><td>The verb "Terminated" indicates that the AU was terminated by the Learner and that the AU will not be sending any more statements for the launch session.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a statement containing the "Terminated" verb. This statement MUST be the last statement (of any kind) sent by the AU in a session.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use the "Terminated" statement to determine that the AU session has ended. Upon receiving a "Terminated" statement, the LMS MUST wait a specified period of time (defined by the LMS implementation) after which it MUST reject statements (of any kind) for the AU session.
</td></tr>
<tr><th align="left">Usage</th><td>See obligations.</td></tr>
</table>

<a name="verbs_satisfied"></a>
### 9.3.9 Satisfied
<table>
<tr><th align="left">Verb</th><td>Satisfied</td></tr>
<tr><th align="left">ID</th><td>https://w3id.org/xapi/adl/verbs/satisfied</td></tr>
<tr><th align="left">Description</th><td>The verb "Satisfied" indicates that the LMS has determined that the Learner has met the moveOn criteria of all AU's in a block or has met the moveOn criteria for all AU's in the course.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<th align="left" nowrap>LMS Obligations</th><td>
The LMS MUST use the "Satisfied" statement when the learner has met the moveOn criteria of all AU's in a block.  In this statement the LMS MUST use the LMS generated block id as the Object id (Section 9.4 - Object) and use "https://w3id.org/xapi/cmi5/activitytype/block" as the value of the "type" property in the Object's Definition.<br>
<br>
The LMS MUST generate a unique block id for the Satisfied Statement. The generated Block id MUST NOT match the publisher’s ID from the course structure.<br>
<br>
The LMS MUST also use the "Satisfied" statement when the learner has met the moveOn criteria for all AU's in a course.  In this statement the LMS MUST use the LMS generated course id as the Object id (Section 9.4 - Object) and use "https://w3id.org/xapi/cmi5/activitytype/course" as the value of the "type" property in the Object's Definition.<br>
<br>
The LMS MUST generate a unique course id for the Satisfied Statement. The generated course id MUST NOT match the publisher’s ID from the course structure.<br>
<br>
For all "Satisfied" statements triggered as a result of an AU launch session, the LMS MUST use the session id from the AU launch in the statements.<br>
<br>
The LMS SHOULD NOT issue multiple statements with "Satisfied" for the same Block or Course within a course registration for a given learner.
</td></tr>
<tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>

<br>
<br>

<a name="object"></a> 
## 9.4 Object 
An Object MUST be present, as specified in this section, in all "cmi5 defined" statements.

Except for Statements with the Satisfied verb, the Object in a cmi5 defined statement represents the AU.  When the Object is the AU, the value of the Object's "id" property for a given AU MUST match the activityId defined in the launch URL.

In Satisfied statements, the Object represents a Block or Course.  (see 9.3.9 - Satisfied)  

<a name="result"></a> 
## 9.5 Result
Result may be present in a statement depending on the cmi5 verb used. 

<a name="score"></a> 
### 9.5.1 Score

A score is not required to be reported.  If a score is reported by an AU, the verb MUST be consistent with "masteryScore" (if defined for the AU in the LMS Launch Data).

The "score" property of the result MAY be set in the following cmi5 defined statements:

- Passed
- Failed

cmi5 defined statements, other than "Passed" or "Failed", MUST NOT include the "score" property.

<ul><li><strong>scaled</strong><br>A decimal value between 0 and 1 (inclusive).</li>
<li><strong>raw</strong><br>An integer value between the "min" and "max" properties (inclusive) of the <em><strong>score</strong></em> object.  The AU MUST provide the "min" and "max" values for <em><strong>score</strong></em> when the "raw" value is provided.</li>
<li><strong>min</strong><br>An integer value indicating the minimum value for the "raw" score property.</li>
<li><strong>max</strong><br>An integer value indicating the maximum value for the "raw" score property.</li>
</ul>

<a name="success"></a>
### 9.5.2 Success 

The "success" property of the result MUST be set to true for the following cmi5 defined statements:

- Passed
- Waived

The "success" property of the result MUST be set to false for the following cmi5 defined statements:

- Failed
 
Other cmi5 defined statements MUST NOT include the "success" property.

<a name="completion"></a>
### 9.5.3 Completion
The "completion" property of the result MUST be set to true for the following cmi5 defined statements:

- Completed
- Waived

Other cmi5 defined statements MUST NOT include the "completion" property.

<a name="duration"></a>
### 9.5.4 Duration
The "duration" property is an ISO 8601 formatted time value required in certain statements as defined in this section. Other cmi5 defined statements MAY include the duration property.
<a name="au_statements_that_include_duration"></a>
#### 9.5.4.1 AU statements that include duration
##### Terminated Statement
The AU MUST include the "duration" property in "Terminated" statements.  The AU SHOULD calculate duration for Terminated statements as the time difference between the "Initialized" statement and the "Terminated" statement.  The AU may use other methods to calculate the duration based on criteria determined by the AU.
##### Completed Statement
The AU MUST include the "duration" property in "Completed" statements.  The AU SHOULD calculate duration as the time spent by the learner to achieve completion status.
##### Passed Statement
The AU MUST include the "duration" property in "Passed" statements.  The AU SHOULD calculate duration as the time spent by the learner to attempt and succeed in a judged activity of the AU. 
##### Failed Statement
The AU MUST include the "duration" property in "Failed" statements. The AU SHOULD calculate duration as the time spent by the learner to attempt and fail in a judged activity of the AU.

<a name="lms_statements_that_include_duration"></a>
#### 9.5.4.2 LMS statements that include duration
##### Abandoned Statement
The duration property MUST be included in "Abandoned" statements. The LMS SHOULD use LMS specific methods (if available) to determine the duration if it has more accurate means of session time calculation than time stamp differences between statements. In the absence of such methods, the duration property MUST be set as the total session time, calculated as the time between the "Launched" statement and the last statement (of any kind) issued by the AU. 

<a name="result_extensions"></a>
### 9.5.5 Extensions
<a name="result_extensions_progress"></a>
#### 9.5.5.1 progress

<table>
    <tr><th align ="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/progress</td></tr>
    <tr><th align ="right" nowrap>Description:</th><td>An integer value between 0 and 100 (inclusive) indicating the completion of the AU as a percentage.</td></tr>
    <tr><th align ="right" nowrap>LMS Usage:</th><td>None</td></tr>
    <tr><th align ="right" nowrap>AU Usage:</th><td>The AU may set this value in statements to indicate level of completion. The AU SHOULD NOT set a progress value in a Completed statement or if it has previously issued a Completed statement for the AU in the current registration.</td></tr>
    <tr><th align ="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
    <tr><th align ="right" nowrap>LMS Obligation:</th><td>None</td></tr>
    <tr><th align ="right" nowrap>Data type:</th><td>Integer</td></tr>
    <tr><th align ="right" nowrap>Value space:</th><td>0 to 100 (inclusive)</td></tr>
</table>

<a name="result_extensions_reason"></a>
#### 9.5.5.2 reason

<table>
    <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/reason</td></tr>
    <tr><th align="right" nowrap>Description:</th><td>Indicates the reason why an AU was "waived" (marked complete by an alternative means)</td></tr>
    <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST set this value in statements it makes with the verb "Waived". The value SHOULD be one of the following -
        <ul>
            <li><b>Tested Out</b> – An Assessment was completed by the student to waive the AU.</li>
            <li><b>Equivalent AU</b> - The student successfully completed an equivalent AU (in the same course) to waive the AU. </li>
            <li><b>Equivalent Outside Activity</b> – The student successfully completed an equivalent activity outside of the course to waive the AU. </li>
            <li><b>Administrative</b> – The LMS administrative user marked the AU complete.</li>
        </ul>
    </td></tr>
    <tr><th align="right" nowrap>AU Usage:</th><td>The AU may retrieve this value from the LRS and use it to change presentation behavior based on the "reason".</td></tr>
    <tr><th align="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
    <tr><th align="right" nowrap>LMS Obligation:</th><td>This is a required extension for LMS statements that include the Waived verb.</td></tr>
    <tr><th align="right" nowrap>Data type:</th><td>String</td></tr>
    <tr><th align="right" nowrap>Value space:</th><td>
        <ul>
            <li>"Tested Out"</li>
            <li>"Equivalent AU"</li>
            <li>"Equivalent Outside Activity"</li>
            <li>"Administrative"</li>
        </ul>
    </td></tr>
    <tr><th align="right" nowrap>Sample value:</th><td>Tested Out</td></tr>
</table>

<a name="context"></a> 
## 9.6 Context

All cmi5 defined statements MUST contain a context that includes all properties as defined in this section. Either the LMS or the AU MAY provide additional properties.

<a name="registration"></a> 
### 9.6.1 registration
The value for the registration property used in the context object MUST be the value provided by the LMS. The LMS MUST generate this value and pass it to the AU via the launch URL.  The LMS MUST evaluate MoveOn criteria in the course structure at the time of registration.  For example, AUs with MoveOn criteria of "Not Applicable" in the course structure would be evaluated and could generate Satisfied statements at this time.

For all Satisfied statements triggered outside of an AU launch session, the LMS MUST generate a unique session id and use it for those statements.

<a name="context_activities"></a>
### 9.6.2 contextActivities
The purpose of this property is to facilitate searches of the LRS by the LMS or other reporting systems. The "contextActivities" property contains list(s) of Activity objects whose ids can be used as a statement list filter.  All cmi5 defined statements MUST include all properties and values defined in the contextActivites of the context template (see section 10 - xAPI State Data Model).

<a name="context_activities_category_cmi5"></a>
#### 9.6.2.1 cmi5 Category Activity
An Activity object with an "id" of "https://w3id.org/xapi/cmi5/context/categories/cmi5" in the "category" context activities list MUST be used in cmi5 defined statements as described in section 7.1.3.

<a name="context_activities_category_moveon"></a>
#### 9.6.2.2 moveOn Category Activity
cmi5 defined statements with a Result object (Section 9.5) that include either "success" or "completion" properties MUST have an Activity object with an "id" of "https://w3id.org/xapi/cmi5/context/categories/moveon" in the "category" context activities list. Other statements MUST NOT include this Activity.

<a name="context_activities_grouping_publisherid"></a>
#### 9.6.2.3 Publisher ID Grouping Activity
Used to identify statements about the AU using the publisher's id from the course structure.

The LMS MUST include an Activity object with an "id" property whose value is the unaltered value of the AU's "id" attribute from the course structure (See Section 13.1.4 AU Metadata – id) in the "grouping" context activities list in the "contextTemplate" as described in the State API (See Section 10) prior to launching an AU. The LMS MUST include the publisher id Activity in the "grouping" context activities list for all "cmi5 defined" and "cmi5 allowed" statements it makes directly in the LRS.

<a name="extensions"></a>
### 9.6.3 extensions
The following are extensions specified for cmi5.  Other extensions are permitted provided they do not conflict or duplicate the ones specified here.

<a name="context_extensions_session_id"></a>
#### 9.6.3.1 session ID

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/sessionid</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>A unique identifier for a single AU launch session based on actor and course registration </td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The value for session ID MUST be generated by the LMS. The LMS MUST record the session ID in the State API (See Section 10) prior to launching an AU. The LMS MUST provide the session ID in the context as an extension for all "cmi5 defined" and "cmi5 allowed" statements it makes directly in the LRS. </td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>An AU MUST include the session ID provided by the LMS in the context as an extension for all "cmi5 defined" and "cmi5 allowed" statements it makes directly in the LRS. </td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>string value</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td></td></tr>
</table>

<a name="context_extensions_masteryScore"></a>
#### 9.6.3.2 masteryScore

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/masteryscore</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>"masteryScore" as provided in the LMS Launch Data for the AU plus registration used to determine the pass/fail result based on score</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add masteryScore to the context of a "Launched" statement when it is provided in the LMS launch data.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>An AU MUST include the "masteryScore" value provided by the LMS in the context as an extension for "passed"/"failed" Statements it makes based on the "masteryScore".</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>Required, when present and evaluated</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required, when in launch data</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>decimal</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Decimal value between 0 and 1 (inclusive) with up to 4 decimal places of precision</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>0.92</td></tr>
</table>

<a name="context_extensions_launchMode"></a>
#### 9.6.3.3 launchMode

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/launchmode</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>Indicates what launch mode an AU was launched with by the LMS</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add launchMode to the context of a "Launched" statement.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Per launchMode vocabulary defined in section 10.0 xAPI State Data Model</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>"Normal"</td></tr>
</table>

<a name="context_extensions_launchURL"></a>
#### 9.6.3.4 launchURL

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/launchurl</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>The URL used by the LMS to launch the AU</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST put a fully qualified URL equivalent to the one that the LMS used to launch the AU without the name/value pairs included as defined in section 8.1 in the context extensions of the "Launched" statement.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>http://www.example.com/LA1/Start.html</td></tr>
</table>

<a name="context_extensions_publisherid"></a>
#### 9.6.3.5 publisherId

This section is no longer applicable. See section 9.6.2.3 Publisher ID Grouping Activity.

<a name="context_extensions_moveOn"></a>
#### 9.6.3.6 moveOn

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/moveon</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>"moveOn" as provided in the LMS Launch Data for the AU plus registration</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>THe LMS MUST add moveOn to the context of a "Launched" statement.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Per moveOn vocabulary defined in section 10.0 xAPI State Data Model</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>"Passed"</td></tr>
</table>

<a name="context_extensions_launchParameters"></a>
#### 9.6.3.7 launchParameters

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/launchparameters</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>"launchParameters" as provided in the LMS Launch Data for the AU plus registration</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add launchParameters to the context of a "Launched" statement when it is provided in the LMS launch data.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required, when in launch data</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Any string value</td></tr>
</table>

<a name="timestamp"></a> 
## 9.7 Timestamp

All statements MUST include a timestamp property per the xAPI specification to ensure statement ordering requirements are met. All timestamps MUST be recorded in UTC time. Timestamps are not required to be unique in statements within a session. The time recorded SHOULD indicate when the condition actually occurred.


<a name="xapi_state"></a>  
# 10.0 xAPI State Data Model

Prior to launching an AU, the LMS MUST create or update a document in the State API record in the LRS.  This MUST be a JSON document, as defined in this section.

__State API PUT Properties__:

* _activityId_: Activity id for the AU
* _agent_: Agent representing the LMS learner being enrolled.  This MUST match the actor property generated by LMS at AU launch time.
* _registration_: Registration id representing the LMS learner enrollment in the course. This MUST match Registration ID used by the LMS at AU launch time.
* _stateId_: LMS.LaunchData


The properties for the "LMS.LaunchData" document are described below.

<table>
  <tr><th colspan=2 align="left">contextTemplate</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>Context template for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>LMS MUST include a "contextTemplate" object and MUST include the following values:
<ul><li>The value for session id placed in an "extensions" property with the id as defined in Section 9.6.3.1.</li>
<li>The publisher id Activity as defined in Section 9.6.2.3 in the "contextActivities.grouping" list</li></ul>
The LMS MAY place additional values in the "contextTemplate".</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>AU MUST get the "contextTemplate" value from the "LMS.LaunchData" State document. The AU MUST NOT modify or delete the "LMS.LaunchData" State document. The AU MUST use the contextTemplate as a template for the "context" property in all xAPI statements it sends to the LMS. While the AU may include additional values in the Context object of such statements, it MUST NOT overwrite any values provided in the contextTemplate. NOTE: this will include the session id specified by the LMS.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>JSON Context object as defined in xAPI specification.</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">launchMode</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The launch mode determined by the LMS. There are three possible values:<br>
      <ul><li>Normal<br>Indicates to the AU that completion-related data MUST be recorded in the LMS using xAPI statements.</li>
          <li>Browse<br>Indicates to the AU that completion-related data MUST NOT be recorded in the LMS using xAPI statements. When Browse mode is used, the AU SHOULD provide a user experience that allows the user to "look around" without judgement.</li>
          <li>Review<br>Indicates to the AU that completion-related data MUST NOT be recorded in the LMS using xAPI statements. When Review mode is used, the AU SHOULD provide a user experience that allows the user to "revisit/review" already completed material.</li>
      </ul></td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>LMS MUST include a value for <strong><em>launchMode</em></strong>.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST conform to the following based on the value of <strong><em>launchMode</em></strong><br>
      <ul><li>Normal<br>The AU MUST send "Initialized" and "Terminated" verb statements.  The AU MUST send other cmi5 defined statements per the requirements defined in section 9.3 – Verbs.</li>
      <li>Browse<br>The AU MUST send "Initialized" and "Terminated" verb statements.  The AU MUST NOT send other cmi5 defined statements.</li>
      <li>Review<br>The AU MUST send "Initialized" and "Terminated" verb statements.  The AU MUST NOT send other cmi5 defined statements.</li></ul></td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>"Normal", "Browse", or "Review"</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"Normal"</td></tr>
</table>

<table>
  <tr><th colspan="2" align="left">launchParameters</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <strong><em>launchParameters</em></strong> defined in the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>If the <strong><em>launchParameters</em></strong> were defined by the course designer in the Course Structure, the LMS MUST include the  <strong><em>launchParameters</em></strong> in the State API document.</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST provide a <strong><em>launchParameters</em></strong> value in the state API document. The <em>launchParameters</em> value written in the State API Document MAY be different than the one in the course structure (e.g. based on content vendor options that may be used by the LMS admin users).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD get the <strong><em>launchParameters</em></strong> value from the State API document if the launch parameters were defined in the Course Structure.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Any string value</td></tr>
</table>

<table>
  <tr><th colspan="2" align="left">masteryScore</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <strong><em>masteryScore</em></strong> from the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>If the <strong><em>masteryScore</em></strong> was defined by the course designer in the Course Structure, the LMS MUST include a "masteryScore" in the State API document.</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>If the <strong><em>masteryScore</em></strong> is provided.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>If a <strong><em>masteryScore</em></strong> is present in the course structure the LMS MUST provide a <strong><em>masteryScore</em></strong> in the State API document. The <strong><em>masteryScore</em></strong> value written in the State API Document MAY be different than the one in the course structure (e.g. based on administrative rules defined by the LMS).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>If the AU issues "Passed" or "Failed" statements they MUST be based on the <strong><em>masteryScore</em></strong> if provided. (See Sections 9.3.4 and 9.3.5)</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>decimal</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Decimal value between 0 and 1 (inclusive) with up to 4 decimal places of precision.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>0.75</td></tr>
</table>

<table>
  <tr><th colspan="2" align="left">moveOn</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <strong><em>moveOn</em></strong> value from the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST provide a <strong><em>moveOn</em></strong> value in the state API document. The <strong><em>moveOn</em></strong> value written in the State API Document MAY be different than the one in the course structure (e.g. based on administrative rules defined by the LMS).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MAY get the <strong><em>moveOn</em></strong> value from the "LMS.LaunchData" state document and MAY use the value to modify its behavior.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td><strong><em>moveOn</em></strong> values as defined in the Course Structure (Section 13.1.4 – AU Metadata)</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"Passed"</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">returnURL</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>Used by the LMS when launching the AU if the LMS requires the AU (in a web-browser environment) to redirect the learner when he or she exits the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>If the <strong><em>returnURL</em></strong> is provided.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MAY include the <strong><em>returnURL</em></strong> when the learner SHOULD be redirected to the <strong><em>returnURL</em></strong> on exiting the AU.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>returnURL</em></strong> value from the "LMS.LaunchData" state document. If the <strong><em>returnURL</em></strong> is provided, the AU MUST redirect the current browser window to the <strong><em>returnURL</em></strong> when the AU is terminated.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String (Not URL encoded)</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Any URL.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>http://www.example.com/lms/mod/xapilaunch/view.php?id=12</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">entitlementKey</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <strong>entitlementKey</strong> object is used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>If an entitlementKey is present in the Course Structure for the AU, the LMS MUST add and an entitlementKey object to the LMS.launchdata state document. The entitlementKey consists of 2 properties, “courseStructure” and “alternate”. See items below for LMS usage requirements.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>JSON Object</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value for entitlementKey properties are defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>{courseStructure: "xyz-123-9999", alternate: "abc-456-1111"}</td></tr>
</table>


<table>
  <tr><th colspan=2 align="left">entitlementKey: courseStructure</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <strong>courseStructure</strong> property contains the value for entitlementKey from the Course Structure. The courseStructure values may be used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST obtain this from the Course Structure.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value is defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"xyz-123-9999"</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">entitlementKey: alternate</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <strong>alternate</strong> property is data from some other source as agreed upon between the LMS and the AU. The alternate property values may be used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST obtain the value for the alternate property from a source as agreed upon with the AU.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value is defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"xyz-123-9999"</td></tr>
</table>

<a name="xapi_agent_profile"></a>   
# 11.0 xAPI Agent Profile Data Model  

In cmi5, Learner Preferences are scoped to the learner.  Both the LMS and the AU MAY write changes to Learner Preferences in the xAPI Agent Profile.  The LMS/LRS MAY choose to ignore or override Learner Preference changes requested by the AU by returning a "403 Forbidden" response as defined in the xAPI specification (Section 7.6).  The AU MUST NOT treat the 403 response as an error condition.

On startup, the AU MUST retrieve the Learner Preferences document from the Agent Profile.

When reading or writing to the Agent Profile, the document name MUST be "cmi5LearnerPreferences" and the format MUST be a JSON structure as shown below:

```javascript
{
  "languagePreference": "<values for languages>",
  "audioPreference": "<on or off>"
}
```
<a name="language_preference"></a>
## 11.1  languagePreference
The languagePreference MUST be a comma-separated list of RFC 5646 Language Tags as indicated in the xAPI specification (Section 5.2).  In the list, languages MUST be specified in order of user preference.  In the example below, the user's first preference for language is en-US.  The user's second preference for language is fr-FR and the third preference is fr-BE.

```javascript
{
  "languagePreference": "en-US,fr-FR,fr-BE",
  ...
}
```

If the AU supports multiple languages, the AU SHOULD display in the language preference order of the user as in the example above. If the AU supported "zh-CN", "fr-BE" and "fr-FR", it SHOULD display in "fr-FR".  If the AU does not support multiple languages, or if no languagePreference is specified in the Agent Profile, it may display in its default language.

<a name="audio_preference"></a>

## 11.2 audioPreference
The audioPrefence value indicates whether the audio SHOULD be "on" or "off".  The AU MUST turn the audio on or off at startup based on this value.  If no value is provided in the Agent Profile for audioPreference the AU MAY use its own default value.

Example:
```javascript
{
  "audioPreference": "on",
  ...
}
```


<a name="xapi_activity_profile"></a>  
# 12.0 xAPI Activity Profile Data Model

The AU MAY use the Activity Profile API according to the xAPI specification (Section 7.5 - Activity Profile API).


<a name="course_requirements"></a>

# 13.0 Course Structure Data Requirements  

<a name="course_structure_data_model"></a>
## 13.1 Course Structure Data Model
All leading/trailing whitespace MUST be removed by the LMS on import of the course structure for all of the data elements defined in this section.

The following Data Types are used in the cmi5 course structure data model, see the cmi5.xsd (section 13.2) for specific format:
   * **decimal** – XSD definition:  "xs:decimal"
   * **IRI** – XSD definition:  "xs:anyURI"
   * **string** –  XSD definition: "xs:string"
   * **langstring** – XSD definition : <xs:element name="langstring" maxOccurs="unbounded" minOccurs="1"/>
   * **objectiveReference** – XSD definition : <xs:element name="objectives" type="referencesObjectivesType" minOccurs="0"/>

<a name="course_level_meta_data"></a>
### 13.1.1 Course Level Metadata  
 
The following metadata attributes and elements are at the course level and  describe the course instance as a whole.

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: Yes<br>
        <strong>Data type</strong>: IRI</p>
    </td>
    <td width="811" valign="top"><p><strong>Description</strong>:<br>
      A globally unique IRI for the course.  Used to explicitly identify the course instance.</p>
      <p><strong>Value space: </strong><br>
        Values are defined by the course designer.<br>
        <strong>Sample value: </strong><br>
         &lt;course id="http&#58;//www.example.com/identifiers/course/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/course&gt;<br></p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: 
      Yes<br>
      <strong>Data type</strong>: 
      langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br>
      A descriptive title that identifies the course.<br>
      </p>
      <p><strong>Value space:</strong><br>
        Values are defined by the course designer.<br>
      </p>
      <p><strong>Sample value</strong>: <br>
    &lt;title&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="en-US"&gt;This is a course title&lt;/langstring&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="es-MX"&gt;Se trata de un título del curso&lt;/langstring&gt;<br>
    &lt;/title&gt;<br>
  </p>
  </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: Yes<br>
        <strong>Data type</strong>: langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br>
      A detailed description of the course.</p>
      <p><strong>Value space:</strong><br>
        Values are defined by the course designer.</p>
      <p><strong>Sample value: </strong><br>
    &lt;description&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="en-US"&gt;This is a course description&lt;/langstring&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="es-MX"&gt;Esta es una descripción del curso&lt;/langstring&gt;<br>
    &lt;/description&gt;<br>  
        </p>
    </td>
  </tr>

</table>

 

<a name="block_meta_data"></a>
### 13.1.2 Block Metadata

The data in this section are used for the block structures with group AUs.  A Block consists of one or more AUs. Blocks can also contain references to objectives and other Blocks.

<table border="1" cellspacing="0" cellpadding="0">
   <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type: </strong> IRI</p></td>
    <td width="811" valign="top"><p><strong>Description: </strong>A globally unique IRI to identify the Block in xAPI requests made by the LMS.</p>
      <p><strong>Value space: </strong>Values defined by course designer</p>
      <p><strong>Sample value:</strong><br>
      &lt;block id="http&#58;//www.example.com/identifiers/aublock/005430bf-b3ba-45e6-b47b-d629603d83d8" &gt; &hellip; &lt;/block&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required:</strong> Yes<br>
        <strong>Data type:</strong> langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br>
      A descriptive title for the Block of AUs<br>
      <strong>Value space:</strong><br>
      Values are defined by the course designer.<br>
      <strong>Sample value:</strong><br>
    &lt;title&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="en-US"&gt;This is the block title&lt;/langstring&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="es-MX"&gt;Este es el título del bloque&lt;/langstring&gt;<br>
    &lt;/title&gt;<br>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: 
      </strong>Yes<br>
      <strong>Data type:</strong> langstring </p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br>
      A detailed verbal description of what the Block contains.<br>
      <strong>Value space</strong>:<br>
      Values are defined by the course designer.<br>
      <strong>Sample value: </strong><br>
&lt;description&gt;<br>
&nbsp;&nbsp;    &lt;langstring lang="en-US"&gt;This is the block description&lt;/langstring&gt;<br>
&nbsp;&nbsp;    &lt;langstring lang="es-MX"&gt;Esta es la descripción de los bloques&lt;/langstring&gt;<br>
&lt;/description&gt;<br>
    </td>
  </tr>
    <tr>
    <td colspan="2" valign="top"><h3>objectives</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: 
      </strong>No<br>
      <strong>Data type:</strong> objectiveReference </p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br>
      A listing of objectives referenced by this block.<br>
      <strong>Value space</strong>:<br>
      Values are defined by the course designer.<br>
      <strong>Sample value: </strong><br>
    &lt;objectives&gt;<br>
    &nbsp;&nbsp; &lt;objective idref="http&#58;//www.example.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" /&gt;<br>
    &lt;/objectives&gt;<br>
    </td>  
  </tr>
</table>


<a name="objective_meta_data"></a>
### 13.1.3 Objective Metadata

The data in this section are used by the Objectives. Objectives can be associated with a Block or with individual AUs. 

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required: </strong>Yes<br>
        <strong>Data type:</strong> IRI</p>
    </td>
    <td width="792" valign="top"><p><strong>Description:</strong><br>
      A unique IRI for the learning objective.<br>
      </p>
      <p><strong>Value space:</strong><br>Values are defined by the course designer.</p>
    <p><strong>Sample value:</strong><br>
    &lt;objective id="http&#58;//www.example.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/objective&gt;</p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required:</strong> Yes<br>
        <strong>Data type</strong>: langstring</p>
    </td>
    <td width="792" valign="top"><p><strong>Description</strong>:<br>
      A descriptive title for the learning objective</p>
      <p><strong>Value space:</strong><br>
        Values are defined by the course designer.<br>
      </p>
      <p><strong>Sample value: </strong><br>
    &lt;title&gt;<br>
    &nbsp;&nbsp; &lt;langstring lang="en-US"&gt;This is the objective title&lt;/langstring&gt;<br>
    &nbsp;&nbsp; &lt;langstring lang="es-MX"&gt;Este es el título del objetivo&lt;/langstring&gt;<br>
    &lt;/title&gt;<br>
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required:</strong> Yes<br>
        <strong>Data type</strong>: langstring </p>
    </td>
    <td width="792" valign="top"><p><strong>Description:</strong><br>
      A detailed verbal description of the learning objective.<br>
      </p>
      <p><strong>Value space:</strong><br>
        Values are defined by the course designer.<br>
        </p>
      <p><strong>Sample value: </strong><br>
    &lt;description&gt;<br>
    &nbsp;&nbsp; &lt;langstring lang="en-US"&gt;This is the objective description&lt;/langstring&gt;<br>
    &nbsp;&nbsp; &lt;langstring lang="es-MX"&gt;Esta es la descripción objetiva&lt;/langstring&gt;<br>
    &lt;/description&gt;<br>
      </p>
    </td>
  </tr>
</table>


<a name="au_meta_data"></a>  
### 13.1.4 AU Metadata  

The data in this section are used by the LMS to locate the AU and provide launch data. AUs may also contain objectives.


<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type: </strong> IRI</p>
    </td>
    <td width="815" valign="top"><p><strong>Description: </strong>A globally unique IRI defined by content creator/publisher that the AU uses to identify itself in xAPI statement contexts. This id MUST be unique within the course structure.</p>
      <p><strong>Value space: </strong>Values are defined by the course designer.</p>
      <p><strong>Sample value:</strong><br>
      &lt;au id="http&#58;//www.example.com/identifiers/activity/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>launchMethod</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type:</strong> string <br>
        <strong>Default Value:</strong> "AnyWindow"
        </p>
    </td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS when launching the AU (in a web-browser environment) to determine whether the AU requires its own window, or whether the LMS may choose the window context for the AU.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>A value of "OwnWindow" will require the LMS to launch the AU either in a new browser window, or the LMS may redirect the current window to the AU.</li>
        <li>A value of "AnyWindow" indicates that the AU does not care about the window context.  All browser window options are acceptable, such as in a Frameset, in a New Window, a browser redirect, etc.</li>
      </ul>
      <p><strong>Value space: </strong>"OwnWindow", "AnyWindow"<br>
        <br>
      <strong>Sample value: </strong><br>
      &lt;au id="&hellip;" launchMethod="OwnWindow"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
    <tr>
    <td colspan="2" valign="top"><h3>masteryScore</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type:</strong> decimal </p></td>
    <td valign="top"><p><strong>Description:</strong> A score used by the LMS to determine passing or failure of judged activity in the AU (if the AU has scoring).</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>The "masteryScore" is passed to the AU at runtime by the LMS (See xAPI State Data Model, Section 10.0).</li>
        <li>If the AU has scoring, it will use the "masteryScore" to determine pass/fail.</li>
        <li>The "masteryScore" is a scaled, decimal value between 0 and 1 (inclusive) with up to 4 decimal places of precision.</li>
      </ul>
      <p><strong>Value space: </strong>Decimal number.<br>
        <br>
      <strong>Sample value: </strong><br>
      &lt;au id="&hellip;" masteryScore="0.85"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  <tr>
    <td colspan="2" valign="top"><h3>moveOn</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type:</strong> string <br>
        <strong>Default Value:</strong> "NotApplicable" </p></td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to determine if an AU has been sufficiently completed for the purposes of determining overall course completion or determining if prerequisites were met for other activities.</p>
      <p><strong>moveOn Values are as follows:</strong></p>
      <ul>
        <li>moveOn Value = "Passed" : If the LMS receives a statement with the verb "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "Completed" : If the LMS receives a statement with the verb "Completed", then the LMS will consider the AU satisfied.<br>
          </li>
        <li>moveOn Value = "CompletedAndPassed" : If the LMS receives statements with the verbs "Completed" and "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "CompletedOrPassed" : If the LMS receives a statement with either of the verbs "Completed" or "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "NotApplicable": The LMS will consider the AU satisfied.</li>
      </ul>
      <p><strong>Usage:</strong></p>
      <p>If all member AUs in a block are satisfied, then the block is considered satisfied for prerequisites and sequencing.<br>If all member AUs and Blocks are satisfied, then the course is considered satisfied for prerequisites or credit in relation to other courses or curricula.</p>
      <p><strong>Value space:</strong></p>
      <blockquote>
        <p>"Passed"<br>
          "Completed"<br>
          "CompletedAndPassed"<br>
          "CompletedOrPassed"<br>
          "NotApplicable"</p>
      </blockquote>
      <p><strong>Sample value: </strong><br>
      &lt;au id="&hellip;" moveOn="Passed"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>activityType</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type:</strong> IRI</p></td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to determine the activity type of the AU before a first start to indicate this type to the user.</p>
      <strong>Sample value: </strong><br>
      &lt;au id="&hellip;" activityType="http://adlnet.gov/expapi/activities/media"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>

  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type:</strong> langstring</p></td>
    <td valign="top"><p><strong>Description:</strong> A descriptive title for the AU.<br>
        </p>
      <p><strong>Value space: </strong> Values are defined by the course designer.<br>
      </p>
      <p><strong>Sample value: </strong><br>
    &lt;title&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="en-US"&gt;This is an activity title.&lt;/langstring&gt;<br>
    &nbsp;&nbsp;&lt;langstring lang="es-MX"&gt;Este es un título de la actividad.&lt;/langstring&gt;<br>
    &lt;/title&gt;<br>
      </p>
    </td>
  </tr>

  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required:
      </strong>Yes<br>
      <strong>Data type:</strong> langstring </p>
    </td>
    <td width="815" valign="top"><p><strong>Description:</strong><br>
      A detailed description of the subject matter and learning activities covered by the AU.</p>
      <p>
        <strong>Value space:</strong> Values are defined by the course designer.<br>
        </p>
      <p><strong>Sample value:</strong><br>
    &lt;description&gt;<br>
    &nbsp;&nbsp; &lt;langstring lang="en-US"&gt;This is the AU description&lt;/langstring&gt;<br>
    &nbsp;&nbsp; &lt;langstring lang="es-MX"&gt;Esta es la descripción de la AU&lt;/langstring&gt;<br>
    &lt;/description&gt;<br>
      </p>
    </td>
  </tr>
    </tr>
    <tr>
    <td colspan="2" valign="top"><h3>objectives</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: 
      </strong>No<br>
      <strong>Data type:</strong> objectiveReference </p>
    </td>
    <td width="815" valign="top"><p><strong>Description:</strong><br>
      A listing of objectives referenced by this AU.</p>
      <p>
          <strong>Value space</strong>: Values are defined by the course designer.<br>
      </p>
      <p>
      <strong>Sample value: </strong><br>
    &lt;objectives&gt;<br>
    &nbsp;&nbsp; &lt;objective idref="http&#58;//www.example.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" /&gt;<br>
    &lt;/objectives&gt;<br>
        </p>
    </td>  
  </tr>  
  <tr>
    <td colspan="2" valign="top"><h3>url</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required:</strong> Yes<br>
        <strong>Data type: </strong> string</p>
    </td>
    <td width="815" valign="top"><p><strong>Description:</strong><br>
    <ul>
          <li>A relative or fully qualified URL that references the launch point of the AU.</li>
          <li>To accommodate "non-browser" applications, an application specific protocol may be used in the url:<br>
              &lt;application&gt;://&lt;URL to content&gt;</li>
          <li>Regardless of the value of &lt;scheme&gt;, the remaining portion of the URL MUST conform to RFC1738 - Uniform Resource Locators (URL).</li>
          <li>If the url includes a query string, the values from that query string MUST be merged with the cmi5 parameters at launch time (see Section 8.1.1 of the cmi5 Runtime Environment).</li>
     </ul>
      <p><strong>Value space:</strong> Values are determined by the course designer.</p>
      <p><strong>Sample value:</strong><br>
      &lt;url&gt;<br>
      http://www.example.com/courseX.html<br>
      &lt;/url&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>launchParameters</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type: </strong>string </p>
    </td>
    <td width="815" valign="top"><p><strong>Description:</strong><br>
      Static launch parameters defined by the course designer.<br>
      </p>
      <p><strong>Value space:</strong><br>
        Values are defined by the course designer.</p>
      <p>
        <strong>Sample value:</strong><br>
        &lt;launchParameters&gt;<br>
        Start=1,QuizMode=1,FastForward=On<br>
         &lt;/launchParameters&gt;<br>
        </p>
    </td>
  </tr>  
  <tr>
    <td colspan="2" valign="top"><h3>entitlementKey</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type:</strong> string </p></td>
    <td valign="top"><p><strong>Description:</strong><br>
        Data used by the AU to determine if the launching LMS is entitled to use the AU. The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.<br>
    </p>
      <p><strong>Value space: </strong>Values are defined by the AU content provider.<br>
        <br>
        <strong>Sample value:</strong><br>
        &lt;entitlementKey&gt;<br>
        xyz-123-9999<br>
        &lt;/entitlementKey&gt;
        </p>
    </td>
  </tr>
</table>

<a name="vendor_meta_data"></a>
### 13.1.5 Vendor Specific Metadata (Extensions)

Course Designers MAY place their own namespaced elements into the course structure and thus define an extension for the source structure specification. For that they MUST provide a XML Schema Definition and SHOULD provide a human readable specification describing these vendor specific extensions. These extensions MUST keep the course structure XML valid. An importing LMS MAY ignore these elements. Therefore the extension SHOULD be created in such a manner that a course is still useable if the LMS does not support the additional elements.

To achieve a larger distribution of their extension course designers SHOULD choose a free or open source license for their specification and make it publicly available.

<a name="course_structure_xsd"></a>  
## 13.2 Course Structure XSD 

Available locally in [v1/CourseStructure.xsd](v1/CourseStructure.xsd) or remotely at https://w3id.org/xapi/profiles/cmi5/v1/CourseStructure.xsd.
All course structures created for LMS import functionality and created by the LMS for export MUST conform to this XSD and be named "cmi5.xml".

<a name="course_package"></a>
# 14.0 Course Package
For the course import and export defined in Section 6.1, the LMS MUST support all of the following formats:
<ul><li>Zip32</li>
<li>Zip64</li>
<li>A course structure XML file</li>
</ul>

<a name="course_packages_in_zip_format"></a>
## 14.1 Course Packages in ZIP Format
The two ZIP file formats MUST follow the specification defined at https://www.pkware.com/support/zip-app-note.  When the ZIP file is used to package a course, it MUST contain the course structure XML file at its root directory and it MAY contain media associated with the course AUs.

<ul><li>Any media included in a ZIP course package MUST use relative URL references in the Course Structure XML.</li>
<li>Any media not included in a ZIP course package MUST use fully qualified URL references in the Course Structure XML.</li>
<li>A ZIP course package MAY contain a mix of fully qualified and relative URLs, provided the rules above are followed.</li>
</ul>

<a name="course_structure_xml_without_a_zip_file_package"></a>
## 14.2 Course Structure XML Without a ZIP File Package
When a course structure XML file is provided without a ZIP file package, all URL references MUST be fully qualified.

<a name="course_structure_examples"></a> 
# 15.0 Course Structure Examples

Using the domain of geology the following two examples demonstrate how simple and complex a course designer can structure a course. The titles and descriptions are fetched or translated from the Earth Sciences Portal at Wikipedia (https://en.wikipedia.org/wiki/Portal:Earth_sciences).

<a name="course_structure_examples_simple"></a> 
## 15.1 Simple

Simple single AU course structure is available in [v1/examples/simple-cmi5.xml](v1/examples/simple-cmi5.xml).

<a name="course_structure_examples_complex"></a> 
## 15.2 Complex

Complex course structure with multiple objectives, multiple blocks with nesting, multiple AU blocks, etc. is available in  [v1/examples/complex-cmi5.xml](v1/examples/complex-cmi5.xml).

<a name="course_structure_examples_extension"></a> 
# 15.3 Extension

An extended simple course structure example is available in [v1/examples/extended-cmi5.xml](v1/examples/extended-cmi5.xml) which uses vendor specific metadata following the XML Schema Definition defined in [v1/examples/extended-cmi5.xsd](v1/examples/extended-cmi5.xsd).

-------

<a id="license_agreement"></a> 
# License Agreement

Copyright &copy; 2012-2016 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defense, All rights reserved

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License. 
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed 
on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for 
the specific language governing permissions and limitations under the License.

-------
