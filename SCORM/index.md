# SCORM vs cmi5 Comparison

### Executive Summary

SCORM is a technical standard developed by Advanced Distributed Learning Initiative (ADL) over 16 years ago that governs how online learning content and Learning Management Systems (LMSs) communicate with each other.  It is the mature de facto industry standard for e-learning interoperability the pre-dates mobile learning and IOT.

cmi5 is a new specification that was co-developed by ADL and the Aviation Industry Computer-Based Training Committee (AICC).  This new specification defines how &quot;LMSs launch content&quot; using the Experience API (xAPI) as the content-to-LMS communication layer.  cmi5 builds upon the lessons learned from AICC and SCORM specifications, address the limitations of each, and adds new capabilities.  cmi5 uses xAPI which was designed with both traditional and non-traditional learning methods (Social, Mobile, Simulations, VR etc.) in mind.  cmi5&#39;s use of xAPI enables the development of interoperable features well beyond the traditional LMS model.  cmi5 is a key component of an xAPI based learning ecosystem and an excellent starting point for organizations that wish to adopt xAPI.

cmi5 provides the following functionality that SCORM does not:

- **Richer Data Collection.** Record any data you want (and get it back!)- SCORM is limited to a &quot;list&quot; of data collected.  cmi5 is open-ended on the data you can collect.
- **Share Data more easily –** cmi5 uses a web service and data structure that allows easy integration with other systems/applications.
- **Distributed Content –** cmi5 content can reside anywhere, it allows for content as a service.
- **Elimination of &quot;Pop-up&quot; Windows -** Eliminates pop-up blocker headaches.
- **Mobile app launch support –** cmi5 content does not require a browser.  Content could be a mobile app.



### SCORM vs. cmi5 Comparison for L&amp;D Professionals

The following table provides a high level comparison of SCORM to cmi5 for learning &amp; development professionals who develop/deliver SCORM content.

|       **Feature**     |     **SCORM**      |      **cmi5**      |       **Description**            |
| ------ | ------ | ------ | ------ |
| Track &quot;anything&quot; | No | Yes | SCORM is constrained to a defined set of data elements.cmi5 allows you to define your own data elements in addition to predefined elements |
| Mobile Friendly | No | Yes | A mobile app cannot be tracked with SCORM, but can with cmi5. |
| Host content anywhere | No | Yes | All SCORM content must reside in the LMS, cmi5 has no such restrictions (content can be located anywhere). |
| Can you get your data? | No | Yes | Most LMSs do not expose all of the data collected with SCORM.With cmi5, you can access to all the data in standard way.You can make your own report writers. |
| Offline Friendly | No | Yes | SCORM requires a continuous connection to a LMS and cmi5 does not. It is therefore possible to design offline cmi5 content. |
| Extensibility | No | Yes | With cmi5, you can collect any data you want from your learning content.Your LMS will use an LRS to support cmi5.  With an LRS you can build a learning ecosystem beyond the LMS, easily connecting to other systems. |



### SCORM vs. cmi5 Detailed Comparison

The following is a side-by-side comparison of SCORM to cmi5 at a detailed feature level.

|       **Feature**     |     **SCORM**      |      **cmi5**      |       **Description**            |
| ------ | ------ | ------ | ------ |
| Content Package | Yes | Yes | SCORM has a package containing local content with an XML manifest that details course structure and all resources. cmi5 has an XML course structure that can reference remote or local content. Both have a ZIP file for transferring content (locally).|
| Objectives | Yes | Yes | SCORM has Objectives Metadata that can be used for sequencing logic (called &quot;simple sequencing&quot;).cmi5 has objective metadata that does not affect course behavior.   |
| Remediation | Yes | No | With SCORM remediation can be implemented by &quot;simple sequencing&quot; logic rules.  cmi5 has no remediation rules.  Remediation is content and LMS vendor specific. |
| Prerequisites | Yes | No | With SCORM, prerequisites can be implemented by &quot;simple sequencing&quot; logic rules.  cmi5 has the notion of &quot;MoveOn&quot; criteria for the completion of individual AU's. |
| Content Launch | Yes | Yes | SCORM uses a JavaScript parent/opener with JavaScript communication object/API provided by the LMS.  cmi5 uses a launch URL with parameters for Web services communication.  This launch mechanism does not necessarily require a browser and content can reside on different domains/platforms.  Content can be launched in a mobile app with cmi5. |
| Course Metadata | Yes | Yes | SCORM has a complex metadata structure, whereas cmi5 has a simpler, lightweight structure. SCORM has IMS manifest that uses the LOM metadata specification to describe content (SCO&#39;s). cmi5 has a course structure file with defined content (AU) metadata and is extensible for content vendor-specific metadata. |
| Content Defined Data | No | Yes | SCORM data collection is restricted to data elements defined in the SCORM Data Model. cmi5 contains a smaller set of defined data elements than SCORM and is highly extensible through the use of xAPI. |
| Client Agnostic | No | Yes | For all practical purposes, SCORM is dependent on browser delivery due to the use of JavaScript API/object for communication.  cmi5 uses a RESTful web service (xAPI) and a JSON data format, neither of which rely on a browser. |
| Distributed Content | No | Yes | With SCORM all content is required to be located in the package and typically stored on the same domain as the LMS.With cmi5, content does not have to be in the package and can be located on any domain/local device. |
| Data Access | No | Yes | In SCORM, there is no standard bulk data access exposed.  cmi5 uses xAPI which is designed to provide bulk access to learner data with simple filtering. |
| Data Portability | No | Yes | SCORM does not allow for standardized system integration.  cmi5 uses xAPI which provides a standard journaling-based data format well suited for transport. |


&nbsp;
&nbsp;

