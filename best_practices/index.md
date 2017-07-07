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
* The Fetch URL should only return an auth token on the first call. (Subsequent calls should return an error – i.e. it should be a “one time use” URL)
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

###  Best Practice #{% increment bpCount %} – Use “progressed” verb for indicating progress during a session.
For recording progress during a session, it is recommend to use a cmi5 allowed statement with the progressed verb (http://adlnet.gov/expapi/verbs/progressed) and a progress extension in the result (see section 9.5.5.1 of specification).  Progress statements should not be sent for progress value of 100% as that indicates completion.  Once the learner reaches 100% it is recommended that a cmi5 defined “completed” statement be issued instead.

------
