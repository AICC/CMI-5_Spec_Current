
**DOCUMENT No. CMI5-008**



## CMI5 Runtime




DRAFT RELEASE DATE :TDB
Revision 0.08  - INTERNAL DRAFT -  Apr 20, 2012






THIS DOCUMENT IS CONTROLLED BY:

**AICC CMI Subcommittee**

ALL REVISIONS TO THE DOCUMENT shall BE APPROVED
BY THE ABOVE ORGANIZATION PRIOR TO RELEASE.



POINT OF CONTACT:

AICC Administrator
18608 20th PL NE
Shoreline, WA 98155
 admin@aicc.org
www.aicc.org



Caveats...

2012 AICC
All rights reserved


The information contained in this document has been assembled by the AICC as an informational resource.  Neither the AICC nor any of its members assumes nor shall any of them have any responsibility for any use by anyone for any purpose of this document or of the data which it contains.



## CMI Guidelines for Interoperability

**Abstract:**
This specification describes the transport mechanism, runtime communication data model, and course data model for learning content and learning management systems. 


**Keywords:**
CBT, CMI, e-learning, LMS


**Introduction:**
The CMI-5 standard incorporates advances in architecture proposed from multiple organizations into one coherent standard. 

The goal of the new standard is to:

* simplify and update CMI standards to reflect changes in technology and content distribution practice 

* provide a user-definable set of data elements 

* provide the option to manage content sequencing by the administrative system.


**Discussion Forum:**
The CMI-5 working group is currently discussed in a private working area located on the AICC website. Once the spec has been written it will be posted in a public area for comments.  You can find the AICC Forum online.[4]

**Contributors**

* William A. McDonald –Boeing Training & Flight Services-AICC CMI Subcommittee Chair
* Edward Cohen – AICC Infrastructure Subcommittee Chair
* Thomas Creighton - ADL
* Nikolaus.Hruska – ADL
* Jonathan Poltrack – ADL
* Mark Schupp – Integrity Learning
* Ray Lowery – Pratt & Whitney
* Christopher Reynolds – Pelesys 
* Mingrui Zheng – Pelesys 
* Andrew Johnson – ADL
* John Kleeman – QuestionMark
* Kris Rockwell – Hybrid Learning Systems


## Revision History

REV 008	Edited for grammar, format and consistency

REV 007	-Made additions and edits to section 7.2 pertaining to error codes, updated WSDL based on latest version, updated XSD based on latest version, added reference to appendix 1 in document, edited certain sections to indicate case sensitivity, added sub sections for section 7.2, modified 7.2 AttemptHistory naming convention, changed URI to URL throughout document, added reference to Best Practices document

REV 006	-Reformatted section 7; formatted should, shall, may, not to lower case; added additional language to Set description in section 7

REV 005	-Edited section 6 to reflect further revisions, updated language and descriptions in section 7

REV 004	-Added CMI-5 description; edited section 6 to increase clarity and explicitness; modified appendices based on updates to WSDL and XML Binding examples; updated section 7 descriptions

REV 003	-Added and formatted appendices; updated terms (e.g. AU to learning activity); added additional definitions; updated Data Model section; consolidated forum feedback

REV 002	-Edited document; added XSD

REV NEW



## Contents

* 1 Overview	1
* 1.1 Scope	1
* Inside of Scope	1
* Outside of Scope	1
* 1.2 Purpose	1
* 2 References	1
* 3 Definitions	3
* 3.1 Abbreviations and acronyms	3
* 4 Conformance	4
* 4.1 Learning Activities	4
* 4.2 Learning Management Systems (LMS)	4
* 4.3 External Launching Systems	5
* 5 Conceptual Model: Informative	5
* 5.1 LMS Data Management Concepts	7
* 5.2 Description of use case	9
* 6 Data Model	10
* 6.1 Core Data	10
* LaunchParameters	10
* ContentState	10
* Completion	11
* Mastery	12
* Score	13
* Time	13
* 6.2 Entitlement Data	14
* Learner Identifier	14
* Entitlement Identifier	14
* 6.3 Content Defined Data	15
* Data Elements - Label	15
* Data Elements –Value	15
* Data Elements –Content Type	16
* Data Elements - Namespace	16
* Data Elements – Scope	17
* Printable	17
* Public	18
* 7 Actions	19
* Set	19
* Get	20
* GetHistory	21
* Exit	22
* 7.1 Action Parameter Structures	24
* CMISessionID	24
* AttemptData	24
* AttemptData.SequenceNumber	24
* AttemptData.Core	24
* AttemptData.Core.LaunchParameters	24
* AttemptData.Core.ContentState	25
* AttemptData.Core.Completion	25
* AttemptData.Core.Mastery	25
* AttemptData.Core.Score	25
* AttemptData.Core.Time	26
* AttemptData.ContentDefined	26
* AttemptData.ContentDefined.Item	26
* AttemptData.ContentDefined.Item.Label	26
* AttemptData.ContentDefined.Item.Value	27
* AttemptData.ContentDefined.Item.ContentType	27
* AttemptData.ContentDefined.Item.NameSpace	27
* AttemptData.ContentDefined.Item.NameSpace.Scope	27
* AttemptData.ContentDefined.Item.NameSpace.Name	28
* AttemptData.ContentDefined.Item.Printable	28
* AttemptData.ContentDefined.Item.Public	28
* AttemptDataFilter	28
* AttemptDataFilter.NumberOfAttempts	29
* AttemptDataFilter.Entitlement	29
* AttemptDataFilter.Entitlement.LearnerIdentifier	29
* AttemptDataFilter.Entitlement.EntitlementIdentifier	29
* AttemptDataFilter.Core	30
* AttemptDataFilter.Core.All	30
* AttemptDataFilter.Core.LaunchParameters	30
* AttemptDataFilter.Core.ContentState	30
* AttemptDataFilter.Core.Completion	31
* AttemptDataFilter.Core.Mastery	31
* AttemptDataFilter.Core.Score	31
* AttemptDataFilter.Core.Time	31
* AttemptDataFilter.ContentDefined	32
* AttemptDataFilter.ContentDefined.Item	32
* AttemptDataFilter.ContentDefined.Item.Label	32
* AttemptDataFilter.ContentDefined.Item.NameSpace	32
* AttemptDataFilter.ContentDefined.Item.NameSpace.Scope	33
* AttemptDataFilter.ContentDefined.Item.NameSpace.Name	33
* 7.2 Action Return Value Structures	33
* SetResponse	33
* SetResponse.Errors	33
* SetResponse.Errors.Error	34
* SetResponse.Errors.Error.Message	34
* SetResponse.Errors.Error.Code	34
* SetResponse.Errors.Error.Details	34
* SetResponse.Errors.Error.DataElement	35
* AttemptHistory	35
* AttemptHistory.Entitlement	35
* AttemptHistory.Entitlement.LearnerIdentifier	35
* AttemptHistory.Entitlement.EntitlementIdentifier	36
* AttemptHistory.Attempts	36
* AttemptHistory.Attempts.Attempt	36
* AttemptHistory.Attempts.Attempt.SequenceNumber	36
* AttemptHistory. Attempts.Attempt.Core	37
* AttemptHistory. Attempts.Attempt.Core.LaunchParameters	37
* AttemptHistory. Attempts.Attempt.Core.ContentState	37
* AttemptHistory. Attempts.Attempt.Core.Completion	37
* AttemptHistory. Attempts.Attempt.Core.Mastery	38
* AttemptHistory. Attempts.Attempt.Core.Score	38
* AttemptHistory.Attempts.Attempt.Core.Time	38
* AttemptHistory.Attempts.Attempt.ContentDefined	38
* AttemptHistory.Attempts.Attempt.ContentDefined.Item 39
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.Label 39
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.Value	39
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.ContentType	39
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.NameSpace	39
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.NameSpace.Scope	40
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.NameSpace.Name	40
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.Printable	40
* AttemptHistory.Attempts.Attempt.ContentDefined.Item.Public	40
* AttemptHistory.Errors	40
* ExitResponse	40
* ExitResponse.ExitURI	41
* ExitResponse.Errors	41
* 8 Content Launch Mechanisms	42
* 8.1 Web (Browser) Environment	42
* cmi-session	42
* cmi-endpoint	42
* 8.2 Other Launch Environments	44
* cmi-session	44
* cmi-endpoint	44
* 9 Web Service Definition	45
* 9.1 Data Model Bindings	45
* XML Binding	45
* 9.2 Transport Bindings	46
* SOAP 1.2 on HTTP	46
* 10 Bibliography	48
* Appendices	49
* 1 Error Codes	49
* 2 Data Model XSD	49
* 3 Service Definition WSDL	56
* 4 XML Binding Examples	60
* 5 Action Request and Response Examples	93
* License Agreement	112


## CMI5 Runtime


### 1	 Overview
The scope and purpose of this specification are discussed in sections 1.1 and 1.2. This specification describes runtime communication between Learning Management Systems ( LMS) and learning content presentations.

#### 1.1	Scope

**Inside of Scope**:
Content Launch Environment
Runtime Data Communication (between content and LMS)
LMS Reporting Obligations

**Outside of Scope**:
End User Authentication
User Interface Design
LMS Course Sequencing

#### 1.2	Purpose
The purpose of this specification is to provide a runtime communication data tracking framework for learning content and learning tracking systems that will be interoperable, regardless of what tracking data is desired by learning content (and LMS) designers.

It is not intended to be a specification of feature sets or to in any way restrict functionality of learning materials or the systems that manage them.

This specification defines data tracking that is learner centric. It assumes that a specific learner launches the training content and that the content is tracking that learner. 

### 2	 References
The following referenced documents are indispensable for the application of this specification. For dated references, only the edition cited applies. For undated references, the latest edition of the referenced document (including any amendments) applies.

CMIxxx – Course Structure

CMIxxx – Reference Model

RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998.

### 3	 Definitions 
For purposes of this specification, the following terms and definitiosns apply: 

**Administrator:** The administrative user that manages the LMS and related systems. Such a user performs tasks such as learner enrollment, course structure definition, and report management.

**Learning Activity:**  A learning content activity launched from an LMS. The learning activity is the unit of tracking and management. The learning activity collects data on the learner and sends it to the LMS system.

**Course:** A collection of learning activities, in a logical grouping, of content. A course is typically an internal data structure. Courses are often assigned to learners and tracked by the LMS.

**Course Structure:** A list of learning activities and launch parameters, with an implied sequence, representing a course.

**Learner:** The end user viewing/using the learning content (learning activities).

**Learning Management System (LMS):** A computer system that may include the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners progress. LMS launching, reporting, and tracking roles are the focus of the CMI5 specification.

**External Launching System:** A computer system has the ability to launch learning activities but not track them. An external launching system must be associated with an LMS to provide the required data services for learning activity tracking and launch parameter retrieval.

#### 3.1	Abbreviations and acronyms
AICC: Aviation Industry Computer-Based Training Committee

CMI: Computer Managed Instruction

JSON: JavaScript Object Notation

JSON-RPC: JavaScript Object Notation Remote Procedure Call

LMS: Learning Management System

PII: Personally Identifiable Information

SOAP: Simple Object Access Protocol

URI: Uniform Resource Identifier

URL: Uniform Resource Locator

URN: Uniform Resource Name

XML: Extensible Markup Language

XSD: Extensible Markup Language Schema Definition

WSDL: Web Service Definition Language

### 4	 Conformance
Conformance to this specification is discussed in ________________

In this specification, “shall” is to be interpreted as a requirement on an implementation; “shall not” is to be interpreted as a prohibition.  

“Should” is to be interpreted as a recommendation for implementation; “should not” is to be interpreted as the converse of “should”.  

“May” is to be interpreted as a course of action that is permissible within the limits of the standard; “need not” indicates a course of action that is not required.


#### 4.1	Learning Activities
Upon being launched in conformance with this specification, a conforming learning activity implementation shall initiate communication with the LMS.

A conforming learning activity implementation shall send messages that conform to this specification and accept message responses from the LMS systems as defined in this specification.

A conforming learning activity implementation shall send an exit message just prior to terminating execution.  

A conforming learning activity implementation shall not send messages after an exit message has been sent.

A conforming learning activity shall implement the ________ Data Model


#### 4.2	Learning Management Systems (LMS)
A conforming LMS implementation shall launch learning activities in a manner that conforms to the CMI5 specification.

A conforming LMS implementation shall accept messages that conform to this specification and generate the required, valid responses.

A conforming LMS implementation shall retain all data passed to it by all learning activity sessions, and retrieve data from past sessions on request from the learning activity.

A conforming LMS implementation shall store and make available (to administrative users), for viewing and printing, all data reported to it by conforming learning activities.

A conforming LMS implementation shall encrypt learner PII (personally identifiable information) in a manner that conforms to this specification for all response messages sent to learning activities.

A conforming LMS shall implement the Runtime Data Model as defined in this specification

A conforming LMS shall be able to implement the Course Structure Data model as defined in this specification.

A conforming LMS may notify administrative users of leaner learning status through email or other proprietary notification systems.


#### 4.3	External Launching Systems
A conforming external launching system shall launch learning activities in a manner that conforms to this specification. 
A conforming external launching system shall associate with a conforming LMS in order to provide the required data services for learning activity tracking and launch parameter retrieval.


### 5	Conceptual Model: Informative
**Synopsis of the CMI5 model:**

* An LMS imports a course structure.

* An LMS administrative user assigns a course or learning activity to a learner.
 
* A learner authenticates with an LMS or related system.
 
* A learner launches a learning activity (learning content) from the LMS or associated launching system, user an interface.
 
* The learning activity sends a message to the LMS requesting launch parameters and previous state information.
 
* Learner views the learning activity content and performs the learning. During this time the learning activity may request and store data.
 
* The learner exits the learning activity.
 
* The learning activity reports final tracking data to the LMS and issues an exit message.
 	
* Administrative users create and view reports of tracking data recorded by learning activities for individual learners.

**Responsibilities of the learning activity:**

* Parse the parameters from the launching environment to determine where the LMS location is and initiate communication with the LMS.

* Acting as “client”, send and receive messages using the defined transport mechanism(s) and associate commands as prescribed in this specification.
 
* Format all data per defined data types and vocabularies defined in this specification.
 
* Send an “exit” message prior to terminating the learning activity’s execution.
	
**Responsibilities of the LMS:**

* Launch the specified learning activity, in the defined environment(s).

