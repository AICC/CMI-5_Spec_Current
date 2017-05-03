---
---

# Best Practices
{% capture tmp %}{% increment bpCount %}{% endcapture %}

------

### Best Practice #{% increment bpCount %} – Use of Objectives

(Since Objectives usage outside of course structure is not defined.)

Objectives are defined for the course structure, but there is no language in the specification concerning their usage in statements. If using Objectives in statements (as Activities) the best practice is to use the Activity Definition type (http://adlnet.gov/expapi/activities/objective) from the ADL vocabulary.

The same Objective can be referenced by multiple AU or Blocks. There are 2 ways to interpret meeting an Objective. The two expected practices are:

1. All elements referencing the Objective need to be Satisfied (or met moveOn criteria)
1. Only one element referencing the Objective needs to be Satisfied (or met moveOn criteria).

It is recommended that LMS developers document how they do this and allow for an extension (in the course structure) to indicate what method should be used.

### Best Practice #{% increment bpCount %} – LMS should always implement the "returnURL"

LMS should always implement the "returnURL"

LMS should not spawn a new window to launch AU (i.e. “popup”). Depending on the settings it could take the following actions to launch an AU:

* **OwnWindow** – Redirect same window to AU location
* **AnyWindow** – Either redirect same window or use iFrame, “LightBox”, etc.

### Best Practice #{% increment bpCount %} – Fetch URLs

* The Fetch URL should be unique for each session.
* Do not reuse auth tokens.

### Best Practice #{% increment bpCount %} – AU Mastery Score

If the LMS issues a Mastery Score, the AU should respond in the following ways:

* If the AU has no notion of scoring, it should not issue Passed or Failed statements.
* If the AU does not have scoring or the learner does not meet the Mastery Score then the AU must not issue a Passed Statement (per the specification).
* The AU can also refuse to execute because the Mastery Score issued is inconsistent with the learning design of the AU. In this situation, the AU should inform the learner why it cannot execute.

### Best Practice #{% increment bpCount %} – LMS Mastery Score

LMS should use caution when adding Mastery Scores to AU course structure entries if they are not present in the original course structure. (As the AU may not be designed to handle scores). It is recommended that such changes be tested prior to enrolling learners.

### Best Practice #{% increment bpCount %} – Always specify a moveOn criterion in the course structure for each AU

When creating a course structure, always specify a moveOn criteria for each AU. Failing to do so will result in a default of “Not Applicable”. This can have the following unintended consequences:

* When failing to specify moveOn criteria or specifying “NotApplicable” as the moveOn criteria for all AU’s in a course, the course will automatically being marked satisfied immediately upon registration of the learner (before the learner launches a single AU).
* If at least one AU has a moveOn criteria specified (other than “NotApplicable”) then the course would be satisfied upon satisfaction of those AU’s.
* It is considered to be a better practice to explicitly specify the moveOn for each AU in a course structure to ensure there is no confusion over the satisfaction requirements of a course.

### Best Practice #{% increment bpCount %} – Launching apps on mobile devices

One of the following options should be used to launch AU's that are apps on mobile devices:

_Option 1_: Use an app protocol in the launch URL.

* AU is an app.
* AU has url with a protocol LMS launches App using URL with app protocol.
* An app redirecting to browser is not useful. If using app protocol to launch, don’t use "returnURL".

_Option 2_: Use and HTML wrapper to launch the app AU is an HTML page (wrapper) that directs from the mobile browser to the app.

### Best Practice #{% increment bpCount %} – In the absence of returnURL, the AU should close browser window to exit.

If the AU is not a mobile app and the LMS does not provide a “returnURL”, the best practice to exit the AU is to close the Window (window.close()) or direct the learner to manually close the browser window.

### Best Practice #{% increment bpCount %}  - LMS error handling of non-conforming cmi5 statements.
If an AU sends a statement that doesn’t conform to cmi5, the LMS should reject it (see section 6.3 of cmi5 specification) and return an HTTP error 403.

### Best Practice #{% increment bpCount %}  - LMS Administrators should use caution when changing the moveOn property.
The AU may not have the capability of sending statements required by any moveOn value that was not in the original course structure. It is recommended that all changes to course structures after import be tested prior to learner assignment.


------

### Best Practice #2 – Resolvable IRI's**

All IRI’s must be unique in the cmi5 spec. However, The Best practice to ensure a unique IRI should include a valid domain/host name and be resolvable.

Per XAPI specification:

> Internationalized Resource Locator (IRL): In the context of this document, an IRL is an IRI that when translated into a URI (per the IRI to URI rules), is a URL. Some communities of practice simply use URL even if they use IRIs, which isn't as technically correct within xAPI.

The resolution of an IRI should return a description of the IRI’s purpose/origin.

### Best Practice #3 – LMS resolution of relative course ID IRI’s.**

If the LMS imports a course with relative IRI’s it should prepend a valid protocol (http://, ftp://, or relative protocol // etc. ), domain, and path.

If other course elements have relative IRI’s, the LMS should prepend the course IRI to the relative course element IRI


> (Course IRI)(AU relative IRI) 
