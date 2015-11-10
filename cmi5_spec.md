  
<p>
<p align=center><img src="https://cloud.githubusercontent.com/assets/1656316/9965238/bc9deb2c-5de9-11e5-9954-63aa03873f88.png" align=center></p>

#cmi5 Specification Profile for xAPI


---
>
>Copyright &copy; 2012-2015 ADL, All rights reserved
>

----


## Table of Contents

[__Disclaimer__](#disclaimer)

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
  * [6.1 Course Structures](#course_structures)
  * [6.2 LMS State API Requirements](#lms_state_api_requirements)
  * [6.3 LMS Statement API Requirements](#lms_statement_api_requirements)
* [__7.0 AU Requirements__](#au_requirements)
  * [7.1 AU State API Requirements](#au_state_api_requirements)
  * [7.2 AU Statement API Requirements](#au_statement_api_requirements)
      * [7.2.1 Placement of the session ID in Statements](#placement)
      * [7.2.2 First Statement API Call](#first_statement_au)
      * [7.2.3 Last Statement Call](#last_statement_au)
      * [7.2.4 Types of Statements](#type_statement_au)
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
      * [9.4.1 objectType](#object_type)
      * [9.4.2 id](#object_id)
  * [9.5 Result](#result)
      * [9.5.1 Score](#score)
      * [9.5.2 Success](#success)
      * [9.5.3 Completion](#completion)
      * [9.5.4 Duration](#duration)
          * [9.5.4.1 AU statements that include duration](#au_statements_that_include_duration)
          * [9.5.4.2 LMS statements that include duration](#lms_statements_that_include_duration)
      * [9.5.5 Extensions](#result_extensions)
          * [9.5.5.1 Progress](#result_extensions_progress)
  * [9.6 Context](#context)
      * [9.6.1 Registration](#registration)
      * [9.6.2 ContextActivities](#context_activities)
      * [9.6.3 Extensions](#extensions)
          * [9.6.3.1 session ID](#context_extensions_session_id)
          * [9.6.3.2 reason](#context_extensions_reason)
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
    * [13.1.3 Objectives Metadata](#objectives_meta_data)
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

<a name="disclaimer"/>  
## Disclaimer
PLEASE NOTE: This is a developer release and is subject to change.

<a name="revhistory"></a>
## Revision History
__Sandstone - 1st Edition (May 15, 2015):__

* Developer release

__0.1 Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__  

* Converted existing working draft to markdown format from Microsoft Word. All previous work from 2012 discarded.


<a name="contributors"></a> 
##Contributors

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
| William A. McDonald  | Boeing                                 |
| Ray Lowery           | Pratt &amp; Whitney                    |
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

<a name="overview"></a>  
#1.0 Overview


This specification describes interoperable runtime communication between Learning Management Systems
(LMS) and Assignable Units (AU).

<a name="scope"></a>  
##1.1 Scope

The scope of this specification is limited to the following:

* Launch by an LMS of AUs.
* Launch and runtime environment used by LMS and AUs.
* Runtime communication data and data transport between the LMS and AUs. 
* LMS course definition as it pertains to runtime data used by AUs.
* LMS Course Structure Import/Export  
* Reporting requirements for the LMS.

This specification references how to use the xAPI specification within this scope.

Other uses of the xAPI specification are outside of this scope.

Uses of activities not explicitly defined above are outside of the scope of this specification.


<a name="references"></a> 
#2.0  References

The following referenced documents are indispensable for the application of this specification. 

* Internationalized Resource Identifiers (IRIs): IRI Syntax January 2005<br>
https://www.ietf.org/rfc/rfc3987.txt
* "Experience API", current specification, ADL, 2012-2013<br>
https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md
* cmi5 Course Structure, Sandstone 1st Edition<br>
https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_coursestructure.md
* MIME Types<br>
http://www.iana.org/assignments/media-types/index.html
* Extensible Markup Language (XML)<br>
http://www.w3.org/XML
* The JSON Data Interchange Format<br>
http://json.org/ 

<a name="definitions"></a>   
#3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user who manages the LMS and related systems. This user performs tasks such as learner enrollment, course structure definition, and report management.

* __Assignable Unit (AU)__:  A learning content presentation launched from an LMS. The AU is the unit of tracking and management. The AU collects data on the learner and sends it to the LMS.

* __Course__: A collection of assignable units, in a logical grouping, of learning content. A course is typically an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied sequence, representing a course.  

* __Experience API (xAPI)__: A runtime data communication specification for learning content (AU) to send and receive data to a Learning Record Store (LRS).  The xAPI specification referenced by this document is used to define the data transport and the data model.

* __Internationalized Resource Identifier (IRI)__: A unique identifier according to RFC 3987.  The IRI may be an IRL. All IRIs SHOULD be a full, absolute IRI that includes a scheme. Relative IRIs SHOULD NOT be used. IRLs SHOULD be defined within a domain controlled by the person creating the IRL.

* __Internationalized Resource Locator (IRL)__: According to the xAPI specification, an IRL is an IRI that, when translated into a URI (according to the IRI to URI rules), is a URL. Some communities of practice simply use "URL" even if they use IRIs, which is not as technically correct within the xAPI.

* __Learner__: The end user viewing/using the learning content (AUs).

* __Learning Activity Provider (AP)__:  Learning Activity Provider (AP) as defined in the xAPI specification.

* __Learning Management System (LMS)__: A computer system that may include the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners' progress. LMS launching, reporting, and tracking roles are the focus of the cmi5 specification. The LMS MUST have an LRS as part of its implementation.

* __Learning Records Store (LRS)__: Defined in the xAPI specification. In this specification, the LMS MUST implement an LRS with the additional requirements specified in this document.

<a name="acronyms"></a> 
##3.1 Abbreviations and Acronyms
<br>
__ADL__: Advanced Distributed Learning  
__AICC__: Aviation Industry Computer-Based Training Committee  
__API__: Application Programming Interface  
__CMI__: Computer Managed Instruction
__JSON__: JavaScript Object Notation
__IRI__: Internationalized Resource Identifier
__IRL__: Internationalized Resource Locator
__LMS__: Learning Management System  
__LRS__: Learning Record Store  
__PII__: Personally Identifiable Information  
__URI__: Uniform Resource Identifier  
__URL__: Uniform Resource Locator  
__URN__: Uniform Resource Name
__xAPI__: Experience API
__XML__: Extensible Markup Language  
__XSD__: XML Schema Definition  
<br>


<a name="conformance"></a>  
#4.0  Conformance

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
##4.1 Assignable Unit (AU)

An Assignable Unit MUST conform to all requirements listed in Section 7 – AU Requirements.

An Assignable Unit MUST conform to all requirements as specified in the xAPI specification (see References).

An Assignable Unit MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.

<a name="lms_conformance"></a> 
##4.2 Learning Management Systems (LMS)

The LMS MUST conform to all LRS requirements as specified in the xAPI specification (see References).

The LMS MUST include the ability to retrieve and show all statements (including attachments and extensions) to a user (with the understanding of scaling permissions/authorization).

The LMS MUST decode the attachment and make it available as a file with the original MIME type.

The LMS MUST conform to all requirements listed in Section 6 – LMS Requirements.

The LMS MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.

<a name="json_conformance"></a> 
##4.3 Optional JSON Values

If JSON properties are indicated as "optional", you MAY leave such properties out of the JSON structure being described. All JSON properties included with non-null values MUST be recorded in the LRS.

<a name="course_conformance"/>
## 4.4 Courses

A course MUST be bundled with course structure data that conform to all requirements listed in Section 13 and Section 14.
  
Course structure data MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  


<a name="concept"></a> 
#5.0 Conceptual Model: Informative  

Synopsis of the cmi5 model:
* An LMS imports a course structure, which may contain one or more AUs.
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
#6.0 LMS Requirements

The LMS MUST meet the following requirements to conform to this specification:  

* The LMS MUST implement an LRS as defined in the xAPI specification.
* The LMS MUST support Course Structures as defined in cmi5 Course Structure.
* The LMS MUST implement additional "State API" requirements to initialize the AU state as defined in Section 10.
* The LMS MUST implement the runtime launch interface as defined in Section 8.0 – Content Launch Mechanisms.
* The LMS MUST implement additional xAPI "Statement API" requirements as defined in Section 9.
* The LMS MUST implement additional xAPI "Agent Profile API" requirements as defined in Section 11.
* The LMS MUST implement a means to import course structures as defined in Section 6.1.
* The LMS MUST NOT provide permissions/credentials which allow the AU to issue voiding Statements.
* The LMS SHOULD implement a means to export course structures as defined in Section 6.1.
* The LMS SHOULD reject statements that conflict with the "Statement API" requirements as defined in Section 9.
* The LMS MUST void statements that are NOT rejected AND conflict with the "Statement API" requirements as defined in Section 9.

<a name="course_structures"></a>  
##6.1 Course Structures

* The LMS SHOULD implement a means to create and maintain course structures.<br>
* The LMS MUST implement the import of the Course Structure defined in Section 13 and Section 14. <br>
* The LMS SHOULD implement the export of the course data structure defined in Section 13 and Section 14. <br>
* The LMS SHOULD provide a user interface to the LMS administrative users to create and edit course structures internally.<br>
* The LMS MUST support course structures containing more than 1000 AUs.
* The LMS MUST support course structures conforming to the XSD schema defined in Section 13.2.


<a name="lms_state_api_requirements"></a>  
##6.2 LMS State API Requirements
The LMS MUST implement the State API Requirements as defined in Section 10.

<a name="lms_statement_api_requirements"></a>  
##6.3 LMS Statement API Requirements
The LMS MUST implement the Statement API Requirements as defined in Section 9.


<a name="au_requirements"></a>  
#7.0 AU Requirements

AU’s MUST meet the following requirements to conform to this specification:

1. The AU MUST implement the runtime launch interface as defined in Section 8 - Content Launch Mechanisms.
2. The AU MUST implement runtime communication defined in the xAPI Specification.
3. The AU MUST implement additional xAPI "Statement API" requirements as defined in Section 9.0.
4. The AU MUST implement additional xAPI "Agent Profile API" requirements as defined in Section 11.0.

<a name="au_state_api_requirements"></a> 
##7.1 AU State API Requirements

AU’s MUST meet the following requirements to conform to this specification:

* The AU MUST implement additional xAPI "Statement API" requirements as defined in Section 9.0 .
* The AU MUST implement additional xAPI "State API" requirements as defined in Section 10.
* The AU MUST implement additional xAPI "Agent Profile API" requirements as defined in Section 11.


<a name="au_statement_api_requirements"></a>  
##7.2 AU Statement API Requirements

<a name="placement"></a> 
###7.2.1 Placement of session ID in Statements

The AU MUST retrieve the value of session ID at launch time as specified in Section 10 State API.  The AU MUST place the value of the session ID in the context extensions for all xAPI statements it records.  

Usage in an xAPI Statement:

```javascript
"extensions": {
  "http://purl.org/xapi/cmi5/context/extensions/sessionid": <The session ID value provided by the LMS>
}
```
Example:
```javascript
"extensions": {
  "http://purl.org/xapi/cmi5/context/extensions/sessionid": "xyz123"
}
```

<a name="first_statement_au"></a> 
###7.2.2 First Statement API Call
The AU MUST issue a statement to the LRS after being launched, initialized, and ready for learner interaction using the Initialized verb as described in Section 9.3.2.

<a name="last_statement_au"></a>  
###7.2.3 Last Statement Call
The AU MUST issue a statement to the LRS prior to termination using the Terminated verb as described in Section 9.3.8.

<a name="type_statement_au"></a>  
###7.2.4 Types of Statements
The statements issued within an AU session could fall within the following categories:

* "cmi5 defined" - Statements using cmi5 defined verbs, category id, and context template.
* "cmi5 allowed" - Statements using any verb and cmi5 context template (but NOT including cmi5 category id).
* "cmi5 not-allowed" - Any statements not conforming with the cmi5 specification.

The AU MAY issue statements that are defined as "cmi5 allowed" statements per section 9.6.2. If "cmi5 allowed" statements are posted by the AU, they MUST occur between cmi5 statements using the "Initialized" verb and the "Terminated" verb. "cmi5 allowed" statements are not considered in cmi5 defined session management and completion rules.

<a name="content_launch"></a>  
#8.0 Content Launch Mechanisms

<a name="launch_method"></a>  
##8.1 Launch Method

The AU MUST be launched by the LMS using one of the following methods, depending on the launchMethod in the Course Structure (Section 7.1.4 AU Meta Data, URL):

When the launchMethod is "OwnWindow", the LMS MUST use one of the following:
* Spawning a new browser window for the AU.
* Re-directing the existing browser window to the AU.

When the launchMethod is "AnyWindow", the LMS may choose the window context of the AU.  All browser window options are acceptable - Frameset, New window, browser redirect, etc.

In either case, the AU MUST be launched by the LMS with a URL having query string launch parameters as defined in this section. The launch parameters MUST be name/value pairs in a query string appended to the URL that launches the AU.

If the AU's URL requires a query string for other purposes, then the names MUST NOT collide with named parameters defined below.

The order of the name/value pairs is not significant. AU’s MUST have the ability to
process them in any order.

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
http://la.cmi5.aicc.org/LA1/Start.html
?endpoint=http://cmi5-lms-system.org/lrslistner/
&fetch=http://cmi5-lms-system.org/tokenGen.htm?k=2390289x0
&actor={"objectType": "Agent","account": 
{"homePage": "http://www.example.com","name": "1625378"}
&registration=760e3480-ba55-4991-94b0-01820dbd23a2
&activityId=http://example.AU-content.com/example/001/statement
```

The values for the URL launch parameters are described below: 

<table>
  <tr><th colspan=2 align="left">endpoint</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>A URL to the LMS listener location for xAPI messages to be sent to.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>endpoint</em></strong> in the query string. The LMS SHOULD limit the use of the <strong><em>auth</em></strong> value for the duration of a specific user/AU/registration</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>endpoint</em></strong> value from the query string. The AU MUST use the <strong><em>endpoint </em></strong>value as the URL location to send xAPI messages to.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A URL-encoded URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>https://mylms.aicc.org/MyCMI5_listener.pl</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">fetch</th></tr>
  <tr><th align="right">Description:</th><td>The <strong><em>fetch</em></strong> URL is used by the AU to obtain an authentication token created &amp; managed by the LMS. The authentication token is used by the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>fetch</em></strong> in the Launch URL.<br>The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses SHOULD generate an error as defined in section 8.2. The authorization token returned by the <strong><em>fetch</em></strong> URL MUST be limited to the duration of a specific user session. </td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>fetch</em></strong> value from the query string. The AU MUST make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve the authorization token as defined in section 8.2. The AU MUST then place the authorization token in the Authorization headers of all HTTP messages made to the endpoint using the xAPI.  The AU SHOULD NOT make more than one post to the <strong><em>fetch</em></strong> URL.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>http://cmi5-lms-system.org/tokenGen.htm?k=2390289x0</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">actor</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>A JSON object of objectType "Agent" (as defined in the xAPI specification) that identifies the learner launching the AU so the AU will be able to include it in xAPI messages.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST populate the <strong><em>actor</em></strong>  parameter in the query string based on the authenticated learner’s identity. The LMS SHOULD create this parameter with an object that is specific to the LMS instance that does NOT include sensitive PII of the learner.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>actor</em></strong> value from the query string. The AU MUST use the <strong><em>actor</em></strong> value in API calls that require an "actor" property when sending xAPI messages.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A JSON object (as defined in Section 9.2)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>{"objectType": "Agent","account": {"homePage": "http://www.example.com","name": "1625378"}</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">registration</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>A Registration ID corresponding to the learner’s enrollment for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>registration</em></strong> in the query string based on the authenticated learner’s corresponding    enrollment for the Course that the AU being launched is a member of.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>registration</em></strong> value from the query string. The AU MUST use the <strong><em>registration</em></strong> value in API calls that require a "registration id" when sending xAPI messages</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>UUID (as defined in the xAPI specification)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td></td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">activityId</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The Activity ID of the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>activityId</em></strong> in the query string based on the definition of the AU in the course    structure.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>activityId</em></strong> value from the query string. The AU MUST use the <strong><em>activityId</em></strong> value in API calls that require an "activity id" when sending xAPI messages.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>IRI (as defined in the cmi5 Course Structure Section 7.1.4 - AU Metadata)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td></td></tr>
</table>

<br>
<a name="fetch_url"></a>  
##8.2 Authorization Token Fetch URL
<a name="fetch_url_overview"></a>  
###8.2.1 Overview
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
###8.2.2 Definition: auth-token
<table>
  <tr><th colspan=2 align="left">auth-token</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>An authorization token used in all xAPI communications with the LMS.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>auth-token</em></strong> in a JSON structure, as shown in Section 8.2.1, in its response to a <strong><em>fetch</em></strong> URL request. The response MUST have a Content-Type of "application/json".</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>auth-token</em></strong> value using an HTTP POST to the <strong><em>fetch</em></strong> URL. The AU MUST then place the authorization token in the Authorization headers of all HTTP messages made to the endpoint using the xAPI.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>QWxhZGRpbjpvcGVuIHNlc2FtZQ==</td></tr>
</table>

<a name="fetch_url_errors"></a>  
###8.2.3 Errors

<a name="duplicate_call_to_fetch_url"></a>  
####8.2.3.1 Duplicate call to fetch URL
The <strong><em>fetch</em></strong> URL is a "one-time use" URL and only the first request SHOULD return the <strong><em>auth-token</em></strong>. Subsequent requests made to the <strong><em>fetch</em></strong> during the session SHOULD generate an error.  The error SHOULD be returned in the form of a JSON structure using Content-Type "application/json".  An example of JSON structure is shown below:
```javascript
{
  "error-code": "1",
  "error-text": "The authorization token has already been returned."
}
```
<a name="fetch_url_error_values"></a>
####8.2.3.2 Error Values
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
##8.3 Other Launch Environments

Other launch environments are not currently implemented in this specification. cmi5 implementations for LMS’s and AU’s in these other environments will use the same REST communication interface as specified in xAPI specification.  The xAPI specification does not specify launch mechanisms.

<a name="xapi_data_model"/>  
#9.0 xAPI Statement Data Model  

<a name="statement_id" ></a>
##9.1 Statement ID
The AU will not provide a statement ID for cmi5 defined statements.  (The LRS will assign statement IDs.)
  
<a name="actor" ></a>
##9.2 Actor
The Actor property will be defined by the LMS. The Actor property for all statements with cmi5 defined verbs MUST be of objectType "Agent" and MUST contain an "account" as defined in the xAPI specification.

An Example of usage in a statement:

```javascript
{
  "actor": {
    "objectType": "Agent",
    "account": {
      "homePage": "http://www.example.com",
      "name": "1625378"
    }
  },
  "verb": {...},
  "object": {...},
  "result": {...},
  "context": {...},
  "attachments": {...}
}
```

<a name="verbs" ></a> 
##9.3 Verbs  

The following xAPI verbs are defined in this specification.

Note that "cmi5 allowed" statements are NOT subject to the usage rules in this section. 

All statements in this section refer to "cmi5 defined" statements unless otherwise noted.

AUs MUST use the below verbs that are indicated as mandatory in other sections of this specification.

AU Verb Ordering Rules within an AU session are as follows:

* Verbs MUST NOT be duplicated (in cmi5 defined statements)
* More than one of the set of {"Passed","Failed"} verbs MUST NOT be used (in cmi5 defined statements)
* The "Initialized" verb MUST be the first statement (cmi5 allowed or defined)
* The "Terminated" verb MUST be the Last statement (cmi5 allowed or defined)

AUs may use additional verbs not listed in this specification.

Regardless of the verbs the AUs use in statements, the LMS MUST record and provide reporting for all statements. 

<a name="verbs_launched"></a>
###9.3.1 Launched
<table>
<tr><th align="left">Verb</th><td>Launched</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/launched</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Launched" }</td></tr>
<tr><th align="left">Description</th><td>The verb "Launched" indicates that the AU was launched by the LMS.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS before launching an AU.  (See Statement API, Section 10) The LMS MUST NOT issue multiple statements with "Launched" for the same AU within a given AU session.</td></tr>
<tr><th align="left">Usage</th><td>A "Launched" statement is used to indicate that the LMS has launched the AU. It SHOULD be used in combination with the "Initialized" statement sent by the AU in a reasonable period of time to determine whether the AU was successfully launched. </td></tr>
</table>

<a name="verbs_initialized"></a>
###9.3.2 Initialized
<table>
<tr><th align="left">Verb</th><td>Initialized</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/initialized</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Initialized" }</td></tr>
<tr><th align="left">Description</th><td>An "Initialized" statement is used by the AU to indicate that it has been fully initialized and MUST follow the "Launched" statement created by the LMS within a reasonable period of time.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST use "Initialized" in the first statement (of any kind) in the AU session.  The AU MUST NOT issue multiple statements with "Initialized" for the same AU within a given AU session.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>Verify that this verb is recorded by the AU immediately after launch.</td></tr>
<tr><th align="left">Usage</th><td>An "Initialized" statement is used by the AU to indicate that it has been fully initialized and SHOULD follow the "Launched" statement created by the LMS within a reasonable period of time.</td></tr>
</table>

<a name="verbs_completed"></a>
###9.3.3 Completed
<table>
<tr><th align="left">Verb</th><td>Completed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/completed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Completed" }</td></tr>
<tr><th align="left">Description</th><td>The verb "Completed" indicates the learner viewed or did all of the relevant activities in an AU presentation.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST record a statement containing the "Completed" verb when the learner has experienced all relevant material in an AU. The AU MUST NOT issue multiple statements with "Completed" for the same AU within a given AU session or course registration for a given learner.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>None.</td></tr>
<tr><th align="left">Usage</th><td>The criterion for "Completed" is determined by the course designer.</td></tr>
</table>

<a name="verbs_passed"></a>
###9.3.4 Passed
<table>
<tr><th align="left">Verb</th><td>Passed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/passed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Passed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and succeeded in a judged activity in the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST record a statement containing the "Passed" verb when the learner has attempted and passed the AU. The AU MUST NOT issue multiple statements with "Passed" for the same AU within a given AU session or course registration for a given learner. If the "Passed" statement contains a (scaled) score, the (scaled) score MUST be equal to or greater than the "MasteryScore" indicated in the course structure. (See course structure section 7.1.4)</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST record "MasteryScore" data in the state API (if present in the course structure) for the AU prior to initial AU launch. (See Section 10) The LMS MUST use either "Passed" or "Completed" statements (or both) based on the moveOn criteria for the AU as defined in the Course Structure. (See Course Structure,  Section 7.1.4 - MoveOn).</td></tr>
<tr><th align="left">Usage</th><td>The AU MUST record a statement containing the "Passed" verb when the learner has attempted and successfully passed the judged activity.</td></tr>
</table>

<a name="verbs_failed"></a>
###9.3.5 Failed
<table>
<tr><th align="left">Verb</th><td>Failed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/failed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Failed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and failed in a judged activity in the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST record a statement containing the "Failed" verb when the learner has attempted and failed the AU.  If the "Failed" statement contains a score, the score MUST be less than the "MasteryScore" indicated in the course structure.  (See Course Structure, Section 7.1.4 - MasteryScore). A "Failed" statement MUST NOT be issued after a "Passed" statement has been issued.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST record "MasteryScore" data in the state API (if present in the course structure) for the AU prior to initial AU launch.  (See Section 10).<br>
<br>
The LMS MUST use either "Passed" or "Completed" statements (or both) for determining course completion (or course collateral credit) criteria for the AU.  (See Course Structure, Section 7.1.4 - MasteryScore).</td></tr>
<tr><th align="left">Usage</th><td>The AU MUST record a statement containing the "Failed" verb when the learner has attempted and failed the judged activity.</td></tr>
</table>

<a name="verbs_abandoned"></a>
###9.3.6 Abandoned
<table>
<tr><th align="left">Verb</th><td>Abandoned</td></tr>
<tr><th align="left">ID</th><td>http://purl.org/xapi/adl/verbs/abandoned</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Abandoned" }</td></tr>
<tr><th align="left">Description</th><td>The verb "Abandoned" indicates that the AU session was abnormally terminated by a learner's action (or due to a system failure).</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use the "Terminated" statement to determine that the AU session has ended.  In the absence of a "Terminated" statement, the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS MUST record an "Abandoned" statement on behalf of the AU indicating an abnormal session termination.  After recording an "Abandoned" statement, the LMS MUST NOT allow any additional statements to be recorded for that session.</td></tr>
<tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>

<a name="verbs_waived"></a>
###9.3.7 Waived
<table>
<tr><th align="left">Verb</th><td>Waived</td></tr>
<tr><th align="left">ID</th><td>http://purl.org/xapi/adl/verbs/waived</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Received Waiver" }</td></tr>
<tr><th align="left">Description</th><td>The verb "Waived" indicates that the LMS has determined that the AU requirements were met by means other than completing the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS when it determines that the AU may be waived.  A statement containing a "Waived" verb MUST include a "reason" in the extension property of the Statement Result.  (See Section 9.6.2.2) The LMS MUST NOT issue multiple statements with "Waived" for the same AU within a given AU session or course registration for a given learner.</td></tr>
<tr><th align="left">Usage</th><td>A "Waived" statement is used by the LMS to indicate that the AU may be skipped by the learner.</td></tr>
</table>

<a name="verbs_terminated"></a>
###9.3.8 Terminated
<table>
<tr><th align="left">Verb</th><td>Terminated</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/terminated</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Terminated" }</td></tr>
<tr><th align="left">Description</th><td>The verb "Terminated" indicates that the AU was terminated by the Learner and that the AU will not be recording any more statements for the launch session.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST record a statement containing the "Terminated" verb. This statement MUST be the last statement (of any kind) recorded by the AU in a session.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use the "Terminated" statement to determine that the AU session has ended.  In the absence of an "Terminated" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS MUST record a "Abandoned" statement on behalf of the AU indicating an abnormal session termination per section 9.3.8 Abandoned.</td></tr>
<tr><th align="left">Usage</th><td>See obligations.</td></tr>
</table>

<a name="verbs_satisfied"></a>
###9.3.9 Satisfied
<table>
<tr><th align="left">Verb</th><td>Satisfied</td></tr>
<tr><th align="left">ID</th><td>http://purl.org/xapi/adl/verbs/satisfied</td></tr>
<tr><th align="left">Description</th><td>The verb "Satisfied" indicates that the LMS has determined that the Learner has met the moveOn criteria of all AU's in a block or has met the moveOn criteria for all AU's in the course.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<th align="left" nowrap>LMS Obligations</th><td>
The LMS MUST use the "Satisfied" statement when the learner has met the moveOn criteria of all AU's in a block.  In this statement the LMS MUST use the block id (Section 7.1.2 in the cmi5 Course Structure document) as the Object id (Section 9.4 - Object).<br>
<br>
The LMS MUST also use the "Satisfied" statement when the learner has met the moveOn criteria for all AU's in a course.  In this statement the LMS MUST use the course id (Section 7.1.1 in the cmi5 Course Structure document) as the Object id (Section 9.4 - Object)  The LMS MUST NOT issue multiple statements with "Satisfied" for the same AU within a given AU session or course registration for a given learner.
</td></tr>
<tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>

<br>
<br>

<a name="object"></a> 
##9.4 Object 
The Object in a cmi5 defined statement represents the AU.  An Object MUST be present, as specified in this section, in all statements with cmi5 defined verbs.

<a name="object_type"></a> 
###9.4.1 objectType
The objectType property of an Object in statements with a cmi5 verb MUST be set to "Activity".

<a name="object_id"></a> 
###9.4.2 id 
The value of the Object's ID property for a given AU MUST match the AU ID (activityId) defined in the launch URL and the Course Structure.

An Example of usage in a statement:

```javascript
{
  "actor": {...},
  "verb": {
    "id": "http://adlnet.gov/expapi/verbs/launched",
    "display": {
      "en-US": "Launched"
    }
  },
  "object": {
    "id":"<AU identifier>",
    "objectType": "Activity"
  },
  "result": {...},
  "context": {...},
  "attachments": {...}
}
```

<a name="result"></a> 
##9.5 Result
Result may be present in a statement depending on the cmi5 verb used.  

Example JSON:
```javascript
"result": {
  "score": {
    "scaled": 0.65,
    "raw": 65,
    "min": 0,
    "max": 100
  },
  "success": false,
  "completion": false,
  "duration": "PT30M",
  "extensions": {
    "http://purl.org/xapi/cmi5/result/extensions/progress": 100
  }
}
 ```

<a name="score"></a> 
###9.5.1 Score

A score is not required to be reported.  If a score is reported by an AU, the verb MUST be consistent with masteryScore (if defined for the AU in the Course Structure).

<ul><li><strong>scaled</strong><br>A decimal value between 0 and 1.</li>
<li><strong>raw</strong><br>An integer value between the "min" and "max" properties of the <em><strong>score</strong></em> object.  When the "raw" value is provided, the AU MUST also provide the "min" and "max" values for <em><strong>score</strong></em>.</li>
<li><strong>min</strong><br>An integer value indicating the minimum value for the "raw" score property.</li>
<li><strong>max</strong><br>An integer value indicating the maximum value for the "raw" score property.</li>
</ul>

<a name="success"></a>
###9.5.2 Success 

The success property of the result MUST be set to true for statements having the following cmi5 defined verbs:

- Passed
- Waived

The success property of the result MUST be set to false for statements having the following cmi5 defined verbs:

- Failed
- Abandoned

<a name="completion"></a>
###9.5.3 Completion
The completion property of the result MUST be set to true for statements having the following cmi5 defined verbs:

- Completed
- Waived

The completion property of the result MUST be set to false for statements having the following cmi5 defined verbs:

- Failed
- Abandoned

<a name="duration"></a>
###9.5.4 Duration
The duration property is an ISO 8601 formatted time value required in certain statements as defined in this section.
<a name="au_statements_that_include_duration"></a>
####9.5.4.1 AU statements that include duration
##### Terminated Statement
The AU MUST include the duration property in "Terminated" statements.  The AU SHOULD calculate duration for Terminated statements as the time difference between the "Initialized" statement and the "Terminated" statement.  The AU may use other methods to calculate the duration based on criteria determined by the AU.
##### Completed Statement
The AU MUST include the duration property in "Completed" statements.  The AU SHOULD calculate duration as the time spent by the learner to achieve completion status.
##### Passed Statement
The AU MUST include the duration property in "Passed" statements.  The AU SHOULD calculate duration as the time spent by the learner to attempt and succeed in a judged activity of the AU. 
##### Failed Statement
The AU MUST include the duration property in "Failed" statements. The AU SHOULD calculate duration as the time spent by the learner to attempt and fail in a judged activity of the AU.

<a name="lms_statements_that_include_duration"></a>
####9.5.4.2 LMS statements that include duration
##### Abandoned Statement
The duration property SHOULD be included in "Abandoned" statements. The duration property SHOULD be set as the total session time, calculated as the time between the "Launched" statement and the last statement issued by the AU.

<a name="result_extensions"></a>
###9.5.5 Extensions
<a name="result_extensions_progress"></a>
####9.5.5.1 Progress
An integer value indicating the completion of the AU as a percentage. The AU may set this value in statements to indicate level of completion between 0 and 100 percent.


Progress is defined in extensions using the following IRI:

      http://purl.org/xapi/cmi5/result/extensions/progress

<a name="context"></a> 
##9.6 Context
All statements with cmi5 defined verbs MUST contain a context as defined in this section. 

Sample JSON:
```javascript
   "context": {
     "registration": "<registration value provided by LMS>",
     "contextActivities": {
        "category": {[
          {"id": "http://purl.org/xapi/cmi5/context/categories/moveon"},
          {"id": "http://purl.org/xapi/cmi5/context/categories/cmi5"}
        ]}
     },
     "extensions" {
       "http://purl.org/xapi/cmi5/context/extensions/sessionid": "<the value of session ID provided by the LMS>",
       "http://purl.org/xapi/cmi5/context/extensions/reason": "<reason for 'waived' verb, if statement is 'waived' statement only>",
      }
   }
```

<a name="registration"></a> 
###9.6.1 registration
The value for the registration property used in the context object MUST be the value provided by the LMS.  The LMS MUST generate this value and pass it to the AU via the launch URL.

<a name="context_activities"></a>
###9.6.2 contextActivities

The purpose of this property is to facilitate searches of the LRS by the LMS or other reporting systems. contextActivities contain category objects whose entries can be used as wildcard searches. Each category is tagged with name value pairs of "id" and an IRI.

All cmi5 defined statements MUST have a category with an "id" of "http://purl.org/xapi/cmi5/context/categories/cmi5".

All statements that do NOT include a category with an "id" of "http://purl.org/xapi/cmi5/context/categories/cmi5" are "cmi5 allowed" statements. An AU MAY issue "cmi5 allowed" statements using cmi5 verbs or verbs defined outside the scope of the cmi5 specification.

Statements with a Result object (Section 9.5) that include either "success" or "completion" properties MUST have a category with an "id" of "http://purl.org/xapi/cmi5/context/categories/moveon". Other statements MUST NOT include this Activity.

<a name="extensions"></a> 
###9.6.3 extensions
The following are extensions specified for cmi5.  Other extensions are permitted provided they do not conflict or duplicate the ones specified here.  

<a name="context_extensions_session_id"></a>
####9.6.3.1 session ID

<table>
  <tr><th align ="right" nowrap>ID:</th><td>http://purl.org/xapi/cmi5/context/extensions/sessionid</td></tr>
  <tr><th align ="right" nowrap>Description:</th><td>A unique identifier for a single AU launch session based on actor and course registration </td></tr>
  <tr><th align ="right" nowrap>LMS Usage:</th><td>The value for session ID is generated by the LMS. The LMS MUST also record the session ID in the State API (See Section 10) prior to launching an AU. The LMS MUST also provide the session ID in the context as an extension for all Statements (with cmi5 defined verbs) it makes directly in the LRS.</td></tr>
  <tr><th align ="right" nowrap>AU Usage:</th><td>An AU MUST include the session ID provided by the LMS in the context as an extension for all Statements (with cmi5 defined verbs) it makes directly in the LRS. </td></tr>
 <tr><th align ="right" nowrap>AU Obligation:</th><td>Required</td></tr>
 <tr><th align ="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align ="right" nowrap>Value space:</th><td>string value</td></tr>
  <tr><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

<a name="context_extensions_reason"></a>
####9.6.3.2 reason

  <table>
  <tr><th align ="right" nowrap>ID:</th><td>http://purl.org/xapi/cmi5/result/extensions/reason</td></tr>
  <tr><th align ="right" nowrap>Description:</th><td>Indicates the reason why an AU was "waived" (marked complete by an alternative means)</td></tr>
  <tr><th align ="right" nowrap>LMS Usage:</th><td>The LMS MUST set this value in statements it makes with the verb "Waived". The value SHOULD be one of the following -

<ul>
<li><b>Tested Out</b> – An Assessment was completed by the student to waive the AU.</li>  
<li><b>Equivalent AU</b> - The student successfully completed an equivalent AU (in the same course) to waive the AU. </li>  
<li><b>Equivalent Outside Activity</b> – The student successfully completed an equivalent activity outside of the course to waive the AU. </li>    
<li><b>Administrative</b> – The LMS administrative user marked the AU complete.</li> 
</ul>
</td></tr>
  <tr><th align ="right" nowrap>AU Usage:</th><td>The AU may retrieve this value from the LRS and use it to change presentation behavior based on the "reason".</td></tr>
 <tr><th align ="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
  <tr><th align ="right" nowrap>LMS Obligation:</th><td>This is a required extension for LMS statements that include the Waived verb.</td></tr>
  <tr><th align ="right" nowrap>Data type:</th><td>String</td></tr>
  <tr><th align ="right" nowrap>Value space:</th><td><ul>
<li>"Tested Out"</li>  
<li>"Equivalent AU"</li>  
<li>"Equivalent Outside Activity"</li>    
<li>"Administrative"</li> 
</ul></td></tr>
  <tr><th align ="right" nowrap>Sample value:</th><td>Tested Out</td></tr>
</table>

<a name="timestamp"></a> 
##9.7 Timestamp

To ensure statement ordering requirements are met, all statements MUST include a timestamp property per the xAPI specification. All timestamps MUST be recorded in UTC time.


<a name="xapi_state"></a>  
#10.0 xAPI State Data Model

Prior to launching an AU, the LMS MUST create a document in the State API record in the LRS.  This MUST be a JSON document, as defined in this section, with a document name (stateId) of "LMS.LaunchData". The LMS MUST only create one State document for the combination of activityId, agent, registration, and stateId.  

An example of the JSON document is shown below.

```javascript
{
  "contextTemplate": {
    "extensions": {
      "http://purl.org/xapi/cmi5/context/extensions/sessionid": "<The LMS generated session ID value>"
    }
  },
  "launchMode": "<launchMode value>",
  "launchParameters": "<launch parameters from Course Structure>",
  "masteryScore": "<mastery score from the Course Structure>",
  "moveOn": "<moveOn value from the Course Structure>",
  "returnURL": "<URL value>",
  "entitlementKey": {
    "courseStructure": "<Entitlement data or key from Course Structure>",
    "alternate": "<alternateEntitlementKey>"
  }
}
```

The properties for the "LMS.LaunchData" document are described below.

<table>
  <tr><th colspan=2 align="left">contextTemplate</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>Context template for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>LMS MUST include a contextTemplate and place the value for <strong><em>session ID</em></strong> in the "http://purl.org/xapi/cmi5/results/extensions/session" element of the context object's extension collection.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>AU MUST get the contextTemplate value from the "LMS.LaunchData" state document. The AU MUST NOT modify or delete the "LMS.LaunchData" state document. The AU MUST use the contextTemplate as a template for the context property in all xAPI statements it records to the LMS. While the AU may include additional values in the context object of such statements, it MUST NOT overwrite any values provided in the contextTemplate. NOTE: this will include the session ID specified by the LMS.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>JSON context object as defined in xAPI 1.0.</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>LMS implementation specific.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td></td></tr>
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
      <ul><li>Normal<br>The AU MUST record Initialized and Terminated verb statements.  The AU MUST record other cmi5 verb statements per the requirements defined in section 9.3 – Verbs.</li>
      <li>Browse<br>The AU MUST record "Initialized" and "Terminated" verb statements.  The AU MUST NOT record other cmi5 verb statements.</li>
      <li>Review<br>The AU MUST record "Initialized" and "Terminated" verb statements.  The AU MUST NOT record other cmi5 verb statements.</li></ul></td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>"Normal", "Browse", or "Review"</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"Normal"</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">launchParameters</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The launch parameters defined in the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>If the <strong><em>launchParameters</em></strong> were defined by the course designer in the Course Structure, the LMS MUST include the  <strong><em>launchParameters</em></strong> in the State API document.</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST include the <strong><em>launchParameters</em></strong> in the State API document when defined in the Course Structure.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD get the <strong><em>launchParameters</em></strong> value from the State API document if the launch parameters were defined in the Course Structure.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>Defined by the course designer.</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Defined by the course designer.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>{"param1": "Lorem ipsum dolor sit amet", "param2": [1,2,3,4,5],"param3": {"a": 1,"b": 2}}</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">masteryScore</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The MasteryScore from the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST include the MasteryScore value based on the value defined in the course structure for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST issue Passed or Failed statements based on the MasteryScore provided. (See Sections 9.3.6 and 9.3.7)</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>decimal</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Decimal value between 0 and 1.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>0.75</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">moveOn</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>The moveOn value from the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST include the moveOn value defined in the course structure for the AU.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MAY get the moveOn value from the "LMS.LaunchData" state document and may use the value to modify its behavior.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>moveOn values as defined in the cmi5 Course Structure Specification (Section 7.1.4 – AU Metadata)</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"Passed"</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">returnURL</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>Used by the LMS when launching the AU if the LMS requires the AU (in a web-browser environment) to redirect the learner when he or she exits the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>If the <strong><em>returnURL</em></strong> is provided.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS may include the <strong><em>returnURL</em></strong> when the learner SHOULD be redirected to the <strong><em>returnURL</em></strong> on exiting the course.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>returnURL</em></strong> value from the "LMS.LaunchData" state document. If the <strong><em>returnURL</em></strong> is provided, the AU MUST redirect the current browser window to the <strong><em>returnURL</em></strong> when the AU is terminated.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>URL</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Any URL.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>http://www.example.com/lms/mod/xapilaunch/view.php?id=12</td></tr>
</table>

<table>
  <tr><th colspan=2 align="left">entitlementKey: courseStructure</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>Entitlement data or key from the Course Structure. The       <strong>entitlementKey</strong> values may be used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
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
  <tr><th align="right" nowrap>Description:</th><td>Entitlement data or key from some other source as agreed upon between the LMS and the AU. The <strong>entitlementKey</strong> values may be used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST obtain the alternate entitlement key from a source as agreed upon with the AU.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value is defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"xyz-123-9999"</td></tr>
</table>

__State API PUT Properties__:

* _activityId_: Activity ID for the AU (from the course structure)  
* _agent_: agent representing the LMS learner being enrolled.  This MUST match the actor property generated by LMS at AU launch time.  
* _registration_: Registration ID representing the LMS learner enrollment in the course. This MUST match Registration ID used by the LMS at AU launch time.  
* _stateId_: LMS.LaunchData  



<a name="xapi_agent_profile"></a>   
#11.0 xAPI Agent Profile Data Model  

In cmi5, Learner Preferences are scoped to the learner.  Both the LMS and the AU may write changes to Learner Preferences in the xAPI Agent Profile.  The LMS/LRS may choose to ignore or override Learner Preference changes requested by the AU by returning a "403 Forbidden" response as defined in the xAPI specification (Section 7.6).  The AU MUST NOT treat the 403 response as an error condition.  

On startup, the AU MUST retrieve the Learner Preferences document from the Agent Profile.

When reading or writing to the Agent Profile, the document name MUST be "CMI5LearnerPreferences" and the format MUST be a JSON structure as shown below:

```javascript
{
  "languagePreference": "<values for languages>",
  "audioPreference": "<on or off>"
}
```
<a name="language_preference"></a>
##11.1  languagePreference
The languagePreference MUST be a comma-separated list of RFC 5646 Language Tags as indicated in the xAPI specification (Section 5.2).  In the list, languages MUST be specified in order of user preference.  In the example below, the user's first preference for language is en-US.  The user's second preference for language is fr-FR and the third preference is fr-BE.

```javascript
{
  "languagePreference": "en-US,fr-FR,fr-BE",
  ...
}
```

If the AU supports multiple languages, the AU SHOULD display in the language preference order of the user as in the example above. If the AU supported "zh-CN", "fr-BE" and "fr-FR", it SHOULD display in "fr-FR".  If the AU does not support multiple languages, or if no languagePreference is specified in the Agent Profile, it may display in its default language.

<a name="audio_preference"></a>
##11.2 audioPreference
The audioPrefence value indicates whether the audio SHOULD be "on" or "off".  The AU MUST turn the audio on or off at startup based on this value.  If no value is provided in the Agent Profile for audioPreference the AU MAY use its own default value.

Example:
```javascript
{
  "audioPreference": "on",
  ...
}
```


<a name="xapi_activity_profile"></a>  
#12.0 xAPI Activity Profile Data Model

The AU may use the Activity Profile API according to the xAPI specification (Section 7.5 - Activity Profile API).


<a name="course_requirements"/>
#13.0 Course Structure Data Requirements  

<a name="course_structure_data_model"/>
##13.1 Course Structure Data Model  

<a name="course_level_meta_data"/>
###13.1.1 Course Level Metadata  
 
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
         &lt;course id="http&#58;//www.yoursite.com/identifiers/course/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/course&gt;<br></p>
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
      A detailed  description of the course.</p>
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



<a name="block_meta_data"/>
### 13.1.2 Block Metadata

The data in this section are used for the block structures with group AUs.  A Block consists of one or more AUs. Blocks can also contain references to objectives and other Blocks.

<table border="1" cellspacing="0" cellpadding="0">
   <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type: </strong> IRI</p></td>
    <td width="811" valign="top"><p><strong>Description: </strong>A globally unique IRI to identify the Block in xAPI messages made by the LMS.</p>
      <p><strong>Value space: </strong>Values defined by course designer</p>
      <p><strong>Sample value:</strong><br>
      &lt;block id="http&#58;//www.yoursite.com/identifiers/aublock/005430bf-b3ba-45e6-b47b-d629603d83d8" &gt; &hellip; &lt;/block&gt;
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
    &nbsp;&nbsp; &lt;objective idref="http&#58;//www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" /&gt;<br>
    &lt;/objectives&gt;<br>
    </td>  
  </tr>
</table>


<a name="objectives_meta_data"/>  
###13.1.3 Objectives Metadata   

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
    &lt;objective id="http&#58;//www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/objective&gt;</p>
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


<a name="au_meta_data"/>  
###13.1.4 AU Metadata  

The data in this section are used by the LMS to locate the AU and provide launch data. AUs may also contain objectives.


<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type: </strong> IRI</p>
    </td>
    <td width="815" valign="top"><p><strong>Description: </strong>A globally unique IRI that the AU uses to identify itself to the LMS in xAPI messages to the LMS.</p>
      <p><strong>Value space: </strong>Values are defined by the course designer.</p>
      <p><strong>Sample value:</strong><br>
      &lt;au id="http&#58;//www.yoursite.com/identifiers/activity/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>launchMethod</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br>
        <strong>Data type:</strong> string </p>
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
        <li>The masteryScore is passed to the AU at runtime by the LMS (as defined in the cmi5 Runtime Specification).</li>
        <li>If the AU has scoring, it will use the masteryScore to determine pass/fail (as defined in the cmi5 Runtime Specification)</li>
        <li>The masteryScore is a scaled, decimal value between 0 and 1.</li>
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
    <td colspan="2" valign="top"><h3>authenticationMethod</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br>
        <strong>Data type:</strong> string </p>
    </td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to specify which authentication method the AU MUST use.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>Based on the value of authenticationMethod, the LMS will place a parameter in the AU launch interface to indicate to the AU which authentication method to use (in accordance with the cmi5 Runtime Specification)</li>
        <li>authenticationMethod Value = "Basic" : If the LMS indicates to the AU launch interface to use basic HTTP authentication and passes an HTTP authentication token to the AU using the launch interface. This is currently the only option.  Future versions of this specification may add other authentication options.</li>
      </ul>
      <p><strong>Value space:</strong></p>
      <blockquote>
        <p>"Basic"<br>
      </p>
      </blockquote>
      <p><strong>Sample value: </strong><br>
      &lt;au id="&hellip;" authenticationMethod="Basic"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>activityType</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br>
        <strong>Data type:</strong> IRI<br><strong>Default value:</strong> <em>None</em> </p></td>
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
      <strong>Data type:</strong> string </p>
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
    &nbsp;&nbsp; &lt;objective idref="http&#58;//www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" /&gt;<br>
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
          <li>Regardless of the value of &lt;application&gt;, the remaining portion of the URL MUST conform to HTTP/S conventions, such as named value pair parameters.</li>
          <li>If the url includes a query string, the values from that query string MUST be merged with the cmi5 parameters at launch time (see Section 8.1.1 of the cmi5 Runtime Environment).</li>
     </ul>
      <p><strong>Value space:</strong> Values are determined by the course designer.</p>
      <p><strong>Sample value:</strong><br>
      &lt;url&gt;<br>
      http://www.mycourses.com/courseX.html<br>
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
      Static launch parameters defined by the course designer.  The LMS is required to store this data and provide it to the AU if    requested by the AU during runtime.<br>
      </p>
      <p><strong>Value space:</strong><br>
        Values are defined by the course designer.</p>
      <p>
        <strong>Sample value:</strong><br>
        &lt;launchParameters&gt;<br>
        {"param1": "Lorem ipsum dolor sit amet", "param2": [1,2,3,4,5],"param3": {"a": 1,"b": 2}}<br>
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

<a name="vendor_meta_data"/>
### 13.1.5 Vendor Specific Metadata (Extensions)

Course Designers MAY place their own namespaced elements into the course structure and thus define an extension for the source structure specification. For that they MUST provide a XML Schema Definition and SHOULD provide a human readable specification describing these vendor specific extensions. These extensions MUST keep the course structure XML valid. An importing LMS MAY ignore these elements. Therefore the extension SHOULD be created in such a manner that a course is still useable if the LMS does not support the additional elements.

To achieve a larger distribution of their extension course designers SHOULD choose a free or open source license for their specification and make it publicly available.

<a name="course_structure_xsd"/>  
## 13.2 Course Structure XSD 

The following is the XML schema for a course structure file.  
All course structures created for LMS import functionality and created by the LMS for export MUST conform to this XSD and be named "cmi5.xml".

```XML
<xs:schema xmlns="http://www.adlnet.gov/cmi5/CourseStructure.xsd"
           xmlns:xs="http://www.w3.org/2001/XMLSchema"
           targetNamespace="http://www.adlnet.gov/cmi5/CourseStructure.xsd" elementFormDefault="qualified"
           id="cmi5CourseStructure">
  <xs:element name="courseStructure" type="courseType"/>
  <xs:complexType name="courseType">
    <xs:sequence>
      <xs:element name="course">
        <xs:complexType>
          <xs:sequence>
            <xs:element name="title" type="textType"/>
            <xs:element name="description" type="textType"/>
            <xs:group ref="anyElement"/>
          </xs:sequence>
          <xs:attributeGroup ref="anyAttribute"/>
          <xs:attribute name="id" type="xs:anyURI" use="required"/>
        </xs:complexType>
      </xs:element>
      <xs:element name="objectives" type="objectivesType" minOccurs="0"/>
      <xs:choice minOccurs="1" maxOccurs="unbounded">
        <xs:element name="au" type="auType"/>
        <xs:element name="block" type="blockType"/>
      </xs:choice>
      <xs:group ref="anyElement"/>
    </xs:sequence>
    <xs:attributeGroup ref="anyAttribute"/>
  </xs:complexType>
  <xs:complexType name="blockType">
    <xs:sequence>
      <xs:element name="title" type="textType"/>
      <xs:element name="description" type="textType"/>
      <xs:element name="objectives" type="referencesObjectivesType" minOccurs="0"/>
      <xs:choice minOccurs="1" maxOccurs="unbounded">
        <xs:element name="au" type="auType"/>
        <xs:element name="block" type="blockType"/>
      </xs:choice>
      <xs:group ref="anyElement"/>
    </xs:sequence>
    <xs:attributeGroup ref="anyAttribute"/>
    <xs:attribute name="id" type="xs:anyURI" use="required"/>
  </xs:complexType>
  <xs:complexType name="auType">
    <xs:sequence>
      <xs:element name="title" type="textType"/>
      <xs:element name="description" type="textType"/>
      <xs:element name="objectives" type="referencesObjectivesType" minOccurs="0"/>
      <xs:element name="url">
        <xs:simpleType>
          <xs:restriction base="xs:anyURI">
            <xs:minLength value="1"/>
          </xs:restriction>
        </xs:simpleType>
      </xs:element>
      <xs:element name="launchParameters" minOccurs="0"/>
      <xs:element name="entitlementKey" minOccurs="0"/>
      <xs:group ref="anyElement"/>
    </xs:sequence>
    <xs:attributeGroup ref="anyAttribute"/>
    <xs:attribute name="id" type="xs:anyURI" use="required"/>
    <xs:attribute name="moveOn" default="NotApplicable">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="NotApplicable"/>
          <xs:enumeration value="Passed"/>
          <xs:enumeration value="Completed"/>
          <xs:enumeration value="CompletedAndPassed"/>
          <xs:enumeration value="CompletedOrPassed"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="masteryScore" use="optional">
      <xs:simpleType>
        <xs:restriction base="xs:decimal">
          <xs:minInclusive value="0"/>
          <xs:maxInclusive value="1"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="authenticationMethod" default="Basic">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="Basic"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="launchMethod" default="AnyWindow">
      <xs:simpleType>
        <xs:restriction base="xs:string">
          <xs:enumeration value="AnyWindow"/>
          <xs:enumeration value="OwnWindow"/>
        </xs:restriction>
      </xs:simpleType>
    </xs:attribute>
    <xs:attribute name="activityType" use="optional" type="xs:string"/>
  </xs:complexType>
  <xs:complexType name="objectivesType">
    <xs:sequence>
      <xs:element name="objective" minOccurs="1" maxOccurs="unbounded">
        <xs:complexType>
          <xs:all>
            <xs:element name="title" type="textType"/>
            <xs:element name="description" type="textType"/>
          </xs:all>
          <xs:attribute name="id" type="xs:anyURI" use="required"/>
        </xs:complexType>
      </xs:element>
      <xs:group ref="anyElement"/>
    </xs:sequence>
    <xs:attributeGroup ref="anyAttribute"/>
  </xs:complexType>
  <xs:complexType name="referencesObjectivesType">
    <xs:sequence>
      <xs:element name="objective" maxOccurs="unbounded">
        <xs:complexType>
          <xs:attribute name="idref" type="xs:anyURI"></xs:attribute>
        </xs:complexType>
      </xs:element>
      <xs:group ref="anyElement"/>
    </xs:sequence>
    <xs:attributeGroup ref="anyAttribute"/>
  </xs:complexType>
  <xs:complexType name="textType">
    <xs:sequence>
      <xs:element name="langstring" maxOccurs="unbounded" minOccurs="1">
        <xs:complexType>
          <xs:simpleContent>
            <xs:extension base="xs:string">
              <xs:attribute name="lang" type="xs:language"/>
              <xs:attributeGroup ref="anyAttribute"/>
            </xs:extension>
          </xs:simpleContent>
        </xs:complexType>
      </xs:element>
      <xs:group ref="anyElement"/>
    </xs:sequence>
    <xs:attributeGroup ref="anyAttribute"/>
  </xs:complexType>
  <xs:simpleType name="baseLanguagesType">
    <xs:list itemType="xs:language"></xs:list>
  </xs:simpleType>
  <xs:complexType name="languagesType">
    <xs:simpleContent>
      <xs:extension base="baseLanguagesType">
        <xs:attributeGroup ref="anyAttribute"/>
      </xs:extension>
    </xs:simpleContent>
  </xs:complexType>

  <xs:group name="anyElement">
    <xs:sequence>
      <xs:any namespace="##other" processContents="lax" minOccurs="0" maxOccurs="unbounded"/>
    </xs:sequence>
  </xs:group>
  <xs:attributeGroup name="anyAttribute">
    <xs:anyAttribute namespace="##other" processContents="lax"/>
  </xs:attributeGroup>
</xs:schema>
```

<a name="course_package"/>
#14.0 Course Package
For the course import and export defined in Section 6.1, the LMS MUST support all of the following formats:
<ul><li>Zip32</li>
<li>Zip64</li>
<li>A course structure XML file</li>
</ul>
<a name="course_packages_in_zip_format"></a>
##14.1 Course Packages in ZIP Format
The two ZIP file formats MUST follow the specification defined at https://www.pkware.com/support/zip-app-note.  When the ZIP file is used to package a course, it MUST contain the course structure XML file at its root directory and it MAY contain media associated with the course AUs.

<ul><li>Any media included in a ZIP course package MUST use relative URL references in the Course Structure XML.</li>
<li>Any media not included in a ZIP course package MUST use fully qualified URL references in the Course Structure XML.</li>
<li>A ZIP course package MAY contain a mix of fully qualified and relative URLs, provided the rules above are followed.</li>
</ul>

<a name="course_structure_xml_without_a_zip_file_package"></a>
##14.2 Course Structure XML Without a ZIP File Package
When a course structure XML file is provided without a ZIP file package, all URL references MUST be fully qualified.

<a name="course_structure_examples"/> 
#15.0 Course Structure Examples

Using the domain of geology the following two examples demonstrate how simple and complex a course designer can structure a course. The titles and descriptions are fetched or translated from the Earth Sciences Portal at Wikipedia (https://en.wikipedia.org/wiki/Portal:Earth_sciences).

<a name="course_structure_examples_simple"/> 
##15.1 Simple

```XML
<?xml version="1.0" encoding="utf-8"?>
<courseStructure xmlns="http://www.adlnet.gov/cmi5/CourseStructure.xsd">
  <course id="http://course-repository.example.edu/identifiers/courses/02baafcf">
    <title>
      <langstring lang="en-US">Introduction to Geology</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        This course will introduce you into the basics of geology. This includes subjects such as
        plate tectonics, geological materials and the history of the Earth.
      </langstring>
    </description>
  </course>
  <au id="http://course-repository.example.edu/identifiers/courses/02baafcf/aus/4c07">
    <title>
      <langstring lang="en-US">Introduction to Geology</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        This course will introduce you into the basics of geology. This includes subjects such as
        plate tectonics, geological materials and the history of the Earth.
      </langstring>
    </description>
    <url>http://course-repository.example.edu/identifiers/courses/02baafcf/aus/4c07/launch.html
    </url>
  </au>
</courseStructure>

```

<a name="course_structure_examples_complex"/> 
##15.2 Complex

```XML
<?xml version="1.0" encoding="utf-8"?>
<courseStructure xmlns="http://www.adlnet.gov/cmi5/CourseStructure.xsd">
  <course id="http://courses.example.edu/identifiers/courses/d07e186b">
    <title>
      <langstring lang="en-US">Geology</langstring>
      <langstring lang="de-DE">Geologie</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        Geology is an earth science comprising the study of solid earth, rhe rocks of which it is
        composed, and the proccesses by which they change. Geology gives insight into the history of
        Earth by providing the primary evidence for plate tectonics, the evolutionary history of
        live, and past climates. Geology is important for mineral and hydrocarbon exploration and
        exploitation, evaluating water resources, understanding of natural hazards, the remediation
        of environmental problems, and for providing insights into past climate change. Geology also
        plays a role in geotechnical engineering and is a major academic discipline.
      </langstring>
      <langstring lang="de-DE">
        Geologie ist eine Geowissenschaften, welche die Untersuchung der festen Erde, der Felsen,
        aus denen sie zusammengesetzt ist, und die Prozesse
        durch die sie sich ändert, umfasst. Geologie gibt Einblick in die Geschichte der Erde. Sie
        bietet die primären Beweise für Plattentektonik,
        die Evolutionsgeschichte des Lebens, und das Klima der Vergangenheit. Geologie ist wichtig
        für Mineral- und Kohlenwasserstoffexploration
        und -gewinnung, die Bewertung der Wasserressourcen, das Verständnis von Naturgefahren, die
        Sanierung von Umweltproblemen,
        und für Einblicke in Vergangenheit Klimawandel. Geologie spielt auch eine Rolle in der
        Geotechnik und ist ein
        akademische Hauptdisziplin.
      </langstring>
    </description>
  </course>
  <objectives>
    <objective id="http://objectives.example.com/identifiers/geology/basics">
      <title>
        <langstring lang="en-US">Geology - Basic knowledge</langstring>
        <langstring lang="de-DE">Geologie - Grundwissen</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          Knowledge about basic terms, theories and applications of geology.
        </langstring>
        <langstring lang="de-DE">
          Wissen über grundlegende Begriffe, Theorien und Anwendungsbereiche der Geologie.
        </langstring>
      </description>
    </objective>
    <objective
        id="http://objectives.example.com/identifiers/geology/material-identification">
      <title>
        <langstring lang="en-US">Identification of common Earth materials.</langstring>
        <langstring lang="de-DE">Identifikation von üblichen Erdmaterialien.</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          Knowledge about properties of minerals and methods to gather data about rocks.
        </langstring>
        <langstring lang="de-DE">
          Wissen über Eigenschaften von Mineralien und Methoden um Daten über Steine zu sammeln.
        </langstring>
      </description>
    </objective>
    <objective
        id="http://courses.example.edu/objectives/scientific-thinking-and-acting">
      <title>
        <langstring lang="en-US">Scientific Thinking and Acting</langstring>
        <langstring lang="de-DE">Wissenschaftliches Denken und Handeln</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          Application of scientific methods to collect, prove and validate knowledge.
        </langstring>
        <langstring lang="de-DE">
          Anwendung wissenschaftlicher Methoden, um Wissen zu sammeln, zu beweisen und zu validieren
        </langstring>
      </description>
    </objective>
    <objective id="http://objectives.example.com/identifiers/history/history-of-science">
      <title>
        <langstring lang="en-US">History of Science</langstring>
        <langstring lang="de-DE">History of Science</langstring>
      </title>
      <description>
        <langstring lang="en-US">Knowledge about the origins and development of science</langstring>
        <langstring lang="de-DE">
          Wissen über die Entstehung und Entwicklung der Wissenschaften
        </langstring>
      </description>
    </objective>
    <objective id="http://courses.example.edu/identifiers/objectives/">
      <title>
        <langstring></langstring>
      </title>
      <description>
        <langstring></langstring>
      </description>
    </objective>
  </objectives>

  <block id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/001">
    <title>
      <langstring lang="en-US">Geologic materials</langstring>
      <langstring lang="de-DE">Geologische Materialien</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        The majority of geological data comes from research on solid Earth materials. These
        typically fall into one of two categories: rock and unconsolidated material.
      </langstring>
      <langstring lang="de-DE">
        Der Großteil der geologischen Daten stammt aus der Forschung von festen Erdmaterialien.
        Diese fallen in der Regel in eine von zwei Kategorien: Gestein und Lockergestein.
      </langstring>
    </description>
    <objectives>
      <objective
          idref="http://objectives.example.com/identifiers/geology/basics"/>
      <objective
          idref="http://objectives.example.com/identifiers/geology/material-identification"/>
    </objectives>
    <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/001/aus/64f6"
        activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
        moveOn="CompletedOrPassed" masteryScore="1.0"
        authenticationMethod="Basic">
      <title>
        <langstring lang="en-US">Rock and rock cycle</langstring>
        <langstring lang="de-DE">Gestein und Kreislauf der Gesteine</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          There are three major types of rock: igneous, sedimentary, and metamorphic. The rock cycle
          is an important concept in geology which illustrates the relationships between these three
          types of rock, and magma.
        </langstring>
        <langstring lang="de-DE">
          Es gibt drei Hauptgesteinsarten: Magmatische, sedimentären und metamorphen. Der Kreislauf
          der Gesteine ist ein wichtiges Konzept in der Geologie, die die Beziehungen zwischen
          diesen drei Arten von Gestein und Magma darstellt.
        </langstring>
      </description>
      <url>
        http://courses.example.edu/identifiers/courses/d07e186b/blocks/001/aus/64f6/launch
      </url>
      <launchParameters>{'initialSpeed':3.0,'mode':1}</launchParameters>
      <entitlementKey>833d0c7c-a3f8-4f9b-a51f-cbd8a9dac9fb</entitlementKey>
    </au>
    <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/001/aus/3ee0"
        activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
        moveOn="NotApplicable">
      <title>
        <langstring lang="en-US">Unconsolidated material</langstring>
        <langstring lang="de-DE">Lockergestein</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          Geologists study unlithified material, which typically comes from more recent deposits.
        </langstring>
        <langstring lang="de-DE">
          Geologen studieren unverfestigtes Material, das von jüngeren Ablagerungen herkommt.
        </langstring>
      </description>
      <url>
        http://courses.example.edu/identifiers/courses/d07e186b/blocks/001/aus/3ee0/launch
      </url>
      <entitlementKey>833d0c7c-a3f8-4f9b-a51f-cbd8a9dac9fb</entitlementKey>
    </au>
  </block>

  <block id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/002">
    <title>
      <langstring lang="en-US">Whole-Earth structure</langstring>
      <langstring lang="de-DE">Struktur der Erde</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        In the 1960s, a series of discoveries showed that the Earth's lithosphere is separated into
        a number of tectonic plates that move across the asthenosphere.
      </langstring>
      <langstring lang="de-DE">
        In den 1960er Jahren zeigte eine Reihe von Entdeckungen, dass die Lithosphäre der Erde in
        eine Reihe von tektonischen Platten geteilt ist, die sich über Asthenosphäre bewegen.
      </langstring>
    </description>
    <objectives>
      <objective
          idref="http://objectives.example.com/identifiers/geology/basics"/>
    </objectives>
    <au id="http://example.com/courses/f59c9fc0/au/6f64"
        activityType="http://adlnet.gov/expapi/activities/lesson"
        launchMethod="OwnWindow" moveOn="Passed" masteryScore="0.1">
      <title>
        <langstring lang="en-US">Plate tectonics</langstring>
        <langstring lang="de-DE">Plattentektonik</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          Plate tectonics is a scientific theory that describes the motion of Earth's lithosphere.
        </langstring>
        <langstring lang="de-DE">
          Als Plattentektonik bezeichnet man die Gliederung der äußeren Erdhülle, der Lithosphäre,
          in Lithosphärenplatten, die dem tieferen Erdmantel aufliegen und darauf umherwandern.
        </langstring>
      </description>
      <objectives>
        <objective
            idref="http://objectives.example.com/identifiers/history/history-of-science"/>
      </objectives>
      <url>http://example.com/courses/f59c9fc0/au/6f64/start</url>
    </au>
    <au id="http://example.com/courses/f59c9fc0/au/6f65"
        activityType="http://adlnet.gov/expapi/activities/lesson"
        launchMethod="OwnWindow" moveOn="CompletedOrPassed" masteryScore="0.3">
      <title>
        <langstring lang="en-US">Structure of the earth</langstring>
        <langstring lang="de-DE">Innerer Aufbau der Erde</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          The interior structure of the Earth is layered in spherical shells, like an onion. These
          layers can be defined by either their chemical or their rheological properties.
        </langstring>
        <langstring lang="de-DE">
          Der Erdkörper ist, idealisiert betrachtet, aus konzentrischen Kugelschalen aufgebaut, die
          jeweils aus Materialien deutlich unterschiedlicher Dichte bestehen.
        </langstring>
      </description>
      <url>http://example.com/courses/f59c9fc0/au/6f65/start</url>
      <launchParameters>
      </launchParameters>
      <entitlementKey></entitlementKey>
    </au>
  </block>

  <block id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003">
    <title>
      <langstring lang="en-US">Geologic time scale</langstring>
      <langstring lang="de-DE">Geologische Zeitskala</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        The geological time scale (GTS) is a system of chronological measurement that relates
        stratigraphy to time, and is used by geologists, paleontologists, and other Earth scientists
        to describe the timing and relationships between events that have occurred throughout
        Earth’s history.
      </langstring>
      <langstring lang="de-DE">
        Die geologische Zeitskala ist eine hierarchische Unterteilung der Erdgeschichte. Sowohl die
        Hierarchie-Ebenen als auch die Zeitabschnitte sind benannt. Die feiner unterteilenden Ebenen
        reichen nicht bis zur Entstehung der Erde zurück.
      </langstring>
    </description>
    <objectives>
      <objective
          idref="http://objectives.example.com/identifiers/geology/basics"/>
      <objective
          idref="http://courses.example.edu/objectives/scientific-thinking-and-acting"/>
    </objectives>
    <au id="http://example.com/courses/f59c9fc0/au/6f66"
        activityType="http://adlnet.gov/expapi/activities/lesson"
        launchMethod="OwnWindow" moveOn="CompletedAndPassed" masteryScore="0.5">
      <title>
        <langstring lang="en-US">History and nomenclature of the time scale</langstring>
        <langstring lang="de-DE">Geschichte und Nomenklatur der Zeitskala</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          The first serious attempts to formulate a geological time scale that could be applied
          anywhere on Earth were made in the late 18th century. In 1977, the Global Commission on
          Stratigraphy (now the International Commission on Stratigraphy) started an effort to
          define global references.
        </langstring>
        <langstring lang="en-US">
          Die ersten ernsthaften Versuche, eine geologische Zeitskala, die überall auf der Erde
          angewandt konnten, wurden im späten 18. Jahrhundert formuliert. Im Jahr 1977 begann die
          Weltkommission für Stratigraphie (jetzt die Internationale Kommission für Stratigraphie)
          eine globale Referenzen zu definieren.
        </langstring>
      </description>
      <url>http://example.com/courses/f59c9fc0/au/6f66/start</url>
    </au>
    <block id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001">
      <title>
        <langstring lang="en-US">Current official geologic time scale</langstring>
        <langstring lang="de-DE">Die aktuelle offizielle geologische Zeitskala</langstring>
      </title>
      <description>
        <langstring lang="en-US">
          The following summarizes the major events and characteristics of the periods of time
          making up the geologic time scale. This scale is based on the International Commission on
          Stratigraphy.
        </langstring>
        <langstring lang="de-US">
          Im Folgenden werden die wichtigsten Ereignisse und die Merkmale der Zeit zusammengefasst,
          aus denen die geologische Zeitskala besteht. Diese Skala basiert auf der Internationalen
          Kommission für Stratigraphie.
        </langstring>
      </description>
      <block
          id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001-001">
        <title>
          <langstring lang="en-US">Phanerozoic</langstring>
          <langstring lang="de-DE">Phanerozoikum</langstring>
        </title>
        <description>
          <langstring lang="en-US">
            The Phanerozoic is the current geologic eon in the geologic timescale, and the one
            during which abundant animal and plant life has existed.
          </langstring>
          <langstring lang="de-DE">
            Das Phanerozoikum ist das jüngste Äon in der Erdgeschichte und dauert bis heute an.
          </langstring>
        </description>
        <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ec9"
            activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
            moveOn="Completed">
          <title>
            <langstring lang="en-US">Cenozoic</langstring>
            <langstring lang="de-DE">Känozoikum</langstring>
          </title>
          <description>
            <langstring lang="en-US">
              The Cenozoic Era is the current and most recent of the three Phanerozoic geological
              eras.
            </langstring>
            <langstring lang="de-DE">
              Das Känozoikum ist das Erdzeitalter, welches innerhalb des Äons Phanerozoikum auf das
              Mesozoikum folgt und das bis heute andauert.
            </langstring>
          </description>
          <url>
            http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ec9/launch
          </url>
        </au>
        <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7eca/"
            activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
            moveOn="Completed">
          <title>
            <langstring lang="en-US">Mesozoic</langstring>
            <langstring lang="de-DE">Mesozoikum</langstring>
          </title>
          <description>
            <langstring lang="en-US">
              The Mesozoic Era is an interval of geological time from about 252 to 66 million years
              ago.
            </langstring>
            <langstring lang="de-DE">
              Das Mesozoikum ist ein Erdzeitalter, das vor etwa 252,2 Millionen Jahren begann und
              vor etwa 66 Millionen Jahren endete.
            </langstring>
          </description>
          <url>
            http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7eca/launch
          </url>
        </au>
        <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecb/"
            activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
            moveOn="Completed">
          <title>
            <langstring lang="en-US">Paleozoic</langstring>
            <langstring lang="de-DE">Paläozoikum</langstring>
          </title>
          <description>
            <langstring lang="en-US">The Paleozoic is the earliest of three geologic eras of the
              Phanerozoic Eon, spanning from roughly 541 to 252.17 million years ago
            </langstring>
            <langstring lang="de-DE">Das Paläozoikum ist das älteste der drei Erdzeitalter (Ären),
              in die das Äon Phanerozoikum innerhalb der geologischen Zeitskala geteilt wird. Es
              umfasst den Zeitraum von ca. 541 Millionen Jahre bis ca. 252,2 Millionen Jahre vor
              heute.
            </langstring>
          </description>
          <url>
            http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecb/launch
          </url>
        </au>
      </block>
      <block
          id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001-002">
        <title>
          <langstring lang="en-US">Proterozoic</langstring>
          <langstring lang="de-DE">Proterozoikum</langstring>
        </title>
        <description>
          <langstring lang="en-US">The Proterozoic Eon extended from 2500 Ma to 542.0±1.0 Ma
            (million years ago)
          </langstring>
          <langstring lang="de-DE">Das Proterozoikum reicht vom Ende des Archaikums von vor ca.
            2.500 Millionen Jahren bis ca. vor 541 Millionen Jahren.
          </langstring>
        </description>
        <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecc/"
            activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
            moveOn="NotApplicable">
          <title>
            <langstring lang="en-US">Neoproterozoic</langstring>
            <langstring lang="de-DE">Neoproterozoikum</langstring>
          </title>
          <description>
            <langstring lang="en-US">Das Neoproterozoikum ist der jüngste Abschnitt des
              Proterozoikums; mit dieser Ära endet zugleich das Präkambrium (Erdurzeit). Das
              Neoproterozoikum beginnt etwa vor 1.000 Millionen Jahren und endet vor etwa 541
              Millionen Jahren.
            </langstring>
            <langstring lang="de-DE">The Neoproterozoic Era is the unit of geologic time from 1,000
              to 541 million years ago.
            </langstring>
          </description>
          <url>
            http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecc/launch
          </url>
        </au>
        <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecd/"
            activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow">
          <title>
            <langstring lang="en-US">Mesoproterozoic</langstring>
            <langstring lang="de-DE">Mesoproterozoikum</langstring>
          </title>
          <description>
            <langstring lang="en-US">The Mesoproterozoic Era is a geologic era that occurred from
              1,600 to 1,000 million years ago.
            </langstring>
            <langstring lang="de-DE">Der Beginn des Mesoproterozoikums wird bei etwa 1.600 Millionen
              Jahren, sein Ende bei etwa 1.000 Millionen Jahren angesetzt.
            </langstring>
          </description>
          <url>
            http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecd/launch
          </url>
        </au>
        <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ece/"
            activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow">
          <title>
            <langstring lang="en-US">Paleoproterozoic</langstring>
            <langstring lang="de-DE">Paläoproterozoikum</langstring>
          </title>
          <description>
            <langstring lang="en-US">The Paleoproterozoic occurred between 2,500 to 1,600 million
              years ago.
            </langstring>
            <langstring lang="de-DE">Das Paläoproterozoikum beginnt vor etwa 2.500 und endet vor
              1.600 Millionen Jahren.
            </langstring>
          </description>
          <url>
            http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ece/launch
          </url>
        </au>
      </block>
      <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecf/"
          activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow">
        <title>
          <langstring lang="en-US">Archean</langstring>
          <langstring lang="de-DE">Archaikum</langstring>
        </title>
        <description>
          <langstring lang="en-US">The Archean Eon is a geologic eon before the Proterozoic Eon,
            before 2.5 Ga (billion years), or 2,500 million years ago.
          </langstring>
          <langstring lang="de-DE">Das Archaikum Es erstreckt sich von ca. 4.000 bis ca. 2.500
            Millionen Jahren vor heute.
          </langstring>
        </description>
        <url>
          http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecf/launch
        </url>
      </au>
      <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ed0/"
          activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
          moveOn="Passed"  masteryScore="0.5">
        <title>
          <langstring lang="en-US">Hadean</langstring>
          <langstring lang="de-DE">Hadaikum</langstring>
        </title>
        <description>
          <langstring lang="en-US">The Hadean began with the formation of the Earth about 4.6
            billion years ago and ended, as defined by the ICS, 4 billion years ago.
          </langstring>
          <langstring lang="de-DE">Das Hadaikum oder Präarchaikum ist das erste Äon der
            Erdgeschichte. Es beginnt mit der Entstehung der Protoerde vor etwa 4.600 Millionen
            Jahren und endet geochronologisch definiert vor 4.000 Millionen Jahren.
          </langstring>
        </description>
        <url>
          http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ed0/launch
        </url>
      </au>
    </block>
  </block>
  <au id="http://quiz-server.example.com/1Hu62hL" masteryScore="0.7" 
      launchMethod="OwnWindow" moveOn="Passed" authenticationMethod="Basic"
      activityType="http://adlnet.gov/expapi/activities/assessment">
    <title>
      <langstring lang="en-US">Quiz</langstring>
      <langstring lang="de-DE">Quiz</langstring>
    </title>
    <description>
      <langstring lang="en-US">Check what you have learned about geology!</langstring>
      <langstring lang="de-De">Überprüfe dein neues Wissen über Geologie!</langstring>
    </description>
    <url>http://quiz-server.example.com/1Hu62hL</url>
    <launchParameters>
      {'level':3,'count':25,'_callback':'http://courses.example.edu/quizes/'}
    </launchParameters>
    <entitlementKey>
      w8GFdWktfOvzQUmFlI1YbUWB4yZX9jyEX3atFKmKW1eN6PTXJKh39wtUYBOvVx1eLt78b6joNZ1r0uj5x20zrSRUKu2
    </entitlementKey>
  </au>
</courseStructure>
```
<a name="course_structure_examples_extension"/> 
#15.3 Extension

The following modification of the simple course structure example uses vendor specific metadata defined in the preceding XML Schema Definition:

```xml
<xs:schema xmlns="http://www.adlnet.gov/cmi5/KeywordExtension.xsd"
           xmlns:xs="http://www.w3.org/2001/XMLSchema"
           xmlns:cmi5="http://www.adlnet.gov/cmi5/CourseStructure.xsd"
           targetNamespace="http://www.adlnet.gov/cmi5/KeywordExtension.xsd" elementFormDefault="qualified"
           id="CMI5KeywordsExtension">
  <xs:import namespace="http://www.adlnet.gov/cmi5/CourseStructure.xsd" schemaLocation="CourseStructure.xsd"/>
  <xs:element name="keywords" type="keywordsType"/>
  <xs:complexType name="keywordsType">
    <xs:sequence>
      <xs:element name="keyword" minOccurs="1" maxOccurs="unbounded">
        <xs:complexType>
          <xs:all>
            <xs:element name="title" type="cmi5:textType"/>
            <xs:element name="description" type="cmi5:textType" minOccurs="0"/>
          </xs:all>
          <xs:attribute name="id" type="xs:anyURI" use="required"/>
        </xs:complexType>
      </xs:element>
      <!--<xs:group ref="cmi5:anyElement"/>-->
    </xs:sequence>
    <xs:attributeGroup ref="cmi5:anyAttribute"/>
  </xs:complexType>
  <xs:element name="keyword">
    <xs:complexType>
      <xs:attribute name="idref" type="xs:anyURI"></xs:attribute>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

```xml
<?xml version="1.0" encoding="utf-8"?>
<!-- The following file is a course structure with extension -->
<courseStructure xmlns="http://www.adlnet.gov/cmi5/CourseStructure.xsd"
                 xmlns:kw="http://www.adlnet.gov/cmi5/KeywordExtension.xsd">
  <course id="http://course-repository.example.edu/identifiers/courses/02baafcf">
    <title>
      <langstring lang="en-US">Introduction to Geology</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        This course will introduce you into the basics of geology. This includes subjects such as
        plate tectonics, geological materials and the history of the Earth.
      </langstring>
    </description>
  </course>
  <au id="http://course-repository.example.edu/identifiers/courses/02baafcf/aus/4c07">
    <title>
      <langstring lang="en-US">Introduction to Geology</langstring>
    </title>
    <description>
      <langstring lang="en-US">
        This course will introduce you into the basics of geology. This includes subjects such as
        plate tectonics, geological materials and the history of the Earth.
      </langstring>
    </description>
    <url>http://course-repository.example.edu/identifiers/courses/02baafcf/aus/4c07/launch.html
    </url>
    <kw:keyword idref="http://words.example/earth_science"></kw:keyword>
    <kw:keyword idref="http://words.example/plate_tectonics"></kw:keyword>
    <kw:keyword idref="http://words.example/open_course"></kw:keyword>
    <kw:keyword idref="http://words.example/video_based_learning"></kw:keyword>
    <kw:keyword idref="http://words.example/secondary_school"></kw:keyword>
  </au>
  <kw:keywords>
    <kw:keyword id="http://words.example/earth_science">
      <kw:title>
        <langstring lang="en-US">Earth Science</langstring>
      </kw:title>
      <kw:description>
        <langstring lang="en-US">Earth science or geoscience is an all-embracing term referring to the fields of science dealing with planet Earth.</langstring>
      </kw:description>
    </kw:keyword>
    <kw:keyword id="http://words.example/plate_tectonics">
      <kw:title>
        <langstring lang="en-US">Plate Tectonics</langstring>
      </kw:title>
      <kw:description>
        <langstring lang="en-US">Plate tectonics is a scientific theory that describes the motion of Earth's lithosphere.</langstring>
      </kw:description>
    </kw:keyword>
    <kw:keyword id="http://words.example/open_course">
      <kw:title>
        <langstring lang="en-US">Open Course</langstring>
      </kw:title>
      <kw:description>
        <langstring lang="en-US">This course is copyrighted with an open license</langstring>
      </kw:description>
    </kw:keyword>
    <kw:keyword id="http://words.example/video_based_learning">
      <kw:title>
        <langstring lang="en-US">Video Based Learning</langstring>
      </kw:title>
    </kw:keyword>
    <kw:keyword id="http://words.example/secondary_school">
      <kw:title>
        <langstring lang="en-US">Secondary School</langstring>
      </kw:title>
      <kw:description>
        <langstring lang="en-US">The content is prepared for secondary school students</langstring>
      </kw:description>
    </kw:keyword>
  </kw:keywords>
</courseStructure>
```


-------

<a id="license_agreement"></a> 
#License Agreement

Copyright 2012-2015 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defense

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License. 
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed 
on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for 
the specific language governing permissions and limitations under the License.

-------
