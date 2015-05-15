cmi5 Runtime Environment 
---
>
>Copyright &copy; 2012-2015 ADL, All rights reserved
>

----


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
* [__5.0 Conceptual Model: Informative__](#concept)
* [__6.0 LMS Requirements__](#lms_requirements)
  * [6.1 Course Structures](#course_structures)
  * [6.3 LMS Statement API Requirements](#lms_statement_api_requirements)
* [__7.0 AU Requirements__](#au_requirements)
  * [7.1 AU State API Requirements](#au_state_api_requirements)
  * [7.2 AU Statement API Requirements](#au_statement_api_requirements)
      * [7.2.1 Placement of the sessionId in Statements](#placement)
      * [7.2.2 First Statement API Call](#first_statement_au)
      * [7.1.2 Last Statement Call](#last_statement_au)
* [__8.0 Content Launch Mechanisms__](#content_launch)
  * [8.1 Web (Browser) Environment](#browser_environment)
  * [8.2 Authorization Token Fetch URL](#fetch_url)
  * [8.3 Other Launch Environments](#other_environment)
* [__9.0 xAPI Statement Data Model__](#xapi_data_model)
  * [9.1 Statement ID](#ID)
  * [9.2 Actor](#Actor)
  * [9.3 Verbs](#verbs)
  * [9.4 Object](#Object)
      * [9.4.1 objectType](#objectType)
      * [9.4.2 Object ID](#Object_ID)
      * [9.4.3 Definition](#Definition)
  * [9.5 Result](#Result)
      * [9.5.1 Score](#Score)
      * [9.5.2 Success](#Success)
      * [9.5.3 Completion](#Completion)
      * [9.5.4 Duration](#Duration)
  * [9.6 Context](#Context)
      * [9.6.1 Registration](#Registration)
      * [9.6.2 ContextActivities] (#ContextActivities)
      * [9.6.3 Extensions](#extensions)
* [__10.0 xAPI State Data Model__](#xapi_state)
* [__11.0 xAPI Agent Profile Data Model__](#xapi_agent_profile)
* [__12.0 xAPI Activity Profile Data Model__](#xapi_activity_profile)

[__Bibliography__](#bibliography)

[__License Agreement__](#license_agreement)

------


<a name="revhistory"></a>	
## Revision History

__0.1 Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__  

Converted existing working draft to markdown format from Microsoft Word.

All previous work from 2012 discarded.


<a name="contributors"></a> 
##Contributors

<table>
	<tr><th>Name:</th><th>Organization:</th></tr>
	<tr><td>Ed Cohen</td><td>AICC Infrastructure Subcommittee Chair</td></tr>
	<tr><td>Aaron Silvers</td><td>ADL</td></tr>
	<tr><td>Jonathan Poltrack</td><td>ADL</td></tr>
	<tr><td>Andy Johnson</td><td>ADL</td></tr>
	<tr><td>Tom Creighton</td><td>ADL</td></tr>
	<tr><td>Nik Hruska</td><td>ADL</td></tr>
	<tr><td>Avron Barr</td><td>The LETSI Foundation</td></tr>
	<tr><td>Mike Rustici</td><td>Rustici Software</td></tr>
	<tr><td>Ben Clark</td><td>Rustici Software</td></tr>
	<tr><td>Megan Bowe</td><td>Rustici Software</td></tr>
	<tr><td>Jacques Talvard</td><td>Airbus</td></tr>
	<tr><td>William A. McDonald</td><td>Boeing</td></tr>
	<tr><td>Ray Lowery</td><td>Pratt &amp; Whitney</td></tr>
	<tr><td>John Kleeman</td><td>Questionmark</td></tr>
	<tr><td>Kris Rockwell</td><td>Hybrid Learning Systems</td></tr>
	<tr><td>Paul Roberts</td><td>Questionmark</td></tr>
	<tr><td>Christopher Reynolds</td><td>Pelesys</td></tr>
	<tr><td>Mingrui Zheng</td><td>Pelesys</td></tr>
	<tr><td>Chris Sawwa</td><td>Meridian Knowledge Systems</td></tr>
	<tr><td>Michael Roberts</td><td>VTraining Room</td></tr>
	<tr><td>Thomas Person</td><td>(Formerly of Adobe)</td></tr>
	<tr><td>Andrew Downes</td><td>Epic Learning</td></tr>
	<tr><td>Henry Ryng</td><td>inXsol</td></tr>
	<tr><td>Art Werkenthin</td><td>RISC, Inc.</td></tr>
	<tr><td>Chris Handorf</td><td>Pearson</td></tr>
</table> 

-------

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
* Reporting requirements for the LMS.

This specification references how to use the xAPI specification within this scope.

Other uses of the xAPI specification are outside of this scope.

Uses of activities not explicitly defined above are outside of the scope of this specification.


<a name="references"></a> 
#2.0  References

The following referenced documents are indispensable for the application of this
specification. 

RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998.

“Experience API”, curent working draft, ADL, 2012-2013  
<https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md>

cmi5 Course Structure, Sandstone 1st Edition    
<https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_coursestructure.md>


<a name="definitions"></a>   
#3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user that manages the LMS and related systems.
Such a user performs tasks such as learner enrollment, course structure definition, and
report management. 

* __Assignable Unit (AU)__:  A learning presentation launched from an
LMS. The AU is the unit of tracking and management. The AU collects data on the learner
and sends it to the LMS system. An Learning Activity Provider maps to a single AU.  

* __Course__: A collection of assignable units, in a logical grouping. A course is typically 
an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied
sequence, representing a course.

* __Experience API (xAPI)__: xAPI is a runtime data communication specification for learning
content (AU) to send and receive data to an LRS. The xAPI specification is referenced by this
document is used to define the data transport and the data model.

* __Learner__: The end user viewing/using the learning content (AU).

* __Learning Activity Provider (AP)__:  Learning Activity Provider (AP) as defined in the
xAPI specification.

* __Learning Management System (LMS)__: A computer system that may include the
capabilities to register learners, launch learning presentations, analyze and report
learner performance, and track learners progress. LMS launching, reporting, and tracking
roles are the focus of the cmi5 specification.  The LMS MUST have an LRS as part of its
implementation.  The use of the term "LMS" in this document MUST refer to the combination of an LMS and an LRS.

* __Learning Records Store (LRS)__: As defined in the xAPI specification. In this 
specification, the LMS MUST implement an LRS with additional requirements as specified in
this document.


<a name="acronyms"></a> 
##3.1 Abbreviations and Acronyms
<BR>
__ADL__: Advanced Distributed Learning  
__AICC__: Aviation Industry Computer-Based Training Committee  
__API__: Application Programming Interface  
__CMI__: Computer Managed Instruction  
__LMS__: Learning Management System  
__LRS__: Learning Record Store  
__PII__: Personally Identifiable Information  
__URI__: Uniform Resource Identifier  
__URL__: Uniform Resource Locator  
__URN__: Uniform Resource Name  
__XAPI__: Experience API  
<BR>


<a name="conformance"></a>  
#4.0  Conformance

Conformance to this specification is defined in section. 

In this specification, 
“MUST” is to be interpreted as a requirement on an implementation.
“MUST NOT” is to be interpreted as a prohibition.
“SHOULD” is to be interpreted as a recommendation for implementation.
“SHOULD NOT” is to be interpreted as the converse of “SHOULD”.
“MAY” is to be interpreted as a course of action that is permissible within the limits of this specification.
“NEED NOT” indicates a course of action that is not required.

Uses of xAPI specification outside the scope this specification do not affect conformance
with this specification.

<a name="au_conformance"></a> 
##4.1 Assignable Unit (AU)

An Assignable Unit MUST conform to all requirements listed in Section 7 – AU Requirements.

An Assignable Unit MUST conform to all requirements as specified in the xAPI specification (see References).

An Assignable Unit MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.

<a name="lms_conformance"></a> 
##4.2 Learning Management Systems (LMS)

A LMS MUST conform to all LRS requirements as specified in the xAPI specification
(see References)

The LMS MUST include the ability to retrieve and show all statements (including attachments and extensions) to a user (with the understanding of scaling permissions/authorization).

The LMS MUST decode the attachment and make it available as a file with the original MIME type.

The LMS MUST conform to all requirements listed in Section 6 – LMS Requirements.

The LMS MUST NOT implement any features or functionality (optional or mandatory)
described in this specification in a non-conforming manner.


<a name="concept"></a> 
#5.0 Conceptual Model: Informative  

Synopsis of the cmi5 model:

* An LMS imports a course structure which may contain one or more Assignable Units.
* An LMS administrative user assigns a course to a learner.
* A learner authenticates with an LMS or related system.
* A learner launches an Assignable Unit (learning content) from the LMS or associated
launching system.
* The LMS writes lauch data to the integrated LRS. 
* The Assignable Unit (AU) sends a message to the LMS requesting launch parameters and recovers
previous state information from the LMS.
* Learner views the AU content and performs the learning. During this time
the AU may request from and store data to the LMS.
* The learner exits the AU.
* The AU reports final tracking data to the LMS and issues a "terminated" message.
* The LMS makes the next AU(s) available to the learner based on the results from the closed AU session and course structure parameters.
* Administrative users create and view reports of tracking data recorded by AU(s) for individual learners.

Responsibilities of the Assignable Unit:

* Parse the parameters from the launching environment to determine where the LMS location
is and initiate communication with the LMS.
* Acting as “client”, send and receive messages using the defined transport mechanism(s)
and associate commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Send an “terminated” message prior to terminating the AU’s execution.

Responsibilities of the LMS:

* Create and maintain course structures.
* Acting as a “server”, receive and reply to messages using the defined transport.
mechanism(s) and associate commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Launch AUs contained in courses, in defined environment(s), when selected by the learner.

<a name="lms_requirements"></a>  
#6.0 LMS Requirements

LMS systems MUST meet the following requirements to conform to this specification:  

1. The LMS MUST implement an LRS as defined in the xAPI specification.
2. The LMS MUST support Course Structures as defined in [cmi5-002] cmi5 Course Structure.
3. The LMS MUST implement additional "State API" requirements to initialize AU state as defined in Section 10.
4. The LMS MUST implement the runtime launch interface as defined in Section 8.0 - Content Launch Mechanisms.
5. The LMS MUST implement additional xAPI "Statement API" requirements as defined in Section 9.
6. The LMS MUST implement additional xAPI "Agent Profile API" requirements as defined in Section 11 

<a name="course_structures"></a>  
##6.1 Course structures

1. The LMS MUST implement the import of Course Structures according to [cmi5-002] cmi5 Course Structure.
2. The LMS SHOULD implement the export of Course Structures according to [cmi5-002] cmi5 Course Structure.
3. The LMS SHOULD implement a user interface to allow the LMS administrative users to create and edit course structures.
4. The LMS MUST be able support course structures with one or more AUs

Course structures MUST contain the following data for each AU in a course:

* URL location – A URL to the AU’s location (entry point)
* Activity ID – The AU’s activity ID as defined in the xAPI specification (determined by the course designer).
* Launch Method - 
    * “OwnWindow” – The LMS MUST either spawn a new window for the AU launched, or redirect the existing window to the AU.
    * “AnyWindow” – The AU does not care about the window context (all browser windows options are acceptable – FrameSet, New Window, redirect, etc.) The LMS may use whichever method desired..
* Authentication Method – The authentication method used by the AU to access the LMS’s
LRS.  (Either HTTP basic or OAuth 1.0)
* Launch Parameters –A set of static data specific to the AU’s design. Used as parameters
by the AU to modify its behavior. 
* Entitlement Key – This is a value provided by the AU content provider and is used by the
AU to determine whether the LMS instance and/or Learner are entitled to view the content.
It is provided to the AU via a State API request.

Course Structures MUST contain at least one AU.

LMS MUST have the ability to create and maintain course structures containing more than
1000 AU’s.

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
3. The AU MUST implement additional xAPI “Statement API” requirements as defined in Section 9.0.
4. The AU MUST implement additional xAPI “Agent Profile API” requirements as defined in Section 11.0.

<a name="au_state_api_requirements"></a> 
##7.1 AU State API Requirements

AU’s MUST meet the following requirements to conform to this specification:

* The AU MUST implement additional xAPI “Statement API” requirements as defined in Section 9.0 .
* The AU MUST implement additional xAPI “State API” requirements as defined in Section 10.
* The AU MUST implement additional xAPI “Agent Profile API” requirements as defined in Section 11.


<a name="au_statement_api_requirements"></a>  
##7.2 AU Statement API Requirements

<a name="placement"></a> 
###7.2.1 Placement of sessionId in Statements

The AU MUST retrieve the value of sessionId at launch time as specified in Section 10 State API.  The AU MUST place the value of the sessionId in the context extensions for all xAPI statements it records.  

Usage in an xAPI Statement:

```javascript
"extensions": {
       “sessionId”: <sessionId value>
     }
```
Example:
```javascript
"extensions": {
       “sessionId”: ”xyz123”
     }
```

<a name="first_statement_au"></a> 
###7.2.2 First Statement API Call
The AU MUST issue a statement to the LRS after being launched, initialized, and ready for learner interaction using the Initialized verb as described in Section 9.3.2.

<a name="last_statement_au"></a>  
###7.1.2 Last Statement Call
The AU MUST issue a statement to the LRS prior to termination using the Terminated verb per section 9.3.8.

<a name="content_launch"></a>  
#8.0 Content Launch Mechanisms

<a name="browser_environment"></a>  
##8.1 Web (Browser) Environment

###8.1.1 Launch Method

The AU MUST be launched by the LMS using one of the following methods, depending on the launchMethod in the Course Structure (Section 7.1.4 AU Meta Data, URL):

When the launchMethod is "OwnWindow", the LMS MUST use one of the following:
<ol><li>Spawning a new browser window for the AU.</li>
<li>Re-directing the existing browser window to the AU.</li>
</ol>

When the launchMethod is "AnyWindow", the LMS may choose the window context of the AU.  All browser window options are acceptable - Frameset, New window, browser redirect, etc.

In either case, the AU MUST be launched by the LMS with a URL having query string launch parameters as
defined in this section. The launch parameters MUST be name/value pairs in a query string appended to the URL that
launches the AU.

If the AU’s URL requires a query string for other purposes, then the names
MUST NOT collide with named parameters defined below.

The order of the name/value pairs is not significant. AU’s MUST have the ability to
process them in any order.

Each value for the associated names MUST be URL-encoded. 

The format of the launching URL is as follows:  

```
<URL to AU>
?endpoint=<URL to LMS Listener>
&fetch=<Fetch URL for Authorization Token (optional)– if OAuth is not used>
&actor=<Actor Object>
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
  <tr><th colspan=3 align ="left">endpoint</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>A URL to the LMS listener location for xAPI messages to be sent to.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS MUST place the <strong><em>endpoint </em></strong>in the query string.<strong></strong>The LMS SHOULD limit the use of the <strong><em>auth</em></strong> value for the duration of a specific/user/AU/registration</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>AU Usage:</th><td>The AU MUST get the <strong><em>endpoint </em></strong>value from the query string. The AU MUST use the <strong><em>endpoint </em></strong>value as the URL location to send xAPI messages to.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>A URL-encoded URL</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>https://mylms.aicc.org/MyCMI5_listener.pl</td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">fetch</th></tr>
  <tr><td>&nbsp;</td><th align ="right">Description:</th><td>The <strong><em>fetch</em></strong> URL is used by the AU to obtain an authentication token created &amp; managed by the LMS.  The <strong><em>fetch</em></strong> URL is only used when OAuth authentication is not practical or desired.  The authentication token is used by the AU being launched.</td></tr>
  <tr><td>&nbsp;</td><th align ="right">LMS Usage:</th><td>The LMS MUST place the <strong><em>fetch</em></strong> in the Launch URL when Basic authentication is indicated in the course structure definition. <br /><br />If OAuth is the method of authentication specified, the LMS MUST NOT place the <strong><em>fetch</em></strong>name/value pair<strong></strong> in the query string.  <br /><br />The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses SHOULD generate an error as defined in section 8.2. The authorization token returned by the <strong><em>fetch</em></strong> URL MUST be limited to the duration of a specific user session. </td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>When Basic authentication is used, the AU MUST get the <strong><em>fetch</em></strong> value from the query string. The AU MUST make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve the authorization token as defined in section 8.2. The AU MUST then place the authorization token in the Authorization headers of all HTTP messages made to the endpoint using the xAPI.  The AU SHOULD NOT make one more than 1 post to the <strong><em>fetch</em></strong> URL</td></tr>
  <tr><td>&nbsp;</td><th align ="right">Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>http://cmi5-lms-system.org/tokenGen.htm?k=2390289x0</td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">actor</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>A JSON object called “actor” (as defined in the xAPI specification) that identifies the learner launching the AU so the AU will be able to include it in xAPI messages.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>actor </em></strong>in the query string based on the authenticated learner’s identity. The    LMS SHOULD create an actor object that is specific to the LMS instance that does NOT include sensitive PII of the learner.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU MUST get the <strong><em>actor </em></strong>value from the query string. AU MUST use the <strong><em>actor </em></strong>value in API calls that require an “actor” object when sending xAPI messages</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td> A JSON Actor object (as defined in Section 9.2)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>{"objectType": "Agent","account": {"homePage": "http://www.example.com","name": "1625378"}</td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">registration</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>A Registration ID corresponding to the learner’s enrollment for the AU being launched.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>registration</em></strong> in the query string based on the authenticated learner’s corresponding    enrollment for the Course that the AU being launched is a member of.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>The AU MUST get the <strong><em>registration</em></strong> value from the query string. AU MUST use the <strong><em>registration</em></strong> value in API calls that require an “registration id” when sending xAPI messages</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>UUID (as defined in the xAPI specification)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

<table>
  <tr><th colspan=3 align ="left">activityId</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>The Activity ID of the AU being launched.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>activityId</em></strong> in the query string based on the definition of the AU in the course    structure.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU MUST get the <strong><em>activityId</em></strong> value from the query string. AU MUST use the <strong><em>activityId</em></strong> value in API calls that require an “activity id” when sending xAPI messages.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>IRI (as defined in the cmi5 Course Structure Section 7.1.4 - AU Metadata)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

<br />
<a name="fetch_url"></a>  
##8.2 Authorization Token Fetch URL
###8.2.1 Overview
When Basic authentication is used, the LMS MUST include the <strong><em>fetch</em></strong> name/value pair in the launch URL.  The AU MUST make an HTTP POST to the <strong><em>fetch</em></strong> URL to retrieve an authorization token.  Please note than an HTTP GET is not allowed in order to prevent caching of the request.

The <strong><em>fetch</em></strong> URL MUST return a JSON structure using a content-type of "application/json". An example JSON structure is shown below:
```javascript
{
  "auth-token": "QWxhZGRpbjpvcGVuIHNlc2FtZQ=="
}
```
The AU MUST place the <strong><em>auth-token</em></strong> in the HTTP header, as defined in <a href='http://tools.ietf.org/html/rfc1945#section-11'>RFC 1945 - 11.1 Basic Authentication Scheme</a>, in all subsequent xAPI communications with the LMS.  The authorization token returned by the <strong><em>fetch</em></strong> URL MUST be limited to the duration of the session.

The AU SHOULD NOT attempt to retrieve the authorization token more than once.  The <strong><em>fetch</em></strong> URL is a "one-time use" URL and subsequent uses SHOULD generate an error (see Section 8.2.3). 


###8.2.2 Definition: auth-token
<table>
  <tr><th colspan=3 align ="left">auth-token</th></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Description:</th><td>An authorization token used in all xAPI communications with the LMS when Basic authentication is used.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>LMS Usage:</th><td>The LMS MUST place the value for <strong><em>auth-token</em></strong> in a JSON structure, as shown in Section 8.2.1, in its response to a <strong><em>fetch</em></strong> URL request. The response MUST have a content-type of "application/json".</td></tr>
  <tr><td>&nbsp;</td><th align ="right" >AU Usage:</th><td>AU MUST get the <strong><em>auth-token</em></strong> value using an HTTP POST to the <strong><em>fetch</em></strong> URL. The AU MUST then place the authorization token in the Authorization headers of all HTTP messages made to the endpoint using the xAPI.</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Value space:</th><td>Defined by the LMS</td></tr>
  <tr><td>&nbsp;</td><th align ="right" nowrap>Sample value:</th><td>QWxhZGRpbjpvcGVuIHNlc2FtZQ==</td></tr>
</table>

###8.2.3 Errors
####8.2.3.1 Duplicate call to fetch URL
The <strong><em>fetch</em></strong> URL is a "one-time use" URL and only the first request SHOULD return the <strong><em>auth-token</em></strong>. Subsequent requests made to the <strong><em>fetch</em></strong> during the session SHOULD generate an error.  The error SHOULD be returned in the form of a JSON structure using content-type "application/json".  An example of JSON structure is shown below:
```javascript
{
  "error-code": "1",
  "error-text": "The authorization token has already been returned."
}
```
####8.2.3.2 Error Values
The following <strong><em>error-code</em></strong> values are allowed.
<table>
<tr><td><strong>Code</strong></td><td><strong>Meaning</strong></td></tr>
<tr><td>1</td><td>Already in Use or Expired</td></tr>
<tr><td>2</td><td>General Security Error</td></tr>
<tr><td>3</td><td>General Application Error</td></tr>
</table>

The values for <strong><em>error-text</em></strong> are defined by the LMS.

<br />

<a name="other_environment"></a>  
##8.3 Other Launch Environments

Other launch environments are not currently implemented in this specification. The
following launch environments are being considered for future releases:  

* Windows/XP/7/8 Pro  
* Windows RT  
* Mac OS X  
* Linux  
* Android  
* iOS  

cmi5 implementations for LMS’s and AU’s in these other environments will use the same
REST communication interface as specified in xAPI specification.  The xAPI specification
does not specify launch mechanisms.

<a name="xapi_data_model"/>  
#9.0 xAPI Statement Data Model  

<a name="ID" ></a>
##9.1 Statement ID
The AU will not provide a statement ID for cmi5 defined statements.  (The LRS will assign statement IDs)  
  
<a name="Actor" ></a>
##9.2 Actor
The Actor object will be defined by the LMS.  The Actor object for all statements with cmi5 defined verbs MUST be of type "Agent" and MUST contain an account object.

An Example of usage in a statement:

```javascript
{
  "actor": {
    "objectType": "Agent",
    "account": {
        "homePage": "http://www.example.com",
        "name": "1625378"
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

AU’s MUST use the below verbs indicated as mandatory in other sections of this
specification.

AU’s may use additional verbs not listed in this specification.

LMS system MUST record and provide reporting for all statements regardless of which verbs
AU’s use in statement.  

###9.3.1 Launched
<table>
<tr><th align="left">Verb</th><td>Launched</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/launched</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Launched" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Launched” indicates that the AU was launched by the LMS.</td>
</tr><tr><th align="left">AU Obligations</th><td>None</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS before launching an AU.  (See Statement API Section 10) </td></tr>
</tr><tr><th align="left">Usage</th><td>A "Launched" statement is used to indicate that the LMS has launched the AU. It SHOULD be used in combination with the "Initialized" statement sent by the AU in a reasonable period of time to determine whether the AU was successfully launched. </td></tr>
</table>

###9.3.2 Initialized
<table>
<tr><th align="left">Verb</th><td>Initialized</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/initialized</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Initialized" }</td></tr>
<tr><th align="left">Description</th><td>An "Initialized" statement is used by the AU to indicate that it has been fully initialized and MUST follow the "Launched" statement created by the LMS within a reasonable period of time.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU MUST use "Initialized" in the first statement in the AU session.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>Verify that this verb is recorded by the AU immediately after launch</td></tr>
</tr><tr><th align="left">Usage</th><td>An "Initialized" statement is used by the AU to indicate that it has been fully initialized and SHOULD follow the "Launched" statement created by the LMS within a reasonable period of time.</td></tr>
</table>

###9.3.3 Completed
<table>
<tr><th align="left">Verb</th><td>Completed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/completed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Completed" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Completed” indicates the learner viewed or did all of the relevant activities in an AU presentation.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU MUST record a statement containing the "Completed" verb when the learner has experienced all relevant material in the AU.  The AU MUST NOT issue multiple statements with "Completed" for the same AU within a given AU session or course registration for a given learner.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>The criterion for "Completed" is determined by the AU design.</td></tr>
</table>

###9.3.4 Passed
<table>
<tr><th align="left">Verb</th><td>Passed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/passed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Passed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and succeed in a judged activity in the AU. </td></tr>
<tr><th align="left">AU Obligations</th><td>The AU MUST record a statement containing the "Passed" verb when the learner has attempted and passed the AU. The AU MUST NOT issue multiple statements with "Passed" for the same AU within a given AU session or course registration for a given learner, unless passIsFinal has been set to false. If the "Passed" statement contains a (scaled) score, the (scaled) score MUST be equal to or greater than the "MasteryScore" indicated in the course structure. (See course structure section 7.1.4)</td></tr>
<tr><th align="left">LMS Obligations</th><td>The LMS MUST record "MasteryScore" data in the state API (if present in the course structure) for the AU prior to initial AU launch. (See Section 10) The LMS MUST use either "Passed" or "Completed" statements (or both) based on the moveOn criteria for the AU as defined in the Course Structure. (See Course Structure,  Section 7.1.4 - MoveOn).</td></tr>
<tr><th align="left">Usage</th><td>The AU MUST record a statement containing the "Passed" verb when the learner has attempted and successfully passed the judged activity.</td></tr>
</table>


###9.3.5 Failed
<table>
<tr><th align="left">Verb</th><td>Failed</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/failed</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Failed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and failed in a judged activity in the AU. </td>
</tr><tr><th align="left">AU Obligations</th><td>The AU MUST record a statement containing the "Failed" verb when the learner has attempted and failed the AU.  If the "Failed" statement contains a score, the score MUST be less than the "MasteryScore" indicated in the course structure.  (See Course Structure, Section 7.1.4 - MasteryScore). A "Failed" statement MUST NOT be issued after a "Passed" statement has been issued, unless passIsFinal has been set to false.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS MUST record "MasteryScore" data in the state API (if present in the course structure) for the AU prior to initial AU launch.  (See Section 10).<br/>
<br/>
The LMS MUST use either "Passed" or "Completed" statements (or both) for determining for course completion (or course collateral credit) criteria for the AU.  (See Course Structure, Section 7.1.4 - MasteryScore).</td></tr>
</tr><tr><th align="left">Usage</th><td>The AU MUST record a statement containing the "Failed" verb when the learner has attempted and failed the judged activity.</td></tr>
</table>


###9.3.6 Abandoned
<table>
<tr><th align="left">Verb</th><td>Abandoned</td></tr>
<tr><th align="left">ID</th><td>http://purl.org/xapi/adl/verbs/abandoned</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Abandoned" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Abandoned” indicates that the AU session was abnormally terminated by a learner's action (or due to a system failure).</td>
</tr><tr><th align="left">AU Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS MUST use the "Terminated" statement to determine that the AU session has ended.  In the absence of an "Terminated" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS MUST record an "Abandoned" statement on behalf of the AU indicating an abnormal session termination. </td></tr>
</tr><tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>



###9.3.7 Waived
<table>
<tr><th align="left">Verb</th><td>Waived</td></tr>
<tr><th align="left">ID</th><td>http://purl.org/xapi/adl/verbs/waived</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Received Waiver" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Waived” indicates that the LMS has determined that the AU 
requirements were met by means other than completing the AU.</td>
</tr><tr><th align="left">AU Obligations</th><td>None</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS MUST use this verb in a statement recorded in the LRS when it determines that the AU may be waived.  A statement containing a "Waived" verb MUST include a "reason" in the extension property of the Statement Result.  (See Section 9.6.2.2) </td></tr>
</tr><tr><th align="left">Usage</th><td>A "Waived" statement is used by the LMS to indicate that the AU may be skipped by the learner.</td></tr>
</table>



###9.3.8 Terminated
<table>
<tr><th align="left">Verb</th><td>Terminated</td></tr>
<tr><th align="left">ID</th><td>http://adlnet.gov/expapi/verbs/terminated</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Terminated" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Terminated” indicates that the AU was terminated by the Learner and that the AU will
not be recording any more statements for the launch session.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU MUST record a statement containing the "Terminated" verb. This statement MUST be the last statement recorded by the AU in a session.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS MUST use the "Terminated" statement to determine that the AU session has ended.  In the absence of an "Terminated" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS MUST record a "Abandoned" statement on behalf of the AU indicating an abnormal session termination per section 9.3.8 Abandoned.</td></tr>
</tr><tr><th align="left">Usage</th><td>See obligations.</td></tr>
</table>

###9.3.9 Satisfied
<table>
<tr><th align="left">Verb</th><td>Satisfied</td></tr>
<tr><th align="left">ID</th><td>http://purl.org/xapi/adl/verbs/satisfied</td></tr>
<tr><th align="left">Description</th><td>The verb “Satisfied” indicates that the LMS has determined that the Learner has met the moveOn criteria of all AU's in a block or has met the moveOn criteria for all AU's in the course.</td></tr>
<tr><th align="left">AU Obligations</th><td>None</td></tr>
<th align="left">LMS Obligations</th><td>
<ol><li>The LMS MUST use the "Satisfied" statement when the learner has met the moveOn criteria of all AU's in a block.  In this statement the LMS MUST use the block id (Section 7.1.2 in the cmi5 Course Structure document) as the Object id (Section 9.4 - Object).</li>
<li>The LMS MUST also use the "Satisfied" statement when the learner has met the moveOn criteria for all AU's in a course.  In this statement the LMS MUST use the course id (Section 7.1.1 in the cmi5 Course Structure document) as the Object id (Section 9.4 - Object)</li>
</ol></td></tr>
<tr><th align="left">Usage</th><td>See LMS obligations.</td></tr>
</table>

<BR>
<BR>

<a name="Object"></a> 
##9.4 Object 
The Object in a cmi5 defined statement represents the AU.  An Object MUST be present, as specified in this section, in all statements with cmi5 defined verbs.

<a name="objectType"></a> 
###9.4.1 objectType
The objectType property of an Object in statements with a cmi5 verb MUST be set to "activity".

<a name="Object_ID"></a> 
###9.4.2 id 
The value of the Object's ID property for a given AU MUST match the AU ID (activityId) defined in the URL launch line and the Course Structure.

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

<a name="Result"></a> 
##9.5 Result
Result may be present in a statement depending on the cmi5 verb used.  

Example JSON:
```javascript
  "result": {
     "score": {
         "scaled": "0.65",
         "raw": "65",
         "min": "0",
         "max": "100"
     },
     "success": "false",
     "duration": "PT30M",
     "extensions": {
         "http://purl.org/xapi/cmi5/result/extensions/progress": "100"
     }
   }
 ```

<a name="Score"></a> 
###9.5.1 Score

A score is not required to be reported.  If a score is reported by an AU, the verb MUST be consistent with masteryScore (if defined for the AU in the Course Structure).

<ul><li><strong>scaled</strong><br/>A decimal value between 0 and 1.</li>
<li><strong>raw</strong><br/>An integer value between the "min" and "max" properties of the <em><strong>score</strong></em> object.  When the "raw" value is provided, the AU MUST also provide the "min" and "max" values for <em><strong>score</strong></em>.</li>
<li><strong>min</strong><br/>An integer value indicating the minimum value for the "raw" score property.</li>
<li><strong>max</strong><br/>An integer value indicating the maximum value for the "raw" score property.</li>
</ul>

<a name="Success"></a>
###9.5.2 Success 

The success property of the result MUST be set to true for statements having the following cmi5 defined verbs:

- Passed
- Waived

The success property of the result MUST be set to false for statements having the following cmi5 defined verbs:

- Failed
- Abandoned

<a name="Completion"></a>
###9.5.3 Completion
The completion property of the result MUST be set to true for statements having the following cmi5 defined verbs:

- Completed
- Waived

The completion property of the result MUST be set to false for statements having the following cmi5 defined verbs:

- Failed
- Abandoned

<a name="Duration"></a>
###9.5.4 Duration
The duration property is an ISO 8601 formatted time value required in certain statements as defined in this section.
####9.5.4.1 AU statements that include duration
##### Terminated Statement
The AU MUST include the duration property in "Terminated" statements.  The AU SHOULD calculate duration for Terminated statements as the time difference between the "Initialized" statement and the "Terminated" statement.  The AU may use other methods to calculate the duration based on criteria determined by the AU.
##### Completed Statement
The AU MUST include the duration property in "Completed" statements.  The AU SHOULD calculate duration as the time spent by the learner to achieve completion status.
##### Passed Statement
The AU MUST include the duration property in "Passed" statements.  The AU SHOULD calculate duration as the time spent by the learner to attempt and succeed in a judged activity of the AU. 
##### Failed Statement
The AU MUST include the duration property in "Failed" statements. The AU SHOULD calculate duration as the time spent by the learner to attempt and fail in a judged activity of the AU.
####9.5.4.2 LMS statements that include duration
##### Abandoned Statement
The duration property SHOULD be included in "Abandoned" statements. The duration property SHOULD be set as the total session time, calculated as the time between the “Launched” statement and the last statement issued by the AU.

###9.5.5 Extensions
####9.5.5.1 Progress
An integer value indicating the completion of the AU as a percentage. The AU may set this value in statements to indicate level of completion between 0 and 100 percent.

<a name="Context"></a> 
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
       "http://purl.org/xapi/cmi5/context/extensions/sessionid": "<session id provided by the LMS>",
       "http://purl.org/xapi/cmi5/context/extensions/reason": "<reason for 'waived' verb, if statement is 'waived' statement only>",
      }
   }
```

<a name="Registration"></a> 
###9.6.1 registration
The value for the registration property used in the context object MUST be the value provided by the LMS.  The LMS MUST generate this value and pass it to the AU via the launch line. 

<a name="ContextActivities"></a>
###9.6.2  contextActivities
Statements with a results object (Section 9.5) that include either "success” or "completion” properties MUST contain a contextActivities object with the "id" property of "moveon". Other statements MUST NOT include this property. The purpose of this property is to facilitate searches of the LRS by the LMS or other reporting systems.

All cmi5 Statements MUST include an object with the "id" property of "cmi5" in contextActivities. This purpose of this property is to identify cmi5 specific statements during LRS searches.

<a name="extensions"></a> 
###9.6.3 extensions
The following are extensions specified for cmi5.  Other extensions are permitted provided they do not conflict or duplicate the ones specified here.  

####9.6.3.1 sessionId

<table>
  <tr><th align ="right" nowrap>ID:</th><td>http://purl.org/xapi/cmi5/context/extensions/sessionid</td></tr>
  <tr><th align ="right" nowrap>Description:</th><td>An unique identifier for an single AU launch session based on actor and course registration </td></tr>
  <tr><th align ="right" nowrap>LMS Usage:</th><td>The value for Session ID is generated by the LMS. The LMS MUST also record the Session ID in the State API (See Section 10) prior to launching an AU. The LMS MUST also provide the Session ID in the context as an extension for all Statements (with cmi5 defined verbs) it makes directly in the LRS.</td></tr>
  <tr><th align ="right" nowrap>AU Usage:</th><td>An AU MUST include the sessionId provided by the LMS in the context as an extension for all Statements (with cmi5 defined verbs) it makes directly in the LRS. </td></tr>
 <tr><th align ="right" nowrap>AU Obligation:</th><td>Required</td></tr>
 <tr><th align ="right" nowrap>LMS Obligation:</th><td>Required</td></tr>
  <tr><th align ="right" nowrap>Data type:</th><td>String (URL-encoded)</td></tr>
  <tr><th align ="right" nowrap>Value space:</th><td>string value</td></tr>
  <tr><th align ="right" nowrap>Sample value:</th><td></td></tr>
</table>

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
 <tr><th align ="right" nowrap>LMS Obligation:</th><td>This is a required extension for LMS statements that include the Waived verb</td></tr>
  <tr><th align ="right" nowrap>Data type:</th><td>String</td></tr>
  <tr><th align ="right" nowrap>Value space:</th><td><ul>
<li>"Tested Out"</li>  
<li>"Equivalent AU"</li>  
<li>"Equivalent Outside Activity"</li>    
<li>"Administrative"</li> 
</ul></td></tr>
  <tr><th align ="right" nowrap>Sample value:</th><td>Tested Out</td></tr>
</table>

<a name="xapi_state"></a>  
#10.0 xAPI State Data Model

Prior to launching an AU, the LMS MUST create a document in the State API record in the 
LRS.  This MUST be a JSON document as defined in this section with a document name (stateId) of "LMS.LaunchData". The LMS MUST only create one State document for the combination of activityId, agent, registration, and stateId.  

An example of the JSON document is shown below.

```javascript
{
   "contextTemplate": {
         "extensions": {
            "http://purl.org/xapi/cmi5/context/extensions/sessionid": "<LMS generated sessionId>"
         }
   },
   "launchMode": "<launchMode value>",
   "launchParameters": "<launch parameters from Course Structure>",
   "masteryScore": "<mastery score from the Course Structure>",
   "passIsFinal" : <passIsFinal from the Course Structure>,
   "moveOn": "<moveOn value from the Course Structure>",
   "returnURL": "<URL value>",
   "entitlementKey": {
       "courseStructure": "<Entitlement data or key from Course Structure>",
       "alternate": "<alternateEntitlementKey>"
   }
 }
```

The properties for the LMSLaunchData document are described below.

<table>
  <tr>
    <th align="left">contextTemplate</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>Context template for the AU being launched.<br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU: Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS MUST include a contextTemplate and place the value for <strong><em>sessionId</em></strong> in the "http://purl.org/xap/adl/cmi5/results/extensions/session" element
of the context object's extension collection.<br />
      <strong>AU Usage: </strong>AU MUST get the contextTemplate value from the LMS.LaunchData state document.  The AU MUST use the contextTemplate as a template for the context property in all xAPI statements it records to the LMS. While the AU may include additional values in the context object of such statements, it MUST NOT overwrite any values provided in the contextTemplate. NOTE: this will include the sessionId specified by the LMS.<br />
      <strong>Data type: </strong>JSON context object as defined in xAPI 1.0<br />
      <strong>Value space:</strong> LMS implementation specific<br />
      <strong>Sample value:</strong></p></td>
  </tr>
  <tr>
    <th align="left">launchMode</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>The launch mode determined by the LMS. There are three possible values:<br />
      <ul><li>Normal<br/>Indicates to the AU that completion-related data MUST be recorded in the LMS using xAPI statements.</li>
          <li>Browse<br/>Indicates to the AU that completion-related data MUST NOT be recorded in the LMS using xAPI statements.  When "Browse" mode is used, the AU SHOULD provide a user experience that allows the user to "look around" without judgement.</li>
          <li>Review<br/>Indicates to the AU that completion-related data MUST NOT be recorded in the LMS using xAPI statements.  When "Review" mode is used, the AU SHOULD provide a user experience that allows the user to "revisit/review" already completed material.</li>
      </ul>
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS MUST include a value for <strong><em>launchMode</em></strong>.<br />
      <strong>AU Usage: </strong>The AU MUST conform to the following based on the value of <strong><em>launchMode</em></strong><br />
      <ul><li>Normal<br/>The AU MUST record Initialized and Terminated verb statements.  The AU MUST record other cmi5 verb statements per the requirements defined in section 9.3 - Verbs.</li>
      <li>Browse<br/>The The AU MUST record "Initialized" and "Terminated" verb statements.  The AU MUST NOT record other cmi5 verb statements.</li>
      <li>Review<br/>The The AU MUST record "Initialized" and "Terminated" verb statements.  The AU MUST NOT record other cmi5 verb statements.</li></ul>
      <strong>Data type: </strong>String<br />
      <strong>Value space: </strong>"Normal", "Browse" or "Review"<br />
      <strong>Sample value: </strong>"Normal"</p></td>
  </tr>
    <tr><th align="left">launchParameters</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>The launch parameters defined in the cmi5 Course Structure<br />
      <strong>LMS Required:</strong> If the <strong><em>launchParameters</em></strong> were defined by the AU developer in the Course Structure, the LMS MUST include the  <strong><em>launchParameters</em></strong> in the State API document.<br />
      <strong>AU Required:</strong> No<br />
      <strong>LMS Usage:</strong> The LMS MUST include the <strong><em>launchParameters</em></strong> in the State API document when defined in the Course Structure.<br />
      <strong>AU Usage:</strong> The AU SHOULD get the <strong><em>launchParameters</em></strong> value 
      from the State API document if the launch parameters were defined in the Course Structure.<br />
      <strong>Data type:</strong> Defined by the AU developer.<br />
      <strong>Value space:</strong> Defined by the AU developer.<br />
      <strong>Sample value: </strong> TBD.</p></td>
  </tr>
  <tr><th align="left">masteryScore</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>The MasteryScore from the cmi5 Course Structure.<br />
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>The LMS MUST include the MasteryScore value based on the value defined in the course structure for the AU being launched.<br />
      <strong>AU Usage: </strong>The AU MUST issue "Passed" or "Failed" statements based on the MasteryScore provided. (See Sections 9.3.6 and 9.3.7)<br />
      <strong>Data type: </strong>decimal<br />
      <strong>Value space: </strong>Decimal value between 0 and 1<br />
      <strong>Sample value: </strong>0.75</p></td>
  </tr>   
  </tr> 
  <tr><th align="left">passIsFinal</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>passIsFinal from the cmi5 Course Structure.<br />
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>The LMS MUST include the passIsFinal value based on the value defined in the Course Structure for the AU being launched.<br />
      <strong>AU Usage: </strong>If true, the AU MUST NOT issue a "Passed" or "Failed" statement after issuing a Passed statement. <br />
      <strong>Data type: </strong>boolean<br />
      <strong>Sample value: </strong>true</p></td>
  </tr>   
  </tr> 
  <tr><th align="left">moveOn</th>
    </tr>
    <tr>
    <tr>
    <td><p><strong>Description: </strong>The moveOn value from the cmi5 Course Structure.<br />
      <strong>LMS Required:</strong> Yes<br />
      <strong>AU Required:</strong> No<br />
      <strong>LMS Usage:  </strong>The LMS MUST include the moveOn value defined in the course structure for the AU.<br />
      <strong>AU Usage: </strong>The AU MAY get the moveOn value from the "LMS.LaunchData" state document and may use the value to modify its behavior.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>moveOn values as defined in the cmi5 Course Structure Specification (Section 7.1.4 - AU Metadata)<br />
      <strong>Sample value: </strong>"Passed"</p></td>
  </tr>   
    <th align="left">returnURL</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>Used by the LMS when launching the AU if the LMS requires the AU (in a web-browser environment) to redirect the learner when he or she exits the AU.<br />
      <strong>LMS Required:</strong> No<br />
      <strong>AU Required:</strong> If the <strong><em>returnURL</em></strong> is provided.<br />
      <strong>LMS Usage: </strong>The LMS may include the <strong><em>returnURL</em></strong> when the learner SHOULD be redirected to the <strong><em>returnURL</em></strong> on exiting the course.<br />
      <strong>AU Usage: </strong>The AU MUST get the <strong><em>returnURL</em></strong> value 
      from the LMSLaunchData state document. If the <strong><em>returnURL</em></strong> is provided, the AU MUST redirect the current browser window to the <strong><em>returnURL</em></strong> when the AU is terminated.<br />
      <strong>Data type: </strong>URL<br />
      <strong>Value space: </strong>Any URL<br />
      <strong>Sample value: </strong>http://www.example.com/lms/mod/xapilaunch/view.php?id=12</p></td>
  </tr>
  <tr>
    <th align="left">entitlementKey: courseStructure</th>
  </tr> 
      <td><p><strong>Description: </strong> Entitlement data or key from the Course Structure.  The       <strong>entitlementKey</strong> values may be used by the AU to determine if the launching LMS system is entitled to use the AU.<br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU Required: </strong>No<br />
      <strong>LMS Usage:  </strong>The LMS MUST obtain this from the Course Structure.<br />
      <strong>AU Usage: </strong> The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>The value is defined by the AU provider<br />
      <strong>Sample value: </strong>"xyz-123-9999"</p></td>
  </tr>
  <tr>
    <th align="left">entitlementKey: alternate</th>
  </tr> 
      <td><p><strong>Description: </strong> Entitlement data or key from some other source as agreed upon between the LMS and the AU.  The <strong>entitlementKey</strong> values may be used by the AU to determine if the launching LMS system is entitled to use the AU.<br />
      <strong>LMS Required: </strong>No<br />
      <strong>AU Required: </strong>No<br />
      <strong>LMS Usage:  </strong>The LMS MUST obtain the alternate entitlement key from a source as agreed upon with the AU.<br />
      <strong>AU Usage: </strong> The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>The value is defined by the AU provider.<br />
      <strong>Sample value: </strong>"xyz-123-9999"</p></td>
  </tr>     
   <tr>
    <th align="left">ContentSpecific</th>
  </tr> 
      <td><p><strong>Description: </strong>Launch parameters that are content specific.  The LMS MUST obtain this value from the Course Structure.<br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU Required: </strong>No<br />
      <strong>LMS Usage:  </strong>Static launch parameters defined by the course designer MUST be obtained by the LMS from the Course Structure.<br />
      <strong>AU Usage: </strong>Determined by the AU.<br />
      <strong>Data type: </strong>string<br />
      <strong>Value space: </strong>Values are defined by the AU provider.<br />
      <strong>Sample value: </strong>"abc-327-999"</p></td>
  </tr>      
</table>

__State API PUT Properties__:

* _activityId_: Activity ID for the AU (from the course structure)  
* _agent_: agent representing the LMS learner being enrolled.  This MUST match actor object
generated by LMS at AU launch time.  
* _registration_: Registration ID representing the LMS learner enrollment in the course.
This MUST match Registration ID used by the LMS at AU launch time.  
* _stateId_: LMS.LaunchData  



<a name="xapi_agent_profile"></a>   
#11.0 xAPI Agent Profile Data Model  

In cmi5, Learner Preferences are scoped to the learner.  Both the LMS and the AU may write changes to Learner Preferences in the xAPI Agent Profile.  The LMS/LRS may choose to ignore or override Learner Preference changes requested by the AU by returning a "403 Forbidden" response as defined in the xAPI specification (Section 7.6).  The AU MUST NOT treat the 403 response as an error condition.  

On startup, the AU MUST retrieve the Learner Preferences document from the Agent Profile.

When reading or writing to the Agent Profile, the document name MUST be CMI5LearnerPreferences and the format MUST be a JSON structure as shown below:

```javascript
{
	"languagePreference": "<values for languages>",
	"audioPreference": "<on or off>"
}
```
##11.1  languagePreference
The languagePreference MUST be a comma-separated list of RFC 5646 Language Tags as indicated in the xAPI specification (Section 5.2).  In the list, languages MUST be specified in order of user preference.  In the example below, the user's first preference for language is en-US.  The user's second preference for language is fr-FR and the third preference is fr-BE.

```javascript
{
	"languagePreference": "en-US,fr-FR,fr-BE",
	...
}
```

If the AU supports multiple languages, the AU SHOULD display in the language preference order of the user as in the example above. If the AU supported "zh-CN", "fr-BE and "fr-FR", it SHOULD display in "fr-FR".  If the AU does not support multiple languages, or if no languagePreference is specified in the Agent Profile, it may display in its default language.

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

<a name="bibliography"></a>   
#Bibliography

[1]  AICC CMI001, CMI Guidelines For Interoperability, Version 4.0

[2]  SCORM – <http://www.adlnet.gov/capabilities/scorm>

[3]  MIME Types – <http://www.iana.org/assignments/media-types/index.html>

[4]  RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998

[5]  Experience API, Version 1.0.1, ADL, 2012-2013 - <https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md>

[6]  cmi5-002 – LMS Course Structure, current working draft, AICC, 2013 -  
<https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_coursestructure.md>


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
