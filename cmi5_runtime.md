<img src="http://aicc.org/joomla/dev/images/aicc-logo.png"> CMI-5 Runtime Environment 
---

**AICC DOCUMENT NUMBER:** CMI5-001  &nbsp;&nbsp; **Revision:** CURRENT WORKING DRAFT   
**THIS DOCUMENT IS CONTROLLED BY:** AICC CMI Subcommittee


#***WORKING DRAFT - NOT FOR IMPLEMENTATION***


---

>Caveats...
>
>Copyright &copy; 2012-2013 AICC, All rights reserved
>
>The information contained in this document has been assembled by the AICC as an
informational resource. Neither the AICC nor any of its members assumes nor shall any of
them have any responsibility for any use by anyone for any purpose of this document or of
the data which it contains. All use of this document is subject to the terms of the
license agreement contained within it.

----


## Table of Contents

[__Revision History__](#revhistory)  

[__Contributors__](#contributors)   


[__1.0 Overview__](#overview)  
&nbsp;&nbsp;&nbsp;&nbsp;[1.1 Scope](#scope)  
&nbsp;&nbsp;&nbsp;&nbsp;[2.0 References](#references)  
[__3.0 Definitions__](#definitions)  
&nbsp;&nbsp;&nbsp;&nbsp;[3.1 Abbreviations and acronyms](#acronyms)  
[__4.0 Conformance__](#conformance)  
&nbsp;&nbsp;&nbsp;&nbsp;[4.1 Assignable Unit (AU)](#au_conformance)  
&nbsp;&nbsp;&nbsp;&nbsp;[4.2 Learning Management Systems (LMS)](#lms_conformance)  
[__5.0 Conceptual Model: Informative__](#concept)  
[__6.0 LMS Requirements__](#lms_requirements)  
&nbsp;&nbsp;&nbsp;&nbsp;[6.1 Course structures](#course_structures)  
&nbsp;&nbsp;&nbsp;&nbsp;[6.2 LMS State API Requirements](#lms_state_api_requirements)  
&nbsp;&nbsp;&nbsp;&nbsp;[6.3 LMS Statement API Requirements](#lms_statement_api_requirements)  
[__7.0 AU Requirements__](#au_requirements)  
&nbsp;&nbsp;&nbsp;&nbsp;[7.1 AU State API Requirements](#au_state_api_requirements)  
&nbsp;&nbsp;&nbsp;&nbsp;[7.2 AU Statement API Requirements](#au_statement_api_requirements)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[7.2.1 Placement of session_id in Statements](#placement)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[7.2.2 First Statement API Call](#first_statement_au)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[7.1.2 Last Statement Call](#last_statement_au)  
[__8.0 Content Launch Mechanisms__](#content_launch)  
&nbsp;&nbsp;&nbsp;&nbsp;[8.1 Web (Browser) Environment](#browser_environment)  
&nbsp;&nbsp;&nbsp;&nbsp;[8.3 Other Launch Environments](#other_environment)  
[__9.0 XAPI Data Model__](#xapi_data_model)  
&nbsp;&nbsp;&nbsp;&nbsp;[9.1 Verbs](#verbs)  
&nbsp;&nbsp;&nbsp;&nbsp;[9.2 Activity Types](#activity_types)  
&nbsp;&nbsp;&nbsp;&nbsp;[9.3 Extensions](#extensions)  
&nbsp;&nbsp;&nbsp;&nbsp;[9.4 Documents](#documents)  

[__10.0 Bibliography__](#bibliography) 

[__License Agreement__](#license_agreement)

------


<a name="revhistory"></a>	
## Revision History

__0.1 Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__  

Converted existing working draft to markdown format from Microsoft Word.

All previous work from 2012 discarded.


<a id="contributors"></a> 
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
</table> 

-------

<a id="overview"></a>  
#1.0 Overview


This specification describes interoperable runtime communication between Learning
Management Systems (LMS) and Learning Activities.

<a id="scope"></a>  
##1.1 Scope

The scope of this specification is limited to following:

* Launch by a Learning Management Systems (LMS) of Learning Activities.
* Launch and Runtime environment used for LMS and Learning Activities.
* Runtime communication data and data transport between LMS systems and Learning Activities 
* LMS course definition as it pertains to runtime data used by Learning Activities.  
* Reporting Requirements for LMS systems

This specification references how to use the XAPI specification within this scope.

Other uses of the XAPI specification are outside the scope.

Uses of Learning Activities and LMS systems not explicitly defined in this specification
are outside of the scope of this specification.


<a id="references"></a> 
#2.0  References

The following referenced documents are indispensable for the application of this
specification. 

RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998.

“Experience API”, curent working draft, ADL, 2012-2013  
<https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md>

CMI5-002  – LMS Course Structure, curent working draft, AICC, 2013  
<https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_coursestructure.md>



<a id="definitions"></a>   
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
sequence, representing a course. Experience API (XAPI): XAPI is a runtime data
communication specification for learning content (AU) to send and receive data to an LRS.
The XAPI specification is referenced by this document is used to define the data transport
and the data model. 

* __Learner__: The end user viewing/using the learning content (Learning Activity).

* __Learning Activity Provider (AP)__:  Learning Activity Provider (AP) as defined in the
XAPI specification.

* __Learning Management System (LMS)__: A computer system that may include the
capabilities to register learners, launch learning presentations, analyze and report
learner performance, and track learners progress. LMS launching, reporting, and tracking
roles are the focus of the CMI5 specification.  The LMS shall have an LRS as part of its
implementation.

* __Learning Records Store (LRS)__: As defined in the XAPI specification. In this 
specification, the LMS shall implement an LRS with additional requirements as specified in
this document.


<a id="acronyms"></a> 
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


<a id="conformance"></a>  
#4.0  Conformance

Conformance to this specification is defined in section. 

In this specification, “shall” is to be interpreted as a requirement on an implementation;
“shall not” is to be interpreted as a prohibition.

“Should” is to be interpreted as a recommendation for implementation; “should not” is to
be interpreted as the converse of “should”.

“May” is to be interpreted as a course of action that is permissible within the limits of
the specification; “need not” indicates a course of action that is not required.

Uses of XAPI specification outside the scope this specification do not affect conformance
with this specification.

<a id="au_conformance"></a> 
##4.1 Assignable Unit (AU)

An Assignable Unit shall conform to all requirements listed in Section 7 – AU Requirements

An Assignable Unit shall conform to all requirements as specified in the XAPI
specification (see References)

An Assignable Unit shall not implement any features or functionality (optional or
mandatory) described in this specification in a non-conforming manner.

<a id="lms_conformance"></a> 
##4.2 Learning Management Systems (LMS)

LMS systems shall conform to all requirements listed in Section 6 – LMS Requirements.

A LMS shall conform to all LRS requirements as specified in the XAPI specification
(see References)

The LMS shall not implement any features or functionality (optional or mandatory)
described in this specification in a non-conforming manner.


<a id="concept"></a> 
#5.0 Conceptual Model: Informative  

Synopsis of the CMI-5 model:

* An LMS imports a course structure.
* An LMS administrative user assigns a course to a learner.
* A learner authenticates with an LMS or related system.
* A learner launches an Assignable Unit (learning content) from the LMS or associated
launching system.
* The learning activity sends a message to the LMS requesting launch parameters and recovers
previous state information from the LRS.
* Learner views the learning activity content and performs the learning. During this time
the learning activity may request and store data.
* The learner exits the learning activity.
* The learning activity reports final tracking data to the LMS and issues an exit message.
* Administrative users create and view reports of tracking data recorded by learning
activities for individual learners.

Responsibilities of the Assignable Unit:

* Parse the parameters from the launching environment to determine where the LMS location
is and initiate communication with the LMS.
* Acting as “client”, send and receive messages using the defined transport mechanism(s)
and associate commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Send an “exit” message prior to terminating the learning activity’s execution.

Responsibilities of the LMS:

* Create and maintain course structures
* Acting as a “server”, receive and reply to messages using the defined transport
mechanism(s) and associate commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Launch the specified learning activity contained in courses, in the defined environment(s).

<a id="lms_requirements"></a>  
#6.0 LMS Requirements

LMS systems shall meet the following requirements to conform to this specification:  

1. The LMS shall implement a LRS as defined in the XAPI Specification.  
2. The LMS shall implement a means to create and edit course structures as defined in
section 6.1 Course structures.  
3. The LMS shall implement additional “State API” requirements to initialize AU state as
defined in section 6.2 LMS State API Requirements.  
4. The LMS shall implement the runtime launch interface as defined in section 8.0 Content
Launch Mechanisms.  
5. The LMS may implement collateral credit features (to preemptively set status) per
section ______.  
6. The LMS shall implement the XAPI “Verb” vocabulary as defined in section 9.1 Verbs.
7. The LMS shall implement the XAPI “Activity Type” vocabulary as defined in section 9.2 Activity Types.  
8. The LMS shall implement additional XAPI “Statement API” requirements as defined in
section __________ .  
9. The LMS shall implement additional XAPI “Agent Profile API” requirements as defined in
section __________ .  
10. The LMS shall implement additional XAPI “Activity Profile API” requirements as defined
in section __________ .  


<a id="course_structures"></a>  
##6.1 Course structures
The LMS shall implement a means to create and maintain course structures.

The LMS shall implement the creation and editing of course structures by one of the
following methods:

1. Implementing the import of CMI-5 course structure data defined in CMI5-xxx
2. Provide a user interface to LMS administrative users to create and edit course
structures.

The LMS should implement both of the above methods.

Course structures shall contain the following data for each AU in a course:

* URL location – A URL to the AU’s location (entry point)
* Activity ID – the AU’s activity ID as defined in the XAPI specification (determined by the AU designer).
* Launch Method - 
    * “New Window” – The LMS shall spawn a new window for the AU launched.
    * “Existing Window” – The LMS shall re-direct the existing browser window for the AU
    launched.
* Authentication Method – The authentication method used by the AU to access the LMS’s
LRS.  (Either HTTP basic or OAuth 1.0)
* Launch Parameters –A set of static data specific to the AU’s design. Used as parameters
by the AU to modify its behavior. 
* Entitlement Key – This is a value provided by the AU content provider and is used by the
AU to determine whether the LMS instance and/or Learner are entitled to view the content.
It is provided to the AU via a State API request.

Course Structures shall contain at least 1 AU.

LMS shall have the ability to create and maintain course structures containing more than
1000 AU’s.

<a id="lms_state_api_requirements"></a>  
##6.2 LMS State API Requirements
The LMS shall initialize the records in its LRS with the state documents as described in
this section when a learner is enrolled in a course (before the learner initially accesses
the course).  The state documents are specific to the learner and course registration.  

####_LMS Launch Data_ 
__Description__: Launch parameter data from course structure for the AU  

__Usage__: Static.  The LMS shall only create one State document for this combination of
activityid, agent, registration, and stated.  

__State Document Format__: Application/JSON  

__State Document Content__: The properties for the LMS.LaunchData document are described
below.

<table>
  <tr>
    <th align="left">context</th>
  </tr> 
<tr>
    <td><p><strong>Description: </strong>Context template for the
    AU being launched.<strong></strong><br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU: Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS shall include a context template and place the value
for <strong><em>session_id</em></strong> in the extension "http://www.aicc.org/cmi-5/extensions/session"
in the context object's extension collection, based on the definition of the AU in the course
structure.<br />
      <strong>AU Usage: </strong>AU shall get the <strong><em>context</em></strong> value 
      from the LMS.LaunchData state document. AU shall use the <strong><em>context</em></strong>
      object as a template context object in all statements it records to the LMS,
      and may include additional values in the context objects of such statements,
      but shall not overwrite any values provided in the context template. NOTE:
      this will include the session_id specified by the LMS.<br />
      <strong>Data type: </strong>JSON context object as defined in xApi 1.0<br />
      <strong>Value space:</strong> LMS implementation specific<br />
      <strong>Sample value:</strong></p></td>
  </tr>
</table>

__State API PUT Properties__:

* _activityid_: Activity ID for the AU (from the course structure)  
* _agent_: agent representing the LMS learner being enrolled.  Shall match actor object
generated by LMS at AU launch time.  
* _registration_: Registration ID representing the LMS learner enrollment in the course.
Shall match Registration ID used by the LMS at AU launch time.  
* _stateid_: LMS.LaunchData  

####_LMS Entitlement Data_  
__Description__: Launch parameter data from course structure for the AU  
__Usage__: Static. The LMS shall only create one State document for this combination of
activityid, agent, registration, and stated

__State Document Format__: Application/JSON  

__State Document Content__: Entitlement data specific to the AU from the course structure.  

__State API PUT Properties__:  

* _activityid_: Activity ID for the AU (from the course structure)  
* _agent_: agent representing the LMS learner being enrolled.  Shall match actor object
generated by LMS at AU launch time.  
* _registration_: Registration ID representing the LMS learner enrollment in the course.
Shall match Registration ID used by the LMS at AU launch time.  
* _stateid_: LMS.EntitlementData  

<BR>
<BR>

<a id="lms_statement_api_requirements"></a>  
##6.3 LMS Statement API Requirements

Prior to launching a learning activity, the LMS shall create a Statement API record in its
LRS to …..

Set Collateral Credit  


<a id="au_requirements"></a>  
#7.0 AU Requirements

AU’s shall meet the following requirements to conform to this specification:

1. The AU shall implement the runtime launch interface as defined in Section 8 Content
Launch Mechanisms.
2. The AU shall implement runtime communication defined in the XAPI Specification
3. The AU shall implement the XAPI “Verb” vocabulary as defined in section __________ .
4. The AU shall implement additional XAPI “Statement API” requirements as defined in
section __________ .
5. The AU shall implement additional XAPI “Agent Profile API” requirements as defined in
section __________ .
6. The AU shall implement additional XAPI “Activity Profile API” requirements as defined
in section __________ .

<a id="au_state_api_requirements"></a> 
##7.1 AU State API Requirements

The AU should retrieve the following the State API documents from the LRS recorded by the
LMS at assignment time.  (See Section 6.1).  
The AU should retrieve these State API documents immediately after launch and prior to
issuing any (State API) PUT statements.  
If the AU requests these State API documents, it shall be done in the following manner:  

AU issues State API GET Command with the following parameters:  

* activityid: Activity ID for the AU (from the course structure)
* agent: agent representing the LMS learner.  Shall match actor object generated by LMS at
AU launch time.
* registration: Registration ID representing the LMS learner enrollment in the course.
Shall match Registration ID used by the LMS at AU launch time.



<a id="au_statement_api_requirements"></a>  
##7.2 AU Statement API Requirements

<a id="placement"></a> 
###7.2.1 Placement of session_id in Statements

The AU shall retrieve the value of session\_id at launch time as specified in Section 8
Content Launch Mechanisms.  The AU shall place the value of the session_id in the context
extensions for all XAPI statements it records.  

Usage in an XAPI Statement:

```javascript
"extensions": {
       “session_id”: <session_id value>
     }
```
Example:
```javascript
"extensions": {
       “session_id”: ”xyz123”
     }
```

<a id="first_statement_au"></a> 
###7.2.2 First Statement API Call

The AU should issue a statement to the LRS after being launched, initialized, and ready
for learner interaction.  If used, the statement shall contain the following:
      Verb:  “Started”
      Actor: <as defined in section 8>
      Object: __________________

If used, the above statement shall be the first Statement API call made by the AU. The
verb “Started” shall only be used in this manner by the AU. 
Example Statement:

```javascript
    {
        "id": "12345678-1234-5678-1234-567812345678",
        "actor":{
	        "mbox":"mailto:userinlms@aicc.org"
	    },
	    "verb":{
	        "id":"http://www.aicc.org/cmi5/verbs/started"
        },
        "object":{
            "id":"http://example.aic.org/activities/quizzes/quiz7"
	    }
    }
```
<a id="last_statement_au"></a>  
###7.1.2 Last Statement Call

The AU shall issue a statement to the LRS after being launched, initialized, and ready for
learner interaction that contains the following:
      Verb:  “Exited”
      Actor: <as defined in section 8>
      Object: ___________________
This shall be the last Statement API call made by the AU prior to it exiting the launch
session. The AU shall not record any other statements prior to exiting.

Example Statement:

```javascript
     {
     }
```
<a id="content_launch"></a>  
#8.0 Content Launch Mechanisms

<a id="browser_environment"></a>  
##8.1 Web (Browser) Environment

###8.1.1 Launch Method

The AU shall be launched by the LMS by one of the following methods:

1. Spawning a new browser window to the URL  
2. Re-directing the existing browser window (or section of the existing window) to the URL  

The Launch method used by the LMS shall be determined by the “Launch Method” defined in
the LMS’s course structure for the AU being launched. (See ______) URL Launch Line

The AU shall be launched by the LMS with a URL having (query string) launch parameters as
defined in this section.

The launch parameters shall be name/value pairs in a query string appended to the URL that
launches the learning activity.

If the learning activity’s URL requires a query string for other purposes, then the names
shall not collide with named parameters defined below.

The order of the name/value pairs is not significant. AU’s shall have the ability to
process them in any order.

Each value for the associated names shall be URL-encoded. 

The format of the launching URL is as follows:  

```
<URL to AU>
?endpoint=<URL to LMS Listener>
&auth=<Authorization Token (optional)– if OAuth is not used>
&actor=<Actor Object>
&registration=<Registration ID>
&activity_id=<AU activity ID>
```

Example:

```
http://la.cmi5.aicc.org/LA1/Start.html
?endpoint=http://cmi-5-lms-system.org/lrslistner/
&auth=OjFjMGY4NTYxNzUwOGI4YWY0NjFkNzU5MWUxMzE1ZGQ1
&actor={ "name" : ["Skip Winger"], "mbox" : ["mailto:skipper@skyhiair.com"] }
&registration=760e3480-ba55-4991-94b0-01820dbd23a2
&activity_id=http://example.AU-content.com/example/001/statement
```

The values for the URL launch parameters are described below: 


<table border="1" cellspacing="0" cellpadding="0" width="100%">
  <tr >
    <td width="100%" valign="top"><h3>endpoint</h3></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><p><strong>Description: </strong>A    URL to the LMS listener location for XAPI messages to be sent to.  <strong></strong><br />
      <strong>LMS Usage:  </strong>LMS shall place the <strong><em>endpoint </em></strong>in the query    string.<strong></strong>The LMS should limit the use of the <strong><em>auth </em></strong>value for the duration    of a specific/user/learning activity/registration   <br />
      <strong>AU Usage: </strong>AU shall    get the <strong><em>endpoint </em></strong>value from the query string. AU shall use the <strong><em>endpoint </em></strong>value as the URL to send XAPI messages to.<strong></strong><br />
      <strong>Data type: </strong>String    (URL-encoded)<br />
      <strong>Value space:</strong> An    URL-encoded URL<br />
      <strong>Sample value: </strong>https://aicc.org/MyCMI5_listener.pl<strong></strong></p></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><h3>auth</h3></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><p><strong>Description: </strong>An    authentication token created &amp; managed by the LMS.  Used when OAuth authentication is not    practical or desired.  The    authentication token is used by the learning activity being launched.<strong></strong><br />
      <strong>LMS Usage:  </strong>LMS shall place the <strong><em>auth </em></strong>in the query    string when “standard authentication” is indicated in the course structure    definition. If OAuth is the method of authentication specified, the LMS shall    NOT place the <strong><em>auth </em></strong>name/value pair<strong></strong>in the query string.  The LMS should limit the use of the <strong><em>auth </em></strong>value for the duration of a specific/user/learning activity/registration   <br />
      <strong>LA Usage: </strong>AU shall    get the <strong><em>auth</em></strong> value from the query string. AU shall place the <em>auth </em>value in the Authorization headers of all HTTP    messages made to the endpoint using the XAPI.<strong> </strong><br />
      <strong>Data type: </strong>String    (based-64 encoded)<br />
      <strong>Value space:</strong> <br />
      <strong>Sample value:</strong> OjFjMGY4NTYxNzUwOGI4YWY0NjFkNzU5MWUxMzE1ZGQ1<strong></strong></p></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><h3>actor</h3></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><p><strong>Description: </strong>A    JSON object called “actor” (as defined in the XAPI specification) that    identifies the learner launching the learning activity so the learning    activity will be able to include it in XAPI messages.<strong></strong><br />
      <strong>LMS Usage:  </strong>The LMS shall place the value for <strong><em>actor </em></strong>in the query string based on the authenticated learner’s identity. The    LMS should create an actor object specific to the LMS instance that does NOT    include sensitive PII of the learner.<strong></strong><br />
      <strong>AU Usage: </strong>AU    shall get the <strong><em>actor </em></strong>value from the query string. AU shall use the <strong><em>actor </em></strong>value in API calls that require an “actor” object when sending XAPI    messages<strong></strong><br />
      <strong>Data type: </strong>String    (URL-encoded)<br />
      <strong>Value space:</strong> A    JSON Actor object (as defined in the XAPI specification)<br />
      <strong>Sample value: </strong>{    &quot;name&quot; : [&quot;Skip Winger&quot;], &quot;mbox&quot; :    [&quot;mailto:skipper@skyhiair.com&quot;] }<strong></strong></p></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><h3>registration</h3></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><p><strong>Description: </strong>A    Registration ID corresponding to the learner’s enrollment for the AU being    launched.<strong></strong><br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU: Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS shall place the value for <strong><em>registration</em></strong> in the query string based on the authenticated learner’s corresponding    enrollment for the Course that the AU being launched is a member of.<strong>  </strong><br />
      <strong>AU Usage: </strong>AU    shall get the <strong><em>registration</em></strong> value from the query string. AU shall use the <strong><em>registration</em></strong> value in API calls that require an “registration id” when sending XAPI    messages<strong></strong><br />
      <strong>Data type: </strong>String    (URL-encoded)<br />
      <strong>Value space:</strong> UUID (as defined in the XAPI specification)<br />
      <strong>Sample value:</strong></p></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><h3>activity_id</h3></td>
  </tr>
  <tr>
    <td width="100%" valign="top"><p><strong>Description: </strong>The    Activity ID of the AU being launched.<strong></strong><br />
      <strong>LMS Required: </strong>Yes<br />
      <strong>AU: Required:</strong> Yes<br />
      <strong>LMS Usage:  </strong>LMS shall place the value for <strong><em>activity_id</em></strong> in the query string based on the definition of the AU in the course    structure.<strong>  </strong><br />
      <strong>AU Usage: </strong>AU    shall get the <strong><em>activity_id</em></strong> value from the query string. AU shall use the <strong><em>activity_id</em></strong> value in API calls that require an “activity id” when sending XAPI messages.<strong></strong><br />
      <strong>Data type: </strong>String    (URL-encoded)<br />
      <strong>Value space:</strong> UUID (as defined in the XAPI specification)<br />
      <strong>Sample value:</strong></p></td>
  </tr>
</table>
<BR>
<BR>

<a id="other_environment"></a>  
##8.3 Other Launch Environments

Other launch environments are not currently implemented in this specification. The
following launch environments are being considered for future releases:  

* Windows/XP/7/8 pro  
* Windows RT  
* Mac OS X  
* Linux  
* Android  
* iOS  

CMI-5 implementations for LMS’s and AU’s in these other environments will use the same
REST communication interface as specified in XAPI specification.  The XAPI specification
does not specify launch mechanisms.

<a name="xapi_data_model"/>  
#9.0 XAPI Data Model  

<a id="verbs" ></a> 
##9.1 Verbs  

The following are XAPI verbs that are specific to this specification.

AU’s shall use the below verbs indicated as mandatory in other sections of this
specification.

AU’s may use additional verbs not listed in this specification.

LMS system shall record and provide reporting for all statements regardless of which verbs
AU’s use in statement.  

###9.1.1 Launched
<table>
<tr><th align="left">Verb</th><td>Launched</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/launched</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Launched" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Launched" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Launched” indicates that the AU was launched by the LMS.</td>
</tr><tr><th align="left">AU Obligations</th><td>None</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS shall use this verb in a statement recorded in the LRS before launching an AU.  See Statement API _____ </td></tr>
</tr><tr><th align="left">Usage</th><td>A "Launched" statement is used to indicate the that the LMS has launched the AU. It should be used in combination with the "Started" statment sent by the AU in a reasonable period of time to determine whether the AU was successfully launched. </td></tr>
</table>

###9.1.2 Started
<table>
<tr><th align="left">Verb</th><td>Started</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/started</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Started" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Started" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Started” indicates that the AU was launched by the LMS.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU must use "Started" in the first statement in the AU session.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>Verify that this verb is recorded by AU immediately after launch</td></tr>
</tr><tr><th align="left">Usage</th><td>A "Started" statement is used by the AU to indicate that it has been successfully started and should follow the "Launched" statement created by the LMS within a reasonable period of time.</td></tr>
</table>

###9.1.3 Suspended
<table>
<tr><th align="left">Verb</th><td>Suspended</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/suspended</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Suspended" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Suspended" }</td></tr>
<tr><th align="left">Description</th><td>The learner exited an AU session (uncompleted) with the intention of returning to the AU.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU shall record a statement containing the "Suspended" verb when the learner exits an AU without experiencing all relevant material in the AU.  The AU shall not issue a "Suspended" statement if the AU previously issued a statement with "Completed". The AU shall not issue any other statements following "Suspend" except for "Exit".</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>The criterion for "Suspended" is determined by the AU design.</td></tr>
</table>

###9.1.4 Resumed 
<table>
<tr><th align="left">Verb</th><td>Resumed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/resumed</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Resumed" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Resumed" }</td></tr>
<tr><th align="left">Description</th><td>The learner resumed an AU that was intentionally left uncompleted.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU shall record a statement containing the "Resumed" verb when the learner returns to an AU that had recorded a "Suspend" statement in the previous session.  The AU shall record "Resumed" immediately following a the "Started" statement. The AU shall not issue a "Resumed" statement under any other circumstances.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>See Obligations.</td></tr>
</table>


###9.1.5 Completed
<table>
<tr><th align="left">Verb</th><td>Completed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/completed</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Completed" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Completed" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Completed” indicates the learner viewed or did all of the relevant activities in an AU presentation.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU shall record a statement containing the "Completed" verb when the learner has experienced all relevant material in an the AU.  The AU shall not issue multiple statements with "Completed" for the same AU within a given AU session or course registration for a given learner.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">Usage</th><td>The criterion for "Completed" is determined by the AU design.</td></tr>
</table>

###9.1.6 Passed
<table>
<tr><th align="left">Verb</th><td>Passed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/passed</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Passed" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Passed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and succeed in a judged activity in the AU. </td>
</tr><tr><th align="left">AU Obligations</th><td>The AU shall record a statement containing the "Passed" verb when the learner has attempted and  AU.  The AU shall not issue multiple statements with "Passed" for the same AU within a given AU session or course registration for a given learner. If the "Passed" statement contains a score, the score must equal to or greater than the "Mastery_Score" indicated in the course structure.  See section _____. </td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS shall record "Mastery_Score" data in the state API (if present in the course structure) for the AU prior to initial AU launch.  See section _____.  
<BR>
<BR>
The LMS shall use either "Passed" or "Completed" statements (or both) for determining for course completion (or course collateral credit) criteria for the AU.  See Section_____. </td></tr>
</tr><tr><th align="left">Usage</th><td>The AU shall record a statement containing the "Passed" verb when the learner has attempted and successfully passed the judged activity. The AU shall not issue multiple statements with "Passed" for the same AU within a given AU session or course registration for a given learner. If the "Passed" statement contains a score, the score must equal to or greater than the "Mastery_Score" indicated in the course structure. See section _____. </td></tr>
</table>


###9.1.7 Failed
<table>
<tr><th align="left">Verb</th><td>Failed</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/failed</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Failed" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Failed" }</td></tr>
<tr><th align="left">Description</th><td>The learner attempted and failed in a judged activity in the AU. </td>
</tr><tr><th align="left">AU Obligations</th><td>The AU shall record a statement containing the "Failed" verb when the learner has attempted and  AU.  If the "Failed" statement contains a score, the score must be less than the "Mastery_Score" indicated in the course structure.  See section _____. </td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS shall record "Mastery_Score" data in the state API (if present in the course structure) for the AU prior to initial AU launch.  See section _____.<BR>
<BR>
The LMS shall use either "Passed" or "Completed" statements (or both) for determining for course completion (or course collateral credit) criteria for the AU.  See Section_____.</td></tr>
</tr><tr><th align="left">Usage</th><td>The AU shall record a statement containing the "Failed" verb when the learner has attempted and failed the judged activity.. If the "Failed" statement contains a score, the score must be less than the "Mastery_Score" indicated in the course structure. See section _____. </td></tr>
</table>




###9.1.8 Abandoned
<table>
<tr><th align="left">Verb</th><td>Abandoned</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/abandoned</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Abandoned" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Abandoned" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Abandoned” indicates that the AU session was abnormally exited by Learner action (or due to a system failure).</td>
</tr><tr><th align="left">AU Obligations</th><td>None.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS shall use the the "Exit" statement to determine that the AU session has ended.  In the absence of an "Exit" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS must record a "Abandoned" statement on behalf of the AU indicating an abnormal session termination per section ______. </td></tr>
</tr><tr><th align="left">Usage</th><td>See obligations.</td></tr>
</table>



###9.1.9 Waived
<table>
<tr><th align="left">Verb</th><td>Waived</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/waived</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Waived" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Received Waiver" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Waived” indicates that the LMS has determined that the AU was met by means other than completing the AU.</td>
</tr><tr><th align="left">AU Obligations</th><td>None</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS shall use this verb in a statement recorded in the LRS when it determines that the AU may be waived.  A statement containing a Waived verb shall include a "reason" in the extension property of the statement Result.  (see section 9.3.2) </td></tr>
</tr><tr><th align="left">Usage</th><td>A "Waived" statement is used by the LMS to indicate that the AU may be skipped by the Learner.</td></tr>
</table>



###9.1.10 Exited
<table>
<tr><th align="left">Verb</th><td>Exited</td></tr>
<tr><th align="left">ID</th><td>http://www.aicc.org/cmi5/verbs/exited</td></tr>
<tr><th align="left">Name</th><td>{ "en-US" : "Exited" }</td></tr>
<tr><th align="left">Display</th><td>{ "en-US" : "Exited" }</td></tr>
<tr><th align="left">Description</th><td>The verb “Exited” indicates that the AU was exited by the Learner and that the AU will
not be recording any more statements for the launch session.</td>
</tr><tr><th align="left">AU Obligations</th><td>The AU shall record a statement containing the "Exit" verb. This statement shall be the last statement recorded by the AU in a session.</td></tr>
</tr><tr><th align="left">LMS Obligations</th><td>The LMS shall use the the "Exit" statement to determine that the AU session has ended.  In the absence of an "Exit" statement the LMS will make the determination if an AU abnormally terminated a session by monitoring new statement or state API calls made for the same leaner/course registration for a different AU.  The LMS must record a "Abandoned" statement on behalf of the AU indicating an abnormal session termination per section ______.</td></tr>
</tr><tr><th align="left">Usage</th><td>See obligations.</td></tr>
</table>
<BR/>
<BR/>
<a name="activity_types"></a>
##9.2 Activity Types

<a name="extensions"></a> 
##9.3 Extensions

###9.3.1 Progress
__ID__ http://www.aicc.org/cmi5/extensions/result/progress
 * An extension to the statement result.
 * The completion of the AU as a percentage.
 * This is an optional extension.
 * Contains an integer between 0 and 100. 
  
 
###9.3.2 Reason
__ID__ http://www.aicc.org/cmi5/extensions/result/reason
 * An extension to the statement result for statements that contain the Waived verb.
 * This extension indicates the reason that the AU was waived.
 * This is a required extension for statements that include the Waived verb.
 * The value of reason should be one of the following - 
    * “Tested Out” – An Assessment was completed by the student to waive the AU.
    * "Equivalent AU" - The student successfully completed an equivalent AU (in the same course) to waive the AU.
    * “Equivalent Outside Activity” – The student successfully completed an equivalent activity outside of the course to waive the AU.
    * "Administrative" – The LMS administrative user marked the AU complete.
	    
 
 
<a name="documents"></a>
##9.4 Documents 


<a id="bibliography"></a>   
#10.0 Bibliography

[1]  AICC CMI001, CMI Guidelines For Interoperability, Version 4.0. 

[2]  SCORM – <http://www.adlnet.gov/capabilities/scorm>

[3]  MIME Types – <http://www.iana.org/assignments/media-types/index.html>

-------

<a id="license_agreement"></a> 
#License Agreement

THE WORK (AS DEFINED HEREIN) ACCOMPANYING THIS LICENSE AGREEMENT ("AGREEMENT") IS PROVIDED
BY THE AICC, A NON-PROFIT CORPORATION ORGANIZED UNDER THE LAWS OF Idaho (“LICENSOR”), TO
YOU (“YOU” OR “LICENSEE”) ONLY UNDER THE TERMS AND CONDITIONS OF THIS AGREEMENT. ANY USE,
REPRODUCTION, DISTRIBUTION OR MODIFICATION OF THE WORK BY YOU CONSTITUTES YOUR ACCEPTANCE
OF THIS AGREEMENT. BY OBTAINING, USING, DISTRIBUTING, REPRODUCING AND/OR MODIFYING THE
WORK, YOU AGREE THAT YOU HAVE READ, UNDERSTOOD, AND WILL COMPLY WITH THE FOLLOWING TERMS
AND CONDITIONS.

####1. DEFINITIONS

“Affiliate” means any entity that directly or indirectly controls, is controlled by, or is
under common control with, another entity, so long as such control exists. For purposes of
this definition, with respect to a business entity, “control” means a majority vote of
voting members.  In the event that such control ceases to exist, any grant of rights or
other contractual powers granted to such Affiliate hereunder will be immediately
withdrawn, and this Agreement as between Licensor and such Affiliate shall be terminated
as set forth in Section 9, below.

“Compliance Test Suite” means any suite of computer programs (e.g., test tools), database
schema, plans, procedures, checklists, documentation and the like developed or adopted by
or for AICC and approved by AICC for the purpose of determining the compliance of an
implementation of a Specification.

“Contribution” means a submission by Licensee or Other Licensee to Licensor in writing
(including a writing in electronic medium) of a change, modification or addition to the
Work for inclusion in future versions of the Work; and which such submission is accepted
for inclusion in the Work by Licensor. Contributions do not include additions to the Work
that: (i) are separate works distributed in conjunction with the Work under their own
license agreement, and (ii) are not Derivative Works of the Work.

“Contributor” means any Licensee or any Other Licensee person or entity that submits a
Contribution.

“Derivative Work” is as defined in the United States Copyright Act 17 U.S.C. § 101, and
means any document, standard, specification, computer program, compilation, technical
data, schema, XML instance document or similar work that includes or derives from major
elements of the Work, whereby such major elements are protected by copyright, patent or
any other recognized intellectual property right.

“AICC” means the Aviation Industry Computer Based Training Committee Corporation, a
non-profit corporation organized under the laws of Idaho.

“Licensee” means you as a party to this Agreement to include all your Affiliates.

“Necessary Claims” means those claims of all patents and patent applications throughout
the world, other than design patents and design registrations, whereby such claims are
necessarily infringed by an implementation of a Work and which are within the bounds of
the Scope, where such infringement could not have been avoided by another commercially
feasible non-infringing implementation of such Work. Necessary Claims do not include any
claims (i) other than those set forth above even if contained in the same patent as
Necessary Claims or (ii) that read solely on an optional implementation example or
optional reference implementation.

“Other Licensee” or “Other Licensees” means a third party licensee (or licensees) other
than you, whereby such third party licensee has separately entered into this Agreement
with Licensor, to include all Affiliates of such third party licensee.

“Scope” means the software interfaces disclosed with particularity in a Specification
where the sole purpose of such disclosure is to enable products to interoperate,
interconnect or communicate as defined within a Specification. Notwithstanding the
foregoing, the Scope shall not include (i) any enabling technologies that may be necessary
to make or use any product or portion thereof that complies with a Specification, but are
not themselves expressly set forth in a Specification (e.g., compiler technology, object
oriented technology, basic operating system technology); (ii) the implementation of other
published specifications not developed by or for AICC, but referred to in the body of a
Specification; or (iii) any portions of any product and any combinations thereof the
purpose or function of which is not required for compliance with a Specification.

“Specification” means a document entitled “Specification” or “Standard” adopted and
approved for release by AICC relating to any AICC implementation, and any updates or
revisions adopted and approved for release.

“Standards Organization” means any entity whose primary activities are developing,
coordinating, promulgating, revising, amending, reissuing, interpreting, or otherwise
maintaining standards that address the interests of a wide base of users or consumers of
such standards outside the standards development organization.

“Technical Note” means a proposal, document or guide, other than a Specification, which
has been approved for release as a AICC Technical Note. Typically, a Technical Note will
contain functional and technical information to aid in the implementation of a
Specification as adopted and approved for release by AICC.

“Work” means any Specification, Technical Note or Compliance Test Suite distributed in
accordance with and licensed under this Agreement.

####2. LICENSE GRANT AND RESTRICTIONS

a. Subject to the terms of this Agreement, Licensor hereby grants to Licensee a
non-exclusive, worldwide, royalty-free license in any copyrights and/or Necessary Claims
in the Work such that Licensee may view, use, reproduce, publicly display, distribute and
prepare Derivative Works of the Work. 

b. Licensee hereby grants to Licensor and all Other Licensees a non-exclusive, worldwide,
royalty- free license in any copyrights and/or Necessary Claims in which Licensee asserts
ownership, such that Licensor and all Other Licensees may view, use, reproduce, publicly
display, distribute and prepare Derivative Works of any Contributions that Licensee may
have made to the Work. Licensee agrees that it will not transfer its ownership of any
copyrights or patents having Necessary Claims for the purpose of circumventing this
Section 2.b. Licensee shall not attempt under its copyrights, Necessary Claims or
otherwise to restrict any Other Licensee from exercising that Other Licensee’s rights
granted to it by Licensor under an agreement with essentially the same terms and
conditions as this Agreement. 

c. To the extent that a Licensee reproduces or distributes copies of the Work, portions
thereof or any Derivative Work in any medium, with or without modifications, such Licensee
shall give a copy of this Agreement to any recipients of the Work. 

d. Licensee hereunder expressly agrees to include the following notice on ALL copies of
the Work, portions thereof or Derivative Works: "Copyright © The AICC. All Rights
Reserved.  <http://www.aicc.org>” 

e. Licensee agrees to include the following notice in all Derivative Works:
“This product implements and complies with the Version CMI-5 [or other version as
applicable] AICC Specifications as published by the AICC at <http://www.aicc.org>”. 

f. Licensee may not facilitate or assist any Learning Technology Standards Organization
other than Licensor in co-opting, copying, distributing, publishing or using the Work
without prior written approval of Licensor. Licensee may not create any Derivative Work
for ownership by, presentation by, distributing by, publishing by or attribution to any
Standards Organization or similar entity other than Licensor, unless specifically approved
in writing by Licensor. 


####3. GRANT OF RIGHTS BY CONTRIBUTORS
Subject to the terms of this Agreement, a Contributor hereby grants to Licensor a
non-exclusive, worldwide, royalty-free license under all intellectual property rights to
make, use, sell, offer to sell, import and otherwise transfer any Contribution of such
Contributor. This license shall apply to the combination of the Contribution and the Work.

####4. TRADEMARKS
This Agreement does not grant permission to use the trade names, trademarks, service
marks, or product names of the Licensor, except as required for reasonable and customary
use in describing the origin of the Work and reproducing the content of the copyright
notice.

####5. WARRANTY
THE WORK ACCOMPANYING THIS AGREEMENT IS PROVIDED "AS IS" WITHOUT WARRANTIES OR CONDITIONS
OF ANY KIND, AND THE HOLDERS OF ANY COPYRIGHT, PATENT OR OTHER INTELLECTUAL PROPERTY RIGHT
THEREIN MAKE NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT
LIMITED TO, WARRANTIES OF MERCHANTABILITY OR FITNESS FOR ANY PARTICULAR PURPOSE OR THAT
THE USE OF THE SOFTWARE OR DOCUMENTATION WILL NOT INFRINGE ANY THIRD PARTY PATENTS,
COPYRIGHTS, TRADEMARKS OR OTHER RIGHTS. You are solely responsible for determining the
appropriateness of using or redistributing the Work and assume any risks associated with
your exercise of permissions under this Agreement.

####6. LIMITATION OF LIABILITY
IN NO EVENT AND UNDER NO LEGAL THEORY, WHETHER IN TORT (INCLUDING NEGLIGENCE), CONTRACT,
OR OTHERWISE, UNLESS REQUIRED BY APPLICABLE LAW (SUCH AS DELIBERATE AND GROSSLY NEGLIGENT
ACTS) OR AGREED TO IN WRITING, SHALL LICENSOR OR ANY CONTRIBUTOR BE LIABLE TO YOU FOR ANY
DAMAGES WHATSOEVER, INCLUDING ANY DIRECT, INDIRECT, EXEMPLARY, PUNITIVE, SPECIAL,
INCIDENTAL, OR CONSEQUENTIAL DAMAGES OF ANY CHARACTER ARISING AS A RESULT OF THIS
AGREEMENT OR OUT OF THE USE OR INABILITY TO USE THE WORK (INCLUDING BUT NOT LIMITED TO
DAMAGES FOR LOSS OF PROFITS, GOODWILL, WORK STOPPAGE, COMPUTER FAILURE OR MALFUNCTION, OR
ANY AND ALL OTHER COMMERCIAL DAMAGES OR LOSSES), EVEN IF LICENSOR OR SUCH CONTRIBUTOR HAS
BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

####7. COMMERCIAL DISTRIBUTION
If you include the Work or any Derivative Work in a commercial product offering, you
hereby agree to defend and indemnify Licensor and every Contributor (the "Indemnitees ")
against any losses, damages and costs (collectively "Losses") arising from claims,
lawsuits and other legal actions brought by a third party against the Indemnitees, to the
extent caused by your acts or omissions in connection with your distribution of the Work
in a commercial product offering. Indemnitees shall: a) promptly notify you in writing of
such claim, and b) allow you to control, and cooperate with you in, the defense and any
related settlement negotiations. Any Indemnitee may participate in any such claim at its
own expense.

####8. PROPRIETARY RIGHTS
Regardless of who owns the media on which the Work resides or is distributed, the Work
expressly remains the intellectual property of Licensor and/or the Contributors, and
Licensor and/or the Contributors retain all right, title and interest in and to the Work
and all copies thereof. Licensor expressly reserves all rights not specifically granted in
this Agreement.

####9. TERMINATION
Licensor reserves the right to terminate this Agreement at any time if you are in breach
of any of its terms and conditions, copyright laws, or any other applicable laws or
regulations. In such a case, the rights granted to you under Section 2 of this Agreement
shall be automatically terminated, and you shall be obliged to cease using the Work and
immediately destroy any copies of the Work and all backup copies. Termination is not the
sole remedy under this Agreement and, whether or not termination is effected, all other
remedies, legal and equitable, will remain available.

####10. UPGRADES
Licensor is under no obligation under this Agreement to provide any fixes, revisions,
upgrades or future versions of the Work to you or to any other party. Should you ever
obtain an upgrade of this Work, the terms and conditions of this Agreement shall also
apply to the upgrade. The Work is subject to change without notice.

####11. GENERAL

a. Independent Contractors. The parties and their respective personnel are and shall be 
independent contractors and neither party by virtue of this Agreement shall have any
right, power or authority to act or create any obligation, express or implied, on behalf
of the other party. 

b. Binding Nature. Subject to all other provisions herein contained, this Agreement shall
be binding on the parties and their successors and permitted assigns. 

c. Assignment. Licensee may not assign or otherwise transfer this Agreement, or any part
hereof, nor delegate any of its duties hereunder, whether by operation of law or
otherwise, to any third party. Licensee may delegate specific duties and obligations
hereunder to an Affiliate, however, in the event that Licensee wishes to assign or
transfer this entire Agreement to an Affiliate, Licensee may do so only via a novation
whereby all parties agree to such novation in writing and the Affiliate in effect becomes
the Licensee hereunder. 

d. Severability. If any provision of this Agreement is found by a court of competent
jurisdiction to be invalid or unenforceable, such invalidity or unenforceability shall
not invalidate or render unenforceable any other part of this Agreement, but the Agreement
shall be construed as not containing the particular provision or provisions held to be
invalid or unenforceable. 

e. Waiver. No delay or omission by either party hereto to exercise any right occurring
upon any noncompliance or default by the other party with respect to any of the terms of
this Agreement shall impair any such right or power or be construed to be a waiver
thereof. A waiver by either of the parties hereto of any of the covenants, conditions or
agreements to be performed by the other shall not be construed to be a waiver of any
succeeding breach thereof or of any covenant, condition or agreement herein contained. 

f. Governing Law; Exclusive Jurisdiction. This Agreement, and all the rights and duties of
the parties arising from or relating in any way to the subject matter of this Agreement or
the transaction(s) contemplated by it, shall be governed by, construed and enforced in
accordance with the law of the State of Idaho (excluding any conflict of laws provisions
of the State of Idaho that would refer to and apply the substantive laws of another
jurisdiction). Any suit or proceeding relating to this Agreement shall be brought in the
state courts of Idaho. Each of the parties consents to the exclusive personal jurisdiction
and venue of the state courts located in Idaho. 

g. No Construction Against Drafter. The parties agree that any principle of construction
or rule of law that provides that an agreement shall be construed against the drafter of
the agreement in the event of any inconsistency or ambiguity in such agreement shall not
apply to the terms and conditions of this Agreement. 

h. Entire Agreement; Modification. This Agreement sets forth the entire, final and
exclusive agreement between the parties as to the subject matter hereof and supersedes
all prior and contemporaneous agreements, understandings, negotiations and discussions,
whether oral or written, between the parties. The parties expressly disclaim the right to
claim the enforceability or effectiveness of any other amendments that are based on course
of dealing, waiver, reliance, estoppel or other similar legal theory. The parties
expressly disclaim the right to enforce any rule of law that is contrary to the terms of
this section. 
	
i. Survival. The following sections shall survive any termination of this Agreement: 2.c,
2.d, 2.e, 2.f, 4, 5, 6, 7, 8 and 11.a.


-------