* Acting as “server”, respond to all request messages from the launched learning activity using the defined transport mechanism (SOAP) and associate commands as prescribed in this specification.
 
* Format all data per defined data types and vocabularies defined in this specification.
 
* Record all data sent by the launched learning activity sessions.
 
* Make viewable and printable all data recorded from launched learning activity sessions.
 
* Maintain data for both current learning activity sessions and previous learning activity sessions and make both available to learning activities (IS THIS CORRECT???) upon request.


#### 5.1	LMS Data Management Concepts
The LMS is responsible for maintaining the following data structures:

**Course** – A collection of given learning activities. The location (URL) and launch parameters of the learning activities shall be defined in the LMS “course”, and not the learning activity media itself. 
	
**Enrollment** – A term defining an instance of an individual learner who has been assigned to a course.
	
**Class** – A group of learners enrolled in the same course.
	
**Learner Session** – The data tracking session for a given learning activity in a given Course for given individual learner. When the content terminates a session, no more data can be added to that session record. There are multiple instances of learner sessions (per learner, per learning activity, per course). The LMS has to be able to provide learner session data (to the learning activity) from the current session and previous sessions. 
	
**NameSpace** – A group of data elements for a given learner or group of learners, which is assigned to a given course. There is only a single instance of this data per namespace.

                   


Figure 1— Conceptual model, Content System-to-Target System communication


#### 5.2	Description of use case
The diagram (Figure 1 above) illustrates stuff.

**Topic 1**
Stuff. 
	note: 

Note Stuff.  
Stuff.
	note: 

Note Stuff. .


**Topic 2**
Stuff. 
	note: 

Note Stuff.  
Stuff.
	note: 

Note Stuff. .

### 6	Data Model
The runtime environment and transport framework described in this specification shall support the following data model. All data elements shall be implemented by the LMS. 


#### 6.1	Core Data 
The following data elements are considered basic elements for the core CMI5 data model:

**LaunchParameters**

	Required: Yes
	
	Data type: String
	
	Default Value: NULL
	
	Value Set By: LMS
	
	Description: Launch data specific to the learning activity being launched. This value shall be set by the LMS (via Course Structure and/or Administrative LMS user).

	Value space: Values defined by learning activity designer
	
	Sample element value: Debug=off, Units=Metric, Chrome=on


**ContentState**

	Required: No
	
	Data Type: String
	
	Default Value: NULL
	
	Value Set By: Learning Activity
	
	Description: State data specific to the learning activity. The learning activity may use this value to store information about its state.
				
	At the end of a learning session, the learning activity may provide updated content state information to the LMS.
				
	The LMS shall store this value as provided by the learning activity at the end of a learner session, unless the value provided is NULL; the LMS shall ignore NULL values as provided by the learning activity and any previously set value shall not be overwritten. 
	
	Value space: Values are defined by learning activity designer.
	
	Sample element value: XYZ123-00011010101-OFF-test=1


**Completion**

	Required: Yes
	
	Data Type: Boolean
	
	Default Value: NULL
	
	Value Set By: Learning Activity
	
	Description: This value indicates if a learner has viewed and/or completed all of the material presented in the learning activity. 

	The LMS shall store this value as provided by the learning activity. The LMS shall set the current completion status of a learning activity as the most recently received value from the learning activity, unless the value provided is NULL; the LMS shall ignore NULL values as provided by the 	learning activity and any previously set value shall not be overwritten.

	*Note that this is independent of the “Mastery” data element. *

	The possible values are as follows:
	
	**NULL Not Determined.** The learning activity is not designed to evaluate the learner or the learner did not engage in the learning activity in a manner which allowed for assessment. 

	**False Incomplete.** The learner has not completed all of the material in the learning 				activity.

	**True Completed.** The learner has completed all of the material in the learning activity.

	Value space: Boolean values defined by specification. 
				
	Vocabulary: 
		NULL
		False
		True

	Sample element value: 
		False


**Mastery**

	Required: Yes
	Data type: Boolean
	Default Value: NULL
	Value Set By: Learning Activity
	Description:  This value indicates if a learner succeeded or failed in mastering the activity presented in the 				learning activity. 

				The LMS shall store this value as provided by the learning activity. The LMS shall set the current 				mastery status of a learning activity as the most recently received value from the learning activity, 				unless the value provided is NULL; the LMS shall ignore NULL values as provided by the learning 				activity and any previously set value shall not be overwritten.

				The possible values are as follows:
				**NULL	Not Determined.** The learning activity is not designed to evaluate the learner or the learner 				did not engage in the activity within the learning activity where they were assessed. This is the 				default value if not set by learning activity.

				**False	Failed.** The learning engaged in the assessed learning activity and did not attain mastery.

				**True	Mastered.** The learner was assessed by the learning activity and did master the activity.

				Value space: Boolean values defined by specification. Default value is NULL.
				
				Vocabulary: 
					NULL
					False
					True

				Sample element value: 
					False


**Score**
	Required: Yes
	Data type: Integer
	Default Value:NULL
	Value Set By: Learning Activity
	Description: A value that defines a score for the learning activity session. Specified as a percentage correct from 			%0 to %100. A value of NULL indicates an unspecified score.

			The LMS shall store this value as provided by the learning activity. The LMS shall set the current score as 			the most recently received value from the learning activity, unless the value provided is NULL; the LMS 			shall ignore NULL values as provided by the learning activity and any previously set value shall not be 			overwritten..

	Value space: Integer value from 0 – 100. Default value is NULL.
	Sample element value: 75


**Time**
	Required: Yes
	Data type: String in Duration format
	Default Value: NULL
	Value Set By: Learning Activity
	Description: A value indicating the total time spent by a learner in a learning session. The learning activity 			shall report the duration of the learning session back to the LMS upon exiting. The LMS shall store this 			value as provided by the learning activity. 

			A value of NULL indicates an unspecified duration.

			The format for this duration value is shall follow the form described in ISO 8601. 

	Value space: Duration format (Specified by ISO 8601), in the following form:P[n]Y[n]M[n]DT[n]H[n]M[n]S	Default value is NULL.

	Sample element value: PT1H30M5S
	
	
### 6.2	Entitlement Data 
The data in this section is used for determining entitlement in content.  

**Learner Identifier**
	Required: Yes
	Data type: String
	Default Value: “” [Empty String]
	Value Set By: LMS
	Description: A value that uniquely identifies the learner in the LMS system. This value shall not contain any PII 			for the learner (such as name, phone number, email, etc.). The LMS or related system may link this value to 			PII. The identification shall be consistent for each launch of a title, but shall be unique across 			different titles. This will allow a vendor to track a resuming individual, but not allow them to track an 			individual across multiple titles.

	Value space: Valid values are determined by the LMS designer.
	Sample element value: XYZ123


**Entitlement Identifier**
	Required: Yes
	Data type: String
	Default Value:“” [Empty String]
	Value Set By: LMS
	Description: This value is set by the LMS and is used by the learning activity to determine if the launching system 			is entitled to use it. This value is provided to the LMS by the vendor when the content is installed. It is 			intended to be used by the entitlement layer of hosted content so the vendor can determine what system the 			learner is originating from.

	Value space: Valid values are determined by the learning activity designer.
	Sample element value: XYZ123


### 6.3	Content Defined Data
Content can define its own data elements for storage and retrieval. The LMS must store and retrieve content defined data elements per the actions defined in section 7.0.
Each (content defined) data element may have the following properties:

**Data Elements - Label**
	Required: Yes
	Data type: Character string 
	Value Set By: Learning Activity
	Description: Refers to the name used to reference the data element for getting and setting data element values. 
			All label values are case sensitive.

			The LMS shall store this value as provided by the learning activity.

	Value space: Reserved Values (if any) defined in data model. All values not colliding with defined data model are 			allowed.

	Sample element value: LearnerFlightPath


**Data Elements –Value**
	Required: Yes
	Data type: Type specified at runtime by learning activity
	Value Set By: Learning Activity

	Description: Refers to the value of the data element defined in the associated label.   

		The LMS shall store this value as provided by the learning activity.

	Value space: Type specified at runtime by learning activity
	Sample element value: True
	
	
**Data Elements –Content Type**

	Required: No
	Data type: String
	Value Set By: Learning Activity
	Description: This value defines the MIME type[3] that should be used by the LMS, or other viewing system, to render 			the data or download the data to a file.
	
			The LMS shall store this value as provided by the learning activity.

	Value space: MIME Type followed by whitespace and file extension
	Sample element value: application/vnd.ms-excel .xls


**Data Elements - Namespace**
	Required: No
	Data type: String
	Value Set By: Learning Activity
	Description: An identifier unique to a learner, or group of learners, enrolled in a given course in the LMS. When 			this field is used, the data element label is considered part of namespace that is shared with any learning 			activity in the same course (for the same learner or group of learners). Any learning activity (in the same 			course) referencing the same Namespace/Label combination can get and set data for the associated values for 			the given learner or group of learners. This allows learning activities associated with the same course to 			share data. It also enables group learning features in learning content and a means for the LMS to 			associate group learners. 
			
			The scope of the namespace (e.g. single learner or group) shall be specified in the associated “Scope” data 			element.

	Value space: String
	Sample element value: AirbusA380CBT 


**Data Elements – Scope**
	Required: No
	Data type: String
	Value Set By: Learning Activity
	Description: Refers to the scope of the associated namespace.

			If the value is set as “learner”, the scope of the associated namespace shall include any learning 			activities in the same course for the same learner.

			If the value is set as “group”, the scope of the associated namespace shall include any learning activities 			in the same course for the same group of learners.

	Value space: A case sensitive string value taking the form of “learner” or “group”
		Vocabulary:
			learner
			group
			
	Sample element value: group
	
	
**Printable**
	Required: No
	Data type: Boolean
	Default Value:False
	Value Set By: Learning Activity
	Description: Indicates whether or not the LMS should allow the data to be printed. 

	Value space: Boolean values defined by specification. 
		Vocabulary: 
			False
			True 

	Sample element value: True
	
	
**Public**
	Required: No
	Data type: Boolean
	Default Value:False
	Value Set By: Learning Activity
	Description: Indicates whether or not the LMS should allow the data to be displayed to external systems by default.  

	Value space: Boolean values defined by specification. 
		Vocabulary: 
			False
			True 

	Sample element value: True



### 7	Actions
The following are commands used by the content to specify specific actions for the LMS to perform. The LMS is required to support all of the following commands:

##### Set

**API Usage (as function call):**
Set(string CMISessionID, AttemptData)
Returns SetResponse record
See section 9-Web Service Definition for binding-specific information.

**Description**:
The Set action is used to assign values for data elements to the current learning attempt. 

The current attempt, learning activity, and learner are identified by the CMI5 Session Id associated with the method call. See 8-Content Launch Mechanisms for information about where the session id is obtained.

An AttemptData record containing data elements to be set is passed to the method. See section 7.1 - Action Parameter Structures for the AttemptData record definition. The learning activity shall provide the CMI5 Session Id and AttemptData record with each Set action request.

The LMS shall return a SetResponse record containing error codes and messages (if any). See section 7.1 - Action Parameter Structures for the SetResponse record definition. See Appendix 1 – Error Codes for error code definitions.

If an error condition occurs for any data element included in the AttemptData record the LMS shall not save values for any of the included data elements. The LMS shall reject the entire set request with the appropriate error message. See Appendix 1 – Error Codes for error code definitions.

The LMS shall not save values for data elements not included in the Attempt Data record. The LMS shall not save the value of Core Data Elements for which a value of NULL is specified in the Attempt Data record (NULL values shall be ignored with no error returned). 

Data element values set using the Set method are associated with the current attempt. The LMS shall overwrite prior values for the current attempt with new values in subsequent calls to Set (previous attempt records will not be affected).  The LMS shall not overwrite data elements not included in the Attempt Data record.

Each Content Defined data element value that is assigned a namespace shall be treated by the LMS as a single shared value with respect to that namespace.  If the same data element label is used to set a value with a different namespace the LMS shall create a separate shared value for that label in that namespace.

The LMS shall update (and share) values for data elements which are associated with a namespace immediately on receipt of the Set request. A call to Exit is not required. 

New values for data elements which are not associated with a namespace may be made available for reporting at the discretion of the LMS until an Exit request is made. Any statistical rollups should not take place until an Exit request is made.

Content Defined data elements are associated with a data type set by the learning activity and may be associated with a MIME media type (see 6.3 – Content Defined Data). Once set for a specific label these types may not be changed. A non-namespaced data element’s type is fixed at the first time it is set for a specific learning activity. A namespaced data element’s type is fixed at the first time its shared value is set within its namespace. If the LMS receives a Set request for a Content Defined data element that contains a value data type, or a ContentType which does not match those set the first time that the data element was received, the LMS shall respond with an error message. See Appendix 1 – Error Codes for error code definitions.


##### Get

**API Us age (as function call):**
Get(CMISessionID, AttemptDataFilter)
Returns AttemptHistory record
See section 9-Web Service Definition for binding-specific information.

**Description:**
The Get action is used to retrieve values for data elements from the current learning attempt. 

Data element values retrieved using the Get method are associated with the current attempt. To retrieve data from previous attempts use GetHistory.

The current attempt, learning activity, and learner are identified by the CMI5 Session Id associated with the method call. See 8-Content Launch Mechanisms for information about where the session id is obtained.

An AttemptDataFilter record containing a list of data elements to be retrieved is passed to the method. See section 7.1 - Action Parameter Structures for the AttemptDatafilter record definition. Core Data elements are identified for retrieval by Boolean flags. Content defined elements are identified by their Label and any associated namespace Name and Scope. The learning activity shall provide the CMI5 Session Id and AttemptDataFilter record with each Get action request.

The LMS shall return an AttemptHistory record containing the values of the requested data elements or error codes and messages (if any). See section 7.1 - Action Parameter Structures for the AttemptHistory record definition. See Appendix 1 – Error Codes for error code definitions.

The LMS shall not return values for data elements not specified in the AttemptDataFilter record.

If a data element is requested that was assigned a value during the current session, the LMS shall return that value.

If a data element is requested that was not assigned a value during the current session, the LMS shall return the current value as described below.

The LMS should determine the current value for a data element by searching through prior attempt records, in descending chronological order, until an attempt record is found in which the data element’s value was set. The LMS should return the value from that attempt record as the current value of the requested data element. EXCEPTION: The LMS should return the default value specified in 6.1 Core Data as the current value for Time.

