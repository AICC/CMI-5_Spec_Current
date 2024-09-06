  
<p>
<p align=center><img src="https://cloud.githubusercontent.com/assets/1656316/9965238/bc9deb2c-5de9-11e5-9954-63aa03873f88.png" align=center></p>

# cmi5 Specification Profile for xAPI


---

## Table of Contents

[__Revision History__](#revhistory)

[__Contributors__](#contributors)

* [__1.0 Overview__](#overview)
  * [1.1 Scope](#scope)
  * [1.2 Document Style Conventions](#Document_Style_Conventions)
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
      * [8.1.1 endpoint](#launch_method_endpoint)
      * [8.1.2 fetch](#launch_method_fetch)
      * [8.1.3 actor](#launch_method_actor)
      * [8.1.4 registration](#launch_method_registration)
      * [8.1.5 activityId](#launch_method_activityId)
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
  * [10.1 Overview](#xapi_state_overview)
  * [10.2 Document Properties](#xapi_state_properties)
      * [10.2.1 contextTemplate](#xapi_state_properties_contextTemplate)
      * [10.2.2 launchMode](#xapi_state_properties_launchMode)
      * [10.2.3 launchParameters](#xapi_state_properties_launchParameters)
      * [10.2.4 masteryScore](#xapi_state_properties_masteryScore)
      * [10.2.5 moveOn](#xapi_state_properties_moveOn)
      * [10.2.6 returnURL](#xapi_state_properties_returnURL)
      * [10.2.7 entitlementKey](#xapi_state_properties_entitlementKey)
          * [10.2.7.1 courseStructure](#xapi_state_properties_entitlementKey_courseStructure)
          * [10.2.7.2 alternate](#xapi_state_properties_entitlementKey_alternate)
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
 * _Major Version_ – Stones (Sandstone, Quartz, etc.) – Major changes in functionality.
 * _Minor Version_ – Editions (1st edition, 2nd edition, etc.) – Minor changes in functionality.
 * _Errata_ – Minor corrections that do not affect functionality are not versioned.  (See GitHub repository for specific revision history).

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

This specification references how to use xAPI within this scope.

Other uses of xAPI are outside of this scope.

Uses of activities not explicitly defined above are outside of the scope of this specification.

<a name="Document_Style_Conventions"></a>  
## 1.2 Document Style Conventions  

 **References to Statements**

This document uses, as shorthand, specific vocabulary such as verbs in conjunction with the word "statement" (e.g., a "completed" statement). This shorthand refers to that statement meeting all requirements that would accompany the correct use of that concept. When using this shorthand with the word “the”, this means the cmi5 defined version of that statement with the verb’s display property. (see [Section 7.1.3 Types of Statements](#type_statement_au) for the definition of cmi5 defined)

For example:

> `the “completed” statement`

Would be a cmi5 defined xAPI statement with a verb display name of ‘completed’ and a verb IRI of ‘http://adlnet.gov/expapi/verbs/completed’.  Similar conventions might be used for other xAPI properties.

**Style Conventions**  
This document uses the following style conventions:

* **Back Ticks ( \` )** – (rendered as "inline code depending on document rendering”) for all literal names of verbs and properties.  
* **Double Quotes ( " ) for shorthand** – the “completed” statement (as described in above).  
* **Literal syntax case**  – for referring to verbs and properties the case will show as they appear in xAPI statements. 
* **Section Titles with verbs/properties** – may use either Capitalized or Literal syntax.  

**Style Usage examples**  

* **Back Ticks ( \` ) example. The ‘score’ property:**  
	for `score` when….  
	
* **Double Quotes ( " ) example. The ‘completed‘ statement:**  
	the "completed" statement  MUST  

* **Literal syntax case example. The actor object with an object type of agent:**  
	The actor object with an objectType of Agent

* **Section Titles with verb example. 	See Section 9.3.1 Launched:**  
	9.3.1 Launched

* **Section Titles with properties example. 	See Section 9.5.4 Duration:**  
	9.5.4 Duration

<a name="references"></a> 
# 2.0  References

The following referenced documents are indispensable for the application of this specification. 

* Internationalized Resource Identifiers (IRIs): IRI Syntax January 2005  
https://www.ietf.org/rfc/rfc3987.txt
* Experience API (xAPI), version 1.0.3  
https://github.com/adlnet/xAPI-Spec
* cmi5 Course Structure, Sandstone 1st Edition (merged into this document)  
MIME Types  
http://www.iana.org/assignments/media-types/index.html
* Extensible Markup Language (XML)  
http://www.w3.org/XML
* The JSON Data Interchange Format  
http://json.org/
* ISO/IEC 21320-1:2015(en) Information technology — Document Container File — Part 1: Core (Commonly called ZIP file format)   [https://www.iso.org/obp/ui/#iso:std:iso-iec:21320:-1&#8203;:ed-1:v1:en](https://www.iso.org/obp/ui/#iso:std:iso-iec:21320:-1:ed-1:v1:en)

<a name="definitions"></a>   
# 3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user who manages the LMS and related systems. This user performs tasks such as learner enrollment, course structure definition, and report management.

* __Activity__: In this specification it is representative of an AU or the Object of a statement with objectType of “Activity”. Thus the granularity can be anything from a single AU course down to a specific interaction.

* __Assignable Unit (AU)__:  A learning content presentation launched from an LMS. The AU is the unit of tracking and management. The AU collects data on the learner and sends it to the LMS.

* __Block__: A grouping of AU's and other Blocks (nesting).

* __Course__: A collection of assignable units, in a logical grouping, of learning content. A course is typically an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied sequence, representing a course.  

* __Experience API (xAPI)__:  A runtime data communication specification for learning content (AU) to send and receive data to a Learning Record Store (LRS). xAPI is used to define the data transport and the data model. 

* __Internationalized Resource Identifier (IRI)__: A unique identifier according to RFC 3987. The IRI might be an IRL. IRLs SHOULD be defined within a domain controlled by the person creating the IRL. Note that IRI’s in this spec MUST be fully qualified and not IRI References.

* __Internationalized Resource Locator (IRL)__: According to xAPI, an IRL is an IRI that, when translated into a URI (according to the IRI to URI rules), is a URL.

* __Learner__: The end user viewing/using the learning content (AUs).

* __Learning Management System (LMS)__: A computer system that could include the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners' progress. LMS launching, reporting, and tracking roles are the focus of the cmi5 specification. The LMS is integrated with an LRS. In the remainder of this document the term “LMS” refers to an integrated entity of LMS and LRS.

* __Learning Records Store (LRS)__: As defined in xAPI.

* __Registration__: An enrollment instance of a learner in a course. (a registration ID uniquely identifies this). The registration ID persists throughout the course progress to completion and during review of a completed course. A new registration is created for new enrollment instances (such as recurrent courses or re-taking courses).

* __Publisher ID__: A unique identifier for each AU and Block, and for the course instance in the Course Structure that is the identifier provided by the publisher to identify the course elements.  The purpose of this ID is to identify the course elements not the publisher itself.

* __Session__: A period of time marked by the launch of an AU until its termination (or abandonment).

<a name="acronyms"></a> 
## 3.1 Abbreviations and Acronyms

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

<a name="conformance"></a>  
# 4.0  Conformance

Conformance to this specification is defined in this section. 

In this specification: 

* "MUST" is to be interpreted as a requirement on an implementation.  
* "MUST NOT" is to be interpreted as a prohibition.  
* "SHOULD" is to be interpreted as a recommendation for implementation.  
* "SHOULD NOT" is to be interpreted as the converse of "SHOULD".  
* "MAY" is to be interpreted as a course of action that is permissible within the limits of the specification.  

Uses of xAPI outside of the scope of this specification do not affect conformance with this specification.  

<a name="au_conformance"></a> 
## 4.1 Assignable Unit (AU)

See Section 7.0 AU Requirements. An Assignable Unit MUST conform to all requirements as specified in xAPI (see References).


<a name="lms_conformance"></a> 
## 4.2 Learning Management Systems (LMS)

See Section 6.0 LMS Requirements. The LMS MUST conform to all LRS requirements as specified in xAPI (see References).

The LMS MUST have an account which is able to retrieve all Resource data (from the Statement API, etc, including attachments and extensions) about another distinct user across multiple sessions for that user.

<a name="json_conformance"></a> 
## 4.3 Optional JSON Values

If JSON properties are indicated as optional, you MAY leave such properties out of the JSON structure being described.

<a name="course_conformance"></a>
## 4.4 Courses

A course MUST be bundled with course structure data that conform to all requirements listed in Section 13.0 Course Structure Data Requirements and Section 14.0 Course Package.
  
Course structure data MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  


<a name="concept"></a> 
# 5.0 Conceptual Model: Informative  

Synopsis of the cmi5 model:

* An LMS imports a course structure which contains at least one AU. Optionally, the course structure can include one or more blocks, which consist of 1 or more AUs or nested blocks.
* An LMS administrative user assigns a course to a learner.
* A learner authenticates with an LMS or a related system.
* A learner launches an AU from the LMS or an associated launching system, using an interface.
* The LMS writes launch data to the integrated LRS.
* The AU sends a message to the LMS requesting launch parameters and previous state information.
* Once the AU is fully initialized for learner viewing, it issues an "initialized" statement.
* The learner views the AU content and performs the learning. During this time, the AU MAY request data from, and store data to, the LMS.
* The learner exits the AU.
* The AU reports the final tracking data to the LMS and issues a "terminated" statement.
* Administrative users create and view reports of the tracking data recorded by the AUs for individual learners.

Responsibilities of the Assignable Unit:

* Parse the parameters from the launching environment to determine where the LMS location is and initiate communication with the LMS.
* Send an "initialized" statement indicating the AU is ready for learner viewing.
* Acting as a client, send and receive messages using the defined transport mechanism(s) and associated commands as prescribed in this specification.
* Format all data according to the defined data types and vocabularies that are defined in this specification.
* Send a "terminated" statement prior to terminating the AU's execution.

Responsibilities of the LMS:

* Create and maintain course structures.
* Acting as a server, receive and reply to messages using the defined transport mechanism(s) and associated commands as prescribed in this specification.
* Format all data according to the defined data types and vocabularies that are defined in this specification.
* Launch the specified AU contained in the courses within the defined environment(s).

<a name="lms_requirements"></a>  
# 6.0 LMS Requirements

The LMS MUST:

* Implement an LRS as defined in xAPI.
* Implement additional State API requirements to initialize the AU state as defined in Section 10.0 xAPI State Data Model.
* Implement the runtime launch interface as defined in Section 8.0 Content Launch Mechanisms.
* Implement additional xAPI Statement API requirements as defined in Section 9.0 xAPI Statement Data Model .
* Implement additional xAPI Agent Profile API requirements as defined in Section 11.0 xAPI Agent Profile Data Model.
* Implement course handling as defined in Section 6.1 Course Handling Requirements.

<a name="course_structures"></a>  
## 6.1 Course Handling Requirements

* The LMS SHOULD implement a means to create, edit, and maintain course structures.
* The LMS MUST implement the import of the Course Structure defined in Section 13.0 Course Structure Data Requirements and the Course Package defined in Section 14.0 Course Package.
* The LMS SHOULD implement the export of the course data structure defined in Section 13.0 Course Structure Data Requirements and the Course Package defined in Section 14.0 Course Package.
* The LMS SHOULD provide a user interface to the LMS administrative users to create and edit course structures internally.
* The LMS MUST support course structures containing more than 1000 AUs.
* The LMS MUST support course structures conforming to the XSD schema defined in Section 14.0 Course Package.


<a name="lms_state_api_requirements"></a>  
## 6.2 LMS State API Requirements
The LMS MUST implement the State API Requirements as defined in Section 10.0 xAPI State Data Model.

<a name="lms_statement_api_requirements"></a>  
## 6.3 LMS Statement API Requirements

The LMS MUST NOT provide permissions/credentials which allow the AU to issue voiding Statements.

The LMS SHOULD reject statements that conflict with the Statement API requirements as defined in Section 9.0 xAPI Statement Data Model.

The LMS MUST Void statements that are NOT rejected AND conflict with the Statement API requirements as defined in Section 9.0 xAPI Statement Data Model.

<a name="au_requirements"></a>  
# 7.0 AU Requirements

An AU MUST:

* Implement the runtime launch interface as defined in Section 8.0 Content Launch Mechanisms.
* Implement runtime communication as defined in xAPI.
* Implement State API requirements in this specification as defined in Section 10.0 xAPI State Data Model.
* Implement Profile API requirements in this specification as defined in Section 11.0 xAPI Agent Profile Data Model.
* Implement Statement API requirements as defined in Section 7.1 AU Statement API Requirements.


<a name="au_statement_api_requirements"></a>  
## 7.1 AU Statement API Requirements

<a name="first_statement_au"></a> 
### 7.1.1 First Statement API Call
The AU MUST issue a statement to the LRS after being launched, initialized, and ready for learner interaction using the "initialized" verb as described in Section 9.3.2 Initialized.

<a name="last_statement_au"></a>  
### 7.1.2 Last Statement Call
The AU MUST issue a "terminated" statement to the LRS as described in Section 9.3.8 Terminated as the last statement in a session.
 
Once the AU has determined that the session will end (e.g. by user action, timeout or some other means) the AU SHOULD issue a "terminated" statement.

<a name="type_statement_au"></a>  
### 7.1.3 Types of Statements
The statements issued within an AU session could fall within the following categories:

* **cmi5 defined** - Statements using cmi5 defined verbs, category ID as defined in Section 9.6.2.1 cmi5 Category Activity, and context template.
* **cmi5 allowed** - Statements using any verb and cmi5 context template (but NOT including cmi5 category ID as defined in Section 9.6.2.1 cmi5 Category Activity).
* **cmi5 not-allowed** - Any statements not conforming with the cmi5 specification.

"cmi5 allowed" statements posted by the AU MUST occur between cmi5 statements using the "initialized" verb and the "terminated" verb. "cmi5 allowed" statements are not considered in "cmi5 defined" session management and satisfaction rules.

<a name="content_launch"></a>  
# 8.0 Content Launch Mechanisms

<a name="launch_method"></a>  
## 8.1 Launch Method

The AU MUST be launched by the LMS using one of the following methods, depending on the `launchMethod` in the Course Structure (Section 13.1.4 AU Meta Data, URL):

When the value of `launchMethod` is "OwnWindow", the LMS MUST use one of the following:

* Spawning a new browser window for the AU.
* Re-directing the existing browser window to the AU.

When the value of `launchMethod` is "AnyWindow", the LMS MUST choose the window context of the AU.  All browser window options are acceptable - Frameset, New window, browser redirect, etc.

Regardless of the `launchMethod` the AU MUST be launched by the LMS with a URL having query string launch parameters as defined in this section. The launch parameters MUST be name/value pairs in a query string appended to the URL that launches the AU.

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

<a name="launch_method_endpoint"></a>
### 8.1.1 endpoint
<table>
  <tr><th align="right" nowrap>Description:</th><td>A URL to the LMS listener location for xAPI requests to be sent to.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>endpoint</em></strong> in the query string.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>endpoint</em></strong> value from the query string. The AU MUST use the <strong><em>endpoint </em></strong>value as the Base Endpoint for xAPI requests.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A URL-encoded URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>https://example.com/my-cmi5-listener/</td></tr>
</table>

<a name="launch_method_fetch"></a>
### 8.1.2 fetch
<table>
  <tr><th align="right">Description:</th><td>The <strong><em>fetch</em></strong> URL is used by the AU to obtain an authorization token created and managed by the LMS. The authorization token is used by the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>fetch</em></strong> in the Launch URL for use as defined in section 8.2.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>fetch</em></strong> value from the query string for use as defined in section 8.2.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A URL-encoded URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>http://lms.example.com/tokenGen.htm?k=2390289x0</td></tr>
</table>

<a name="launch_method_actor"></a>
### 8.1.3 actor
<table>
  <tr><th align="right" nowrap>Description:</th><td>A JSON object of <code>objectType</code> of <code>Agent</code> (as defined in xAPI) that identifies the learner launching the AU so the AU will be able to include it in xAPI requests.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST populate the <strong><em>actor</em></strong>  parameter in the query string based on the authenticated learner's identity conforming to Section 9.2 Actor. The LMS SHOULD create this parameter with an object that is specific to the LMS instance that does NOT include sensitive PII of the learner.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <code>actor</code> value from the query string. The AU MUST use the <code>actor</code> value in xAPI requests that require an <code>actor</code> property or that require an <code>agent</code> parameter.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>A JSON object (as defined in Section 9.2 Actor)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>{"objectType": "Agent","account": {"homePage": "http://www.example.com","name": "1625378"}}</td></tr>
</table>

<a name="launch_method_registration"></a>
### 8.1.4 registration
<table>
  <tr><th align="right" nowrap>Description:</th><td>A Registration ID corresponding to the learner's enrollment for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>registration</em></strong> in the query string based on the authenticated learner's corresponding    enrollment for the Course that the AU being launched is a member of.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>registration</em></strong> value from the query string. The AU MUST use this <strong><em>registration</em></strong> value in xAPI requests that require a<code>registration</code>.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>UUID (as defined in xAPI)</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td></td></tr>
</table>

<a name="launch_method_activityId"></a>
### 8.1.5 activityId
<table>
  <tr><th align="right" nowrap>Description:</th><td>The Activity ID of the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST generate a unique activityId for the AU. The LMS MUST place its value in the query string. The activityId generated MUST NOT match the AU's ID (publisher ID) from the course structure (See Section 13.1.4 - AU Metadata). The LMS MUST use the same generated activityId on all subsequent launches (for the same AU) within the same registration. The LMS SHOULD use the same generated activityId (for the same AU) for all registrations.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>activityId</em></strong> value from the query string. The AU MUST use the <strong><em>activityId</em></strong> value as the ID property of the Object in all "cmi5 defined" statements.</td></tr>
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

The <strong><em>fetch</em></strong> URL response MUST include an HTTP status code of "200" for a valid request (including one that generates error as described in Section 8.2.3 Errors). The response MUST have a Content-Type of "application/json". The response body MUST be a JSON structure. The structure MUST be an object with the property <code>auth-token</code> in the first successful response. An example JSON structure is shown below:
```javascript
{
  "auth-token": "QWxhZGRpbjpvcGVuIHNlc2FtZQ=="
}
```
The AU MUST place the <code>auth-token</code> in the HTTP header, as defined in <a href='http://tools.ietf.org/html/rfc1945#section-11'>RFC 1945 - 11.1 Basic Authentication Scheme</a>, in all subsequent xAPI communications with the LMS.  The authorization token returned by the <strong><em>fetch</em></strong> URL MUST be limited to the duration of the session.

The AU SHOULD NOT attempt to retrieve the authorization token more than once.  The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses SHOULD generate an error (see Section 8.2.3 Errors). 

<a name="definition_auth_token"></a>  
### 8.2.2 Definition: auth-token
<table>
  <tr><th colspan=2 align="left">auth-token</th></tr>
  <tr><th align="right" nowrap>Description:</th><td>An authorization token used in all xAPI communications with the LMS.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <code>auth-token</code> in a JSON structure, as shown in Section 8.2.1 Overview, in its response to a <strong><em>fetch</em></strong> URL request.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <code>auth-token</code> value using an HTTP POST to the <strong><em>fetch</em></strong> URL. The AU MUST then place the authorization token in the Authorization headers of all HTTP requests made to the endpoint using xAPI.</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>QWxhZGRpbjpvcGVuIHNlc2FtZQ==</td></tr>
</table>

<a name="fetch_url_errors"></a>  
### 8.2.3 Errors

<a name="duplicate_call_to_fetch_url"></a>  
#### 8.2.3.1 Duplicate call to fetch URL
The <strong><em>fetch</em></strong> URL is a "one-time use" URL and MUST NOT return an authorization token more than once. Subsequent requests made to the <strong><em>fetch</em></strong> URL during the session SHOULD generate an error.  An example JSON structure is shown below:
```javascript
{
  "error-code": "1",
  "error-text": "The authorization token has already been returned."
}
```
<a name="fetch_url_error_values"></a>
#### 8.2.3.2 Error Values
The following `error-code` values are allowed.
<table>
<tr><td><strong>Code</strong></td><td><strong>Meaning</strong></td></tr>
<tr><td><code>1</code></td><td><strong>Already in Use or Expired</strong> - Token has been used before or the AU session has expired</td></tr>
<tr><td><code>2</code></td><td><strong>General Security Error</strong> - All other security issues including invalid tokens</td></tr>
<tr><td><code>3</code></td><td><strong>General Application Error</strong> - Application or environment failures</td></tr>
</table>

The values for `error-text` are defined by the LMS.

<br>

<a name="other_environment"></a>  
## 8.3 Other Launch Environments

Other launch environments are not currently implemented in this specification. cmi5 implementations for LMS's and AU's in these other environments will use the same REST communication interface as specified in xAPI. xAPI does not specify launch mechanisms.

<a name="xapi_data_model"></a>  
# 9.0 xAPI Statement Data Model  

<a name="statement_id" ></a>
## 9.1 Statement ID
The AU MUST assign a statement `id` property in UUID format (as defined in xAPI) for all statements it issues.
  
<a name="actor" ></a>
## 9.2 Actor
The `actor` property MUST be defined by the LMS. The`actor` property for all cmi5 defined statements MUST be of objectType `agent`. The Actor property MUST contain an `account` property as defined in xAPI.

<a name="verbs" ></a> 
## 9.3 Verbs  

The following xAPI verbs are defined in this specification.

Note that cmi5 allowed statements are NOT subject to the usage rules in this section. 

All statements in this section refer to cmi5 defined statements unless otherwise noted.

AUs MUST use the below verbs that are indicated as mandatory in other sections of this specification.

For all requirements listed below including language involving order, the order is determined by the value of the `timestamp` property.

AU Verb Ordering Rules within an AU session are as follows: 
 
* Verbs MUST NOT be duplicated (in cmi5 defined statements).  
* More than one of the set of {`passed`,`failed`} verbs MUST NOT be used (in cmi5 defined statements).  
* The initialized verb MUST be the first statement (cmi5 allowed or defined).  
* The terminated verb MUST be the last statement (cmi5 allowed or defined).  

AU Verb Ordering Rules within a registration (per AU) are as follows:  

* Exactly zero or one "completed" cmi5 defined statement MUST be used per registration.  
* Exactly zero or one "passed" cmi5 defined statement MUST be used per registration.  
* A "failed" statement MUST NOT follow a "passed" statement (in cmi5 defined statements) per registration.  

AUs MAY use additional verbs not listed in this specification.

The LMS MUST record and provide reporting for all "cmi5 defined" and "cmi5 allowed" statements that are not being rejected regardless of the verbs used in statements sent by AUs.

LMS verb ordering rules are as follows:  

* LMS MAY issue multiple "satisfied" statements (in a session).  
* LMS SHOULD NOT issue multiple "satisfied" statements per object (Block or Course) (in a registration).  
* LMS MUST NOT issue more than one "abandoned" statement for a session.  
* LMS MUST NOT issue more than one "waived" statement per session and MUST not issue more than one "waived" statement per registration per AU.  


<a name="verbs_launched"></a>
### 9.3.1 Launched
<table>
<tr><th align="left">Verb</th><td>launched</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/launched</td></tr>
<tr><th align="left">Description</th><td>This verb indicates that the AU was launched by the LMS.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS before launching an AU.  (See Statement API, Section 10.0 xAPI State Data Model) The LMS MUST NOT issue multiple "launched" statements for the same AU within a given AU session.</td></tr>
<tr><th align="left">Usage</th><td>A "launched" statement is used to indicate that the LMS has launched the AU. </td></tr>
</table>

<a name="verbs_initialized"></a>
### 9.3.2 Initialized
<table>
<tr><th align="left">Verb</th><td>initialized</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/initialized</td></tr>
<tr><th align="left">Description</th><td>An "initialized" statement is used by the AU to indicate that it has been fully initialized. The "initialized" statement MUST follow, within a reasonable period of time, the "launched" statement created by the LMS.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST use initialized in the first statement (of any kind) in the AU session.  The AU MUST NOT issue multiple "initialized" statements with for the same AU within a given AU session.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>None</td></tr>
<tr><th align="left">Usage</th><td>An "initialized" statement is used by the AU to indicate that it has been fully initialized.</td></tr>
</table>

<a name="verbs_completed"></a>
### 9.3.3 Completed
<table>
<tr><th align="left">Verb</th><td>completed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/completed</td></tr>
<tr><th align="left">Description</th><td>The verb indicates the learner viewed or did all of the relevant activities in an AU presentation.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a "completed" statement when the learner has experienced all relevant material in an AU. The AU MUST NOT issue multiple "completed" statements for the same AU within a given course registration for a given learner.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use "completed" statements based on the "moveOn" criteria for the AU as provided in the LMS Launch Data. (See Section 10.0 xAPI State Data Model – moveOn).</td></tr>
<tr><th align="left">Usage</th><td>The criterion for progress towards completion is determined by the course designer. The use of this verb indicates progress of 100%.</td></tr>
</table>

<a name="verbs_passed"></a>
### 9.3.4 Passed
<table>
<tr><th align="left">Verb</th><td>passed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/passed</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and succeeded in a judged activity in the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a statement containing the "passed" verb when the learner has attempted and passed the AU. If the "passed" statement contains a "scaled" score, the <code>scaled</code> value MUST be equal to or greater than the <code>masteryScore</code> indicated in the LMS Launch Data. (See Section 10.0 xAPI State Data Model – masteryScore). The AU MUST NOT issue multiple "passed" statements for the same AU within a given course registration for a given learner.</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use "passed" statements based on the "moveOn" criteria for the AU as provided in the LMS Launch Data. (See Section 10.0 xAPI State Data Model – moveOn).</td></tr>
<tr><th align="left">Usage</th><td>The criterion for passed is determined by the course designer.</td></tr>
</table>

<a name="verbs_failed"></a>
### 9.3.5 Failed
<table>
<tr><th align="left">Verb</th><td>Failed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/failed</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and failed in a judged activity in the AU.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>The AU MUST send a statement containing the "Failed" verb when the learner has attempted and failed the AU.  If the "Failed" statement contains a (scaled) score, the (scaled) score MUST be less than the "masteryScore" indicated in the <code>LMS.LaunchData</code> document. (See Section 10.0 xAPI State Data Model – masteryScore).</td></tr>
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
<tr><th align="left" nowrap>LMS Obligations</th><td>If an LMS launches an AU with the same registration as an active session, the previous session with that registration MUST be abandoned. The LMS MUST record an "Abandoned" statement on behalf of the AU indicating an abnormal session termination. The LMS MUST NOT allow any statements to be recorded for a session after recording an "Abandoned" statement.</td></tr>
<tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>

<a name="verbs_waived"></a>
### 9.3.7 Waived
<table>
<tr><th align="left">Verb</th><td>Waived</td></tr>
<tr><th align="left">ID</th><td>https://w3id.org/xapi/adl/verbs/waived</td></tr>
<tr><th align="left">Description</th><td>The verb "Waived" indicates that the LMS has determined that the AU requirements were met by means other than the moveOn criteria being met.</td></tr>
<tr><th align="left" nowrap>AU Obligations</th><td>None</td></tr>
<tr><th align="left" nowrap>LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS when it determines that the AU MAY be waived. A statement containing a "Waived" verb MUST include a "reason" in the extension property of the Statement Result. (See Section 9.5.5.2 reason) The LMS MUST generate a unique session ID for the statement containing a "Waived" verb and MUST NOT issue any other statements (except for statements with the "Satisfied" verb) using that session ID. The LMS MUST NOT issue multiple statements with "Waived" for the same AU within a course registration. </td></tr>
<tr><th align="left">Usage</th><td>A "Waived" statement is used by the LMS to indicate that the AU can be skipped by the learner.</td></tr>
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
The LMS MUST consider that an AU that was previously issued a “Waived” statement by the LMS to have met the moveOn criteria for that AU.  The LMS MUST use the "Satisfied" statement when the learner has met the moveOn criteria of all AU's in a block.  In this statement the LMS MUST use the block object per Section 9.4 Object . The LMS MUST use the same block object for all Satisfied statements that refer to that block.  
<br><br>
The LMS MUST also use the "Satisfied" statement when the learner has met the moveOn criteria for all AU's in a course. In this statement the LMS MUST use the course object per Section 9.4 Object.  The LMS MUST use the same course object for all Satisfied statements that refer to that course.   
<br><br>
The LMS MUST use the session ID from the AU launch for all "Satisfied" statements triggered as a result of an AU launch session.<br>
<br>
The LMS MUST generate a unique session ID for all "Satisfied" statements triggered outside of an AU launch session.<br>
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

Except for statements with the satisfied verb, the Object in a cmi5 defined statement represents the AU.  When the Object is the AU, the value of the Object's `id` property for a given AU MUST match the `activityId` defined in the launch URL.

In "satisfied" statements, the Object represents a Block or Course.  (see 9.3.9 - Satisfied)  

The LMS MUST generate a unique ID for each block object.  The generated block ID MUST NOT match the publisher’s ID from the course structure. The LMS block object MUST use `https://w3id.org/xapi/cmi5/activitytype/block` as the value of the `objectType` property in the Object's Definition.

The LMS MUST generate a unique ID for each course object.  The generated course ID MUST NOT match the publisher’s ID from the course structure. The LMS course object MUST use `https://w3id.org/xapi/cmi5/activitytype/course` as the value of the `objectType` property in the Object's Definition.

<a name="result"></a> 
## 9.5 Result
A Result MAY be present in a statement depending on the cmi5 verb used. 

<a name="score"></a> 
### 9.5.1 Score

A score MAY be reported. If a score is reported by an AU, the verb MUST be consistent with "masteryScore" (if defined for the AU in the `LMS.LaunchData` document).

The `score` property of the `result` object MAY be set in the following cmi5 defined statements:

- passed
- failed

cmi5 defined statements, other than passed or failed, MUST NOT include the `score` property.

 The following are properties of the <code>score</code> object per xAPI: 
<ul>
<li><code>scaled</code><br>A decimal value between 0 and 1 (inclusive).</li>
<li><code>raw</code><br>An integer value between the <code>min</code> and <code>max</code> properties (inclusive) of the <code>score</code> object.  The AU MUST provide the <code>min</code> and <code>max</code>  values for <code>score</code> object when the <code>raw</code> value is provided.</li>
<li><code>min</code><br>An integer value indicating the minimum value for the score in the <code>raw</code> property.</li>
<li><code>max</code><br>An integer value indicating the maximum value for the score in the <code>raw</code> property.</li>
</ul>

<a name="success"></a>
### 9.5.2 Success 

The `success` property of the result MUST be set to `true` for the following cmi5 defined statements:

- passed
- waived

The `success` property of the result MUST be set to `false` for the following cmi5 defined statements:

- failed
 
cmi5 defined statements, other than passed, waived or failed, MUST NOT include the `success` property.

<a name="completion"></a>
### 9.5.3 Completion
The `completion` property of the result MUST be set to `true` for the following cmi5 defined statements:

- completed
- waived

cmi5 defined statements, other than completed or waived, MUST NOT include the `completion` property.

<a name="duration"></a>
### 9.5.4 Duration
The `duration` property is an ISO 8601 formatted time value required in certain statements as defined in this section. Other cmi5 defined statements MAY include the `duration` property.
<a name="au_statements_that_include_duration"></a>
#### 9.5.4.1 AU statements that include duration
##### Terminated Statement
The AU MUST include the `duration` property in "terminated" statements.  The AU SHOULD calculate the duration for "terminated" statements as the time difference between the "initialized" statement and the "terminated" statement.  The AU MAY use other methods to calculate the duration based on criteria determined by the AU.
##### Completed Statement
The AU MUST include the `duration` property in "completed" statements.  The AU SHOULD calculate the duration as the time spent by the learner to achieve completion status.
##### Passed Statement
The AU MUST include the `duration` property in "passed" statements.  The AU SHOULD calculate the duration as the time spent by the learner to attempt and succeed in a judged activity of the AU. 
##### Failed Statement
The AU MUST include the `duration` property in "failed" statements. The AU SHOULD calculate the duration as the time spent by the learner to attempt and fail in a judged activity of the AU.

<a name="lms_statements_that_include_duration"></a>
#### 9.5.4.2 LMS statements that include duration
##### Abandoned Statement
The `duration` property MUST be included in "abandoned" statements. The LMS SHOULD use LMS specific methods (if available) to determine the duration if it has more accurate means of session time calculation than time stamp differences between statements. In the absence of such methods, the `duration` property MUST be set as the total session time, calculated as the time between the "launched" statement and the last statement (of any kind) issued by the AU. 

<a name="result_extensions"></a>
### 9.5.5 Extensions
<a name="result_extensions_progress"></a>
#### 9.5.5.1 progress

<table>
    <tr><th align ="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/progress</td></tr>
    <tr><th align ="right" nowrap>Description:</th><td>An integer value between 0 and 100 (inclusive) indicating the completion of the AU as a percentage.</td></tr>
    <tr><th align ="right" nowrap>LMS Usage:</th><td>None</td></tr>
    <tr><th align ="right" nowrap>AU Usage:</th><td>The AU MAY set this value in statements to indicate level of completion. The AU SHOULD NOT set a progress value in a "completed" statement or if it has previously issued a "completed" statement for the AU in the current registration.</td></tr>
    <tr><th align ="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
    <tr><th align ="right" nowrap>LMS Obligation:</th><td>None</td></tr>
    <tr><th align ="right" nowrap>Data type:</th><td>Integer</td></tr>
    <tr><th align ="right" nowrap>Value space:</th><td>0 to 100 (inclusive)</td></tr>
</table>

<a name="result_extensions_reason"></a>
#### 9.5.5.2 reason

<table>
    <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/reason</td></tr>
    <tr><th align="right" nowrap>Description:</th><td>Indicates the reason why an AU was waived (marked complete by an alternative means).</td></tr>
    <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST set this value in statements it makes with the "waived" verb. The value SHOULD be one of the following:
        <ul>
            <li><b>Tested Out</b> – An Assessment was completed by the student to waive the AU.</li>
            <li><b>Equivalent AU</b> - The student successfully completed an equivalent AU (in the same course) to waive the AU. </li>
            <li><b>Equivalent Outside Activity</b> – The student successfully completed an equivalent activity outside of the course to waive the AU. </li>
            <li><b>Administrative</b> – The LMS administrative user marked the AU complete.</li>
        </ul>
    </td></tr>
    <tr><th align="right" nowrap>AU Usage:</th><td>The AU MAY retrieve this value from the LRS and use it to change presentation behavior based on the reason.</td></tr>
    <tr><th align="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
    <tr><th align="right" nowrap>LMS Obligation:</th><td>This is a required extension for LMS statements that include the "waived" verb.</td></tr>
    <tr><th align="right" nowrap>Data type:</th><td>String</td></tr>
    <tr><th align="right" nowrap>Value space:</th><td>Any string value</td></tr>
    <tr><th align="right" nowrap>Sample value:</th><td>Tested Out</td></tr>
</table>

<a name="context"></a> 
## 9.6 Context

All cmi5 defined statements MUST contain a context that includes all properties as defined in this section. Either the LMS or the AU MAY provide additional properties.

<a name="registration"></a> 
### 9.6.1 registration
The value for the `registration` property used in the context object MUST be the value provided by the LMS. The LMS MUST generate this value and pass it to the AU via the launch URL.  The LMS MUST evaluate `moveOn` criteria in the course structure at the time of registration.  For example, AUs with `moveOn` criteria of `NotApplicable` in the course structure would be evaluated and could generate "satisfied" statements at this time.

<a name="context_activities"></a>
### 9.6.2 contextActivities
The purpose of this property is to facilitate searches of the LRS by the LMS or other reporting systems. The `contextActivities` property contains list(s) of activity objects whose IDs can be used as a statement list filter.  All cmi5 defined statements MUST include all properties and values defined in the `contextActivities` of the `contextTemplate` (see Section 10.0 xAPI State Data Model).

<a name="context_activities_category_cmi5"></a>
#### 9.6.2.1 cmi5 Category Activity
An activity object with an `id` of `https://w3id.org/xapi/cmi5/context/categories/cmi5` in the `category`  list of the `contextActivities` object MUST be used in cmi5 defined statements as described in Section 7.1.3 Types of Statements.

<a name="context_activities_category_moveon"></a>
#### 9.6.2.2 moveOn Category Activity
cmi5 defined statements with a `result` object (Section 9.5 Result) that include either `success` or `completion` properties MUST have an activity object with an `id` of `https://w3id.org/xapi/cmi5/context/categories/moveon` in the `category`  list of the `contextActivities` object. Other statements MUST NOT include this activity.

<a name="context_activities_grouping_publisherid"></a>
#### 9.6.2.3 Publisher ID Grouping Activity
Used to identify statements about the course, block, or AU using the publisher ID from the course structure.

The LMS MUST include an activity object with an ID property whose value is the unaltered value of the AU's ID attribute from the course structure (See Section 13.1.4 AU Metadata – ID) in the `grouping` list of `contextActivities` in the `contextTemplate` object as described in the State API (See Section 10.0 xAPI State Data Model) prior to launching an AU. 

The LMS MUST include the publisher ID activity in the `grouping` list of the `contextActivities` object for all cmi5 defined and cmi5 allowed statements it makes directly in the LRS.

<a name="extensions"></a>
### 9.6.3 Extensions
The following are extensions specified for cmi5. Statements MAY include extensions not specified here.

<a name="context_extensions_session_id"></a>
#### 9.6.3.1 session ID

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/sessionid</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>A unique identifier for a single AU launch session based on actor and course registration. </td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The value for session ID MUST be generated by the LMS. The LMS MUST record the session ID in the State API (See Section 10.0 xAPI State Data Model) prior to launching an AU. The LMS MUST provide the session ID in the context as an extension for all cmi5 defined and cmi5 allowed statements it makes directly in the LRS. </td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>An AU MUST include the session ID provided by the LMS in the context as an extension for all cmi5 defined and cmi5 allowed statements it makes directly in the LRS. </td></tr>
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
  <tr><th align="right" nowrap>Description:</th><td><code>masteryScore</code> as provided in the <code>LMS.LaunchData</code> document for the AU and is used to determine the pass/fail result based on score.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add <code>masteryScore</code> to the context of a "launched" statement when it is provided in the <code>LMS.LaunchData</code> document.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>An AU MUST include the <code>masteryScore</code> value provided by the LMS in the context as an extension for "passed" or "failed" statements it makes based on the <code>masteryScore</code>.</td></tr>
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
  <tr><th align="right" nowrap>Description:</th><td>Indicates the <code>launchMode</code> that was used by the LMS to launch an AU.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add this extension to the context of a "launched" statement with the value from <code>launchMode</code> in the <code>LMS.LaunchData</code> document.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Per <code>launchMode</code> vocabulary defined in Section 10.0 xAPI State Data Model</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>"Normal"</td></tr>
</table>

<a name="context_extensions_launchURL"></a>
#### 9.6.3.4 launchURL

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/launchurl</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>The URL used by the LMS to launch the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST put a fully qualified URL equivalent to the one that the LMS used to launch the AU without the name/value pairs included as defined in Section 8.1 Launch Method in the context extensions of the "launched" statement.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>URL</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>http://www.example.com/LA1/Start.html</td></tr>
</table>

<a name="context_extensions_publisherid"></a>
#### 9.6.3.5 publisherId

This section is no longer applicable. See Section 9.6.2.3 Publisher ID Grouping Activity.

<a name="context_extensions_moveOn"></a>
#### 9.6.3.6 moveOn

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/moveon</td></tr>
  <tr><th align="right" nowrap>Description:</th><td>The <code>moveOn</code> value as provided in the <code>LMS.LaunchData</code> document for the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add <code>moveOn</code> to the context of a "launched" statement.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Per <code>moveOn</code> vocabulary defined in Section 10.0 xAPI State Data Model</td></tr>
  <tr><th align="right" nowrap>Sample value:</th><td>"Passed"</td></tr>
</table>

<a name="context_extensions_launchParameters"></a>
#### 9.6.3.7 launchParameters

<table>
  <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/context/extensions/launchparameters</td></tr>
  <tr><th align="right" nowrap>Description:</th><td><code>launchParameters</code> as provided in the <code>LMS.LaunchData</code> document for the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add <code>launchParameters</code> to the context of a "launched" statement when it is provided in the <code>LMS.LaunchData</code> document</code>.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>Not Applicable</td></tr>
  <tr><th align="right" nowrap>AU Obligation:</th><td>None</td></tr>
  <tr><th align="right" nowrap>LMS Obligation:</th><td>Required, when present in the <code>LMS.LaunchData</code> document</td></tr>
  <tr><th align="right" nowrap>Data type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value space:</th><td>Any string value</td></tr>
</table>

<a name="timestamp"></a> 
## 9.7 Timestamp

All statements MUST include a `timestamp` property per the xAPI specification to ensure statement ordering requirements are met. All timestamps MUST be recorded in UTC time. Timestamps are not required to be unique in statements within a session. The time recorded SHOULD indicate when the condition actually occurred.


<a name="xapi_state"></a>  
# 10.0 xAPI State Data Model

<a name="xapi_state_overview"></a>
## 10.1 Overview

Prior to launching an AU, the LMS MUST create or update a document in the State API record in the LRS.  This MUST be a JSON document, as defined in this section.

__State API PUT Properties__:

* _activityId_: Activity id for the AU. This MUST match the activity id used by the LMS at AU launch time.
* _agent_: Agent representing the LMS learner being enrolled.  This MUST match the actor property used by the LMS at AU launch time.
* _registration_: Registration ID representing the LMS learner enrollment in the course. This MUST match the registration used by the LMS at AU launch time.
* _stateId_: `LMS.LaunchData`


The properties for the `LMS.LaunchData` document are described below.

<a name="xapi_state_properties"></a>
## 10.2 Document Properties

<a name="xapi_state_properties_contextTemplate"></a>
### 10.2.1 contextTemplate
<table>
  <tr><th align="right" nowrap>Description:</th><td><code>contextTemplate</code> for the AU being launched.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST include a <code>contextTemplate</code> object and MUST include the following values:
<ul><li>The value for session id placed in an <code>extensions</code> object with the ID as defined in Section 9.6.3.1 session ID.</li>
<li>The publisher ID Activity as defined in Section 9.6.2.3 Publisher ID Grouping Activity in the <code>contextActivities.grouping</code> list.</li></ul>
The LMS MAY place additional values in the <code>contextTemplate</code>.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST get the <code>contextTemplate</code> value from the  <code>LMS.LaunchData</code> State document. The AU MUST NOT modify or delete the  <code>LMS.LaunchData</code> State document. The AU MUST use the <code>contextTemplate</code> as a template for the <code>context</code> property in all xAPI statements it sends to the LMS. While the AU MAY include additional values in the <code>context</code> object of such statements, it MUST NOT overwrite any values provided in the <code>contextTemplate</code>. NOTE: this will include the session ID specified by the LMS.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>JSON <code>context</code> object as defined in xAPI.</td></tr>
</table>

<a name="xapi_state_properties_launchMode"></a>
### 10.2.2 launchMode
<table>
  <tr><th align="right" nowrap>Description:</th><td>The launch mode determined by the LMS. There are three possible values:<br>
      <ul><li><code>Normal</code><br>Indicates to the AU that satisfaction-related data MUST be recorded in the LMS using xAPI statements.</li>
          <li><code>Browse</code><br>Indicates to the AU that satisfaction-related data MUST NOT be recorded in the LMS using xAPI statements. When Browse mode is used, the AU SHOULD provide a user experience that allows the user to "look around" without judgement.</li>
          <li><code>Review</code><br>Indicates to the AU that satisfaction-related data MUST NOT be recorded in the LMS using xAPI statements. When Review mode is used, the AU SHOULD provide a user experience that allows the user to "revisit/review" already completed material.</li>
      </ul></td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST include a value for <strong><em>launchMode</em></strong>.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST conform to the following based on the value of <strong><em>launchMode</em></strong><br>
      <ul><li>Normal<br>The AU MUST send "Initialized" and "Terminated" verb statements.  The AU MAY send other cmi5 defined statements per the requirements defined in Section 9.3 Verbs.</li>
      <li>Browse<br>The AU MUST send "Initialized" and "Terminated" verb statements.  The AU MUST NOT send other cmi5 defined statements.</li>
      <li>Review<br>The AU MUST send "Initialized" and "Terminated" verb statements.  The AU MUST NOT send other cmi5 defined statements.</li></ul></td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>"Normal", "Browse", or "Review"</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"Normal"</td></tr>
</table>

<a name="xapi_state_properties_launchParameters"></a>
### 10.2.3 launchParameters
<table>
  <tr><th align="right" nowrap>Description:</th><td>The <code>launchParameters</code> defined in the cmi5 Course Structure.
  </td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>The LMS MUST include the  <code>launchParameters</code> in the <code>LMS.LaunchData</code> State document if the <code>launchParameters</code> were defined by the course designer in the Course Structure.</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The <code>launchParameters</code> value written in the <code>LMS.LaunchData</code> State document MAY be different than the one in the course structure (e.g. based on content vendor options that might be used by the LMS admin users).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD get the <code>launchParameters</code> value from the <code>LMS.LaunchData</code> State document if the launch parameters were defined in the Course Structure.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Any string value</td></tr>
</table>

<a name="xapi_state_properties_masteryScore"></a>
### 10.2.4 masteryScore
<table>
  <tr><th align="right" nowrap>Description:</th><td>The <code>masteryScore</code> from the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>The LMS MUST include a <code>masteryScore</code> in the <code>LMS.LaunchData</code> State document if the <code>masteryScore</code> was defined by the course designer in the Course Structure.</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>If the <code>masteryScore</code> is provided.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The <code>masteryScore</code> value written in the <code>LMS.LaunchData</code> State document MAY be different than the one in the course structure (e.g. based on administrative rules defined by the LMS).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>If the AU issues "passed" or "failed" statements they MUST be based on the <code>masteryScore</code> if provided. (See Sections 9.3.4 Passed and 9.3.5 Failed)</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>decimal</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Decimal value between 0 and 1 (inclusive) with up to 4 decimal places of precision.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>0.75</td></tr>
</table>

<a name="xapi_state_properties_moveOn"></a>
### 10.2.5 moveOn
<table>
  <tr><th align="right" nowrap>Description:</th><td>The <code>moveOn</code> value from the cmi5 Course Structure.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST provide a <code>moveOn</code> value in the State API document. The <code>moveOn</code> value written in the State API Document MAY be different than the one in the course structure (e.g. based on administrative rules defined by the LMS).</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MAY get the <code>moveOn</code> value from the  <code>LMS.LaunchData</code> state document and MAY use the value to modify its behavior.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td><code>moveOn</code> values as defined in the Course Structure (Section 13.1.4 AU Metadata)</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"Passed"</td></tr>
</table>

<a name="xapi_state_properties_returnURL"></a>
### 10.2.6 returnURL
<table>
  <tr><th align="right" nowrap>Description:</th><td>Used by the LMS when launching the AU if the LMS requires the AU (in a web-browser environment) to redirect the learner when he or she exits the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>If the <code>returnURL</code> is provided.</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MAY include the <code>returnURL</code> when the learner SHOULD be redirected to the <code>returnURL</code> on exiting the AU.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU MUST attempt to get the <code>returnURL</code> value from the  <code>LMS.LaunchData</code> state document. The AU MUST redirect the current browser window or frame to the <code>returnURL</code> when the AU is terminated if the <code>returnURL</code> is provided.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>String (Not URL encoded)</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>Any URL.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>http://www.example.com/lms/mod/xapilaunch/view.php?id=12</td></tr>
</table>

<a name="xapi_state_properties_entitlementKey"></a>
### 10.2.7 entitlementKey
<table>
  <tr><th align="right" nowrap>Description:</th><td>The <code>entitlementKey</code> object is used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST add an <code>entitlementKey</code> object to the  <code>LMS.LaunchData</code> state document if an <code>entitlementKey</code> is present in the Course Structure for the AU. The <code>entitlementKey</code> consists of 2 properties, <code>courseStructure</code> and <code>alternate</code>. See items below for LMS usage requirements.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>JSON Object</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value for <code>entitlementKey</code> properties are defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>{"courseStructure": "xyz-123-9999", "alternate": "abc-456-1111"}</td></tr>
</table>

<a name="xapi_state_properties_entitlementKey_courseStructure"></a>
#### 10.2.7.1 courseStructure
<table>
  <tr><th align="right" nowrap>Description:</th><td>The <code>courseStructure</code> property contains the value for <code>entitlementKey</code> from the Course Structure. The <code>courseStructure</code> values MAY be used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>Yes</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST obtain this from the Course Structure.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value is defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"xyz-123-9999"</td></tr>
</table>

<a name="xapi_state_properties_entitlementKey_alternate"></a>
#### 10.2.7.2 alternate
<table>
  <tr><th align="right" nowrap>Description:</th><td>The <code>alternate</code> property is data from some other source as agreed upon between the LMS and the AU. The <code>alternate</code> property values MAY be used by the AU to determine if the launching LMS is entitled to use the AU.</td></tr>
  <tr><th align="right" nowrap>LMS Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>AU Required:</th><td>No</td></tr>
  <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MUST obtain the value for the <code>alternate</code> property from a source as agreed upon with the AU.</td></tr>
  <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.</td></tr>
  <tr><th align="right" nowrap>Data Type:</th><td>string</td></tr>
  <tr><th align="right" nowrap>Value Space:</th><td>The value is defined by the AU provider.</td></tr>
  <tr><th align="right" nowrap>Sample Value:</th><td>"xyz-123-9999"</td></tr>
</table>

<a name="xapi_agent_profile"></a>   
# 11.0 xAPI Agent Profile Data Model  

In cmi5, Learner Preferences are scoped to the Agent representing the enrolled LMS learner. The agent used in xAPI Agent Profile requests MUST match the actor property generated by the LMS at AU launch time.  Both the LMS and the AU MAY write changes to Learner Preferences in the xAPI Agent Profile.  The LMS/LRS MAY choose to ignore or override Learner Preference changes requested by the AU by returning a "403 Forbidden" response as defined in xAPI.  The AU MUST NOT treat the 403 response as an error condition.

The AU MUST retrieve the Learner Preferences document from the Agent Profile on startup.

When reading or writing to the Agent Profile, the document name MUST be "cmi5LearnerPreferences". The document content MUST be a JSON object with the <code>languagePreference</code> and <code>audioPreference</code> properties as described in Section 11.1  languagePreference and 11.2 audioPreference respectively. For example:

```javascript
{
  "languagePreference": "<values for languages>",
  "audioPreference": "<on or off>"
}
```
<a name="language_preference"></a>
## 11.1  languagePreference
The <code>languagePreference</code> MUST be a comma-separated list of RFC 5646 Language Tags.  In the list, languages MUST be specified in order of user preference.  In the example below, the user's first preference for language is <code>en-US</code>.  The user's second preference for language is <code>fr-FR</code> and the third preference is <code>fr-BE</code>.

```javascript
{
  "languagePreference": "en-US,fr-FR,fr-BE",
  ...
}
```

The AU SHOULD display in the language preference order of the user as in the example above (as supported). 

<a name="audio_preference"></a>

## 11.2 audioPreference
The `audioPreference` value indicates whether the audio SHOULD be "on" or "off".  The AU MUST turn the audio on or off at startup based on this value.  If no value is provided in the Agent Profile for `audioPreference` the AU MAY use its own default value.

Example:
```javascript
{
  "audioPreference": "on",
  ...
}
```


<a name="xapi_activity_profile"></a>  
# 12.0 xAPI Activity Profile Data Model

The AU MAY use the Activity Profile API according to xAPI.


<a name="course_requirements"></a>

# 13.0 Course Structure Data Requirements  

<a name="course_structure_data_model"></a>
## 13.1 Course Structure Data Model
All leading/trailing whitespace MUST be removed by the LMS on import of the course structure for all of the data elements defined in this section.

The following Data Types are used in the cmi5 course structure data model, see the CourseStructure.xsd (Section 14.0 Course Package) for specific format:

   * **decimal** – XSD definition:  `xs:decimal`
   * **IRI** – XSD definition:  `xs:anyURI`
   * **string** –  XSD definition: `xs:string`
   * **langstring** – XSD definition : `<xs:element name="langstring" maxOccurs="unbounded" minOccurs="1"/>`
   * **objectiveReference** – XSD definition : `<xs:element name="objectives" type="referencesObjectivesType" minOccurs="0"/>`

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
      A globally unique IRI to identify the course.</p>
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

The data in this section are used for the block structures which group AUs.  A Block consists of one or more AUs. Blocks can also contain references to objectives and other Blocks.

<table border="1" cellspacing="0" cellpadding="0">
   <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type: </strong> IRI</p></td>
    <td width="811" valign="top"><p><strong>Description: </strong>A globally unique IRI to identify the Block. This ID MUST be unique within the course structure.</p>
      <p><strong>Value space: </strong>Values defined by course designer.</p>
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
      A descriptive title for the Block of AUs.<br>
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
      A globally unique IRI to identify the learning objective. This ID MUST be unique within the course structure.<br>
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

The data in this section are used by the LMS to locate the AU and provide launch data. AUs might also contain objectives.


<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: </strong> Yes<br>
        <strong>Data type: </strong> IRI</p>
    </td>
    <td width="815" valign="top"><p><strong>Description: </strong>A globally unique IRI to identify the AU. This ID MUST be unique within the course structure.</p>
      <p><strong>Value space: </strong>Values are defined by the AU publisher.</p>
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
    <td valign="top"><p><strong>Description:</strong> Used by the LMS when launching the AU (in a web-browser environment) to determine whether the AU requires its own window, or whether the LMS can choose the window context for the AU.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>A value of "OwnWindow" will require the LMS to launch the AU either in a new browser window, or the LMS MAY redirect the current window to the AU.</li>
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
        <li>The <code>masteryScore</code> is passed to the AU at runtime by the LMS (See Section 10.0 xAPI State Data Model).</li>
        <li>If the AU has scoring, it will use the <code>masteryScore</code> to determine pass/fail.</li>
        <li>The <code>masteryScore</code> is a scaled, decimal value between 0 and 1 (inclusive) with up to 4 decimal places of precision.</li>
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
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to determine if an AU has been sufficiently satisfied for the purposes of determining overall course satisfaction or determining if prerequisites were met for other activities.</p>
      <p><strong>moveOn Values are as follows:</strong></p>
      <ul>
        <li><code>moveOn</code> Value = "Passed" : If the LMS receives a statement with the verb "Passed", then the LMS will consider the AU satisfied.</li>
        <li><code>moveOn</code> Value = "Completed" : If the LMS receives a statement with the verb "Completed", then the LMS will consider the AU satisfied.<br>
          </li>
        <li><code>moveOn</code> Value = "CompletedAndPassed" : If the LMS receives statements with the verbs "Completed" and "Passed", then the LMS will consider the AU satisfied.</li>
        <li><code>moveOn</code> Value = "CompletedOrPassed" : If the LMS receives a statement with either of the verbs "Completed" or "Passed", then the LMS will consider the AU satisfied.</li>
        <li><code>moveOn</code> Value = "NotApplicable": The LMS will consider the AU satisfied.</li>
      </ul>
      <p><strong>Usage:</strong></p>
      <p>If all member AUs in a block are satisfied, then the block is considered satisfied for prerequisites and sequencing.<br>If all member AUs and Blocks are satisfied, then the course is considered satisfied for prerequisites or credit in relation to other courses or curricula.</p>
      <p><strong>Value space: </strong>"Passed", "Completed", "CompletedAndPassed", "CompletedOrPassed", "NotApplicable"</p>
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
          <li>To accommodate "non-browser" applications, an application specific protocol MAY be used in the url:<br>
              &lt;application&gt;://&lt;URL to content&gt;</li>
          <li>Regardless of the value of &lt;scheme&gt;, the remaining portion of the URL MUST conform to RFC1738 - Uniform Resource Locators (URL).</li>
          <li>If the url includes a query string, the values from that query string MUST be merged with the cmi5 parameters at launch time (see Section 8.1 Launch Method).</li>
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

<a name="course_package"></a>
# 14.0 Course Package

Conceptually, a course package is a collection of all of the components (AUs) of the course. While previous standards often equated this with the gathering of all resources into a single archive (often a .ZIP file), cmi5 does not have this restriction; all files can be "packaged", even by reference.

Technically, a course package is an XML file format with a course structure. It can be standalone or contained in a ZIP file. A course package, when located in a ZIP file, MUST be named "cmi5.xml". The course package MUST conform to https://w3id.org/xapi/profiles/cmi5/v1/CourseStructure.xsd. Available locally in v1/CourseStructure.xsd.

An LMS MUST provide functionality such that a targeted course package is processed, resulting in a Course Structure import (See Section 3.0 Course Structure Data Requirements ). An LMS MUST support Course Packages in at least these three file formats:

* Standalone XML file
* 32-bit Zip Format
* 64-bit Zip Format
 
An LMS MAY support alternate course package formats.

<a name="course_packages_in_zip_format"></a>
## 14.1 Course Packages in ZIP Format
The two ZIP file formats MUST follow the specification defined at https://www.pkware.com/support/zip-app-note. When the ZIP file is used to package a course, it MUST contain the course structure XML file at its root directory and it MAY contain media associated with the course AUs.

* Any entry point for an AU included in a ZIP course package SHOULD be referenced by a relative URL in the Course Structure XML.
* Any entry point for an AU not included in a ZIP course package MUST be referenced by a fully qualified URL in the Course Structure XML.
* A ZIP course package MAY contain a mix of fully qualified and relative URLs, provided the rules above are followed.

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

Copyright &copy; 2012-2021 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defense, All rights reserved

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License. 
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed 
on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for 
the specific language governing permissions and limitations under the License.

-------
