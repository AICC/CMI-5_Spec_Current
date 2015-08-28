﻿cmi5 Course Structure 
------------------------------------------------------------------------------------
>
>Copyright &copy; 2012-2015 ADL, All rights reserved



# Table of Contents

[__Disclaimer__](#disclaimer)

[__Revision History__](#revhistory)

[__Contributors__](#contributors)

* [__1.0 Overview__](#overview)
  * [1.1 Scope](#scope)
  * [2.0 References](#references)
* [__3.0 Definitions__](#definitions)
  * [3.1 Abbreviations and Acronyms](#acronyms)
* [__4.0 Conformance__](#conformance)
  * [4.1 Assignable Unit (AU)](#au_conformance)
  * [4.2 Learning Management Systems (LMS)](#lms_conformance)
* [__5.0 Conceptual Model: Informative__](#concept)
* [__6.0 LMS Requirements__](#lms_requirements)
  * [6.1 Course Structure Requirements](#course_structures)
* [__7.0 Course Structure Data Requirements__](#course_requirements)
  * [7.1 Course Structure Data Model](#course_structure_data_model)
    * [7.1.1 Course Level Metadata](#course_level_meta_data)
    * [7.1.2 Block Metadata](#block_meta_data)
    * [7.1.3 Objectives Metadata](#objectives_meta_data)
    * [7.1.4 AU Metadata](#au_meta_data)
    * [7.1.5 Vendor Specific Metadata](#vendor_meta_data)
  * [7.2 Course Structure XSD](#course_structure_xsd)
* [__8.0 Course Package__](#course_package)
* [__9.0 Course Structure Examples__](#course_structure_examples)
  * [9.1 Simple](#course_structure_examples_simple)
  * [9.2 Complex](#course_structure_examples_complex)
* [__10.0 Bibliography__](#bibliography)
  
[__License Agreement__](#license_agreement)

------

<a name="dislaimer"/>  
## Disclaimer
PLEASE NOTE: This is a developer release and is subject to change.

<a name="revhistory"/>  
## Revision History
__Sandstone - 1st Edition (May 15, 2015):__

* Developer release

__0.1 Convert Working Draft to Markdown in GitHub (Feb 20, 2013):__  

* Converted existing working draft to markdown format from Microsoft Word. All previous work from 2012 discarded.



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
| Andrew Downes        | Rustici Software                       |
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
| David Pesce          | Exputo Inc.                            |
| Henry Ryng           | inXsol					|
| Chris Handorf        | Pearson                                |
| Jamie Burns          | Virtual College                        |
-------

<a name="overview"/> 
# 1.0 Overview


This specification describes the course structure interchange format for Learning Management Systems (LMS).  

<a name="scope"/> 
## 1.1 Scope

The scope of this specification is limited to the following:
* LMS Course Structure Import/Export
* LMS Course Definition as it pertains to runtime data used by AUs.  


<a name="references"/> 
# 2.0  References

The following referenced documents are indispensable for the application of this specification. 

* RFC 2396, "Uniform Resource Identifiers (URI): Generic Syntax," August 1998.<br/>
https://www.ietf.org/rfc/rfc2396.txt
* "Experience API", current specification, ADL, 2012-2013<br/>
https://github.com/adlnet/xAPI-Spec/blob/master/xAPI.md
* cmi5 Runtime Environment, Sandstone 1st Edition<br/>
<https://github.com/AICC/CMI-5_Spec_Current/blob/master/cmi5_runtime.md>




<a name="definitions"/>  
# 3.0 Definitions  


For purposes of this specification, the following terms and definitions apply: 

* __Administrator__: The administrative user who manages the LMS and related systems. This user performs tasks such as learner enrollment, course structure definition, and report management.

* __Assignable Unit (AU)__:  A learning content presentation launched from an LMS. The AU is the unit of tracking and management. The AU collects data on the learner and sends it to the LMS.

* __Course__: A collection of assignable units, in a logical grouping, of learning content. A course is typically an internal data structure. Courses are often assigned to learners and tracked by the LMS.

* __Course Structure__: A list of assignable units and launch parameters, with an implied sequence, representing a course.  

* __Experience API (xAPI)__: A runtime data communication specification for learning content (AU) to send and receive data to a Learning Record Store (LRS).  The xAPI specification is referenced by this document is used to define the data transport and the data model. 

* __Internationalized Resource Identifier (IRI)__: A unique identifier according to RFC 3987.  The IRI may be an IRL. All IRIs SHOULD be a full, absolute IRI that includes a scheme. Relative IRIs SHOULD NOT be used. IRLs SHOULD be defined within a domain controlled by the person creating the IRL.

* __Internationalized Resource Locator (IRL)__: According to the xAPI specification, an IRL is an IRI that, when translated into a URI (according to the IRI to URI rules), is a URL. Some communities of practice simply use "URL" even if they use IRIs, which is not as technically correct within the xAPI.

* __Learner__: The end user viewing/using the learning content (AUs).

* __Learning Management System (LMS)__: A computer system that may include the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners progress. LMS launching, reporting, and tracking roles are the focus of the cmi5 specification. The LMS MUST have an LRS as part of its implementation.

* __Learning Records Store (LRS)__: Defined in the xAPI specification. In this specification, the LMS MUST implement an LRS with the additional requirements specified in this document.

* __MUST / SHOULD / MAY__: The three levels of obligation with regards to conformance to the cmi5 specification. A system that fails to implement a MUST (or a MUST NOT) requirement is not in conformance. Failing to meet a SHOULD requirement is not a violation of conformity, but it goes against best practices. MAY indicates an option, which is to be decided by the developer, with no consequences for lack of conformity.
<BR />
<BR />


<a name="acronyms"/>  
## 3.1 Abbreviations and Acronyms

__ADL__: Advanced Distributed Learning  
__AICC__: Aviation Industry Computer-Based Training Committee  
__API__: Application Programming Interface  
__LMS__: Learning Management System  
__LRS__: Learning Record Store  
__PII__: Personally Identifiable Information  
__URI__: Uniform Resource Identifier  
__URL__: Uniform Resource Locator  
__URN__: Uniform Resource Name  
__XAPI__: Experience API  


<a name="conformance"/>
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

<a name="au_conformance"/>
## 4.1 Courses

A course MUST be bundled with course structure data that conform to all requirements listed in Section 7.  
Course structure data MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  


<a name="lms_conformance"/>
## 4.2 Learning Management Systems (LMS)

The LMS MUST conform to all requirements listed in Section 6 – LMS Requirements.  
The LMS MUST NOT implement any features or functionality (optional or mandatory) described in this specification in a non-conforming manner.  

<a name="concept"/>
# 5.0 Conceptual Model: Informative  

Synopsis of the cmi5 model:
* An LMS imports a course structure, which MUST contain one or more AUs.
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

<a name="lms_requirements"/>
# 6.0 LMS Requirements

The LMS MUST meet the following requirements to conform to this specification:  

* The LMS MUST implement an LRS as defined in the xAPI specification.
* The LMS MUST support Course Structures as defined in cmi5 Course Structure.
* The LMS MUST implement additional "State API" requirements to initialize the AU state as defined in Section 10.
* The LMS MUST implement the runtime launch interface as defined in Section 8.0 – Content Launch Mechanisms.
* The LMS MUST implement additional xAPI "Statement API" requirements as defined in Section 9.
* The LMS MUST implement additional xAPI "Agent Profile API" requirements as defined in Section 11.
* The LMS MUST implement a means to import course structures as defined in Section 6.1.
* The LMS SHOULD implement a means to export course structures as defined in Section 6.1.

<a name="course_structures"/>
## 6.1 Course structure requirements
* The LMS SHOULD implement a means to create and maintain course structures.<br/>
* The LMS MUST implement the import of the Course Structure defined in Section 7. <br/>
* The LMS SHOULD implement the export of the course data structure defined in Section 7. <br/>
* The LMS SHOULD provide a user interface to the LMS administrative users to create and edit course structures internally.<br/>
* The LMS MUST support course structures containing more than 1000 AUs.
* The LMS MUST support course structures conforming to the XSD schema defined in Section 7.2.

<BR>
<BR>


<a name="course_requirements"/>
# 7.0 Course Structure Data Requirements  

<a name="course_structure_data_model"/>
## 7.1 Course Structure Data Model  

<a name="course_level_meta_data"/>
### 7.1.1 Course Level Metadata  
 
The following metadata attributes and elements are at the course level and  describe the course instance as a whole.

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: Yes<br />
        <strong>Data type</strong>: IRI</p>
    </td>
    <td width="811" valign="top"><p><strong>Description</strong>:<br />
      A globally unique IRI (see RFC 3987) for the course.  Used to explicitly identify the course instance.</p>
      <p><strong>Value space: </strong><br />
        Values are defined by the course designer.<br />
        <strong>Sample value: </strong><br />
         &lt;course id="http&#58;//www.yoursite.com/identifiers/course/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/course&gt;<br/></p>
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
        Values are defined by the course designer.<br />
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
        Values are defined by the course designer.</p>
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
### 7.1.2 Block Metadata

The data in this section are used for the block structures with group AUs.  A Block consists of one or more AUs. Blocks can also contain references to objectives and other Blocks.

<table border="1" cellspacing="0" cellpadding="0">
   <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: </strong> Yes<br />
        <strong>Data type: </strong> IRI</p></td>
    <td width="1471" valign="top"><p><strong>Description: </strong>A globally unique IRI to identify the Block in xAPI messages made by the LMS.</p>
      <p><strong>Value space: </strong>Values defined by course designer</p>
      <p><strong>Sample value:</strong><br/>
      &lt;block id="http&#58;//www.yoursite.com/identifiers/aublock/005430bf-b3ba-45e6-b47b-d629603d83d8" &gt; &hellip; &lt;/block&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td width="164" valign="top"><p><strong>Required:</strong> Yes<br />
        <strong>Data type:</strong> langstring</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      A descriptive title for the Block of AUs<br />
      <strong>Value space:</strong><br />
      Values are defined by the course designer.<br />
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
      Values are defined by the course designer.<br />
      <strong>Sample value: </strong><br />
&lt;description&gt;<br />
&nbsp;&nbsp;    &lt;langstring lang="en-US"&gt;This is the block description&lt;/langstring&gt;<br/>
&nbsp;&nbsp;    &lt;langstring lang="es-MX"&gt;Esta es la descripción de los bloques&lt;/langstring&gt;<br/>
&lt;/description&gt;<br />
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
      Values are defined by the course designer.<br />
      <strong>Sample value: </strong><br />
    &lt;objectives&gt;<br/>
    &nbsp;&nbsp; &lt;objective idref="http&#58;//www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" /&gt;<br/>
    &lt;/objectives&gt;<br/> 
    </td>  
  </tr>
</table>


<a name="objectives_meta_data"/>  
### 7.1.3 Objectives Metadata   

The data in this section are used by the Objectives. Objectives can be associated with a Block or with individual AUs. 

<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="183" valign="top"><p><strong>Required: </strong>Yes<br />
        <strong>Data type:</strong> IRI</p>
    </td>
    <td width="792" valign="top"><p><strong>Description:</strong><br />
      A unique IRI for the learning objective.<br />
      </p>
      <p><strong>Value space:</strong><br/>Values are defined by the course designer.</p>
    <p><strong>Sample value:</strong><br />
    &lt;objective id="http&#58;//www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt;&hellip;&lt;/objective&gt;</p>
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
        Values are defined by the course designer.<br />
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
        Values are defined by the course designer.<br />
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
### 7.1.4 AU Metadata  

The data in this section are used by the LMS to locate the AU and provide launch data. AUs may also contain objectives.


<table border="1" cellspacing="0" cellpadding="0">
  <tr>
    <td colspan="2" valign="top"><h3>id</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required: </strong> Yes<br />
        <strong>Data type: </strong> IRI</p>
    </td>
    <td width="1471" valign="top"><p><strong>Description: </strong>A globally unique IRI that the AU uses to identify itself to the LMS in xAPI messages to the LMS.</p>
      <p><strong>Value space: </strong>Values are defined by the course designer.</p>
      <p><strong>Sample value:</strong><br/>
      &lt;au id="http&#58;//www.yoursite.com/identifiers/activity/005430bf-b3ba-45e6-b47b-d629603d83d2" &gt; &hellip; &lt;/au&gt;
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
        <li>A value of "AnyWindow" indicates that the AU does not care about the window context.  All browser window options are acceptable, such as in a Frameset, in a New Window, a browser redirect, etc.</li>
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
    <td valign="top"><p><strong>Required:</strong> No<br />
        <strong>Data type:</strong> decimal </p></td>
    <td valign="top"><p><strong>Description:</strong> A score used by the LMS to determine passing or failure of judged activity in the AU (if the AU has scoring).</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>The masteryScore is passed to the AU at runtime by the LMS (as defined in the cmi5 Runtime Specification).</li>
        <li>If the AU has scoring, it will use the Masteryscore to determine pass/fail (as defined in the cmi5 Runtime Specification)</li>
        <li>The masteryScore is a scaled, decimal value between 0 and 1.</li>
      </ul>
      <p><strong>Value space: </strong>Decimal number.<br />
        <br />
      <strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" masteryScore="0.85"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
    <tr>
    <td colspan="2" valign="top"><h3>passIsFinal</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br />
        <strong>Data type:</strong> boolean<br /><strong>Default value:</strong> true </p></td>
    <td valign="top"><p><strong>Description:</strong> If true, the content MUST NOT send any "Passed" or "Failed" statements after sending a "Passed" statement.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>The value of passIsFinal is passed to the AU at runtime by the LMS (as defined in the cmi5 Runtime Specification).</li>
        <li>The AU will use this value to determine if it MUST NOT send "Passed" or "Failed" statements after sending a "Passed" statement.</li>
      </ul>
        <br />
      <strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" passIsFinal="true"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>moveOn</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br />
        <strong>Data type:</strong> string <br/>
        <strong>Default Value:</strong> "NotApplicable" </p></td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to determine if an AU has been sufficiently completed for the purposes of determining overall course completion or determining if prerequisites were met for other activities.. </p>
      <p><strong>moveOn Values are as follows:</strong></p>
      <ul>
        <li>moveOn Value = "Passed" : If the LMS receives a statement with the verb "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "Completed" : If the LMS receives a statement with the verb "Completed", then the LMS will consider the AU satisfied.<br />
          </li>
        <li>moveOn Value = "CompletedAndPassed" : If the LMS receives statements with the verbs "Completed" and "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "CompletedOrPassed" : If the LMS receives a statements with either of the verbs "Completed" or "Passed", then the LMS will consider the AU satisfied.</li>
        <li>moveOn Value = "NotApplicable": The LMS will consider the AU satisfied.</li>
      </ul>
      <p><strong>Usage:</strong></p>
      <p>If all member AUs in a block are satisfied, then the block is considered satisfied for prerequisites and sequencing.<br/>If all member AUs and Blocks are satisfied, then the course is considered satisfied for prerequisites or credit in relation to other courses or curricula.</p>
      <p><strong>Value space:</strong></p>
      <blockquote>
        <p>"Passed"<br />
          "Completed"<br />
          "CompletedAndPassed"<br />
          "CompletedOrPassed"<br />
          "NotApplicable"</p>
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
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to specify which authentication method the AU MUST be used to access the LMS's Learning Record Store.</p>
      <p><strong>Usage: </strong></p>
      <ul>
        <li>Based on the value of authenticationMethod, the LMS will place a parameter in the AU launch interface to indicate to the AU which authentication method to use (in accordance with the cmi5 Runtime Specification)</li>
        <li>authenticationMethod Value = "Basic" : If the LMS indicates to the AU launch interface to use basic HTTP authentication and passes an HTTP authentication token to the AU using the launch interface. This is currently the only option.  Future versions of this specification may add other authentication options.</li>
      </ul>
      <p><strong>Value space:</strong></p>
      <blockquote>
        <p>"Basic"<br />
      </p>
      </blockquote>
      <p><strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" authenticationMethod="Basic"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>activityType</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br />
        <strong>Data type:</strong> IRI<br /><strong>Default value:</strong> <em>None</em> </p></td>
    <td valign="top"><p><strong>Description:</strong> Used by the LMS to determine the activity type of the AU before a first start to indicate this type to the user.</p>
      <strong>Sample value: </strong><br/>
      &lt;au id="&hellip;" activityType="http://adlnet.gov/expapi/activities/media"&gt; &hellip; &lt;/au&gt;
      </p>
    </td>
  </tr>

  <tr>
    <td colspan="2" valign="top"><h3>title</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required: </strong> Yes<br />
        <strong>Data type:</strong> langstring</p></td>
    <td valign="top"><p><strong>Description:</strong> A descriptive title for the AU.<br />
        </p>
      <p><strong>Value space: </strong> Values are defined by the course designer.<br />
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
        Values are defined by the course designer.<br />
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
     Values are defined by the course designer.<br />
      <strong>Sample value: </strong><br />
    &lt;objectives&gt;<br/>
    &nbsp;&nbsp; &lt;objective idref="http&#58;//www.yoursite.com/identifiers/objective/005430bf-b3ba-45e6-b47b-d629603d83d2" /&gt;<br/>
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
    <ul>
      	<li>A relative or fully qualified URL that references the launch point of the AU.</li>
      	<li>To accommodate "non-browser" applications, an application specific protocol may be used in the url:<br/>
      &lt;application&gt;://&lt;URL to content&gt;</li>
      	<li>Regardless of the value of &lt;application&gt;, the remaining portion of the URL MUST conform to HTTP/S conventions, such as named value pair parameters.</li>
      	<li>If the url includes a query string, the values from that query string MUST be merged with the cmi5 parameters at launch time (see Section 8.1.1 of the cmi5 Runtime Environment).</li>
     </ul>
      <p><strong>Value space:</strong>Values are determined by the course designer.</p>
      <p><strong>Sample value:</strong><br/>
      &lt;url&gt;<br/>
      http://wwww.mycourses.com/courseX.html<br/>
      &lt;/url&gt;
      </p>
    </td>
  </tr>
  <tr>
    <td colspan="2" valign="top"><h3>launchParameters</h3></td>
  </tr>
  <tr>
    <td width="160" valign="top"><p><strong>Required:</strong> No<br />
        <strong>Data type: </strong>string </p>
    </td>
    <td width="1471" valign="top"><p><strong>Description:</strong><br />
      Static launch parameters defined by the course designer.  The LMS is required to store this data and provide it to the AU if    requested by the AU during runtime.<br />
      </p>
      <p><strong>Value space:</strong><br />
        Values are defined by the course designer.</p>
      <p><br />
        <strong>Sample value:</strong><br/>
        &lt;launchParameters&gt;<br/>
        {"param1": "Lorem ipsum dolor sit amet", "param2": [1,2,3,4,5],"param3": {"a": 1,"b": 2}}<br />
         &lt;/launchParameters&gt;<br/>
        </p>
    </td>
  </tr>  
  <tr>
    <td colspan="2" valign="top"><h3>entitlementKey</h3></td>
  </tr>
  <tr>
    <td valign="top"><p><strong>Required:</strong> No<br />
        <strong>Data type:</strong> string </p></td>
    <td valign="top"><p><strong>Description:</strong><br />
        Data used by the AU to determine if the launching LMS is entitled to use the AU. The AU SHOULD use this data in combination with other data provided from the LMS to determine entitlement.<br />
    </p>
      <p><strong>Value space: </strong>Values are defined by the AU content provider.<br />
        <br />
        <strong>Sample value:</strong><br/>
        &lt;entitlementKey&gt;<br/>
        xyz-123-9999<br/>
        &lt;/entitlementKey&gt;
        </p>
    </td>
  </tr>
</table>

<a name="vendor_meta_data"/>
### 7.1.5 Vendor Specific Metadata

Course Designer MAY place their own namespaced elements into the course structure. For that he MUST provide a XML Schema Definition and SHOULD provide a human readable specification describing these vendor specific extensions. These extensions MUST keep the course structure XML valid. An importing LMS MAY ignore these elements. 

The course designer MAY provide his extensions as potential addition to the course structure specification as an Issue or Pull Request to the [official cmi5 repository](https://github.com/AICC/CMI-5_Spec_Current).

<a name="course_structure_xsd"/>  
## 7.2 Course Structure XSD 

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
    <xs:attribute name="passIsFinal" use="optional" type="xs:boolean" default="true"/>
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
<a name="example_cmi5_xml"/>  
### 7.2.1 Example cmi5.xml 

```XML
<?xml version="1.0" encoding="utf-8"?>
<courseStructure p1:any_Attr="anySimpleType" xmlns:p1="otherNS" xmlns="http://www.adlnet.gov/cmi5/CourseStructure.xsd">
  <course p1:any_Attr="anySimpleType" id="http://uri1">
    <title p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="en">langstring1</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="fr">langstring2</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="de">langstring3</langstring>
    </title>
    <description p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="da">langstring4</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="el">langstring5</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="it">langstring6</langstring>
    </description>
    <languages p1:any_Attr="anySimpleType">en fr de </languages>
  </course>
  <objectives p1:any_Attr="anySimpleType">
    <objective id="http://uri1">
      <description p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring7</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="en">langstring8</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="fr">langstring9</langstring>
      </description>
      <title p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="de">langstring10</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="da">langstring11</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="el">langstring12</langstring>
      </title>
    </objective>
    <objective id="http://uri2">
      <description p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="it">langstring13</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring14</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="en">langstring15</langstring>
      </description>
      <title p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="fr">langstring16</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="de">langstring17</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="da">langstring18</langstring>
      </title>
    </objective>
    <objective id="http://uri3">
      <description p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="el">langstring19</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="it">langstring20</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring21</langstring>
      </description>
      <title p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="en">langstring22</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="fr">langstring23</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="de">langstring24</langstring>
      </title>
    </objective>
  </objectives>
  <au p1:any_Attr="anySimpleType" id="http://uri1" moveOn="NotApplicable" masteryScore="0" passIsFinal="true" authenticationMethod="Basic" launchMethod="AnyWindow" activityType="activityType1">
    <title p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="da">langstring25</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="el">langstring26</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="it">langstring27</langstring>
    </title>
    <description p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring28</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="en">langstring29</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="fr">langstring30</langstring>
    </description>
    <objectives p1:any_Attr="anySimpleType">
      <objective idref="http://uri1" />
      <objective idref="http://uri2" />
      <objective idref="http://uri3" />
    </objectives>
    <url>http://uri1</url>
    <launchParameters>anyType</launchParameters>
    <entitlementKey>anyType</entitlementKey>
  </au>
  <block p1:any_Attr="anySimpleType" id="http://uri1">
    <title p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="de">langstring31</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="da">langstring32</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="el">langstring33</langstring>
    </title>
    <description p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="it">langstring34</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring35</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="en">langstring36</langstring>
    </description>
    <objectives p1:any_Attr="anySimpleType">
      <objective idref="http://uri4" />
      <objective idref="http://uri5" />
      <objective idref="http://uri6" />
    </objectives>
    <au p1:any_Attr="anySimpleType" id="http://uri1" moveOn="NotApplicable" masteryScore="0" passIsFinal="true" authenticationMethod="Basic" launchMethod="AnyWindow" activityType="activityType1">
      <title p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="fr">langstring37</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="de">langstring38</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="da">langstring39</langstring>
      </title>
      <description p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="el">langstring40</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="it">langstring41</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring42</langstring>
      </description>
      <objectives p1:any_Attr="anySimpleType">
        <objective idref="http://uri7" />
        <objective idref="http://uri8" />
        <objective idref="http://uri9" />
      </objectives>
      <url>http://uri1</url>
      <launchParameters>anyType</launchParameters>
      <entitlementKey>anyType</entitlementKey>
    </au>
    <block p1:any_Attr="anySimpleType" id="http://uri1">
      <title p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="en">langstring43</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="fr">langstring44</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="de">langstring45</langstring>
      </title>
      <description p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="da">langstring46</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="el">langstring47</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="it">langstring48</langstring>
      </description>
      <objectives p1:any_Attr="anySimpleType">
        <objective idref="http://uri10" />
        <objective idref="http://uri11" />
        <objective idref="http://uri12" />
      </objectives>
      <au p1:any_Attr="anySimpleType" id="http://uri2" moveOn="NotApplicable" masteryScore="1" passIsFinal="true" authenticationMethod="Basic" launchMethod="AnyWindow" activityType="activityType2">
        <title p1:any_Attr="anySimpleType">
          <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring49</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="en">langstring50</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="fr">langstring51</langstring>
        </title>
        <description p1:any_Attr="anySimpleType">
          <langstring p1:any_Attr="anySimpleType" lang="de">langstring52</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="da">langstring53</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="el">langstring54</langstring>
        </description>
        <objectives p1:any_Attr="anySimpleType">
          <objective idref="http://uri13" />
          <objective idref="http://uri14" />
          <objective idref="http://uri15" />
        </objectives>
        <url>http://uri2</url>
        <launchParameters>anyType</launchParameters>
        <entitlementKey>anyType</entitlementKey>
      </au>
      <block p1:any_Attr="anySimpleType" id="http://uri2">
        <title p1:any_Attr="anySimpleType">
          <langstring p1:any_Attr="anySimpleType" lang="it">langstring55</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring56</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="en">langstring57</langstring>
        </title>
        <description p1:any_Attr="anySimpleType">
          <langstring p1:any_Attr="anySimpleType" lang="fr">langstring58</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="de">langstring59</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="da">langstring60</langstring>
        </description>
        <objectives p1:any_Attr="anySimpleType">
          <objective idref="http://uri16" />
          <objective idref="http://uri17" />
          <objective idref="http://uri18" />
        </objectives>
        <au p1:any_Attr="anySimpleType" id="http://uri3" moveOn="Passed" masteryScore="0.1" passIsFinal="false" authenticationMethod="Basic" launchMethod="OwnWindow" activityType="activityType3">
          <title p1:any_Attr="anySimpleType">
            <langstring p1:any_Attr="anySimpleType" lang="el">langstring61</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="it">langstring62</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring63</langstring>
          </title>
          <description p1:any_Attr="anySimpleType">
            <langstring p1:any_Attr="anySimpleType" lang="en">langstring64</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="fr">langstring65</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="de">langstring66</langstring>
          </description>
          <objectives p1:any_Attr="anySimpleType">
            <objective idref="http://uri19" />
            <objective idref="http://uri20" />
            <objective idref="http://uri21" />
          </objectives>
          <url>http://uri3</url>
          <launchParameters>anyType</launchParameters>
          <entitlementKey>anyType</entitlementKey>
        </au>
        <au p1:any_Attr="anySimpleType" id="http://uri4" moveOn="Completed" masteryScore="0.9" passIsFinal="true" authenticationMethod="Basic" launchMethod="AnyWindow" activityType="activityType4">
          <title p1:any_Attr="anySimpleType">
            <langstring p1:any_Attr="anySimpleType" lang="da">langstring67</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="el">langstring68</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="it">langstring69</langstring>
          </title>
          <description p1:any_Attr="anySimpleType">
            <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring70</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="en">langstring71</langstring>
            <langstring p1:any_Attr="anySimpleType" lang="fr">langstring72</langstring>
          </description>
          <objectives p1:any_Attr="anySimpleType">
            <objective idref="http://uri22" />
            <objective idref="http://uri23" />
            <objective idref="http://uri24" />
          </objectives>
          <url>http://uri4</url>
          <launchParameters>anyType</launchParameters>
          <entitlementKey>anyType</entitlementKey>
        </au>
      </block>
      <au p1:any_Attr="anySimpleType" id="http://uri5" moveOn="CompletedAndPassed" masteryScore="0.2" passIsFinal="false" authenticationMethod="Basic" launchMethod="OwnWindow" activityType="activityType5">
        <title p1:any_Attr="anySimpleType">
          <langstring p1:any_Attr="anySimpleType" lang="de">langstring73</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="da">langstring74</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="el">langstring75</langstring>
        </title>
        <description p1:any_Attr="anySimpleType">
          <langstring p1:any_Attr="anySimpleType" lang="it">langstring76</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring77</langstring>
          <langstring p1:any_Attr="anySimpleType" lang="en">langstring78</langstring>
        </description>
        <objectives p1:any_Attr="anySimpleType">
          <objective idref="http://uri25" />
          <objective idref="http://uri26" />
          <objective idref="http://uri27" />
        </objectives>
        <url>http://uri5</url>
        <launchParameters>anyType</launchParameters>
        <entitlementKey>anyType</entitlementKey>
      </au>
    </block>
    <au p1:any_Attr="anySimpleType" id="http://uri6" moveOn="CompletedOrPassed" masteryScore="0.8" passIsFinal="true" authenticationMethod="Basic" launchMethod="AnyWindow" activityType="activityType6">
      <title p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="fr">langstring79</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="de">langstring80</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="da">langstring81</langstring>
      </title>
      <description p1:any_Attr="anySimpleType">
        <langstring p1:any_Attr="anySimpleType" lang="el">langstring82</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="it">langstring83</langstring>
        <langstring p1:any_Attr="anySimpleType" lang="en-US">langstring84</langstring>
      </description>
      <objectives p1:any_Attr="anySimpleType">
        <objective idref="http://uri28" />
        <objective idref="http://uri29" />
        <objective idref="http://uri30" />
      </objectives>
      <url>http://uri6</url>
      <launchParameters>anyType</launchParameters>
      <entitlementKey>anyType</entitlementKey>
    </au>
  </block>
  <au p1:any_Attr="anySimpleType" id="http://uri2" moveOn="NotApplicable" masteryScore="1" passIsFinal="true" authenticationMethod="Basic" launchMethod="AnyWindow" activityType="activityType2">
    <title p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="en">langstring85</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="fr">langstring86</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="de">langstring87</langstring>
    </title>
    <description p1:any_Attr="anySimpleType">
      <langstring p1:any_Attr="anySimpleType" lang="da">langstring88</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="el">langstring89</langstring>
      <langstring p1:any_Attr="anySimpleType" lang="it">langstring90</langstring>
    </description>
    <objectives p1:any_Attr="anySimpleType">
      <objective idref="http://uri31" />
      <objective idref="http://uri32" />
      <objective idref="http://uri33" />
    </objectives>
    <url>http://uri2</url>
    <launchParameters>anyType</launchParameters>
    <entitlementKey>anyType</entitlementKey>
  </au>
</courseStructure>

```

<a name="course_package"/>
# 8.0 Course Package
For the course import and export defined in Section 6.1, the LMS MUST support all of the following formats:
<ul><li>Zip32</li>
<li>Zip64</li>
<li>A course structure XML file</li>
</ul>
## 8.1 Course Packages in ZIP Format
The two ZIP file formats MUST follow the specification defined at https://www.pkware.com/support/zip-app-note.  When the ZIP file is used to package a course, it may contain media associated with the course AUs.  
<ul><li>Any media included in a ZIP course package MUST use relative URL references in the Course Structure XML.</li>
<li>Any media not included in a ZIP course package MUST use fully qualified URL references in the Course Structure XML</li>
<li>A ZIP course package may contain a mix of fully qualified and relative URLs,provided the rules above are followed.</li>
</ul>
## 8.2 Course Structure XML Without a ZIP File Package
When a course structure XML file is provided without a ZIP file package, all URL references MUST be fully qualified.

<a name="course_structure_examples"/> 
# 9.0 Course Structure Examples

Using the domain of geology the following two examples demonstrate how simple and complex a course designer can structure a course. The titles and descriptions are fetched or translated from the Earth Sciences Portal at Wikipedia (https://en.wikipedia.org/wiki/Portal:Earth_sciences).

<a name="course_structure_examples_simple"/> 
## 9.1 Simple

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
## 9.2 Complex

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
        moveOn="CompletedOrPassed" passIsFinal="false" masteryScore="1.0"
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
        launchMethod="OwnWindow" moveOn="Passed" passIsFinal="false" masteryScore="0.1">
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
        launchMethod="OwnWindow" moveOn="CompletedOrPassed" passIsFinal="true" masteryScore="0.3">
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
        launchMethod="OwnWindow" moveOn="CompletedAndPassed" passIsFinal="false" masteryScore="0.5">
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
          <langstring lang="en-US">Das Archaikum Es erstreckt sich von ca. 4.000 bis ca. 2.500
            Millionen Jahren vor heute.
          </langstring>
          <langstring lang="de-DE">The Archean Eon is a geologic eon before the Proterozoic Eon,
            before 2.5 Ga (billion years), or 2,500 million years ago.
          </langstring>
        </description>
        <url>
          http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ecf/launch
        </url>
      </au>
      <au id="http://courses.example.edu/identifiers/courses/d07e186b/blocks/003-001/aus/7ed0/"
          activityType="http://adlnet.gov/expapi/activities/lesson" launchMethod="AnyWindow"
          moveOn="Passed" passIsFinal="true" masteryScore="0.5">
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
  <au id="http://quiz-server.example.com/1Hu62hL" masteryScore="0.7" passIsFinal="true"
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

<a name="bibliography"/> 
# 10.0 Bibliography

[1]  AICC CMI001, CMI Guidelines for Interoperability, Version 4.0. 

[2]  SCORM – http://www.adlnet.gov/capabilities/scorm 

[3]  MIME Types – http://www.iana.org/assignments/media-types/index.html  



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