If no current value is identified for a Core Data element, the LMS should return the element’s default value as specified in 6.1 Core Data.

If no current value is identified for a Content Defined data element, the LMS should not return that data element.

The LMS may use a different set of rules to determine current values of requested data elements. e.g.; An LMS might be configured to always report Mastery as True after the first attempt, in which it was set to True regardless of whether or not a subsequent attempt set Mastery to False. Similar reasoning could apply to any data element at the discretion of the LMS.

A content defined data element associated with a namespace shall have a single shared value with respect to that namespace. The LMS shall always return that shared value if that data element is requested. The LMS shall return the associated namespace Name and Scope with the element’s value.

The LMS may include the SequenceNumber data element in the single AttemptData record included in the AttemptHistory record returned but this inclusion is not required.


##### GetHistory

**API Usage (as function call):**
GetHistory(CMISessionID, AttemptDataFilter)
Returns AttemptHistory record
See section 9-Web Service Definition for binding-specific information.

**Description:**
The GetHistory action is used to retrieve values for data elements from the prior learning attempts. 

Data element values retrieved using the GetHistory method are associated with learning attempts prior to the current attempt. To retrieve data from the current attempt use Get.

The learning activity and learner are identified by the CMI5 Session Id associated with the method call. See 8-Content Launch Mechanisms for information about where the session id is obtained.

An AttemptDataFilter record containing a list of data elements to be retrieved is passed to the GetHistory method. See section 7.1 - Action Parameter Structures for the AttemptDatafilter record definition. Core Data elements are identified for retrieval by Boolean flags. Content defined elements are identified by their Label and any associated namespace Name and Scope. . The learning activity shall provide the CMI5 Session Id and AttemptDataFilter record with each GetHistory action request.

The LMS shall return an AttemptHistory record containing a list of AttemptData records holding the values of the requested data elements or error codes and messages (if any). See section 7.1 - Action Parameter Structures for the AttemptHistory record definition. See Appendix 1 – Error Codes for error code definitions.

The LMS shall not return values for data elements not specified in the AttemptDataFilter record. 

If a core data element value is requested, through GetHistory that was not assigned in a particular prior attempt, the LMS shall return a null value for the data element in the returned AttemptData record for that attempt.

The number of requested attempt records is specified using the AttemptDataFilter NumberOfAttempts element. The LMS shall return a maximum of NumberOfAttempts AttemptData records. The AttemptData SequenceNumber element shall contain a valid non-zero positive integer. AttemptData records shall be ordered by SequenceNumber in reverse chronological order (where 1 is the most recent, 2 is next most recent, etc.). AttemptData records may not necessarily be in physical sequential order in the AttemptHistory record.

If a content defined data element value is requested through GetHistory that was not assigned in a particular prior attempt, then the LMS shall not include that data element in the returned AttemptData record for that attempt.
If a content defined data element is associated with a namespace in the AttemptDataFilter for the request, the LMS shall return the current shared value for that data element in that namespace in all returned AttemptData records.
The LMS shall return the associated namespace Name and Scope with the element’s value for each requested data element that is associated with a namespace

If no value was ever assigned to a requested data element that is associated with a namespace, then the LMS shall not include that data element in the returned AttemptData record for any returned attempts.


##### Exit

**API Usage (as function call):**
Exit(CMISessionID) 
Returns ExitResponse record
See section 9-Web Service Definition for binding-specific information.

**Description:**
The Exit action is used to notify the Learning Management System that the learner is exiting the current attempt. 

The current attempt, learning activity, and learner are identified by the CMI5 Session Id associated with the method call. See 8-Content Launch Mechanisms for information about where the session id is obtained.

The learning activity shall provide the CMI5 Session Id with each Exit action request.

On receipt of an Exit request the LMS shall close the current attempt and learning session. The LMS shall create a new current attempt record and learning session on subsequent re-launch of the learning activity for the associated student.

The LMS shall return an ExitResponse record containing error codes and messages (if any). The LMS may include an ExitURI element in the ExitResponse record. See section 7.1 - Action Parameter Structures for the ExitResponse record definition. See Appendix 1 – Error Codes for error code definitions.

If ExitURI exists, it shall contain a reference to the action the LMS would like the client system to take next. For web-browser based systems, this shall be a fully-qualified HTTP URL to a browser-accessible resource. If the learning activity is hosted in a web-browser or is capable of emulating a web-browser it should redirect the learner to this URI. Usage of this element for non-browser based systems is undefined but not prohibited.


#### 7.1	Action Parameter Structures

**CMISessionID**
	Required: Yes
	Data type: String, no whitespace
	Multiplicity:Exactly 1
	BPNote: avoid xml reserved characters so that <![CDATA[ ]]> or encoding is not required.

	Description: The CMISessionID parameter is used in all actions to identify the Learner Session that is to be 			affected by the action (the learner session is associate with the Student, Course, learning activity, 			Learning Record, and current attempt on the LMS).

			The value for this parameter is provided by the LMS. See section 8 Content Launch Mechanisms for 			information about how this value is provided.


**AttemptData**
	Required: Yes
	Data type: structure
	Multiplicity: Exactly 1
	
	Description: The AttemptData structure is used in the Set action to hold the data element values being passed to 			the LMS. 

			The associated record structure is also returned as part of the response to Get and GetHistory.


**AttemptData.SequenceNumber**
 	Not used for Set action.

	See AttemptHistory.Attempts.Attempt.SequenceNumber in 7.2 Action Return Value Structures for an explanation of this 	element.


**AttemptData.Core**
	Required: No
	Data type: structure
	Multiplicity: 0 or 1 
	Description: The Core structure contains values of the Core data elements to be set. 
	
	*See 6.1 Core Data for specifics about each data element. *


**AttemptData.Core.LaunchParameters**

	*See 6.1 Core Data.*


**AttemptData.Core.ContentState**
 	Required: No
	Data type: String, nillable
	Multiplicity: 0 or 1

	*See 6.1 Core Data. *


**AttemptData.Core.Completion**
 	Required: No
	Data type: Boolean, nillable
	Multiplicity:0 or 1

	*See 6.1 Core Data. *


**AttemptData.Core.Mastery**
 	Required: No
	Data type: Boolean, nillable
	Multiplicity: 0 or 1

	*See 6.1 Core Data.* 


**AttemptData.Core.Score**
 	Required: No
	Data type: Integer, nillable
	Multiplicity: 0 or 1

	*See 6.1 Core Data.* 


**AttemptData.Core.Time**
	Required: No
	Data type: String, nillable ISO 8601 duration
	Multiplicity: 0 or 1

	**See 6.1 Core Data. **


**AttemptData.ContentDefined**
	Required: No
	Data type: structure
	Multiplicity: 0 or 1 
	Description: The ContentDefined structure contains a list of non-standard data elements.


**AttemptData.ContentDefined.Item**
	Required: No
	Data type: structure
	Multiplicity: unbounded
	Description: The Item structure contains the sub-elements of a single content defined data element.

	*See 6.3 Content Defined Data for specifics about each sub-element. *


**AttemptData.ContentDefined.Item.Label**
 	Required: Yes
	Data type: string
	Multiplicity: Exactly 1

	*See 6.3 Content Defined Data – Label.*
	

**AttemptData.ContentDefined.Item.Value**
 	Required: Yes
	Data type: Any type
	Multiplicity: Exactly 1

	*See 6.3 Content Defined Data – Value.*
	

**AttemptData.ContentDefined.Item.ContentType**
 	Required: No
	Data type: string MIME Media Type
	Multiplicity: 0 or 1

	*See 6.3 Content Defined Data – ContentType.*


**AttemptData.ContentDefined.Item.NameSpace**
 	Required: No
	Data type: structure
	Multiplicity: 0 or 1

	*See 6.3 Content Defined Data – NameSpace.*

AttemptData.ContentDefined.Item.NameSpace.Scope
Required: 
Yes
Data type: 
string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data – NameSpace:Scope.

AttemptData.ContentDefined.Item.NameSpace.Name
Required: 
Yes
Data type: 
string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data – NameSpace:Name.

AttemptData.ContentDefined.Item.Printable
Required: 
No
Data type: 
boolean
Multiplicity:
0 or 1
See 6.3 Content Defined Data – Printable.

AttemptData.ContentDefined.Item.Public
Required: 
No
Data type: 
boolean
Multiplicity:
0 or 1
See 6.3 Content Defined Data – Public.


AttemptDataFilter
Required: 
Yes
Data type: 
structure
Multiplicity:
Exactly 1
Description:
The AttemptDataFilter structure is used in the Get and GetHistory actions to specify which data elements are to be returned by the LMS. 


AttemptDataFilter.NumberOfAttempts
Required: 
Get: No GetHistory: Yes
Data type: 
Positive non-zero integer or -1
Multiplicity:
0 or 1
Description:
The NumberOfAttempts element specifies how many previous attempt records are to be returned in the response to a GetHistory action.  A value of “-1” indicates that all available attempts are to be returned. Not required for Get action.



AttemptDataFilter.Entitlement
Required: 
No
Data type:  structure
Multiplicity:
0 or 1
Description:
The Entitlement structure contains flag elements that specify which entitlement elements the LMS should include in the response to a Get Action. Not used for GetHistory action.

See 6.2 Entitlement Data for information about Entitlement data elements.
AttemptDataFilter.Entitlement.LearnerIdentifier
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The LearnerIdentifier flag element specifies whether or not the LearnerIdentifier data element is to be included in the response to a Get Action. 


AttemptDataFilter.Entitlement.EntitlementIdentifier
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The EntitlementIdentifier flag element specifies whether or not the EntitlementIdentifier data element is to be included in the response to a Get Action. 


AttemptDataFilter.Core
Required: 
No
Data type:  structure
Multiplicity:
0 or 1
Description:
The Core structure contains flag elements that specify which core data elements the LMS should include in the response to a Get or GetHistory Action. See 6.1 Core Data for information about Core data elements

AttemptDataFilter.Core.All
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The All flag element specifies whether or not the all of the core data elements are to be included in the response to a Get or GetHistory Action or just specific elements. 

If present and true, all Core data elements must be returned by the LMS.
AttemptDataFilter.Core.LaunchParameters
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The LaunchParameters flag element specifies whether or not the LaunchParameters data element is to be included in the response to a Get or GetHistory Action. 

If present and true, the LaunchParameters element must be returned by the LMS.
AttemptDataFilter.Core.ContentState
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The ContentState flag element specifies whether or not the ContentState data element is to be included in the response to a Get or GetHistory Action. 

If present and true, the ContentState element must be returned by the LMS.
AttemptDataFilter.Core.Completion
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The Completion flag element specifies whether or not the Completion data element is to be included in the response to a Get or GetHistory Action. 

If present and true, the Completion element must be returned by the LMS.
AttemptDataFilter.Core.Mastery
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The Mastery flag element specifies whether or not the Mastery data element is to be included in the response to a Get or GetHistory Action. 

If present and true, the Mastery element must be returned by the LMS.
AttemptDataFilter.Core.Score
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The Score flag element specifies whether or not the Score data element is to be included in the response to a Get or GetHistory Action. 

If present and true, the Score element must be returned by the LMS.
AttemptDataFilter.Core.Time
Required: 
No
Data type:  boolean
Multiplicity:
0 or 1
Description:
The Time flag element specifies whether or not the Time data element is to be included in the response to a Get or GetHistory Action. 

If present and true, the Time element must be returned by the LMS.
AttemptDataFilter.ContentDefined
Required: 
No
Data type:  structure
Multiplicity:
0 or 1
Description:
The ContentDefined structure contains a list of Item structures that specify which content defined data elements the LMS should include in the response to a Get or GetHistory Action. See 6.3 Content Defined Data for information about ContentDefined data elements.

AttemptDataFilter.ContentDefined.Item
Required: 
No
Data type:  structure
Multiplicity:
unbounded
Description:
The Item structure contains elements that identify a content defined data element that the LMS should include in the response to a Get or GetHistory Action. 
AttemptDataFilter.ContentDefined.Item.Label
Required: 
Yes
Data type: String 
Multiplicity:
Exactly 1
Description:
The Label element specifies the Label of a content defined data element that is to be included in the response to a Get or GetHistory Action. 


AttemptDataFilter.ContentDefined.Item.NameSpace
Required: 
No
Data type:  structure
Multiplicity:
0 or 1
Description:
The NameSpace structure contains elements that identify a content defined data namespace the LMS should use, along with the Label element, in identifying the content defined data element to include in the response to a Get or GetHistory Action. 
AttemptDataFilter.ContentDefined.Item.NameSpace.Scope
Required: 
Yes
Data type:  string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data: NameSpace for a description of NameSpace Scope values.
AttemptDataFilter.ContentDefined.Item.NameSpace.Name
Required: 
Yes
Data type:  string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data: NameSpace for a description of NameSpace Name values.
7.2	Action Return Value Structures
SetResponse
Required: 
Yes
Data type: 
structure
Multiplicity:
Exactly 1
Description:
The SetResponse structure is returned by the LMS from a Set action. It contains error messages, if any errors occurred, during processing of the Set request. An empty structure is returned if no errors occurred. 


SetResponse.Errors
Required: 
No
Data type: 
structure
Multiplicity:
0 or 1
Description:
The Errors structure contains a list of Error structures, if any errors occurred during processing of the request. 
See appendix 1 for a list of standard error codes.

SetResponse.Errors.Error
Required: 
No
Data type: 
structure
Multiplicity:
Unbounded
Description:
The Error structure contains elements associated with an error that occurred during request processing.
SetResponse.Errors.Error.Message
Required: 
No
Data type:  string
Multiplicity:
0 or 1
Description:
The Message element contains a textual description of the error.


SetResponse.Errors.Error.Code
Required: 
Yes
Data type:  string
Multiplicity:
Exactly 1
Description:
The ErrorCode element contains a code identifying the error. 


SetResponse.Errors.Error.Details
Required: 
No
Data type:  string
Multiplicity:
0 or 1
Description:
The Details element contains LMS-specific error information.
SetResponse.Errors.Error.DataElement
Required: 
No
Data type:  string
Multiplicity:
0 or 1
Description:
The DataElement element contains the name of the data element (if any) associated with the error. Core data element names are in the format Core.<element name>. Content Defined data element names are in the format ContentDefined.<label[.namespace scope.namespace name]>.
ie.; 
Core.Score
ContentDefined.MyLabel
ContentDefined.MyOtherLabel.learner.mynamespace
AttemptHistory
Required: 
Yes
Data type: 
structure
Multiplicity:
Exactly 1
Description:
The AttemptHistory structure is returned by the LMS from a Get or GetHistory action. It contains the requested data elements or any errors that occurred during request processing.  If an error occurs, no data elements included.


