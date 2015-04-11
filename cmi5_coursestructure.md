CMI-5 Course Structure 
------------------------------------------------------------------------------------


**AICC DOCUMENT NUMBER:** CMI5-002  &nbsp;&nbsp; **Revision:** CURRENT WORKING DRAFT   
**THIS DOCUMENT IS CONTROLLED BY:** AICC CMI Subcommittee


# *WORKING DRAFT - NOT FOR IMPLEMENTATION*


---

>Caveats...
>
>Copyright &copy; 2012-2015 AICC, All rights reserved
>
>The information contained in this document has been assembled by the AICC as an informational resource. Neither the AICC nor any of its members assumes nor shall any of them have any responsibility for any use by anyone for any purpose of this document or of the data which it contains. All use of this document is subject to the terms of the license agreement contained within it.

---


# Table of Contents

[__Revision History__](#revhistory)

[__Contributors__](#contributors)

* [__1.0 Overview__](#overview)
  * [1.1 Scope](#scope)
  * [2.0 References](#references)
* [__3.0 Definitions__](#definitions)
  * [3.1 Abbreviations and acronyms](#acronyms)
* [__4.0 Conformance__](#conformance)
  * [4.1 Assignable Unit (AU)](#au_conformance)
  * [4.2 Learning Management Systems (LMS)](#lms_conformance)
* [__5.0 Conceptual Model: Informative__](#concept)
* [__6.0 LMS Requirements__](#lms_requirements)
  * [6.1 Course structure requirements](#course_structures)
* [__7.0 Course Structure Data Requirements__](#course_requirements)
  * [7.1 Course Structure Data Model](#course_structure_data_model)
    * [7.1.1 Course Level Meta Data](#course_level_meta_data)
    * [7.1.2 Block Meta Data](#block_meta_data)
    * [7.1.3 Objectives Meta Data](#objectives_meta_data)
    * [7.1.4 AU Meta Data](#au_meta_data)
  * [7.2 Course Structure XSD](#course_structure_xsd)
* [__8.0 Course Package__](#course_package)
* [__9.0 Bibliography__](#bibliography)

[__License Agreement__](#license_agreement)

------

<a name="revhistory"/>  
## Revision History
__0.1 Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__  

Converted existing working draft to markdown format from Microsoft Word. 
All previous work from 2012 discared


<a name="contributors"/> 
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

-------

<a name="overview"/> 
# 1.0 Overview


This specification describes the course structure interchange format for Learning Management Systems (LMS).  

<a name="scope"/> 
## 1.1 Scope

The scope of this specification is limited to following:
* LMS Course Structure Import/Export
* LMS course definition as it pertains to runtime data used by Learning Activities.  


<a name="references"/> 
# 2.0  References

The following referenced documents are indispensable for the application of this specification. 

RFC 2396, “Uniform Resource Identifiers (URI): Generic Syntax,” August 1998.<br/>

“Experience API”, current specification, ADL, 2012-2013<br/>
https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md

CMI5-001  – CMI-5 Runtime Environment, Version x.x, AICC, TBD  




<a name="definitions"/>  
# 3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user that manages the LMS and related systems. Such a user performs tasks such as learner enrollment, course structure definition, and report management.

* __Course__: A collection of assignable units, in a logical grouping, of learning content. A course is typically an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied sequence, representing a course.  

* __Experience API (XAPI)__: XAPI is a runtime data communication specification for learning content (AU) to send and receive data to an LRS.  The XAPI specification is referenced by this document is used to define the data transport and the data model. 

* __Internationalized Resource Identifier (IRI)__: A unique identifier per RFC 3987.  The IRI may be an IRL. All IRIs should be a full absolute IRIs including a scheme. Relative IRIs should not be used. IRLs should be defined within a domain controlled by the person creating the IRL.

* __Internationalized Resource Locator (IRL)__: Per the xAPI specification, an IRL is an IRI that when translated into a URI (per the IRI to URI rules), is a URL. Some communities of practice simply use URL even if they use IRIs, which isn't as technically correct within xAPI.

* __Learner__: The end user viewing/using the learning content (Learning Activity).

* __Assignable Unit (AU)__:  A learning content presentation launched from an LMS. The AU is the unit of tracking and management. The AU collects data on the learner and sends it to the LMS system.

* __Learning Management System (LMS)__: A computer system that may include the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners progress. LMS launching, reporting, and tracking roles are the focus of the CMI5 specification.  The LMS must have an LRS as part of its implementation.

* __Learning Records Store (LRS)__: As defined in the XAPI specification.  In this specification, the LMS must implement an LRS with additional requirements as specified in this document.

* __Must / Should / May__: Three levels of obligation with regards to conformance to the CMI-5 specification. A system that fails to implement a MUST (or a MUST NOT) requirement is non-conformant. Failing to meet a SHOULD requirement is not a violation of conformity, but goes against best practices. MAY indicates an option, to be decided by the developer with no consequences for conformity.
<BR />
<BR />


<a name="acronyms"/>  
## 3.1 Abbreviations and Acronyms

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


<a name="conformance"/>
# 4.0  Conformance

Conformance to this specification is defined in section. 

In this specification, “must” is to be interpreted as a requirement on an implementation; “must not” is to be interpreted as a prohibition.  
“Should” is to be interpreted as a recommendation for implementation; “should not” is to be interpreted as the converse of “should”.  
“May” is to be interpreted as a course of action that is permissible within the limits of the specification; “need not” indicates a course of action that is not required.
Uses of XAPI specification outside the scope this specification do not affect conformance with this specification.

<a name="au_conformance"/>
## 4.1 Courses

A course must be bundled with a course structure data that conform to all requirements listed in Section 7  
Course structure data must not implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  


<a name="lms_conformance"/>
## 4.2 Learning Management Systems (LMS)

LMS systems must conform to all requirements listed in Section 6 – LMS Requirements.  
The LMS must not implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  

<a name="concept"/>
# 5.0 Conceptual Model: Informative  

Synopsis of the CMI-5 model:
* An LMS imports a course structure.
* An LMS administrative user assigns a course to a learner.
* A learner authenticates with an LMS or related system.
* A learner launches an Assignable Unit (learning content) from the LMS or associated launching system, using an interface.
* The learning activity (AU) sends a message to the LMS requesting launch parameters and previous state information.
* Learner views the learning activity content and performs the learning. During this time the learning activity may request data from and store data to the LMS.
* The learner exits the learning activity.
* The learning activity reports final tracking data to the LMS and issues an exit message.
* Administrative users create and view reports of tracking data recorded by learning activities for individual learners.

Responsibilities of the Assignable Unit:
* Parse the parameters from the launching environment to determine where the LMS location is and initiate communication with the LMS.
* Acting as “client”, send and receive messages using the defined transport mechanism(s) and associated commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Send an “exit” message prior to terminating the learning activity’s execution.

Responsibilities of the LMS:
* Create and maintain course structures.
* Acting as a “server”, receive and reply to messages using the defined transport mechanism(s) and associated commands as prescribed in this specification.
* Format all data per defined data types and vocabularies defined in this specification.
* Launch the specified learning activity contained in courses, in the defined environment(s).

<a name="lms_requirements"/>
# 6.0 LMS Requirements

LMS systems must meet the following requirements to conform to this specification:  

1. The LMS must implement a means to import course structures as defined in section 6.1
2. The LMS must implement a means to export course structures as defined in section 6.1

<a name="course_structures"/>
## 6.1 Course structure requirements
The LMS must implement a means to create and maintain course structures.<br/>
1.	The LMS must implement the import of the course data structure defined in section 7. <br/>
2.	The LMS must implement the export of the course data structure defined in section 7. <br/>
3.	The LMS should provide a user interface to LMS administrative users to create and edit course structures internally.<br/>
4.	The LMS must be able support course structures with one or more AU’s.
<BR>
<BR>


<a name="course_requirements"/>
# 7.0 Course Structure Data Requirements  

<a name="course_structure_data_model"/>
## 7.1 Course Structure Data Model  

<a name="course_level_meta_data"/>
### 7.1.1 Course Level Meta-data  
 
The following meta data attribute and elements are at the course level and  describe the course instance as a whole

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: Yes<br />
        <strong>Data type</strong>: IRI</p>
    </td>
    <td width="811" valign="top"><p><strong>Description</strong>:<br />
      A globally unique IRI (Internationalized Resource Identifier per RFC 3987) for the course.  Used to explicitly identify the course instance.</p>
      <p><strong>Value space: </strong><br />
        Values defined by course designer<br />
        <strong>Sample value: </strong><br />
         &lt;course id="<span>http</span>://www.yoursite.com/identifiers/course/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/course&gt;<br/></p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: 
      Yes<br />
      <strong>Data type</strong>: 
      langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A descriptive title that identifies the course.<br />
      </p>
      <p><strong>Value space:</strong><br />
        Values defined by course designer<br />
      </p>
      <p><strong>Sample value</strong>: <br />
      

    &lt;title&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="en-US"&gt;This is a course title&lt;/langstring&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="es-MX"&gt;Se trata de un título del curso&lt;/langstring&gt;<br/>
    &lt;/title&gt;<br/>      
      
	</p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: Yes<br />
        <strong>Data type</strong>: langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A detailed  description of the course.</p>
      <p><strong>Value space:</strong><br />
        Values defined by course designer</p>
      <p><strong>Sample value: </strong><br />
    &lt;description&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="en-US"&gt;This is a course description&lt;/langstring&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="es-MX"&gt;Esta es una descripción del curso&lt;/langstring&gt;<br/>
    &lt;/description&gt;<br/>  
    
        </p>
    </td>
  </tr>
</table>



<a name="block_meta_data"/>
### 7.1.2 Block Meta Data

The data in this section is used for the block structures with group AU’s.  A Block consists of one or more AU’s. Blocks can also contain references to objectives and other Blocks.

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A descriptive title for the Block of AU’s<br />
      <strong>Value space:</strong><br />
      Values defined by course designer<br />
      <strong>Sample value:</strong> <br />
    &lt;title&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="en-US"&gt;This is the block title&lt;/langstring&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="es-MX"&gt;Este es el título del bloque&lt;/langstring&gt;<br/>
    &lt;/title&gt;<br/>            
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: 
      </strong>Yes<br />
      <strong>Data type:</strong> langstring </p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A detailed verbal description of what the Block contains.<br />
      <strong>Value space</strong>:<br />
      Values defined by course designer<br />
      <strong>Sample value: </strong><br />
      ```html
<description>
    <langstring lang="en-US">This is the block title</langstring><br/>
    <langstring lang="es-MX">Esta es la descripción de los bloques</langstring><br/>
</description>
    ```
    </td>
  </tr>
    <tr>
    <td colspan="2" valign="top"><h3>objectives</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: 
      </strong>No<br />
      <strong>Data type:</strong> objectiveReference </p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A listing of objectives referenced by this block.<br />
      <strong>Value space</strong>:<br />
      Values defined by course designer<br />
      <strong>Sample value: </strong><br />
    &lt;objectives&gt;<br/>
    &nbsp;&nbsp; &lt;objective idref="<span>http</span>://www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2"/&gt;<br/>
    &lt;/objectives&gt;<br/> 
    </td>  
  </tr>
</table>


<a name="objectives_meta_data"/>  
### 7.1.3 Objectives Meta Data   

The data in this section is used by Objectives. Objectives can be associated with a Block or with individual AU’s. 

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required: </strong>Yes<br />
        <strong>Data type:</strong> IRI</p>
    </td>
    <td width="792" valign="top"><p><strong>Description:</strong><br />
      A unique IRI for the learning objective<br />
      </p>
      <p><strong>Value space:</strong><br/>Values defined by the course developer</p>
    <p><strong>Sample value:</strong><br />
    &lt;objective id="<span>http</span>://www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2"&gt;&hellip;&lt;/objectiveId&gt;</p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type</strong>: langstring</p>
    </td>
    <td width="792" valign="top"><p><strong>Description</strong>:<br />
      A descriptive title for the learning objective</p>
      <p><strong>Value space:</strong><br />
        Values defined by course designer<br />
      </p>
      <p><strong>Sample value: </strong><br/>
    &lt;title&gt;<br/>
    &nbsp;&nbsp; &lt;langstring lang="en-US"&gt;This is the objective title&lt;/langstring&gt;<br/>
    &nbsp;&nbsp; &lt;langstring lang="es-MX"&gt;Este es el título del objetivo&lt;/langstring&gt;<br/>
    &lt;/title&gt;<br/> 
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type</strong>: langstring </p>
    </td>
    <td width="792" valign="top"><p><strong>Description:</strong><br />
      A detailed verbal description of the learning objective.<br />
      </p>
      <p><strong>Value space:</strong><br />
        Values defined by course designer<br />
        </p>
      <p><strong>Sample value: </strong><br/>
    &lt;description&gt;<br/>
    &nbsp;&nbsp; &lt;langstring lang="en-US"&gt;This is the objective description&lt;/langstring&gt;<br/>
    &nbsp;&nbsp; &lt;langstring lang="es-MX"&gt;Esta es la descripción objetiva&lt;/langstring&gt;<br/>
    &lt;/description&gt;<br/>      
      </p>
    </td>
  </tr>
</table>


<a name="au_meta_data"/>  
### 7.1.4 AU Meta Data  

The data in this section is used by the LMS to locate the AU and provide launch data. 
AU’s may also contain objectives.


<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: </strong> Yes<br />
        <strong>Data type: </strong> IRI</p></td>
    <td width="1471" valign="top"><p><strong>Description: </strong>A globally unique IRI that the AU uses to identify itself to the LMS in xAPI messages to the LMS.</p>
      <p><strong>Value space: </strong>Values defined by course designer</p>
      <p><strong>Sample value:</strong><br/>
      &lt;au id="<span>http</span>://www.yoursite.com/identifiers/activity/005430bf-b3ba-45e6-b47b-d629603d83d2"&lt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>launchMethod</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> string </p>
    </td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS when launching the AU (in a web-browser environment) to determine whether the AU requires its own window, or whether the LMS may choose the window context for the AU.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>A value of "OwnWindow" will require the LMS to launch the AU either in a new browser window, or the LMS may redirect the current window to the AU.</li>
        <li>A value of "AnyWindow" indicates that the AU does not care about the window context.  All browser window options are exceptable, such as in a Framset, in a New Window, a browser redirect, etc.</li>
      </ul>
      <p><strong>Value space: </strong>"OwnWindow", "AnyWindow"<br />
        <br />
      <strong>Sample value: </strong> <br/>
      &lt;au id="&hellip;" launchMethod="OwnWindow"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
    <tr>
    <td colspan="2" valign="top"><h3>masteryScore</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> string </p></td>
    <td valign="top"><p><strong>Description:</strong> A score used by the LMS to determine passing or failure of judged activity in the AU (if the AU has scoring).</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>The MasteryScore is passed to the AU at runtime by the LMS (as defined in the CMI5 Runtime Specification)</li>
        <li>If the AU has scoring, it will use the MasteryScore to detemine pass/fail (as defined in the CMI5 Runtime Specification)</li>
        <li>The mastery score is a scaled, decimal value between 0 and 1.</li>
        <li>If value of MasteryScore is an empty string (""), then a MasteryScore is not defined for the AU</li>
      </ul>
      <p><strong>Value space: </strong>Decimal number or empty string<br />
        <br />
      <strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" masteryScore="0.85"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>moveOn</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> string <br/>
        <strong>Default Value:</strong> "Not Applicable" </p></td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to determine if a AU has been sufficiently completed for the purposes determining overall course completion or determining if prequisites were met for other activites.. </p>
      <p><strong>moveOn Values are as follows:</strong></p>
      <ul>
        <li>moveOn Value = "Passed" : If the LMS receives a statement with the verb "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "Completed" : If the LMS receives a statement with the verb "Completed", then the LMS will consider the AU satisfied.<br />
          </li>
        <li>moveOn Value = "CompletedAndPassed" : If the LMS receives statements with the verbs "Completed" and "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "CompletedOrPassed" : : If the LMS receives a statements with either of the verbs "Completed" or "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "Not Applicable": The LMS will consider the AU satisfied.</li>
      </ul>
      <p><strong>Usage:</strong></p>
      <p>If all member AU's in a block are satisfied, then the block is considered satisfied for prerequisites and sequencing.<br/>If all member AU's and Blocks are satisfied, then the course is considered satisfied for prerequisites or credit in relation to other courses or curricula.</p>
      <p><strong>Value space:</strong></p>
      <blockquote>
        <p>"Passed"<br />
          "Completed"<br />
          "CompletedAndPassed"<br />
          "CompletedOrPassed"<br />
          "Not Applicable"</p>
      </blockquote>
      <p><strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" moveOn="Passed"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>authenticationMethod</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> string </p>
    </td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to specify which authentication method the AU must used to access the LMS's Learning Record Store.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>Based on the value of authenticationMethod, the LMS will place an  parameter in the AU launch interface to indicate to the AU which authentication method to use (as per the CMI-5 Runtime specification)</li>
        <li>authenticationMethod Value = "Basic" : If the LMS will indicate to the AU launch interface to use basic HTTP authentication and will pass and HTTP authentication token to the AU using the launch interface.</li>
        <li>authenticationMethod Value = "OAuth" : If the LMS will indicate to the AU launch interface to use  OAuth authentication..</li>
      </ul>
      <p><strong>Value space:</strong></p>
      <blockquote>
        <p>"Basic"<br />
        "OAuth"<br />
      </p>
      </blockquote>
      <p><strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" authenticationMethod="Basic"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>

  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required: </strong> Yes<br />
        <strong>Data type:</strong> langstring</p></td>
    <td valign="top"><p><strong>Description:</strong> A descriptive title for the AU<br />
        </p>
      <p><strong>Value space: </strong> Values defined by course designer<br />
      </p>
      <p><strong>Sample value: </strong><br/>

    &lt;title&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="en-US"&gt;This is an activity title.&lt;/langstring&gt;<br/>
    &nbsp;&nbsp;	&lt;langstring lang="es-MX"&gt;Este es un título de la actividad.&lt;/langstring&gt;<br/>
    &lt;/title&gt;<br/>

      </p>
    </td>
  </tr>

  <tr>
    <td colspan="2" valign="top"><h3>description</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: 
      </strong>Yes<br />
      <strong>Data type:</strong> string </p>
    </td>
    <td width="1471" valign="top"><p><strong>Description:</strong><br />
      A detailed description of the subject matter and learning activities covered by the AU.</p>
      <p><br />
        <strong>Value space:</strong><br />
        Values defined by AU designer<br />
        </p>
      <p><strong>Sample value:</strong><br/>
    &lt;description&gt;<br/>
    &nbsp;&nbsp; &lt;langstring lang="en-US"&gt;This is the AU description&lt;/langstring&gt;<br/>
    &nbsp;&nbsp; &lt;langstring lang="es-MX"&gt;Esta es la descripción de la AU&lt;/langstring&gt;<br/>
    &lt;/description&gt;<br/>   
      </p>
    </td>
  </tr>
    </tr>
    <tr>
    <td colspan="2" valign="top"><h3>objectives</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required: 
      </strong>No<br />
      <strong>Data type:</strong> objectiveReference </p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A listing of objectives referenced by this AU.<br />
      <strong>Value space</strong>:<br />
      Values defined by course designer<br />
      <strong>Sample value: </strong><br />
    &lt;objectives&gt;<br/>
    &nbsp;&nbsp; &lt;objective idref="<span>http</span>://www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2"/&gt;<br/>
    &lt;/objectives&gt;<br/> 
    </td>  
  </tr>  
  <tr>
    <td colspan="2" valign="top"><h3>url</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type: </strong> string</p>
    </td>
    <td width="1471" valign="top"><p><strong>Description:</strong><br />
      A relative or fully qualified URL that references the launch point of the AU.<br/>&nbsp;<br/>
      To accomodate "non-browser" applications, an application specific protocol may be used in the url:<br/>
      &lt;application&gt;://&lt;URL to content&gt;
      
      Regardless of the value of &lt;application&gt;, the remaining portion of the URL must conform to HTTP/S conventions, such as named value pair parameters.<br/>&nbsp;<br/>If the url includes a query string, the values from that query string must be merged with the CMI-5 parameters at launch time (see section 8.1.1 of the CMI-5 Runtime Environment).
      </p>
      <p><strong>Value space:</strong>Determined by AU developer</p>
      <p><strong>Sample value:</strong><br/>
      &lt;url&gt;<br/>
      <span>http</span>://wwww.mycourses.com/courseX.html<br/>
      &lt;/url&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>launchParameters</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type: </strong>string </p>
    </td>
    <td width="1471" valign="top"><p><strong>Description:</strong><br />
      Static launch parameters defined by the AU designer.  The LMS is required to store this data and provide to the AU if    requested by the AU during runtime.<br />
      </p>
      <p><strong>Value space:</strong><br />
        Values defined by AU designer</p>
      <p><br />
        <strong>Sample value: </strong> TBD</p>
    </td>
  </tr>  
  <tr>
    <td colspan="2" valign="top"><h3>entitlementKey</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> string </p></td>
    <td valign="top"><p><strong>Description:</strong><br />
        Data used by the AU to determine if the launching LMS system is entitled to use the AU. The AU should use this data in combination with other data provided from the LMS to determine entitlement.<br />
    </p>
      <p><strong>Value space: </strong>Values defined by AU content provider.<br />
        <br />
        <strong>Sample value:</strong><br/>
        &lt;entitlementKey&gt;<br/>
        xyz-123-9999<br/>
        &lt;/entitlementKey&gt;
        </p>
    </td>
  </tr>
</table>

<a name="course_structure_xsd"/>  
## 7.2 Course Structure XSD 

The following is the XML Schema for a course structure file.  
All course structures created for LMS import and created by the LMS for export must conform to this XSD and be named cmi5.xml.

```XML
<xs:schema xmlns="http://aicc.org/CMI5/CourseStructure.xsd"
           xmlns:xs="http://www.w3.org/2001/XMLSchema"
           targetNamespace="http://aicc.org/CMI5/CourseStructure.xsd" elementFormDefault="qualified"
           id="CMI5CourseStructure">
    <xs:element name="courseStructure" type="courseType"/>
    <xs:complexType name="courseType">
        <xs:all>
            <xs:element name="course">
                <xs:complexType>
                    <xs:all>
                        <xs:element name="title" type="textType"/>
                        <xs:element name="description" type="textType"/>
                    </xs:all>
                    <xs:attribute name="id" type="xs:anyURI" use="required"/>
                </xs:complexType>
            </xs:element>
            <xs:element name="block" type="blockType"/>
            <xs:element name="objectives" type="objectivesType" minOccurs="0"/>
        </xs:all>
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
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="auType">
        <xs:all>
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
            <xs:element name="launchParameters"/>
            <xs:element name="entitlementKey"/>
        </xs:all>
        <xs:attribute name="id" type="xs:anyURI" use="required"/>
        <xs:attribute name="moveOn" default="Not Applicable">
            <xs:simpleType>
                <xs:restriction base="xs:string">
                    <xs:enumeration value="Not Applicable"/>
                    <xs:enumeration value="Passed"/>
                    <xs:enumeration value="Completed"/>
                    <xs:enumeration value="Completed And Passed"/>
                    <xs:enumeration value="Completed Or Passed"/>
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
                    <xs:enumeration value="OAuth"/>
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
        </xs:sequence>
    </xs:complexType>

    <xs:complexType name="referencesObjectivesType">
        <xs:sequence>
            <xs:element name="objective" maxOccurs="unbounded">
                <xs:complexType>
                    <xs:attribute name="idref" type="xs:anyURI"></xs:attribute>
                </xs:complexType>
            </xs:element>
        </xs:sequence>
    </xs:complexType>
    <xs:complexType name="textType">
        <xs:complexContent>
            <xs:extension base="xs:string">
                <xs:sequence>
                    <xs:element name="langstring" maxOccurs="unbounded" minOccurs="0">
                        <xs:complexType>
                            <xs:complexContent>
                                <xs:extension base="xs:string">
                                    <xs:attribute name="lang" type="xs:language"/>
                                </xs:extension>
                            </xs:complexContent>
                        </xs:complexType>
                    </xs:element>
                </xs:sequence>
            </xs:extension>
        </xs:complexContent>
    </xs:complexType>
</xs:schema>
```

<a name="course_package"/>
# 8.0 Course Package
For the course import and export defined in section 6.1, the LMS must support all of the following formats:
<ul><li>Zip32</li>
<li>Zip64</li>
<li>A course structure XML file</li>
</ul>
## 8.1 Course Packages in ZIP format
The two ZIP file formats must follow the specification defined at https://www.pkware.com/support/zip-app-note.  When the ZIP file is used to package the course, it may contain media associated with the course AU's.  
<ul><li>Any media included in a ZIP course package must use relative URL references in the Course Structure XML.</li>
<li>Any media not included in a ZIP course package must use fully qualified URL references in the Course Strucutre XML</li>
<li>A ZIP course package may contain a mix of fully qualified and relavie URL's,provided the rules above are followed.</li>
</ul>
## 8.2 Course Structure XML without a ZIP file package
When a course structure XML file is provided without a ZIP file package, all URL references must be fully qualified.

<a name="bibliography"/> 
# 9.0 Bibliography

[1]  AICC CMI001, CMI Guidelines For Interoperability, Version 4.0. 

[2]  SCORM – http://www.adlnet.gov/capabilities/scorm 

[3]  MIME Types – http://www.iana.org/assignments/media-types/index.html  

-------

<a name="license_agreement"/> 
# License Agreement

THE WORK (AS DEFINED HEREIN) ACCOMPANYING THIS LICENSE AGREEMENT ("AGREEMENT") IS PROVIDED BY THE AICC, A NON-PROFIT CORPORATION ORGANIZED UNDER THE LAWS OF Idaho (“LICENSOR”), TO YOU (“YOU” OR “LICENSEE”) ONLY UNDER THE TERMS AND CONDITIONS OF THIS AGREEMENT. ANY USE, REPRODUCTION, DISTRIBUTION OR MODIFICATION OF THE WORK BY YOU CONSTITUTES YOUR ACCEPTANCE OF THIS AGREEMENT. BY OBTAINING, USING, DISTRIBUTING, REPRODUCING AND/OR MODIFYING THE WORK, YOU AGREE THAT YOU HAVE READ, UNDERSTOOD, AND WILL COMPLY WITH THE FOLLOWING TERMS AND CONDITIONS.

#### 1. DEFINITIONS

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

#### 2. LICENSE GRANT AND RESTRICTIONS

a. Subject to the terms of this Agreement, Licensor hereby grants to Licensee a non-exclusive, worldwide, royalty-free license in any copyrights and/or Necessary Claims in the Work such that Licensee may view, use, reproduce, publicly display, distribute and prepare Derivative Works of the Work. 

b. Licensee hereby grants to Licensor and all Other Licensees a non-exclusive, worldwide, royalty- free license in any copyrights and/or Necessary Claims in which Licensee asserts ownership, such that Licensor and all Other Licensees may view, use, reproduce, publicly display, distribute and prepare Derivative Works of any Contributions that Licensee may have made to the Work. Licensee agrees that it will not transfer its ownership of any copyrights or patents having Necessary Claims for the purpose of circumventing this Section 2.b. Licensee shall not attempt under its copyrights, Necessary Claims or otherwise to restrict any Other Licensee from exercising that Other Licensee’s rights granted to it by Licensor under an agreement with essentially the same terms and conditions as this Agreement. 

c. To the extent that a Licensee reproduces or distributes copies of the Work, portions thereof or any Derivative Work in any medium, with or without modifications, such Licensee shall give a copy of this Agreement to any recipients of the Work. 

d. Licensee hereunder expressly agrees to include the following notice on ALL copies of the Work, portions thereof or Derivative Works: "Copyright © The AICC. All Rights Reserved.  http://www.aicc.org” 

e. Licensee agrees to include the following notice in all Derivative Works: “This product implements and complies with the Version CMI-5 [or other version as applicable] AICC Specifications as published by the AICC at http://www.AICC.org”. 

f. Licensee may not facilitate or assist any Learning Technology Standards Organization other than Licensor in co-opting, copying, distributing, publishing or using the Work without prior written approval of Licensor. Licensee may not create any Derivative Work for ownership by, presentation by, distributing by, publishing by or attribution to any Standards Organization or similar entity other than Licensor, unless specifically approved in writing by Licensor. 


#### 3. GRANT OF RIGHTS BY CONTRIBUTORS
Subject to the terms of this Agreement, a Contributor hereby grants to Licensor a non-exclusive, worldwide, royalty-free license under all intellectual property rights to make, use, sell, offer to sell, import and otherwise transfer any Contribution of such Contributor. This license shall apply to the combination of the Contribution and the Work.

#### 4. TRADEMARKS
This Agreement does not grant permission to use the trade names, trademarks, service marks, or product names of the Licensor, except as required for reasonable and customary use in describing the origin of the Work and reproducing the content of the copyright notice.

#### 5. WARRANTY
THE WORK ACCOMPANYING THIS AGREEMENT IS PROVIDED "AS IS" WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, AND THE HOLDERS OF ANY COPYRIGHT, PATENT OR OTHER INTELLECTUAL PROPERTY RIGHT THEREIN MAKE NO REPRESENTATIONS OR WARRANTIES, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO, WARRANTIES OF MERCHANTABILITY OR FITNESS FOR ANY PARTICULAR PURPOSE OR THAT THE USE OF THE SOFTWARE OR DOCUMENTATION WILL NOT INFRINGE ANY THIRD PARTY PATENTS, COPYRIGHTS, TRADEMARKS OR OTHER RIGHTS. You are solely responsible for determining the appropriateness of using or redistributing the Work and assume any risks associated with your exercise of permissions under this Agreement.

#### 6. LIMITATION OF LIABILITY
IN NO EVENT AND UNDER NO LEGAL THEORY, WHETHER IN TORT (INCLUDING NEGLIGENCE), CONTRACT, OR OTHERWISE, UNLESS REQUIRED BY APPLICABLE LAW (SUCH AS DELIBERATE AND GROSSLY NEGLIGENT ACTS) OR AGREED TO IN WRITING, SHALL LICENSOR OR ANY CONTRIBUTOR BE LIABLE TO YOU FOR ANY DAMAGES WHATSOEVER, INCLUDING ANY DIRECT, INDIRECT, EXEMPLARY, PUNITIVE, SPECIAL, INCIDENTAL, OR CONSEQUENTIAL DAMAGES OF ANY CHARACTER ARISING AS A RESULT OF THIS AGREEMENT OR OUT OF THE USE OR INABILITY TO USE THE WORK (INCLUDING BUT NOT LIMITED TO DAMAGES FOR LOSS OF PROFITS, GOODWILL, WORK STOPPAGE, COMPUTER FAILURE OR MALFUNCTION, OR ANY AND ALL OTHER COMMERCIAL DAMAGES OR LOSSES), EVEN IF LICENSOR OR SUCH CONTRIBUTOR HAS BEEN ADVISED OF THE POSSIBILITY OF SUCH DAMAGES.

#### 7. COMMERCIAL DISTRIBUTION
If you include the Work or any Derivative Work in a commercial product offering, you hereby agree to defend and indemnify Licensor and every Contributor (the "Indemnitees ") against any losses, damages and costs (collectively "Losses") arising from claims, lawsuits and other legal actions brought by a third party against the Indemnitees, to the extent caused by your acts or omissions in connection with your distribution of the Work in a commercial product offering. Indemnitees shall: a) promptly notify you in writing of such claim, and b) allow you to control, and cooperate with you in, the defense and any related settlement negotiations. Any Indemnitee may participate in any such claim at its own expense.

#### 8. PROPRIETARY RIGHTS
Regardless of who owns the media on which the Work resides or is distributed, the Work expressly remains the intellectual property of Licensor and/or the Contributors, and Licensor and/or the Contributors retain all right, title and interest in and to the Work and all copies thereof. Licensor expressly reserves all rights not specifically granted in this Agreement.

#### 9. TERMINATION
Licensor reserves the right to terminate this Agreement at any time if you are in breach of any of its terms and conditions, copyright laws, or any other applicable laws or regulations. In such a case, the rights granted to you under Section 2 of this Agreement shall be automatically terminated, and you shall be obliged to cease using the Work and immediately destroy any copies of the Work and all backup copies.
Termination is not the sole remedy under this Agreement and, whether or not termination is effected, all other remedies, legal and equitable, will remain available.

#### 10. UPGRADES
Licensor is under no obligation under this Agreement to provide any fixes, revisions, upgrades or future versions of the Work to you or to any other party. Should you ever obtain an upgrade of this Work, the terms and conditions of this Agreement shall also apply to the upgrade. The Work is subject to change without notice.

#### 11. GENERAL

a. Independent Contractors. The parties and their respective personnel are and shall be independent contractors and neither party by virtue of this Agreement shall have any right, power or authority to act or create any obligation, express or implied, on behalf of the other party. 

b. Binding Nature. Subject to all other provisions herein contained, this Agreement shall be binding on the parties and their successors and permitted assigns. 

c. Assignment. Licensee may not assign or otherwise transfer this Agreement, or any part hereof, nor delegate any of its duties hereunder, whether by operation of law or otherwise, to any third party. Licensee may delegate specific duties and obligations hereunder to an Affiliate, however, in the event that Licensee wishes to assign or transfer this entire Agreement to an Affiliate, Licensee may do so only via a novation whereby all parties agree to such novation in writing and the Affiliate in effect becomes the Licensee hereunder. 

d. Severability. If any provision of this Agreement is found by a court of competent jurisdiction to be invalid or unenforceable, such invalidity or unenforceability shall not invalidate or render unenforceable any other part of this Agreement, but the Agreement shall be construed as not containing the particular provision or provisions held to be invalid or unenforceable. 

e. Waiver. No delay or omission by either party hereto to exercise any right occurring upon any noncompliance or default by the other party with respect to any of the terms of this Agreement shall impair any such right or power or be construed to be a waiver thereof. A waiver by either of the parties hereto of any of the covenants, conditions or agreements to be performed by the other shall not be construed to be a waiver of any succeeding breach thereof or of any covenant, condition or agreement herein contained. 

f. Governing Law; Exclusive Jurisdiction. This Agreement, and all the rights and duties of the parties arising from or relating in any way to the subject matter of this Agreement or the transaction(s) contemplated by it, shall be governed by, construed and enforced in accordance with the law of the State of Idaho (excluding any conflict of laws provisions of the State of Idaho that would refer to and apply the substantive laws of another jurisdiction). Any suit or proceeding relating to this Agreement shall be brought in the state courts of Idaho. Each of the parties consents to the exclusive personal jurisdiction and venue of the state courts located in Idaho. 

g. No Construction Against Drafter. The parties agree that any principle of construction or rule of law that provides that an agreement shall be construed against the drafter of the agreement in the event of any inconsistency or ambiguity in such agreement shall not apply to the terms and conditions of this Agreement. 

h. Entire Agreement; Modification. This Agreement sets forth the entire, final and exclusive agreement between the parties as to the subject matter hereof and supersedes all prior and contemporaneous agreements, understandings, negotiations and discussions, whether oral or written, between the parties. The parties expressly disclaim the right to claim the enforceability or effectiveness of any other amendments that are based on course of dealing, waiver, reliance, estoppel or other similar legal theory. The parties expressly disclaim the right to enforce any rule of law that is contrary to the terms of this section. 
	
i. Survival. The following sections shall survive any termination of this Agreement: 2.c, 2.d, 2.e, 2.f, 4, 5, 6, 7, 8 and 11.a. 



-------
