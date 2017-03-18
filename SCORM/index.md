# cmi5 vs SCORM Comparison

### Executive Summary

SCORM is a technical standard developed by Advanced Distributed Learning Initiative (ADL) over 16 years ago that governs how online learning content and Learning Management Systems (LMSs) communicate with each other.  It is the mature de facto industry standard for e-learning interoperability the pre-dates mobile learning and IOT.

cmi5 is a new specification that was co-developed by ADL and the Aviation Industry Computer-Based Training Committee (AICC).  This new specification defines how &quot;LMSs launch content&quot; using the Experience API (xAPI) as the content-to-LMS communication layer.  cmi5 builds upon the lessons learned from AICC and SCORM specifications, address the limitations of each, and adds new capabilities.  cmi5 uses xAPI which was designed with both traditional and non-traditional learning methods (Social, Mobile, Simulations, VR etc.) in mind.  cmi5&#39;s use of xAPI enables the development of interoperable features well beyond the traditional LMS model.  cmi5 is a key component of an xAPI based learning ecosystem and an excellent starting point for organizations that wish to adopt xAPI.

cmi5 provides the following functionality that SCORM does not:

- **Richer Data Collection.** Record any data you want (and get it back!)- SCORM is limited to a &quot;list&quot; of data collected.  cmi5 is open-ended on the data you can collect.
- **Share Data more easily –** cmi5 uses a web service and data structure that allows easy integration with other systems/applications.
- **Distributed Content –** cmi5 content can reside anywhere, it allows for content as a service.
- **Elimination of &quot;Pop-up&quot; Windows -** eliminate pop-up blocker headaches)
- **Mobile app launch support –** cmi5 content does not require a browser.  Content could be a mobile app.



### SCORM vs. cmi5 Comparison for L&amp;D Professionals

The following table provides a high level comparison of SCORM to cmi5 for learning &amp; development professionals who develop/deliver SCORM content.

|&nbsp;&nbsp; **Feature** &nbsp;&nbsp;|&nbsp;&nbsp; **SCORM** &nbsp;&nbsp;|&nbsp;&nbsp; **cmi5** &nbsp;&nbsp;|&nbsp;&nbsp; **Description** &nbsp;&nbsp;|
| ------ | ------ | ------ | ------ |
| Track &quot;anything&quot; | No | Yes | SCORM is constrained to a defined set of data elements.cmi5 allows you to define your own data elements in addition to predefined elements |
| Mobile Friendly | No | Yes | A mobile app cannot be tracked with SCORM, but can with cmi5. |
| Host content anywhere | No | Yes | All SCORM content must reside in the LMS, cmi5 has no such restrictions (content can be located anywhere). |
| Can you get your data? | No | Yes | Most LMSs do not expose all of the data collected with SCORM.With cmi5, you can access to all the data in standard way.You can make your own report writers. |
| Offline Friendly | No | Yes | SCORM requires a continuous connection to a LMS and cmi5 does not. It is therefore possible to design offline cmi5 content. |
| Extensibility | No | Yes | With cmi5, you can collect any data you want from your learning content.Your LMS will use an LRS to support cmi5.  With an LRS you can build a learning ecosystem beyond the LMS, easily connecting to other systems. |



### SCORM vs. cmi5 Detailed Comparison

The following is a side-by-side comparison of SCORM to cmi5 at a detailed feature level.

|&nbsp;&nbsp; **Feature** &nbsp;&nbsp;|&nbsp;&nbsp; **SCORM** &nbsp;&nbsp;|&nbsp;&nbsp; **cmi5** &nbsp;&nbsp;|&nbsp;&nbsp; **Comments** &nbsp;&nbsp;|
| ------ | ------ | ------ | ------ |
| Content Package | YES | YES | SCORM has a package containing local content with an XML manifest that details course structure and all resources. cmi5 has an XML course structure that can reference remote or local content. Both have a ZIP file for transferring content (locally).
 |
| Objectives | YES | YES | SCORM has Objectives Metadata that can be used for sequencing logic (called &quot;simple sequencing&quot;).cmi5 has objective metadata that does not affect course behavior.   |
| Remediation | YES | NO | With SCORM remediation can be implemented by &quot;simple sequencing&quot; logic rules.cmi5 has no remediation rules.  Remediation is content and LMS vendor specific. |
| Prerequisites | Yes | No | With SCORM, prerequisites can be implemented by &quot;simple sequencing&quot; logic rules.cmi5 has the notion of &quot;MoveOn&quot; criteria for completion of individual AU or groups of AU. |
| Content Launch | Yes | Yes | SCORM uses as JavaScript parent/opener with JavaScript communication object/API provided by the LMS. The LMS determines how the content is redirected/launched to (pop up window, iframe, re-direct). The Content must discover the object/API.cmi5 uses a launch URL with parameters for Web services communication. The course structure settings determine windowing (&quot;own window&quot; or &quot;any window&quot;) used by the LMS to launch the content. The content uses query string parameters to discover the xAPI endpoint for recording data. |
| Communication Interface | Yes | Yes | SCORM uses a LMS-provided JavaScript runtime communication object/API that the content discovers and makes calls and receives responses.cmi5 uses a RESTful web service (xAPI) that the content uses to send requests/receive responses with JSON data structures. |
| Course Metadata | Yes | Yes | SCORM has IMS manifest that uses the LOM metadata specification to describe content (SCO&#39;s). cmi5 has a course structure file with defined content (AU) metadata and is extensible for content vendor-specific metadata. |
| Content Defined Data | No | Yes | SCORM data collection is restricted to data elements defined in the SCORM Data Model. With cmi5, there is a smaller set of defined data elements than SCORM and is highly extensible through the use of xAPI.   |
| Client Agnostic | No | Yes | For all practical purposes, SCORM is dependent on browser delivery due to the use of JavaScript API/object for communication.  cmi5 uses a RESTful web service (xAPI) and use a JSON data format, neither of which rely on a browser. |
| Distributed Content | No | Yes | With SCORM all content is required to be located in the package and typically stored on the same domain as the LMS.With cmi5, content does not have to be in the package and can be located on any domain/local device. |
| Data Access | No | Yes | In SCORM, the only specification protocol for returning data was available at Run-Time for the current user within current SCO only.  Access to data requires access to the Database (which is outside the scope of SCORM).cmi5 uses xAPI which has querying (GET Requests) built-in to allow return of data.  LRSs cannot be write-only. All requests for data subject to security policies. |
| Data Readability | No | Yes | With SCORM, the structure of data is not defined so the data format varies from system to system.cmi5 is xAPI based with a standardized JSON / document structure. |
| Data Portability | No | Yes | SCORM runtime data does not allow for easy import/export. The cmi5 JSON structure allows for easy portability across systems. |
| Distributed Content | No | Yes | Native SCORM content effectively does not support distributed content delivery.cmi5 natively enables distribute content delivery. |
| Flexible Content Types | No | Yes | In SCORM, content types are limited to &quot;SCO&quot; and &quot;asset&quot;cmi5 uses xAPI which allows for many activity types. |
| Support for Non-traditional Learning Types | No | Yes | SCORM is constrained to single-user, self-paced, browser-based learning.Since cmi5, is xAPI based it does not have these constraints. |