AttemptHistory.Entitlement
Required: 
no
Data type: 
structure
Multiplicity:
0 or 1
Description:
The Entitlement structure contains the elements with Entitlement data from the LMS. See 6.2 Entitlement Data for descriptions of the entitlement data elements.


AttemptHistory.Entitlement.LearnerIdentifier
Required: 
No
Data type: 
string
Multiplicity:
0 or 1
See 6.2 Entitlement Data.

AttemptHistory.Entitlement.EntitlementIdentifier
Required: 
No
Data type: 
string
Multiplicity:
0 or 1
See 6.2 Entitlement Data.


AttemptHistory.Attempts
Required: 
no
Data type: 
structure
Multiplicity:
0 or 1
Description:
The Attempts structure contains a list of AttemptData structures containing the data elements returned by the LMS for a Get or GetHistory action request.


AttemptHistory.Attempts.Attempt
Required: 
No
Data type: 
structure
Multiplicity:
unbounded
Description:
The AttemptData structure containing data elements returned by the LMS for a specific Learner Attempt. 


AttemptHistory.Attempts.Attempt.SequenceNumber
 Required: 
For GetHistory
Data type: 
Integer, non-zero, positive
Multiplicity:
0 or 1

Description:
The SequenceNumber element is returned by the LMS for GetHistory Action requests. It contains a sequence number which corresponds to the reverse-chronological order of the returned AttemptData structures.

Must be returned for GetHistory requests. Optional for Get requests.

NOTE: Some bindings do not guarantee that the physical order of elements will be preserved. SequenceNumber should be used to place the AttemptData structures in the correct order.
AttemptHistory. Attempts.Attempt.Core
Required: 
No
Data type: 
structure
Multiplicity:
0 or 1 
Description:
The Core structure contains values of the Core data elements returned. See 6.1 Core Data for specifics about each data element. 

AttemptHistory. Attempts.Attempt.Core.LaunchParameters
 Required: 
No
Data type: 
String, nillable
Multiplicity:
0 or 1
See 6.1 Core Data. 

AttemptHistory. Attempts.Attempt.Core.ContentState
 Required: 
No
Data type: 
String, nillable
Multiplicity:
0 or 1
See 6.1 Core Data. 

AttemptHistory. Attempts.Attempt.Core.Completion
 Required: 
No
Data type: 
Integer, nillable
Multiplicity:
0 or 1
See 6.1 Core Data. 

AttemptHistory. Attempts.Attempt.Core.Mastery
 Required: 
No
Data type: 
Integer, nillable
Multiplicity:
0 or 1
See 6.1 Core Data. 

AttemptHistory. Attempts.Attempt.Core.Score
 Required: 
No
Data type: 
Integer, nillable
Multiplicity:
0 or 1
See 6.1 Core Data. 

AttemptHistory.Attempts.Attempt.Core.Time
 Required: 
No
Data type: 
String, nillable
ISO 8601 duration
Multiplicity:
0 or 1
See 6.1 Core Data. 

AttemptHistory.Attempts.Attempt.ContentDefined
Required: 
No
Data type: 
structure
Multiplicity:
0 or 1 
Description:
The ContentDefined structure contains a list of non-standard data elements.

AttemptHistory.Attempts.Attempt.ContentDefined.Item
Required: 
No
Data type: 
structure
Multiplicity:
unbounded
Description:
The Item structure contains the sub-elements of a single content defined data element.

See 6.3 Content Defined Data for specifics about each sub-element. 

AttemptHistory.Attempts.Attempt.ContentDefined.Item.Label
 Required: 
Yes
Data type: 
string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data – Label.

AttemptHistory.Attempts.Attempt.ContentDefined.Item.Value
 Required: 
Yes
Data type: 
Any type
Multiplicity:
Exactly 1
See 6.3 Content Defined Data – Value.

AttemptHistory.Attempts.Attempt.ContentDefined.Item.ContentType

See 6.3 Content Defined Data – ContentType. 
AttemptHistory.Attempts.Attempt.ContentDefined.Item.NameSpace
 Required: 
No
Data type: 
structure
Multiplicity:
0 or 1
See 6.3 Content Defined Data – NameSpace.

AttemptHistory.Attempts.Attempt.ContentDefined.Item.NameSpace.Scope
 Required: 
Yes
Data type: 
string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data – NameSpace:Scope.

AttemptHistory.Attempts.Attempt.ContentDefined.Item.NameSpace.Name
 Required: 
Yes
Data type: 
string
Multiplicity:
Exactly 1
See 6.3 Content Defined Data – NameSpace:Name.

AttemptHistory.Attempts.Attempt.ContentDefined.Item.Printable

See 6.3 Content Defined Data – Printable. 
AttemptHistory.Attempts.Attempt.ContentDefined.Item.Public

See 6.3 Content Defined Data – Public.
AttemptHistory.Errors

See 7.2 SetResponse.Errors

ExitResponse
Required: 
Yes
Data type: 
structure
Multiplicity:
Exactly 1
Description:
The ExitResponse structure is returned by the LMS from an Exit action. It contains error messages if any errors occurred during processing of the Exit request. If no errors occur it may return a URI indicating what action the LMS would like the learning activity to take. 

ExitResponse.ExitURI
Required: 
No
Data type: 
string
Multiplicity:
0 or 1
Description:
If ExitURI is returned by the LMS it will contain a reference to the action that the LMS would like the client system to take next. For web-browser based systems, this will be a fully-qualified HTTP URL to a browser-accessible resource. If the learner client system is a web-browser, or is capable of emulating a browser, it should redirect the learner to this URI. Usage of this element for non-browser based systems is implementation-specific.

ExitResponse.Errors

See 7.2 SetResponse.Errors


8	Content Launch Mechanisms
8.1	Web (Browser) Environment
AU shall be launched by URL with launch parameters as defined in this section. 
The launch parameters shall be name/value pairs in a query string appended to the URL that launches the learning activity.  
If the learning activity’s URL requires a query string for other purposes, then the names shall not collide with parameters defined below.  
The order of the name/value pairs is not significant. Conforming Content shall have the ability to process them in any order.
Each value for the associated names shall be URL-encoded.
The format of the launching URL is as follows:
<URL to learning activity>?<other learning activity specific name/value pairs>&cmi-endpoint=<sessionID>&cmi-session=<sessionID>
The values for the launch parameters are described below: 
cmi-session

Required: 
Yes
Data type: 
String (URL-encoded), see Best Practices 
Description:
Uniquely defines the specific learning activity runtime session and learner to LMS, in messages sent to the LMS, by the learning activity.
Value space:
Any, valid, url-encoded string
Sample value: 
XZY1234-65445654d-4t
cmi-endpoint

Required: 
Yes
Data type: 
String (URL-encoded), see Best Practices
Description:
A URL to the LMS listening service. It is used by the learning activity to send messages to the LMS.
Value space:
Any, valid, url-encoded string
Sample element value: 
https://cmi.aicc.org/listener.asp?

8.2	Other Launch Environments
The following data must be provided to the Learning content prior to content launch. The manner under which the content is launched and how the content receives the following data is content-implementation specific at this time.
The values for the launch parameters are described below: 
cmi-session

Required: 
Yes
Data type: 
String
Description:
Uniquely defines the specific learning activity runtime session and learner to the LMS in messages sent to the LMS by the learning activity.
Value space:
String
Sample value: 
XZY1234-65445654d-4t
cmi-endpoint

Required: 
Yes
Data type: 
String
Description:
A URL to the LMS listening service. It is used by the learning activity to send messages to the LMS.
Value space:
Any valid URL
Sample element value: 
https://cmi.aicc.org/listener.asp?


9	Web Service Definition
CMI5 uses Web services for communication between the learning activity and the LMS. A definition and description of SOAP web service architecture can be found at http://www.w3.org/TR/2004/notE-ws-arch-20040211. Additional information about SOAP web service architecture can be found at www.ws-i.org.
Web services using other protocols such as REST and JSON-RPC are also possible.
The CMI 5 Web service definition consists of a data model binding and transport binding. The data model binding is described by an XML Schema Definition (XSD). The transport binding is described by a Web Service Definition Language (WSDL) file. These files allow for automated creation of a compatible web service interface on which learning activity and LMS applications may be constructed.

9.1	Data Model Bindings
XML Binding
XML (Extensible Markup Language) is a standardized text-based format for representing information. It is widely used for communication between disparate systems and across networks. The XML specification is available at http://www.w3.org/TR/xml11/.
The CMI5 XML data model binding is described by the XSD (XML Schema Definitions) in Appendix 2 - Data Model XSD. This XSD may also be found on-line at http://www.aicc.org/XXXXXXXXXXXXX.
XML reserved characters
The characters &, <, and (in some circumstances) > are reserved for XML markup and must be escaped or wrapped in a CDATA section as described in the XML specification.
Examples:
<ContentState>&lt;page&gt;37&lt;/page&gt;&lt;percentcomplete&gt;37&lt;/percentcomplete&gt;&lt;path&gt;advanced&lt;/path&gt;</ContentState>

<ContentState><![CDATA[<page>37</page><percentcomplete>37</percentcomplete><path>advanced</path>]]></ContentState>
Content Defined Data Value element data type
All CMI5 data model leaf elements have a specific XML Schema scalar type, except for the content defined data Value element. The data type for Value is specified at runtime. If no type is specified then Value is assumed to be XML markup.
Examples (where xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xmlns:xsd="http://www.w3.org/2001/XMLSchema"):
<Value xsi:type="xsd:string">string data</Value>

<Value xsi:type="xsd:integer">12345</Value>

<Value xsi:type="xsd:base64Binary">IEJjSFVCY0hVQmNIVUJjSFVCY0hV</Value>

<Value>
<hello>World</hello>
</Value>

Whitespace
Whitespace in data element values, including leading and trailing whitespace, must be preserved by the LMS.
Action Parameter XML Bindings
See 7.1 Action Parameter Structures for an explanation of each structure and element as it applies to a particular action. The XML binding element names and structure are identical to those described in that section.
See Appendix 4 – XML Binding Examples for detailed XML binding examples.

9.2	Transport Bindings
SOAP 1.2 on HTTP
SOAP (Simple Object Access Protocol) is a standardized protocol specification for transferring structured information between disparate systems. It uses an XML-based message format and an external protocol layer for message transmission. 
Standards relating to SOAP can be found at www.w3.org/standards/techs/soap.
The CMI 5 SOAP binding uses SOAP version 1.2 over HTTP in a request/response scenario. A CMI5 Action request is made by transmitting a SOAP message containing the action’s parameters to the LMS in the body of an HTTP POST request. The LMS returns the response record in the body of the HTTP response as a SOAP message.
Requesting an Action
A learning activity requests an action from the LMS by wrapping the action parameters in a SOAP 1.2  envelope and sending the resulting message to the LMS in an HTTP POST request to the cmi-endpoint provided to the learning activity when it is launched. See section 8 – Content Launch Mechanisms for more information about how the endpoint is provided. The desired action is specified in the HTTP Content-Type header associated with the POST request.
See Appendix 5 – Action Request and Response Examples for detailed examples of action requests and responses.


10	Bibliography
[1]  AICC CMI001, CMI Guidelines For Interoperability, Version 4.0.
[2]  SCORM – http://www.adlnet.gov/capabilities/scorm  
[3] MIME Types – http://www.iana.org/assignments/media-types/index.html 
[4] AICC Forum – http://forum.aicc.org/ Appendices
1	Error Codes
TBD


