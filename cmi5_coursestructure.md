cmi5 Course Structure 
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
* [__9.0 Bibliography__](#bibliography)

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
  <tr>
    <td colspan="2" valign="top"><h3>languages</h3></td>
  </tr>
  <tr>
    <td width="168" valign="top"><p><strong>Required</strong>: No<br />
        <strong>Data type</strong>: RFC 5646 language tags</p>
    </td>
    <td width="811" valign="top"><p><strong>Description:</strong><br />
      Specifies which languages will be supported by the course. All of the languages list MUST be present in a langstring for each title or description element. The LMS will be expected to display the language specific titles and descriptions for course elements based on the learner’s language preference.</p>
      <p><strong>Value space:</strong><br />
         Values defined by course designer</p>
      <p><strong>Sample value: </strong><br />
    &lt;languages&gt;<br/>
    &nbsp;&nbsp;en-US<br/>
    &nbsp;&nbsp;es-MX<br/>
    &lt;/languages&gt;<br/>
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

<a name="#vendor_meta_data"/>
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
            <xs:element name="languages" minOccurs="0" type="languagesType"></xs:element>
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

<a name="bibliography"/> 
# 9.0 Bibliography

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
