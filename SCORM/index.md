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


### Content Package

SCORM has a package containing local content with an XML manifest that details course structure and all resources. cmi5 has an XML course structure that can reference remote or local content. Both have a ZIP file for transferring content (locally).

The cmi5 Course Package is defined in section 14.0 of the cmi5 Specification.

There are basically two formats for the package.  It can either be zipped (using either Zip32 or Zip64) or not zipped.  The Zip64 option is for larger cmi5 packages.  This is an improvement over SCORM where Zip32 was the standard package format.

For packages that do not include content media, a cmi5 package can simply be an XML file (which has the course structure and fully qualified links to the content).

For any content you include in the cmi5 course package, you must use relative URL&#39;s in the course structure.  It will be the job of the LMS to position your content on the web server so that your relative URL&#39;s work properly (in the same manner as SCORM).

### Objectives

SCORM has Objectives Metadata that can be used for sequencing logic (called &quot;simple sequencing&quot;). cmi5 has objective metadata that does not affect course behavior.

Given the experience with SCORM, cmi5 was intentionally designed to not include sequencing rules in the course structure.  The rationale being that the customers of course structures would rather choose their own sequencing rules based on their business needs.

### Remediation

With SCORM remediation can be implemented by &quot;simple sequencing&quot; logic rules.  cmi5 has no remediation rules. Remediation is content and LMS vendor specific.  (for the same reasons stated for Objectives)

### Prerequisites

With SCORM, prerequisites can be implemented by &quot;simple sequencing&quot; logic rules. cmi5 has the notion of &quot;MoveOn&quot; criteria for completion of individual AU&#39;s.

Each assignable unit (AU) in a cmi5 course has an associated &quot;moveOn&quot; property (see Section 13.1.4 of the cmi5 specification).  The cmi5 moveOn value is used by the LMS to determine if the AU has been sufficiently completed in order to &quot;move on&quot; to the next AU.  The following values are allowed for the moveOn property.

- **Passed -** If the LMS receives a statement with the verb &quot;Passed&quot;, then the LMS will consider the AU satisfied.
- **Completed** - If the LMS receives a statement with the verb &quot;Completed&quot;, then the LMS will consider the AU satisfied.

- **CompletedAndPassed** - In this case the LMS must receive two statements; one with the cmi5 verb &quot;Completed&quot; and one with the cmi5 verb &quot;Passed&quot;.  The AU is considered satisfied only when both statements have been received.
- **CompletedOrPassed** - If the LMS receives a statement with either of the cmi5 verbs &quot;Completed&quot; or &quot;Passed&quot;, then the LMS will consider the AU satisfied.
- **NotApplicable** - The LMS will consider the AU satisfied as soon as the student registers for the course.

It is important to note that there is nothing in the specification to prevent the LMS Administrator from changing the cmi5 moveOn criteria (see Section 10 of the cmi5 specification).  For this reason the specification requires that the LMS write the current value of the moveOn property to the State API document.

### Content Launch

SCORM uses a JavaScript parent/opener with a JavaScript communication object/API provided by the LMS.  The content must discover the object/API via recursively searching the browser window tree. cmi5 uses a launch URL with parameters for Web services communication. The content uses query string parameters to discover the xAPI endpoint for recording data.  This method of discovery is more reliable as the query string is always available to the content.

### Course Metadata

SCORM has an IMS manifest that uses the LOM metadata specification to describe content (SCO&#39;s). cmi5 has a course structure file with defined content (AU) metadata and is extensible for content vendor-specific metadata. With cmi5, the course structure file can reference content from anywhere, it does not have be hosted on the same system.  The cmi5 course structure is only references the URL for the content, it does not contain all assets as SCORM does.  Like SCORM, cmi5 is also extensible.

### Content Defined Data

SCORM data collection is restricted to data elements defined in the SCORM Data Model. cmi5 contains a smaller set of defined data elements than SCORM and is highly extensible through the use of xAPI.  This extensibility is interoperable for data collection and retrieval with xAPI. cmi5 further enhances interoperability in this area by providing session identifiers to group statements.


### Client Agnostic

For all practical purposes, SCORM is dependent on browser delivery due to the use of JavaScript API/object for communication. cmi5 uses a RESTful web service (xAPI) that the content uses to send requests/receive responses with JSON data structures.  

Since cmi5 does not rely on JavaScript, a web-browser is not required for content delivery.  Because of this, content can be developed in any programming language that can support HTTP communication.

### Distributed Content

With SCORM all content is required to be located in the package and typically stored on the same domain as the LMS.  With cmi5, content does not have to be in the package and can be located on any domain/local device.

The cmi5 course structure (cmi5.xml) can contain either relative or fully qualified URLs to the content launch point. Content can be hosted in central locations allowing for automated updates and simple distribution for content discovery.  Content can also by dynamically created and configured at runtime if hosted.

The cmi5 course structure also provides for an “entitlementKey” which allows for content for metered access to content as a service.


### Data Access

In SCORM, the only specification protocol for returning data was available at Run-Time for the current user within current SCO only. Access to data requires access to the Database (which is outside the scope of SCORM).  cmi5 uses xAPI which has bulk data retrieval capabilities (using GET Requests) built-in to allow return of data. LRSs cannot be write-only. All requests for data subject to security policies.

### Data Portability

SCORM does not allow for standardized system integration.  cmi5 uses xAPI which provides a standard journaling-based data format well suited for transport.

SCORM has a standard model but does not have a standardized data format for export/retrieval.  cmi5 is xAPI based and uses a standardized JSON / document structure.  cmi5 adds context requirements to xAPI more easily group statements based on learner sessions.