2	Data Model XSD
<?xml version="1.0" encoding="UTF-8"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" 
	xmlns:cmi5="http://www.aicc.org/2012/01/cmi5" 
	targetNamespace="http://www.aicc.org/2012/01/cmi5" 
	elementFormDefault="qualified" attributeFormDefault="unqualified">
	<!-- Request parameter definitions -->
	<xs:element name="cmiSessionID" type="cmi5:CMISessionID"/>
	<xs:simpleType name="CMISessionID">
		<xs:annotation>
			<xs:documentation>Session ID parameter for all requests. Must be all non-whitespace characters.</xs:documentation>
		</xs:annotation>
		<xs:restriction base="xs:string">
			<xs:pattern value="\S{1,}"/>
		</xs:restriction>
	</xs:simpleType>
	<xs:element name="attemptDataFilter" type="cmi5:AttemptDataFilter"/>
	<xs:complexType name="AttemptDataFilter">
		<xs:annotation>
			<xs:documentation>Filter parameter for Get and GetHistory requests.</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="NumberOfAttempts" minOccurs="0" maxOccurs="1">
				<xs:annotation>
					<xs:documentation>Number of past attempts requested for GetHistory requests.</xs:documentation>
				</xs:annotation>
				<xs:simpleType>
					<xs:restriction base="xs:integer">
						<xs:pattern value="[1-9]{1,1}[0-9]*|-1"/>
					</xs:restriction>
				</xs:simpleType>
			</xs:element>
			<xs:element name="Entitlement" type="cmi5:EntitlementFilter" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Core" type="cmi5:CoreElementFilter" minOccurs="0" maxOccurs="1"/>
			<xs:element name="ContentDefined" type="cmi5:ContentDefinedElementFilter" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:element name="attemptData" type="cmi5:AttemptData"/>
	<xs:complexType name="AttemptData">
		<xs:annotation>
			<xs:documentation>Attempt data for Set/Get requests.</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="SequenceNumber" minOccurs="0" maxOccurs="1">
				<xs:simpleType>
					<xs:restriction base="xs:integer">
						<xs:pattern value="[1-9]{1,1}[0-9]*"/>
					</xs:restriction>
				</xs:simpleType>
			</xs:element>
			<xs:element name="Core" type="cmi5:CoreElements" minOccurs="0" maxOccurs="1"/>
			<xs:element name="ContentDefined" minOccurs="0" maxOccurs="1">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="Item" minOccurs="0" maxOccurs="unbounded">
							<xs:complexType>
								<xs:sequence>
									<xs:element name="Label" type="xs:string" minOccurs="1" maxOccurs="1"/>
									<xs:element name="Value" type="xs:anyType" minOccurs="1" maxOccurs="1"/>
									<xs:element name="ContentType" type="xs:string" minOccurs="0" maxOccurs="1"/>
									<xs:element name="NameSpace" minOccurs="0" maxOccurs="1">
										<xs:complexType>
											<xs:sequence>
												<xs:element name="Scope" minOccurs="1" maxOccurs="1">
													<xs:simpleType>
														<xs:restriction base="xs:string">
															<xs:enumeration value="learner"/>
															<xs:enumeration value="group"/>
														</xs:restriction>
													</xs:simpleType>
												</xs:element>
												<xs:element name="Name" type="xs:string" minOccurs="1" maxOccurs="1"/>
											</xs:sequence>
										</xs:complexType>
									</xs:element>
									<xs:element name="Printable" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
									<xs:element name="Public" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
								</xs:sequence>
							</xs:complexType>
						</xs:element>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
		</xs:sequence>
	</xs:complexType>
	<!-- Response record definitions-->
	<xs:element name="attemptHistory" type="cmi5:AttemptHistory"/>
	<xs:complexType name="AttemptHistory">
		<xs:annotation>
			<xs:documentation>Response data record for Get and GetHistory requests.</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="Entitlement" type="cmi5:EntitlementIdentifiers" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Attempts">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="Attempt" type="cmi5:AttemptData" maxOccurs="unbounded"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="Errors" type="cmi5:RequestErrors" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:element name="setResponse" type="cmi5:SetResponse"/>
	<xs:complexType name="SetResponse">
		<xs:annotation>
			<xs:documentation>Response record for Set requests.</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="Errors" type="cmi5:RequestErrors" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:element name="exitResponse" type="cmi5:ExitResponse"/>
	<xs:complexType name="ExitResponse">
		<xs:annotation>
			<xs:documentation>Response record for Exit requests.</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="ExitURI" type="xs:string" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Errors" type="cmi5:RequestErrors" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<!-- Shared types-->
	<xs:complexType name="CoreElementFilter">
		<xs:annotation>
			<xs:documentation>Filter flags for Core data elements being requested.  Predefined in the specification</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="All" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="LaunchParameters" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="ContentState" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Completion" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Mastery" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Score" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Time" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:complexType name="ContentDefinedElementFilter">
		<xs:annotation>
			<xs:documentation>List of Content Defined Data elements being requested</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="Item" minOccurs="0" maxOccurs="unbounded">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="Label" type="xs:string" minOccurs="1" maxOccurs="1"/>
						<xs:element name="NameSpace" minOccurs="0" maxOccurs="1">
							<xs:complexType>
								<xs:sequence>
									<xs:element name="Scope" minOccurs="1" maxOccurs="1">
										<xs:simpleType>
											<xs:restriction base="xs:string">
												<xs:enumeration value="learner"/>
												<xs:enumeration value="group"/>
											</xs:restriction>
										</xs:simpleType>
									</xs:element>
									<xs:element name="Name" type="xs:string" minOccurs="1" maxOccurs="1"/>
								</xs:sequence>
							</xs:complexType>
						</xs:element>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
		</xs:sequence>
	</xs:complexType>
	<xs:complexType name="EntitlementIdentifiers">
		<xs:annotation>
			<xs:documentation>Data elements that control entitlement.  Content specific or CaaS (Content Relay) specific </xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="LearnerIdentifier" type="xs:string" minOccurs="0" maxOccurs="1"/>
			<xs:element name="EntitlementIdentifier" type="xs:string" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:complexType name="EntitlementFilter">
		<xs:annotation>
			<xs:documentation>Filter flags for Entitlement elements</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="LearnerIdentifier" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
			<xs:element name="EntitlementIdentifier" type="xs:boolean" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:complexType name="CoreElements">
		<xs:sequence>
			<xs:element name="LaunchParameters" type="xs:string" nillable="true" minOccurs="0" maxOccurs="1"/>
			<xs:element name="ContentState" type="xs:string" nillable="true" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Completion" type="xs:boolean" nillable="true" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Mastery" type="xs:boolean" nillable="true" minOccurs="0" maxOccurs="1"/>
			<xs:element name="Score" nillable="true" minOccurs="0" maxOccurs="1">
				<xs:simpleType>
					<xs:restriction base="xs:integer">
						<xs:minInclusive value="0"/>
						<xs:maxInclusive value="100"/>
					</xs:restriction>
				</xs:simpleType>
			</xs:element>
			<xs:element name="Time" type="xs:duration" nillable="true" minOccurs="0" maxOccurs="1"/>
		</xs:sequence>
	</xs:complexType>
	<xs:complexType name="RequestErrors">
		<xs:annotation>
			<xs:documentation>Errors.  Only present if message was not sucessfully processed.</xs:documentation>
		</xs:annotation>
		<xs:sequence>
			<xs:element name="Error" maxOccurs="unbounded">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="Code" type="xs:string" minOccurs="1" maxOccurs="1">
							<xs:annotation>
								<xs:documentation>Error Code TBD</xs:documentation>
							</xs:annotation>
						</xs:element>
						<xs:element name="Message" type="xs:string" minOccurs="0" maxOccurs="1">
							<xs:annotation>
								<xs:documentation>Error Descriptions TBD</xs:documentation>
							</xs:annotation>
						</xs:element>
						<xs:element name="Details" type="xs:string" minOccurs="0" maxOccurs="1">
							<xs:annotation>
								<xs:documentation>Vendor-specific error details.</xs:documentation>
							</xs:annotation>
						</xs:element>
						<xs:element name="DataElement" type="xs:string" minOccurs="0" maxOccurs="1">
							<xs:annotation>
								<xs:documentation>Identifier of the data element associated with the error.</xs:documentation>
							</xs:annotation>
						</xs:element>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
		</xs:sequence>
	</xs:complexType>
</xs:schema>

3	Service Definition WSDL
<?xml version="1.0" encoding="UTF-8"?>
<wsdl:definitions xmlns:wsdl="http://schemas.xmlsoap.org/wsdl/" 
	xmlns:http="http://schemas.xmlsoap.org/wsdl/http/" 
	xmlns:xs="http://www.w3.org/2001/XMLSchema" 
	xmlns:soap="http://schemas.xmlsoap.org/wsdl/soap/" 
	xmlns:soapenc="http://schemas.xmlsoap.org/soap/encoding/" 
	xmlns:soap12="http://schemas.xmlsoap.org/wsdl/soap12/" 
	xmlns:mime="http://schemas.xmlsoap.org/wsdl/mime/" 
	xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
	xmlns:tns="http://www.aicc.org/2012/01/cmi5" 
	xmlns:ns="http://www.aicc.org/2012/01/cmi5" 
	targetNamespace="http://www.aicc.org/2012/01/cmi5">
	<wsdl:import namespace="http://www.aicc.org/2012/01/cmi5" location="CMI5DataTypes.xsd"/>
	<wsdl:types>
		<xs:schema xmlns:xsi="http://www.w3.org/2001/XMLSchema" 
			targetNamespace="http://www.aicc.org/2012/01/cmi5" elementFormDefault="qualified">
			<xs:element name="Set">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="CMISessionID" type="tns:CMISessionID"/>
						<xs:element name="AttemptData" type="tns:AttemptData"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="SetResponse">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="result" type="tns:SetResponse"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="Get">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="CMISessionID" type="tns:CMISessionID"/>
						<xs:element name="AttemptDataFilter" type="tns:AttemptDataFilter"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="GetResponse">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="result" type="tns:AttemptHistory"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="GetHistory">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="CMISessionID" type="tns:CMISessionID"/>
						<xs:element name="AttemptDataFilter" type="tns:AttemptDataFilter"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="GetHistoryResponse">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="result" type="tns:AttemptHistory"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="Exit">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="CMISessionID" type="tns:CMISessionID"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
			<xs:element name="ExitResponse">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="result" type="tns:ExitResponse"/>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
		</xs:schema>
	</wsdl:types>
	<wsdl:message name="SoapGetIn">
		<wsdl:part name="Get" element="tns:Get"/>
	</wsdl:message>
	<wsdl:message name="SoapGetOut">
		<wsdl:part name="GetResponse" element="tns:GetResponse"/>
	</wsdl:message>
	<wsdl:message name="SoapSetIn">
		<wsdl:part name="Set" element="tns:Set"/>
	</wsdl:message>
	<wsdl:message name="SoapSetOut">
		<wsdl:part name="SetResponse" element="tns:SetResponse"/>
	</wsdl:message>
	<wsdl:message name="SoapGetHistoryIn">
		<wsdl:part name="GetHistory" element="tns:GetHistory"/>
	</wsdl:message>
	<wsdl:message name="SoapGetHistoryOut">
		<wsdl:part name="GetHistoryResponse" element="tns:GetHistoryResponse"/>
	</wsdl:message>
	<wsdl:message name="SoapExitIn">
		<wsdl:part name="Exit" element="tns:Exit"/>
	</wsdl:message>
	<wsdl:message name="SoapExitOut">
		<wsdl:part name="ExitResponse" element="tns:ExitResponse"/>
	</wsdl:message>
	<wsdl:portType name="cmi5.soap">
		<wsdl:operation name="Get">
			<wsdl:input message="tns:SoapGetIn"/>
			<wsdl:output message="tns:SoapGetOut"/>
		</wsdl:operation>
		<wsdl:operation name="Set">
			<wsdl:input message="tns:SoapSetIn"/>
			<wsdl:output message="tns:SoapSetOut"/>
		</wsdl:operation>
		<wsdl:operation name="GetHistory">
			<wsdl:input message="tns:SoapGetHistoryIn"/>
			<wsdl:output message="tns:SoapGetHistoryOut"/>
		</wsdl:operation>
		<wsdl:operation name="Exit">
			<wsdl:input message="tns:SoapExitIn"/>
			<wsdl:output message="tns:SoapExitOut"/>
		</wsdl:operation>
	</wsdl:portType>
	<wsdl:binding name="cmi5.soap" type="tns:cmi5.soap">
		<soap12:binding style="document" transport="http://schemas.xmlsoap.org/soap/http"/>
		<wsdl:operation name="Get">
			<soap12:operation soapAction="http://www.aicc.org/2012/01/cmi5/Get"/>
			<wsdl:input>
				<soap12:body use="literal"/>
			</wsdl:input>
			<wsdl:output>
				<soap12:body use="literal"/>
			</wsdl:output>
		</wsdl:operation>
		<wsdl:operation name="Set">
			<soap12:operation soapAction="http://www.aicc.org/2012/01/cmi5/Set"/>
			<wsdl:input>
				<soap12:body use="literal"/>
			</wsdl:input>
			<wsdl:output>
				<soap12:body use="literal"/>
			</wsdl:output>
		</wsdl:operation>
		<wsdl:operation name="GetHistory">
			<soap12:operation soapAction="http://www.aicc.org/2012/01/cmi5/GetHistory"/>
			<wsdl:input>
				<soap12:body use="literal"/>
			</wsdl:input>
			<wsdl:output>
				<soap12:body use="literal"/>
			</wsdl:output>
		</wsdl:operation>
		<wsdl:operation name="Exit">
			<soap12:operation soapAction="http://www.aicc.org/2012/01/cmi5/Exit"/>
			<wsdl:input>
				<soap12:body use="literal"/>
			</wsdl:input>
			<wsdl:output>
				<soap12:body use="literal"/>
			</wsdl:output>
		</wsdl:operation>
	</wsdl:binding>
	<wsdl:service name="CMI5Service">
		<wsdl:port name="cmi5.soap" binding="tns:cmi5.soap">
			<soap12:address location="http://www.aicc.org/services/cmi5service.svc"/>
		</wsdl:port>
	</wsdl:service>
</wsdl:definitions>


4	XML Binding Examples
CMISessionID
Type Definition:
<xs:simpleType name="CMISessionID">
	<xs:restriction base="xs:string">
		<xs:pattern value="\S{1,}"/>
	</xs:restriction>
</xs:simpleType>
Example:
<CMISessionID>cmisessionid</CMISessionID>
AttemptData
Type Definition:
<xs:complexType name="AttemptData">
	<xs:sequence>
		<xs:element name="SequenceNumber" 
minOccurs="0" maxOccurs="1">
			<xs:simpleType>
				<xs:restriction base="xs:integer">
					<xs:pattern value="[1-9]{1,1}[0-9]*"/>
				</xs:restriction>
			</xs:simpleType>
		</xs:element>
		<xs:element name="Core" minOccurs="0" maxOccurs="1">
			<xs:complexType>
				<xs:sequence>
					<xs:element name="LaunchParameters" 
						type="xs:string" nillable="true" 
minOccurs="0" maxOccurs="1"/>
					<xs:element name="ContentState" 
type="xs:string" nillable="true" 
minOccurs="0" maxOccurs="1"/>
					<xs:element name="Completion" 
type="xs:boolean" nillable="true" 
minOccurs="0" maxOccurs="1"/>
					<xs:element name="Mastery" 
type="xs:boolean" nillable="true" 
minOccurs="0" maxOccurs="1"/>
					<xs:element name="Score" nillable="true" 
						minOccurs="0" maxOccurs="1">
						<xs:simpleType>
							<xs:restriction base="xs:integer">
								<xs:minInclusive value="0"/>
								<xs:maxInclusive value="100"/>
							</xs:restriction>
						</xs:simpleType>
					</xs:element>
					<xs:element name="Time" type="xs:duration" 
						nillable="true" minOccurs="0" maxOccurs="1"/>
				</xs:sequence>
			</xs:complexType>
		</xs:element>
		<xs:element name="ContentDefined" 
minOccurs="0" maxOccurs="1">
			<xs:complexType>
				<xs:sequence>
					<xs:element name="Item" 
minOccurs="0" maxOccurs="unbounded">
						<xs:complexType>
							<xs:sequence>
<xs:element name="Label" type="xs:string" 
	minOccurs="1" maxOccurs="1"/>
								<xs:element name="Value" type="xs:anyType" 
									minOccurs="1" maxOccurs="1"/>
								<xs:element name="ContentType" 
									type="xs:string" 
minOccurs="0" maxOccurs="1"/>
								<xs:element name="NameSpace" 
