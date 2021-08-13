---
---

# Best Practices
{% capture tmp %}{% increment bpCount %}{% endcapture %}

------

### Best Practice #{% increment bpCount %} – Use of Objectives

(Since Objectives usage outside of course structure is not defined.)

Objectives are defined for the course structure, but there is no language in the specification concerning their usage in statements. If an AU is using Objectives in statements, the best practice is to add the objective (with the same objective id provided in the course structure) to the context activities “parent” property as an activity type of `http://adlnet.gov/expapi/activities/objective` from the ADL vocabulary.

### Best Practice #{% increment bpCount %} – LMS should always implement the "returnURL"

LMS should always implement the "returnURL"

LMS should not spawn a new window to launch AU (i.e. “popup”). Depending on the settings it could take the following actions to launch an AU:

* **OwnWindow** – Redirect same window to AU location
* **AnyWindow** – Either redirect same window or use iFrame, “LightBox”, etc.

### Best Practice #{% increment bpCount %} – Fetch URLs

* The Fetch URL must be unique for each session.
* The Fetch URL must only return an auth token on the first call. (Subsequent calls must return an error – i.e. it must be a “one time use” URL)
* The Fetch URL must not reuse auth tokens.
* The Fetch URL should return a 4xx HTTP error if an HTTP method other than POST is used.
* Since the Fetch URL can only be called once, the auth token should be stored in non-volatile storage (see best practice "Persist AU Session State") 

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

###  Best Practice #{% increment bpCount %} – Provide registration id in all statements.
It is strongly recommend to include the registration id provided by the LMS at launch time in the context of all statements issued by the LMS and AU.

###  Best Practice #{% increment bpCount %} – LMS create "satisfied" statements for AU's.

It is recommended that the LMS create a cmi5 “allowed” statement (with a satisfied verb) when an AU has met its moveOn criteria.  The statement should also include the same AU activityId used in cmi5 defined statements.

###  Best Practice #{% increment bpCount %} – Use of Objectives (in LMS/Course Structure)

Objectives are defined for the course structure so that the LMS can associate learning objectives to AU and Blocks in the course structure.  If an LMS has features for managing or reporting on objectives it should use the objectives defined in the course structure (to make the association of objectives to the AUs & Blocks).

###  Best Practice #{% increment bpCount %} – LMS should use the Session ID and authorization token to validate actor

When the LMS receives a Statement, it should verify that the Actor in the statement matches the actor provided on the launch URL and that the authorization token provided was the same one issued for that specific launch session.  If the Session ID, authorization token, actor in statement, and actor do not match, then the LMS/LRS should reject the Statement with a HTTP 403 (Forbidden) Error.

###  Best Practice #{% increment bpCount %} – AU should use a derived activity ID for "cmi.interaction" statements

When the AU issues statements with an activity type of "cmi.interaction" it should use an activity ID derived from the AU’s activity ID by appending the following convention:

/test/**_{TestID}_**/question/**_{QuestionID}_**

 Where :

   * **_{TestID}_** is a vendor defined identifier for the test embedded in AU.
   * **_{QuestionID}_** is a vendor defined identifier for the test question.

Example:

   * https://example.com/au/xyz123/test/997980ef-2089-4685-97ee-6949541a27e5/question/3f45e67c-f070-4ded-8fd8-82c4069e8526

###  Best Practice #{% increment bpCount %} – Persist AU Session State 

There are certain situations, such as browser window refresh, that may inadvertently cause cmi5 errors related to operations that must occur only once in a session.  To prevent such issues, AU’s should be designed to use non-volatile storage (local to AU) to preserve the state of following operations that have been performed during the session:

* Fetch URL token retrieval (which can only be called once in session)
* All cmi5 defined statements that can only be sent once in a session.




------