minOccurs="0" maxOccurs="1">
									<xs:complexType>
										<xs:sequence>
											<xs:element name="Scope" 
												minOccurs="1" maxOccurs="1">
												<xs:simpleType>
													<xs:restriction 
														base="xs:string">
														<xs:enumeration 
															value="learner"/>
														<xs:enumeration 
															value="group"/>
													</xs:restriction>
												</xs:simpleType>
											</xs:element>
											<xs:element name="Name" 
												type="xs:string" 
minOccurs="1" maxOccurs="1"/>
										</xs:sequence>
									</xs:complexType>
								</xs:element>
								<xs:element name="Printable" 
									type="xs:boolean" 
minOccurs="0" maxOccurs="1"/>
								<xs:element name="Public" type="xs:boolean" 
									minOccurs="0" maxOccurs="1"/>
							</xs:sequence>
						</xs:complexType>
					</xs:element>
				</xs:sequence>
			</xs:complexType>
		</xs:element>
	</xs:sequence>
</xs:complexType>
Example:
<AttemptData>
	<Core>
		<ContentState>content state data</ContentState>
		<Completion>true</Completion>
		<Mastery>false</Mastery>
		<Score>95</Score>
		<Time>P0DT1H0M0S</Time>
	</Core>
	<ContentDefined>
		<Item>
			<Label>mylabel1</Label>
			<Value xsi:type="xsd:string">mylabel1 data</Value>
			<NameSpace>
				<Scope>learner</Scope>
				<Name>mylearnernamespace</Name>
			</NameSpace>
			<Printable>true</Printable>
			<Public>true</Public>
		</Item>
		<Item>
			<Label>mylabel2</Label>
			<Value xsi:type="xsd:string">mylabel2 data</Value>
			<NameSpace>
				<Scope>group</Scope>
				<Name>mygroupnamespace</Name>
			</NameSpace>
			<Printable>true</Printable>
		</Item>
		<Item>
			<Label>mybinary</Label>
			<Value xsi:type="xsd:base64Binary">
IEJjSFVCY0hVQmNIVUJjSFVCY0hV</Value>
			<ContentType>application/pdf</ContentType>
			<Printable>true</Printable>
		</Item>
		<Item>
			<Label>myxml</Label>
			<Value>
				<hello>world</hello>
			</Value>
		</Item>
		<Item>
			<Label>mytypedxml</Label>
			<Value>
				<hello xmlns="http/mynamespaceuri">my world</hello>
			</Value>
		</Item>
	</ContentDefined>
</AttemptData>

AttemptDataFilter
Type Definition:
<xs:complexType name="AttemptDataFilter">
	<xs:sequence>
		<xs:element name="NumberOfAttempts" 
minOccurs="0" maxOccurs="1">
			<xs:simpleType>
				<xs:restriction base="xs:integer">
					<xs:pattern value="[1-9]{1,1}[0-9]*|-1"/>
				</xs:restriction>
			</xs:simpleType>
		</xs:element>
		<xs:element name="Entitlement" 
minOccurs="0" maxOccurs="1">
			<xs:complexType>
				<xs:sequence>
					<xs:element name="LearnerIdentifier"
type="xs:boolean" minOccurs="0" maxOccurs="1"/>
					<xs:element name="EntitlementIdentifier" 
						type="xs:boolean" minOccurs="0" maxOccurs="1"/>
				</xs:sequence>
			</xs:complexType>
		</xs:element>
		<xs:element name="Core" minOccurs="0" maxOccurs="1">
			<xs:complexType>
				<xs:sequence>
					<xs:element name="All" type="xs:boolean" 
						minOccurs="0" maxOccurs="1"/>
					<xs:element name="LaunchParameters" 
						type="xs:boolean" minOccurs="0" maxOccurs="1"/>
					<xs:element name="ContentState" type="xs:boolean" 
						minOccurs="0" maxOccurs="1"/>
					<xs:element name="Completion" type="xs:boolean" 
						minOccurs="0" maxOccurs="1"/>
					<xs:element name="Mastery" type="xs:boolean" 
						minOccurs="0" maxOccurs="1"/>
					<xs:element name="Score" type="xs:boolean" 
						minOccurs="0" maxOccurs="1"/>
					<xs:element name="Time" type="xs:boolean" 
						minOccurs="0" maxOccurs="1"/>
				</xs:sequence>
			</xs:complexType>
		</xs:element>
		<xs:element name="ContentDefined" 
minOccurs="0" maxOccurs="1">
			<xs:complexType>
				<xs:sequence>
					<xs:element name="Item" 
minOccurs="0" maxOccurs="unbounded">
						<xs:complexType>
							<xs:sequence>
								<xs:element name="Label" type="xs:string" 
									minOccurs="1" maxOccurs="1"/>
								<xs:element name="NameSpace" 
minOccurs="0" maxOccurs="1">
									<xs:complexType>
										<xs:sequence>
											<xs:element name="Scope" 
												minOccurs="1" maxOccurs="1">
												<xs:simpleType>
													<xs:restriction 
														base="xs:string">
														<xs:enumeration 
															value="learner"/>
														<xs:enumeration 
															value="group"/>
													</xs:restriction>
												</xs:simpleType>
											</xs:element>
											<xs:element name="Name" 
												type="xs:string" 
minOccurs="1" maxOccurs="1"/>
										</xs:sequence>
									</xs:complexType>
								</xs:element>
							</xs:sequence>
						</xs:complexType>
					</xs:element>
				</xs:sequence>
			</xs:complexType>
		</xs:element>
	</xs:sequence>
</xs:complexType>
Example (Get action):
	<AttemptDataFilter>
		<Entitlement>
			<LearnerIdentifier>true</LearnerIdentifier>
			<EntitlementIdentifier>true</EntitlementIdentifier>
		</Entitlement>
		<Core>
			<LaunchParameters>true</LaunchParameters>
			<ContentState>true</ContentState>
			<Completion>true</Completion>
		</Core>
		<ContentDefined>
			<Item>
				<Label>mylabel1</Label>
				<NameSpace>
					<Scope>learner</Scope>
					<Name>mylearnernamespace</Name>
				</NameSpace>
			</Item>
			<Item>
				<Label>mylabel2</Label>
				<NameSpace>
					<Scope>group</Scope>
					<Name>mygroupnamespace</Name>
				</NameSpace>
			</Item>
			<Item>
				<Label>mybinary</Label>
			</Item>
			<Item>
				<Label>myxml</Label>
			</Item>
			<Item>
				<Label>mytypedxml</Label>
			</Item>
		</ContentDefined>
	</AttemptDataFilter>
Example (GetHistory action):
<AttemptDataFilter>
	<NumberOfAttempts>2</NumberOfAttempts>
	<Core>
		<LaunchParameters>true</LaunchParameters>
		<ContentState>true</ContentState>
		<Completion>true</Completion>
	</Core>
	<ContentDefined>
		<Item>
			<Label>mylabel1</Label>
			<NameSpace>
				<Scope>learner</Scope>
				<Name>mylearnernamespace</Name>
			</NameSpace>
		</Item>
		<Item>
			<Label>mylabel2</Label>
			<NameSpace>
				<Scope>group</Scope>
				<Name>mygroupnamespace</Name>
			</NameSpace>
		</Item>
		<Item>
			<Label>mybinary</Label>
		</Item>
		<Item>
			<Label>myxml</Label>
		</Item>
		<Item>
			<Label>mytypedxml</Label>
		</Item>
	</ContentDefined>
</AttemptDataFilter>
Action Return Value Structures
SetResponse
Type Definition:
<xs:complexType name="SetResponse">
	<xs:sequence>
		<xs:element name="Errors" minOccurs="0" maxOccurs="1">
<xs:complexType>
				<xs:sequence>
					<xs:element name="Error" maxOccurs="unbounded">
						<xs:complexType>
							<xs:sequence>
								<xs:element name="ErrorDescription" 
									type="xs:string" 
minOccurs="0" maxOccurs="1">
								</xs:element>
								<xs:element name="ErrorCode" 
									type="xs:string" 
minOccurs="1" maxOccurs="1">
								</xs:element>
								<xs:element name="ExceptionType" 
									type="xs:string" 
minOccurs="0" maxOccurs="1">
								</xs:element>
							</xs:sequence>
						</xs:complexType>
					</xs:element>
				</xs:sequence>
</xs:complexType>
		</xs:element>
	</xs:sequence>
</xs:complexType>

Examples:
Successful Set Action
<SetResponse/>

Unsuccessful Set action:
<SetResponse>
	<Errors xmlns="http://www.aicc.org/2012/01/cmi5">
		<Error>
			<ErrorDescription>
Invalid Parameter: Invalid Session Id
</ErrorDescription>
			<ErrorCode>-32602</ErrorCode>
		</Error>
	</Errors>
</SetResponse>

AttemptHistory
Type Definition:
<xs:complexType name="AttemptHistory">
	<xs:sequence>
		<xs:element name="Entitlement" 
minOccurs="0" maxOccurs="1">
<xs:complexType>
				<xs:sequence>
					<xs:element name="LearnerIdentifier" 
						type="xs:string" minOccurs="0" maxOccurs="1"/>
					<xs:element name="EntitlementIdentifier" 
						type="xs:string" minOccurs="0" maxOccurs="1"/>
				</xs:sequence>
</xs:complexType>
</xs:element>
		<xs:element name="Attempts">
			<xs:complexType>
				<xs:sequence>
					<xs:element name="Attempt" maxOccurs="unbounded">
<xs:complexType name="AttemptData">
							<xs:sequence>
								<xs:element name="SequenceNumber" 
									minOccurs="0" maxOccurs="1">
									<xs:simpleType>
										<xs:restriction base="xs:integer">
											<xs:pattern 
value="[1-9]{1,1}[0-9]*"/>
										</xs:restriction>
									</xs:simpleType>
								</xs:element>
								<xs:element name="Core" 
									minOccurs="0" maxOccurs="1">
<xs:complexType>
										<xs:sequence>
											<xs:element name="LaunchParameters" 
												type="xs:string" 
nillable="true" 
minOccurs="0" maxOccurs="1"/>
											<xs:element name="ContentState" 
												type="xs:string" nillable="true" 
												minOccurs="0" maxOccurs="1"/>
											<xs:element name="Completion" 
												type="xs:boolean" nillable="true" 
												minOccurs="0" maxOccurs="1"/>
											<xs:element name="Mastery" 
												type="xs:boolean" nillable="true" 
												minOccurs="0" maxOccurs="1"/>
											<xs:element name="Score" 
												nillable="true" 
minOccurs="0" maxOccurs="1">
												<xs:simpleType>
													<xs:restriction 
														base="xs:integer">
														<xs:minInclusive value="0"/>
														<xs:maxInclusive value="100"/>
													</xs:restriction>
												</xs:simpleType>
											</xs:element>
											<xs:element name="Time" 
												type="xs:duration" nillable="true" 
												minOccurs="0" maxOccurs="1"/>
										</xs:sequence>
</xs:complexType>
								</xs:element>
								<xs:element name="ContentDefined" 
									minOccurs="0" maxOccurs="1">
									<xs:complexType>
										<xs:sequence>
											<xs:element name="Item" minOccurs="0" 
												maxOccurs="unbounded">
												<xs:complexType>
													<xs:sequence>
														<xs:element name="Label" 
															type="xs:string" 
															minOccurs="1" 
															maxOccurs="1"/>
														<xs:element name="Value" 
															type="xs:anyType" 
															minOccurs="1" 
															maxOccurs="1"/>
														<xs:element name="ContentType" 
															type="xs:string" 
															minOccurs="0"																							maxOccurs="1"/>
														<xs:element name="NameSpace" 
															minOccurs="0" maxOccurs="1">
															<xs:complexType>
																<xs:sequence>
																	<xs:element 
																		name="Scope" 
																		minOccurs="1" 
																		maxOccurs="1">
																		<xs:simpleType>
<xs:restriction 
		base="xs:string">
																				<xs:enumeration 
																				value="learner"/>
																				<xs:enumeration 
																				value="group"/>
																			</xs:restriction>
																		</xs:simpleType>
																	</xs:element>
																	<xs:element name="Name" 
																		type="xs:string" 
																		minOccurs="1" 
																		maxOccurs="1"/>
																</xs:sequence>
															</xs:complexType>
														</xs:element>
<xs:element name="Printable" 
	type="xs:boolean" 
	minOccurs="0" maxOccurs="1"/>
													<xs:element name="Public" 
														type="xs:boolean" 
														minOccurs="0" maxOccurs="1"/>
												</xs:sequence>
											</xs:complexType>
										</xs:element>
									</xs:sequence>
								</xs:complexType>
							</xs:element>
						</xs:sequence>
</xs:complexType>
				</xs:element>
			</xs:sequence>
		</xs:complexType>
	</xs:element>
<xs:element name="Errors" minOccurs="0" maxOccurs="1">
<xs:complexType>
		<xs:sequence>
			<xs:element name="Error" maxOccurs="unbounded">
				<xs:complexType>
					<xs:sequence>
						<xs:element name="ErrorDescription" 
							type="xs:string" minOccurs="0" maxOccurs="1">
						</xs:element>
						<xs:element name="ErrorCode" 
							type="xs:string" minOccurs="1" maxOccurs="1">
						</xs:element>
						<xs:element name="ExceptionType" 
							type="xs:string" minOccurs="0" maxOccurs="1">
						</xs:element>
					</xs:sequence>
				</xs:complexType>
			</xs:element>
		</xs:sequence>
</xs:complexType>
</xs:element>
</xs:sequence>
</xs:complexType>

Example (Get response):
<AttemptHistory>
	<Attempts xmlns="http://www.aicc.org/2012/01/cmi5">
		<Attempt>
			<Core>
				<LaunchParameters>
launch parameter data</LaunchParameters>
				<ContentState>content state data</ContentState>
				<Completion>true</Completion>
				<Score xsi:nil="true"/>
				<Time xsi:nil="true"/>
			</Core>
			<ContentDefined>
				<Item>
					<Label>mylabel1</Label>
					<Value xsi:type="xsd:string">mylabel1 data</Value>
					<NameSpace>
						<Scope>learner</Scope>
						<Name>mylearnernamespace</Name>
					</NameSpace>
				</Item>
				<Item>
					<Label>mylabel2</Label>
					<Value xsi:type="xsd:string">mylabel2 data</Value>
					<NameSpace>
						<Scope>group</Scope>
						<Name>mygroupnamespace</Name>
					</NameSpace>
				</Item>
				<Item>
					<Label>mybinary</Label>
					<Value xsi:type="xsd:string">mybinary data</Value>
				</Item>
				<Item>
					<Label>myxml</Label>
					<Value>
						<hello>world</hello>
					</Value>
				</Item>
				<Item>
					<Label>mytypedxml</Label>
					<Value>
						<hello 
xmlns="http/mynamespaceuri">my world</hello>
					</Value>
				</Item>
			</ContentDefined>
		</Attempt>
	</Attempts>
</AttemptHistory>

Example (GetHistory response):
<AttemptHistory>
	<Attempts xmlns="http://www.aicc.org/2012/01/cmi5">
		<Attempt>
			<SequenceNumber>1</SequenceNumber>
			<Core>
				<LaunchParameters>
launch parameter data</LaunchParameters>
				<ContentState>content state data</ContentState>
				<Completion>false</Completion>
				<Score xsi:nil="true"/>
				<Time xsi:nil="true"/>
			</Core>
			<ContentDefined>
				<Item>
					<Label>mylabel1</Label>
					<Value xsi:type="xsd:string">mylabel1 data</Value>
					<NameSpace>
						<Scope>learner</Scope>
						<Name>mylearnernamespace</Name>
					</NameSpace>
				</Item>
				<Item>
					<Label>mylabel2</Label>
					<Value xsi:type="xsd:string">mylabel2 data</Value>
					<NameSpace>
						<Scope>group</Scope>
						<Name>mygroupnamespace</Name>
					</NameSpace>
				</Item>
				<Item>
					<Label>mybinary</Label>
					<Value xsi:type="xsd:string">mybinary data</Value>
				</Item>
				<Item>
					<Label>myxml</Label>
					<Value>
						<hello>world</hello>
					</Value>
				</Item>
				<Item>
					<Label>mytypedxml</Label>
					<Value>
						<hello 
xmlns="http/mynamespaceuri">my world</hello>
					</Value>
				</Item>
			</ContentDefined>
		</Attempt>
		<Attempt>
			<SequenceNumber>2</SequenceNumber>
			<Core>
				<LaunchParameters xsi:nil="true"/>
				<ContentState xsi:nil="true"/>
				<Completion xsi:nil="true"/>
				<Score xsi:nil="true"/>
				<Time xsi:nil="true"/>
			</Core>
			<ContentDefined>
				<Item>
					<Label>mylabel1</Label>
					<Value xsi:type="xsd:string">mylabel1 data</Value>
					<NameSpace>
						<Scope>learner</Scope>
						<Name>mylearnernamespace</Name>
					</NameSpace>
				</Item>
				<Item>
					<Label>mylabel2</Label>
					<Value xsi:type="xsd:string">mylabel2 data</Value>
					<NameSpace>
						<Scope>group</Scope>
						<Name>mygroupnamespace</Name>
					</NameSpace>
				</Item>
				<Item>
					<Label>mybinary</Label>
					<Value xsi:type="xsd:string">mybinary data</Value>
				</Item>
				<Item>
					<Label>myxml</Label>
					<Value>
						<hello>world</hello>
					</Value>
				</Item>
				<Item>
					<Label>mytypedxml</Label>
					<Value>
						<hello 
xmlns="http/mynamespaceuri">my world</hello>
					</Value>
				</Item>
			</ContentDefined>
		</Attempt>
	</Attempts>
</AttemptHistory>
ExitResponse
Type Definition:
<xs:complexType name="ExitResponse">
	<xs:sequence>
		<xs:element name="ExitURI" type="xs:string" 
			minOccurs="0" maxOccurs="1"/>
		<xs:element name="Errors" minOccurs="0" maxOccurs="1">
<xs:complexType>
				<xs:sequence>
					<xs:element name="Error" maxOccurs="unbounded">
						<xs:complexType>
							<xs:sequence>
								<xs:element name="ErrorDescription" 
									type="xs:string" 
minOccurs="0" maxOccurs="1">
								</xs:element>
								<xs:element name="ErrorCode" 
									type="xs:string" 
minOccurs="1" maxOccurs="1">
								</xs:element>
								<xs:element name="ExceptionType" 
									type="xs:string" 
minOccurs="0" maxOccurs="1">
								</xs:element>
							</xs:sequence>
						</xs:complexType>
					</xs:element>
				</xs:sequence>
</xs:complexType>
		</xs:element>
	</xs:sequence>
</xs:complexType>

Example:
<ExitResponse>
	<ExitUri xmlns="http://www.aicc.org/2012/01/cmi5">
http://www.aicc.org/lms/return.php</ExitUri>
</ExitResponse>

5	Action Request and Response Examples

Set
Content-Type header (wrapped for readability, must be on a single line in the request):
Content-Type: application/soap+xml; charset=utf-8; action="http://www.aicc.org/2012/01/cmi5/Set"
Example Request Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<Set xmlns="http://www.aicc.org/2012/01/cmi5">
			<CMISessionID>cmisessionid</CMISessionID>
			<AttemptData>
				<Core>
					<LaunchParameters xsi:nil="true"/>
					<ContentState>content state data</ContentState>
					<Completion>true</Completion>
					<Mastery>false</Mastery>
					<Score>95</Score>
					<Time>PT1H</Time>
				</Core>
				<ContentDefined>
					<Item>
						<Label>mylabel1</Label>
						<Value xsi:type="xsd:string">mylabel1 data</Value>
						<NameSpace>
							<Scope>learner</Scope>
							<Name>mylearnernamespace</Name>
						</NameSpace>
						<Printable>true</Printable>
						<Public>true</Public>
					</Item>
					<Item>
						<Label>mylabel2</Label>
						<Value xsi:type="xsd:string">mylabel2 data</Value>
						<NameSpace>
							<Scope>group</Scope>
							<Name>mygroupnamespace</Name>
						</NameSpace>
						<Printable>true</Printable>
					</Item>
					<Item>
						<Label>mybinary</Label>
						<Value xsi:type="xsd:base64Binary">IEJjSFVCY0hVQmNIVUJjSFVCY0hV</Value>
						<ContentType>application/pdf</ContentType>
						<Printable>true</Printable>
					</Item>
					<Item>
						<Label>myxml</Label>
						<Value>
							<hello>world</hello>
						</Value>
					</Item>
					<Item>
						<Label>mytypedxml</Label>
						<Value>
							<hello xmlns="http/mynamespaceuri">my world</hello>
						</Value>
					</Item>
				</ContentDefined>
			</AttemptData>
		</Set>
	</s:Body>
</s:Envelope> 
Example Response Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<SetResponse xmlns="http://www.aicc.org/2012/01/cmi5">
			<result/>
		</SetResponse>
	</s:Body>
</s:Envelope>
Get
Content-Type header (wrapped for readability, must be on a single line in the request):
Content-Type: application/soap+xml; charset=utf-8; action="http://www.aicc.org/2012/01/cmi5/Get"
Example Request Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<Get xmlns="http://www.aicc.org/2012/01/cmi5">
			<CMISessionID>cmisessionid</CMISessionID>
			<AttemptDataFilter>
				<Entitlement>
					<LearnerIdentifier>true</LearnerIdentifier>
					<EntitlementIdentifier>true</EntitlementIdentifier>
				</Entitlement>
				<Core>
					<LaunchParameters>true</LaunchParameters>
					<ContentState>true</ContentState>
					<Completion>true</Completion>
				</Core>
				<ContentDefined>
					<Item>
						<Label>mylabel1</Label>
						<NameSpace>
							<Scope>learner</Scope>
							<Name>mylearnernamespace</Name>
						</NameSpace>
					</Item>
					<Item>
						<Label>mylabel2</Label>
						<NameSpace>
							<Scope>group</Scope>
							<Name>mygroupnamespace</Name>
						</NameSpace>
					</Item>
					<Item>
						<Label>mybinary</Label>
					</Item>
					<Item>
						<Label>myxml</Label>
					</Item>
					<Item>
						<Label>mytypedxml</Label>
					</Item>
				</ContentDefined>
			</AttemptDataFilter>
		</Get>
	</s:Body>
</s:Envelope>
Example Response Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<GetResponse xmlns="http://www.aicc.org/2012/01/cmi5">
			<result>
				<Attempts>
					<Attempt>
						<Core>
							<LaunchParameters>launch parameter data</LaunchParameters>
							<ContentState>content state data</ContentState>
							<Completion>true</Completion>
						</Core>
						<ContentDefined>
							<Item>
								<Label>mylabel1</Label>
								<Value xsi:type="xsd:string">mylabel1 data</Value>
								<NameSpace>
									<Scope>learner</Scope>
									<Name>mylearnernamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mylabel2</Label>
								<Value xsi:type="xsd:string">mylabel2 data</Value>
								<NameSpace>
									<Scope>group</Scope>
									<Name>mygroupnamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mybinary</Label>
								<Value xsi:type="xsd:string">mybinary data</Value>
							</Item>
							<Item>
								<Label>myxml</Label>
								<Value>
									<hello>world</hello>
								</Value>
							</Item>
							<Item>
								<Label>mytypedxml</Label>
								<Value>
									<hello xmlns="http/mynamespaceuri">my world</hello>
								</Value>
							</Item>
						</ContentDefined>
					</Attempt>
				</Attempts>
			</result>
		</GetResponse>
	</s:Body>
</s:Envelope>
GetHistory
Content-Type header (wrapped for readability, must be on a single line in the request):
Content-Type: application/soap+xml; charset=utf-8; action="http://www.aicc.org/2012/01/cmi5/GetHistory"
Example Request Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<GetHistory xmlns="http://www.aicc.org/2012/01/cmi5">
			<CMISessionID>cmisessionid</CMISessionID>
			<AttemptDataFilter>
				<NumberOfAttempts>3</NumberOfAttempts>
				<Core>
					<LaunchParameters>true</LaunchParameters>
					<ContentState>true</ContentState>
					<Completion>true</Completion>
				</Core>
				<ContentDefined>
					<Item>
						<Label>mylabel1</Label>
						<NameSpace>
							<Scope>learner</Scope>
							<Name>mylearnernamespace</Name>
						</NameSpace>
					</Item>
					<Item>
						<Label>mylabel2</Label>
						<NameSpace>
							<Scope>group</Scope>
							<Name>mygroupnamespace</Name>
						</NameSpace>
					</Item>
					<Item>
						<Label>mybinary</Label>
					</Item>
					<Item>
						<Label>myxml</Label>
					</Item>
					<Item>
						<Label>mytypedxml</Label>
					</Item>
				</ContentDefined>
			</AttemptDataFilter>
		</GetHistory>
	</s:Body>
</s:Envelope>
Example Response Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<GetHistoryResponse xmlns="http://www.aicc.org/2012/01/cmi5">
			<result>
				<Attempts>
					<Attempt>
						<SequenceNumber>1</SequenceNumber>
						<Core>
							<LaunchParameters>launch parameter data</LaunchParameters>
							<ContentState>content state data</ContentState>
							<Completion>false</Completion>
						</Core>
						<ContentDefined>
							<Item>
								<Label>mylabel1</Label>
								<Value xsi:type="xsd:string">mylabel1 data</Value>
								<NameSpace>
									<Scope>learner</Scope>
									<Name>mylearnernamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mylabel2</Label>
								<Value xsi:type="xsd:string">mylabel2 data</Value>
								<NameSpace>
									<Scope>group</Scope>
									<Name>mygroupnamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mybinary</Label>
								<Value xsi:type="xsd:string">mybinary data</Value>
							</Item>
							<Item>
								<Label>myxml</Label>
								<Value>
									<hello>world</hello>
								</Value>
							</Item>
							<Item>
								<Label>mytypedxml</Label>
								<Value>
									<hello xmlns="http/mynamespaceuri">my world</hello>
								</Value>
							</Item>
						</ContentDefined>
					</Attempt>
					<Attempt>
						<SequenceNumber>2</SequenceNumber>
						<Core>
							<LaunchParameters xsi:nil="true"/>
							<ContentState xsi:nil="true"/>
							<Completion xsi:nil="true"/>
						</Core>
						<ContentDefined>
							<Item>
								<Label>mylabel1</Label>
								<Value xsi:type="xsd:string">mylabel1 data</Value>
								<NameSpace>
									<Scope>learner</Scope>
									<Name>mylearnernamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mylabel2</Label>
								<Value xsi:type="xsd:string">mylabel2 data</Value>
								<NameSpace>
									<Scope>group</Scope>
									<Name>mygroupnamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mybinary</Label>
								<Value xsi:type="xsd:string">mybinary data</Value>
							</Item>
							<Item>
								<Label>myxml</Label>
								<Value>
									<hello>world</hello>
								</Value>
							</Item>
							<Item>
								<Label>mytypedxml</Label>
								<Value>
									<hello xmlns="http/mynamespaceuri">my world</hello>
								</Value>
							</Item>
						</ContentDefined>
					</Attempt>
					<Attempt>
						<SequenceNumber>3</SequenceNumber>
						<Core>
							<LaunchParameters>launch parameter data</LaunchParameters>
							<ContentState>content state data</ContentState>
							<Completion>true</Completion>
						</Core>
						<ContentDefined>
							<Item>
								<Label>mylabel1</Label>
								<Value xsi:type="xsd:string">mylabel1 data</Value>
								<NameSpace>
									<Scope>learner</Scope>
									<Name>mylearnernamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mylabel2</Label>
								<Value xsi:type="xsd:string">mylabel2 data</Value>
								<NameSpace>
									<Scope>group</Scope>
									<Name>mygroupnamespace</Name>
								</NameSpace>
							</Item>
							<Item>
								<Label>mybinary</Label>
								<Value xsi:type="xsd:string">mybinary data</Value>
							</Item>
							<Item>
								<Label>myxml</Label>
								<Value>
									<hello>world</hello>
								</Value>
							</Item>
							<Item>
								<Label>mytypedxml</Label>
								<Value>
									<hello xmlns="http/mynamespaceuri">my world</hello>
								</Value>
							</Item>
						</ContentDefined>
					</Attempt>
				</Attempts>
			</result>
		</GetHistoryResponse>
	</s:Body>
</s:Envelope>
Exit
Content-Type header (wrapped for readability, must be on a single line in the request):
Content-Type: application/soap+xml; charset=utf-8; action="http://www.aicc.org/2012/01/cmi5/Exit"
Example Request Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<Exit xmlns="http://www.aicc.org/2012/01/cmi5">
			<CMISessionID>cmisessionid</CMISessionID>
		</Exit>
	</s:Body>
</s:Envelope>
Example Response Message:
<s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope">
	<s:Body xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" 
		xmlns:xsd="http://www.w3.org/2001/XMLSchema">
		<ExitResponse xmlns="http://www.aicc.org/2012/01/cmi5">
			<result>
				<ExitURI>http://www.aicc.org/content/return.html</ExitURI>
			</result>
		</ExitResponse>
	</s:Body>
</s:Envelope>

JavaScript Transmission Example
//variable “xml” contains the SOAP message
//variable “actionName” contains the CMI5 action
var xmlhttp = new XMLHttpRequest();
xmlhttp.open("POST", endPoint, false);
xmlhttp.setRequestHeader("Content-Type", 
"application/soap+xml; charset=utf-8; action=\"" +
“http://www.aicc.org/2012/01/cmi5/”  + actionName + 
"\"");
xmlhttp.send(xml);




License Agreement
THE WORK (AS DEFINED HEREIN) ACCOMPANYING THIS LICENSE AGREEMENT ("AGREEMENT") IS PROVIDED BY THE AICC, A NON-PROFIT CORPORATION ORGANIZED UNDER THE LAWS OF Idaho (“LICENSOR”), TO YOU (“YOU” OR “LICENSEE”) ONLY UNDER THE TERMS AND CONDITIONS OF THIS AGREEMENT. ANY USE, REPRODUCTION, DISTRIBUTION OR MODIFICATION OF THE WORK BY YOU CONSTITUTES YOUR ACCEPTANCE OF THIS AGREEMENT. BY OBTAINING, USING, DISTRIBUTING, REPRODUCING AND/OR MODIFYING THE WORK, YOU AGREE THAT YOU HAVE READ, UNDERSTOOD, AND WILL COMPLY WITH THE FOLLOWING TERMS AND CONDITIONS.
1. DEFINITIONS
“Affiliate” means any entity that directly or indirectly controls, is controlled by, or is under common control with, another entity, so long as such control exists. For purposes of this definition, with respect to a business entity, “control” means a majority vote of voting members.  In the event that such control ceases to exist, any grant of rights or other contractual powers granted to such Affiliate hereunder will be immediately withdrawn, and this Agreement as between Licensor and such Affiliate shall be terminated as set forth in Section 9, below.
“Compliance Test Suite” means any suite of computer programs (e.g., test tools), database schema, plans, procedures, checklists, documentation and the like developed or adopted by or for AICC and approved by AICC for the purpose of determining the compliance of an implementation of a Specification.
“Contribution” means a submission by Licensee or Other Licensee to Licensor in writing (including a writing in electronic medium) of a change, modification or addition to the Work for inclusion in future versions of the Work; and which such submission is accepted for inclusion in the Work by Licensor. Contributions do not include additions to the Work that: (i) are separate works distributed in conjunction with the Work under their own license agreement, and (ii) are not Derivative Works of the Work.
“Contributor” means any Licensee or any Other Licensee person or entity that submits a Contribution.


“Derivative Work” is as defined in the United States Copyright Act 17 U.S.C. § 101, and means any document, standard, specification, computer program, compilation, technical data, schema, XML instance document or similar work that includes or derives from major elements of the Work, whereby such major elements are protected by copyright, patent or any other recognized intellectual property right.
“AICC” means the Aviation Industry Computer Based Training Committee Corporation, a non-profit corporation organized under the laws of Idaho.
“Licensee” means you as a party to this Agreement to include all your Affiliates.
“Necessary Claims” means those claims of all patents and patent applications throughout the world, other than design patents and design registrations, whereby such claims are necessarily infringed by an implementation of a Work and which are within the bounds of the Scope, where such infringement could not have been avoided by another commercially feasible non-infringing implementation of such Work. Necessary Claims do not include any claims (i) other than those set forth above even if contained in the same patent as Necessary Claims or (ii) that read solely on an optional implementation example or optional reference implementation.
“Other Licensee” or “Other Licensees” means a third party licensee (or licensees) other than you, whereby such third party licensee has separately entered into this Agreement with Licensor, to include all Affiliates of such third party licensee.
“Scope” means the software interfaces disclosed with particularity in a Specification where the sole purpose of such disclosure is to enable products to interoperate, interconnect or communicate as defined within a Specification. Notwithstanding the foregoing, the Scope shall not include (i) any enabling technologies that may be necessary to make or use any product or portion thereof that complies with a Specification, but are not themselves expressly set forth in a Specification (e.g., compiler technology, object oriented technology, basic operating system technology); (ii) the implementation of other published specifications not developed by or for AICC, but referred to in the body of a Specification; or (iii) any portions of any product and any combinations thereof the purpose or function of which is not required for compliance with a Specification.
“Specification” means a document entitled “Specification” or “Standard” adopted and approved for release by AICC relating to any AICC implementation, and any updates or revisions adopted and approved for release.


“Standards Organization” means any entity whose primary activities are developing, coordinating, promulgating, revising, amending, reissuing, interpreting, or otherwise maintaining standards that address the interests of a wide base of users or consumers of such standards outside the standards development organization.
“Technical Note” means a proposal, document or guide, other than a Specification, which has been approved for release as a AICC Technical Note. Typically, a Technical Note will contain functional and technical information to aid in the implementation of a Specification as adopted and approved for release by AICC.
“Work” means any Specification, Technical Note or Compliance Test Suite distributed in accordance with and licensed under this Agreement.
2. LICENSE GRANT AND RESTRICTIONS
a.	Subject to the terms of this Agreement, Licensor hereby grants to Licensee a non-exclusive, worldwide, royalty-free license in any copyrights and/or Necessary Claims in the Work such that Licensee may view, use, reproduce, publicly display, distribute and prepare Derivative Works of the Work. 
b.	Licensee hereby grants to Licensor and all Other Licensees a non-exclusive, worldwide, royalty- free license in any copyrights and/or Necessary Claims in which Licensee asserts ownership, such that Licensor and all Other Licensees may view, use, reproduce, publicly display, distribute and prepare Derivative Works of any Contributions that Licensee may have made to the Work. Licensee agrees that it will not transfer its ownership of any copyrights or patents having Necessary Claims for the purpose of circumventing this Section 2.b. Licensee shall not attempt under its copyrights, Necessary Claims or otherwise to restrict any Other Licensee from exercising that Other Licensee’s rights granted to it by Licensor under an agreement with essentially the same terms and conditions as this Agreement. 
c.	To the extent that a Licensee reproduces or distributes copies of the Work, portions thereof or any Derivative Work in any medium, with or without modifications, such Licensee shall give a copy of this Agreement to any recipients of the Work. 
d.	Licensee hereunder expressly agrees to include the following notice on ALL copies of the Work, portions thereof or Derivative Works: "Copyright © The AICC. All Rights Reserved.  http://www.aicc.org” 


e.	Licensee agrees to include the following notice in all Derivative Works: “This product implements and complies with the Version CMI-5 [or other version as applicable] AICC Specifications as published by the AICC at http://www.AICC.org”. 
f.	Licensee may not facilitate or assist any Learning Technology Standards Organization other than Licensor in co-opting, copying, distributing, publishing or using the Work without prior written approval of Licensor. Licensee may not create any Derivative Work for ownership by, presentation by, distributing by, publishing by or attribution to any Standards Organization or similar entity other than Licensor, unless specifically approved in writing by Licensor. 


3. GRANT OF RIGHTS BY CONTRIBUTORS
Subject to the terms of this Agreement, a Contributor hereby grants to Licensor a non-exclusive, worldwide, royalty-free license under all intellectual property rights to make, use, sell, offer to sell, import and otherwise transfer any Contribution of such Contributor. This license shall apply to the combination of the Contribution and the Work.
4. TRADEMARKS
This Agreement does not grant permission to use the trade names, trademarks, service marks, or product names of the Licensor, except as required for reasonable and customary use in describing the origin of the Work and reproducing the content of the copyright notice.
5. WARRANTY
THE WORK ACCOMPANYING THIS AGREEMENT IS PROVIDED "AS IS" WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, AND THE HOLDERS OF ANY COPYRIGHT, PATENT OR OTHER INTELLECTUAL PROPERTY RIGHT THEREIN MAKE NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO, WARRANTIES OF MERCHANTABILITY OR FITNESS FOR ANY PARTICULAR PURPOSE OR THAT THE USE OF THE SOFTWARE OR DOCUMENTATION WILL NOT INFRINGE ANY THIRD PARTY PATENTS, COPYRIGHTS, TRADEMARKS OR OTHER RIGHTS. You are solely responsible for determining the appropriateness of using or redistributing the Work and assume any risks associated with your exercise of permissions under this Agreement.
6. LIMITATION OF LIABILITY
IN NO EVENT AND UNDER NO LEGAL THEORY, WHETHER IN TORT (INCLUDING NEGLIGENCE), CONTRACT, OR OTHERWISE, UNLESS REQUIRED BY APPLICABLE LAW (SUCH AS DELIBERATE AND GROSSLY NEGLIGENT ACTS) OR AGREED TO IN WRITING, SHALL LICENSOR OR ANY CONTRIBUTOR BE LIABLE TO YOU FOR ANY DAMAGES WHATSOEVER, INCLUDING ANY DIRECT, INDIRECT, EXEMPLARY, PUNITIVE, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES OF ANY CHARACTER ARISING AS A RESULT OF THIS AGREEMENT OR OUT OF THE USE OR INABILITY TO USE THE WORK (INCLUDING BUT NOT LIMITED TO DAMAGES FOR LOSS OF PROFITS, GOODWILL, WORK STOPPAGE, COMPUTER FAILURE OR MALFUNCTION, OR ANY AND ALL OTHER COMMERCIAL DAMAGES OR LOSSES), EVEN IF LICENSOR OR SUCH CONTRIBUTOR HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.
7. COMMERCIAL DISTRIBUTION
If you include the Work or any Derivative Work in a commercial product offering, you hereby agree to defend and indemnify Licensor and every Contributor (the "Indemnitees ") against any losses, damages and costs (collectively "Losses") arising from claims, lawsuits and other legal actions brought by a third party against the Indemnitees, to the extent caused by your acts or omissions in connection with your distribution of the Work in a commercial product offering. Indemnitees must: a) promptly notify you in writing of such claim, and b) allow you to control, and cooperate with you in, the defense and any related settlement negotiations. Any Indemnitee may participate in any such claim at its own expense.
8. PROPRIETARY RIGHTS
Regardless of who owns the media on which the Work resides or is distributed, the Work expressly remains the intellectual property of Licensor and/or the Contributors, and Licensor and/or the Contributors retain all right, title and interest in and to the Work and all copies thereof. Licensor expressly reserves all rights not specifically granted in this Agreement.


9. TERMINATION
Licensor reserves the right to terminate this Agreement at any time if you are in breach of any of its terms and conditions, copyright laws, or any other applicable laws or regulations. In such a case, the rights granted to you under Section 2 of this Agreement shall be automatically terminated, and you shall be obliged to cease using the Work and immediately destroy any copies of the Work and all backup copies.
Termination is not the sole remedy under this Agreement and, whether or not termination is effected, all other remedies, legal and equitable, will remain available.
10. UPGRADES
Licensor is under no obligation under this Agreement to provide any fixes, revisions, upgrades or future versions of the Work to you or to any other party. Should you ever obtain an upgrade of this Work, the terms and conditions of this Agreement shall also apply to the upgrade. The Work is subject to change without notice.
11. GENERAL
a.	Independent Contractors. The parties and their respective personnel are and shall be independent contractors and neither party by virtue of this Agreement shall have any right, power or authority to act or create any obligation, express or implied, on behalf of the other party. 
b.	Binding Nature. Subject to all other provisions herein contained, this Agreement shall be binding on the parties and their successors and permitted assigns. 
c.	Assignment. Licensee may not assign or otherwise transfer this Agreement, or any part hereof, nor delegate any of its duties hereunder, whether by operation of law or otherwise, to any third party. Licensee may delegate specific duties and obligations hereunder to an Affiliate, however, in the event that Licensee wishes to assign or transfer this entire Agreement to an Affiliate, Licensee may do so only via a novation whereby all parties agree to such novation in writing and the Affiliate in effect becomes the Licensee hereunder. 


d.	Severability. If any provision of this Agreement is found by a court of competent jurisdiction to be invalid or unenforceable, such invalidity or unenforceability shall not invalidate or render unenforceable any other part of this Agreement, but the Agreement shall be construed as not containing the particular provision or provisions held to be invalid or unenforceable. 
e.	Waiver. No delay or omission by either party hereto to exercise any right occurring upon any noncompliance or default by the other party with respect to any of the terms of this Agreement shall impair any such right or power or be construed to be a waiver thereof. A waiver by either of the parties hereto of any of the covenants, conditions or agreements to be performed by the other shall not be construed to be a waiver of any succeeding breach thereof or of any covenant, condition or agreement herein contained. 
f.	Governing Law; Exclusive Jurisdiction. This Agreement, and all the rights and duties of the parties arising from or relating in any way to the subject matter of this Agreement or the transaction(s) contemplated by it, shall be governed by, construed and enforced in accordance with the law of the State of Idaho (excluding any conflict of laws provisions of the State of Idaho that would refer to and apply the substantive laws of another jurisdiction). Any suit or proceeding relating to this Agreement shall be brought in the state courts of Idaho. Each of the parties consents to the exclusive personal jurisdiction and venue of the state courts located in Idaho. 
g.	No Construction Against Drafter. The parties agree that any principle of construction or rule of law that provides that an agreement shall be construed against the drafter of the agreement in the event of any inconsistency or ambiguity in such agreement shall not apply to the terms and conditions of this Agreement. 
h.	Entire Agreement; Modification. This Agreement sets forth the entire, final and exclusive agreement between the parties as to the subject matter hereof and supersedes all prior and contemporaneous agreements, understandings, negotiations and discussions, whether oral or written, between the parties. The parties expressly disclaim the right to claim the enforceability or effectiveness of any other amendments that are based on course of dealing, waiver, reliance, estoppel or other similar legal theory. The parties expressly disclaim the right to enforce any rule of law that is contrary to the terms of this section. 
i.	Survival. The following sections shall survive any termination of this Agreement: 2.c, 2.d, 2.e, 2.f, 4, 5, 6, 7, 8 and 11.a. 


