

# **cmi5 Testing Requirements Document - Working Draft**

_**Disclaimer: This is a working draft, do NOT implement systems based on this information.**_

**1.0 Overview**

**1.1 Scope**

**2.0 References**

**3.0 Definitions**

* **cmi5\_3.0\_1**  Internationalized Resource Identifier (IRI): All id&#39;s must conform to RFC 3987

* **cmi5\_3.0\_2**  Learning Management System (LMS): Must be xAPI conformant (must pass ADL LRS conformance tests.)

* **cmi5\_3.0\_3**  Learning Management System (LMS): LRS must be integrated with LRS  _(comment – may be indirectly tested)_

3.1 Abbreviations and Acronyms

4.0 Conformance

4.1 Assignable Unit (AU)

4.2 Learning Management Systems (LMS)

* **cmi5\_4.2\_1**  Learning Management System (LMS): The LMS MUST (have access to) be able to retrieve all Resource data (from the Statement API, etc., including attachments and extensions) about another distinct user across multiple sessions for that user.

**Reference the following Requirements:**

4.3 Optional JSON Values

4.4 Courses

5.0 Conceptual Model: Informative

6.0 LMS Requirements

6.1 Course Structures

* **cmi5\_6.1\_1**  Learning Management System (LMS): The LMS MUST be able to import and process course structures containing more than 1000 AU&#39;s.

6.2 LMS State API Requirements

6.3 LMS Statement API Requirements

* **cmi5\_6.3\_1**  The LMS MUST NOT provide permissions/credentials which allow the AU to issue voiding Statements.

* **cmi5\_6.3\_2**  The LMS MUST Void statements that are NOT rejected AND conflict with the &quot;Statement API&quot; requirements as defined in Section 9

* **cmi5\_6.3\_3**    All &quot;cmi5 allowed&quot; and &quot;cmi5 defined&quot; statements issued by the LMS MUST include the &quot;content template&quot; as defined in section 10.0 xAPI State Data Model.

7.0 AU Requirements

7.1 AU Statement API Requirements

7.1.1 First Statement API Call

* **cmi5\_7.1.1\_1**  Assignable Unit (AU): The AU MUST issue an initialized statement before issuing any other statements in a session.

7.1.2 Last Statement Call

* **cmi5\_7.1.2\_1**  Assignable Unit (AU): The AU MUST issue a Terminated statement as the last statement in a session.

7.1.3 Types of Statements

* **cmi5\_7.1.3\_1**  If &quot;cmi5 allowed&quot; statements are posted by the AU, they MUST occur between cmi5 &quot;initialized&quot; and &quot;terminated&quot; statements in the same session.

* **cmi5\_7.1.3\_2**  (Place holder) &quot;cmi5 allowed&quot; statements are not considered in cmi5 defined session management and completion rules.

* **cmi5\_7.1.3\_3**  All &quot;cmi5 allowed&quot; and  &quot;cmi5 defined&quot; statements issued by the AU must include the &quot;content template&quot; as defined in section 10.0 xAPI State Data Model.



8.0 Content Launch Mechanisms

8.1 Launch Method

* **cmi5\_8.1\_1**  Learning Management System (LMS): The AU MUST be launched by the LMS using either a new browser window or redirecting the existing browser window to a new location.

* **cmi5\_8.1\_2**  Learning Management System (LMS): The AU MUST be launched by the LMS using the method specified in the course structure metadata.  ("OwnWindow" or "AnyWindow")

* **cmi5\_8.1\_3**  Learning Management System (LMS): The AU MUST be launched by the LMS with a launch URL containing query string parameters (endpoint, fetch, actor, registration, and activityId).

* **cmi5\_8.1\_4**  endpoint - Learning Management System (LMS): The AU MUST be launched by the LMS with a launch URL containing a &quot;endpoint&quot; name/value pair in the query string containing the endpoint to the LRS.

* **cmi5\_8.1\_5**  endpoint - Assignable Unit (AU): The AU MUST get the endpoint value from the query string and use the endpoint value as the Base Endpoint for xAPI requests.

* **cmi5\_8.1\_6**  fetch - Learning Management System (LMS):  the LMS MUST place the _fetch_ name/value pair in the query string.

* **cmi5\_8.1\_7**  fetch - Assignable Unit (AU): The AU MUST retrieve the fetch value from the query string.

* **cmi5\_8.1\_8**  actor - Learning Management System (LMS): The LMS MUST populate the actor with a valid value.

* **cmi5\_8.1\_9**  actor - Assignable Unit (AU): The AU MUST get the actor value from the query string. The AU MUST use the actor value in API calls that require an &quot;actor&quot; property when sending xAPI requests.

* **cmi5\_8.1\_10**  registration - Learning Management System (LMS):  The LMS MUST place a UUID value for registration id in the query string.

* **cmi5\_8.1\_11**  registration - Assignable Unit (AU):  The AU MUST use the registration id provided query string in API calls that require a &quot;registration id&quot; when sending xAPI requests.

* **cmi5\_8.1\_12**  activityId- Learning Management System (LMS):  The LMS MUST generate an activityId for the AU and place its value in the query string.

* **cmi5\_8.1\_13**  activityId- Learning Management System (LMS):  The activityId generated MUST NOT match the AU&#39;s id (publisher id) from the course structure

* **cmi5\_8.1\_14**  activityId- Learning Management System (LMS):  The LMS MUST use the same generated activityId on all subsequent launches (for the same AU) within the same registration. The LMS SHOULD use the same generated activityId (for the same AU) for all registrations.

* **cmi5\_8.1\_13**  activityId- Assignable Unit (AU):  The AU MUST get the activityId value from the query string and use the activityId value in API calls that require an &quot;activity id&quot; when issuing cmi5 defined statements.

8.2 Authorization Token Fetch URL

8.2.1 Overview

* **cmi5\_8.2.1\_1**         Learning Management System (LMS):  The LMS MUST include a _ **fetch** _ name/value pair in the launch URL.

* **cmi5\_8.2.1\_2** Learning Management System (LMS):  The _ **fetch** _ URL MUST accept POST requests and MUST NOT accept GET requests.

* **cmi5\_8.2.1\_3** Assignable Unit (AU):  The AU MUST issue only one request to the _ **fetch** _ URL.

* **cmi5\_8.2.1\_4** Assignable Unit (AU):  The AU MUST NOT issue any type of HTTP requests other than POST to the _ **fetch** _ URL.

* **cmi5\_8.2.1\_5** Learning Management System (LMS):  The LMS must return an auth token in a the JSON structure specified from a valid fetch URL call.

8.2.2 Definition: auth-token

* **cmi5\_8.2.2\_1** Learning Management System (LMS):  The LMS MUST return an HTTP status code of &quot;200&quot; for a valid (POST) request to the fetch URL.

* **cmi5\_8.2.2\_2** Assignable Unit (AU):  The AU MUST place the authorization token returned from the fetch URL in the Authorization headers of all HTTP requests made to the LRS endpoint.

8.2.3 Errors

8.2.3.1 Duplicate call to fetch URL

8.2.3.2 Error Values

8.3 Other Launch Environments

9.0 xAPI Statement Data Model

9.1 Statement ID

* **cmi5\_9.1\_1** Assignable Unit (AU):  The AU MUST assign a statement id property in UUID format for all statements it issues.

9.2 Actor

* **cmi5\_9.2\_1** Learning Management System (LMS):  The LMS MUST provide an actor objectwith an objectType of &quot;Agent&quot; and MUST contain an &quot;account&quot; as defined in the xAPI specification.

* **cmi5\_9.2\_2** Learning Management System (LMS):  The Actor object defined by the LMS must be used as the actor in all cmi5 defined statements made by the LMS.

* **cmi5\_9.2\_3** Assignable Unit (AU):  The Actor object defined by the LMS must be used as the actor in all cmi5 defined statements made by the AU.

9.3 Verbs

* **cmi5\_9.3\_1** Assignable Unit (AU):  The AU MUST NOT issue duplicate verbs (in cmi5 defined statements) within an AU session. (see cmi5 verbs…)

* **cmi5\_9.3\_2** Assignable Unit (AU):  The AU MUST NOT use a Passed and a Failed verb (in cmi5 defined statements) within an AU session.

* **cmi5\_9.3\_4** Assignable Unit (AU):  The AU MUST issue a Terminated (cmi5 defined) statement as its last statement in a session.

* **cmi5\_9.3\_6** Assignable Unit (AU):  The AU MUST issue only one Passed (cmi5 defined) statement per ActivityId per registration.

* **cmi5\_9.3\_7** Assignable Unit (AU):  The AU MUST NOT issue a Failed (cmi5 defined) statement following a Passed (cmi5 defined) statement per ActivityId per registration.

* **cmi5\_9.3\_8** Learning Management System (LMS):  All statements from AUs must be recorded to the LRS.

* **cmi5\_9.3\_9** Learning Management System (LMS):  LMS MUST NOT issue more than one abandoned (cmi5 defined) statement for a session  id.

* **cmi5\_9.3\_10** Learning Management System (LMS):  LMS MUST NOT issue more than one waived statement per session per AU and MUST not issue more than one waived statement per registration per AU.

9.3.1 Launched

* **cmi5\_9.3.1\_1** Learning Management System (LMS):  The LMS MUST issue a Launched (cmi5 defined) statement before launching an AU.

* **cmi5\_9.3.1\_2** Learning Management System (LMS):  The LMS MUST NOT issue multiple Launched (cmi5 defined) statements for given a session id.

9.3.2 Initialized

* **cmi5\_9.3.2\_1** Assignable Unit (AU):  The AU MUST issue a Initialized (cmi5 defined) statement as its first statement in a session.

* **cmi5\_9.3.2\_2** Assignable Unit (AU):  The AU MUST NOT issue more than one Initialized (cmi5 defined) statement in a session.

9.3.3 Completed

* **cmi5\_9.3.3\_1** Assignable Unit (AU):  The AU MUST issue only one Completed (cmi5 defined) statement per ActivityId per registration.

* **cmi5\_9.3.3\_2** _Assignable Unit (__AU):  __The AU MUST issue a (cmi5 defined) statement containing the &quot;completed&quot; verb when the learner has experienced all relevant material in an AU._ _(testing is subject to AU instructions – human inspection – not automatable)_

9.3.4 Passed

* **cmi5\_9.3.4\_1** _Assignable Unit (__AU):  __The AU MUST record a (cmi5 defined) statement containing the &quot;passed&quot; verb when the learner has attempted and passed the AU._ _(testing is subject to AU instruction – human inspection – not automatable)_

* **cmi5\_9.3.4\_2** _Assignable Unit (__AU):  _. If a &quot;passed&quot; (cmi5 defined) statement contains a (scaled) score and the LMS Launch Data contains a &quot;masteryScore&quot;, then the (scaled) score MUST be equal to or greater than the masteryScore

9.3.5 Failed

* **cmi5\_9.3.5\_1** _Assignable Unit (__AU):  __The AU MUST record a_ (cmi5 defined) _statement containing the &quot;failed&quot; verb when the learner has attempted and failed the AU.._ _(testing is subject to AU instruction – human inspection – not automatable)_

* **cmi5\_9.3.5\_2** _Assignable Unit (__AU):  _. If a &quot; failed&quot; (cmi5 defined) statement contains a (scaled) score and the LMS Launch Data contains a &quot;masteryScore&quot;, then the (scaled) score MUST be less than the masteryScore

9.3.6 Abandoned

* **cmi5\_9.3.6\_1** Learning Management System (LMS): The LMS MUST record an &quot;abandoned&quot; (cmi5 defined) statement on behalf of an given AU if the previous session (with the same learner/course registration) of that AU did not include a &quot;terminated&quot; statement(cmi5 defined).

* **cmi5\_9.3.6\_2** Learning Management System (LMS):   After recording an &quot;abandoned&quot; (cmi5 defined) statement for a given session, the LMS MUST NOT allow any additional statements to be recorded for that session.

9.3.7 Waived

* **cmi5\_9.3.7\_1** Learning Management System (LMS): A (cmi5 defined) statement containing a &quot;waived&quot; verb MUST include a &quot;reason&quot; in the extension property of the Statement Result.

* **cmi5\_9.3.7\_2** Learning Management System (LMS):   The LMS MUST generate a unique session id for a (cmi5 defined) statement containing a &quot;waived&quot; verb and MUST NOT issue any other statements (except for cmi5 defined statements with the &quot;satisfied&quot; verb) using that session id.

* **cmi5\_9.3.7\_3** Learning Management System (LMS):   The LMS MUST NOT issue multiple (cmi5 defined) statements with &quot;waived&quot; for the same AU within a course registration.

9.3.8 Terminated

* **cmi5\_9.3.8\_1** Assignable Unit (AU):  The AU MUST record a (cmi5 defined) statement containing the &quot;terminated&quot; verb as the last statement in a session.

* **cmi5\_9.3.8\_2** Learning Management System (LMS):   Upon receiving a (cmi5 defined) &quot;terminated&quot; statement, the LMS MUST reject statements (of any kind) for the AU session received after its (LMS defined) specified period of time.

9.3.9 Satisfied

* **cmi5\_9.3.9 \_1** Learning Management System (LMS):   The LMS MUST generate a unique block id for each block in the course structure. 

* **cmi5\_9.3.9 \_2** Learning Management System (LMS):The generated Block id MUST NOT match the publisher&#39;s ID from the course structure.

* **cmi5\_9.3.9 \_3** Learning Management System (LMS):  The LMS MUST issue a (cmi5 defined)  &quot;satisfied&quot; statement when the learner has met the moveOn criteria of all AU&#39;s in a (course structure) block. The &quot;satisfied&quot; statement must include the block id generated by the LMS and use &quot;https://w3id.org/xapi/cmi5/activitytype/block&quot; as the value of the &quot;type&quot; property in the Object&#39;s Definition.

* **cmi5\_9.3.9 \_4** Learning Management System (LMS):   The LMS MUST generate a unique course id for the course structure. 

* **cmi5\_9.3.9 \_5** Learning Management System (LMS):The generated course id MUST NOT match the publisher&#39;s ID from the course structure.

* **cmi5\_9.3.9 \_6** Learning Management System (LMS):  The LMS MUST issue a (cmi5 defined)  &quot;satisfied&quot; statement when the learner has met the moveOn criteria of all AU&#39;s in a course. The &quot;satisfied&quot; statement must include the course id generated by the LMS and use &quot;https://w3id.org/xapi/cmi5/activitytype/block&quot; as the value of the &quot;type&quot; property in the Object&#39;s Definition.

* **cmi5\_9.3.9 \_7** Learning Management System (LMS):   For all &quot;satisfied&quot; statements triggered as a result of an AU launch session, the LMS MUST use the session id from the AU launch in the statements.

9.4 Object

* **cmi5\_9.4\_1** Assignable Unit (AU):  The AU must provide an object in all (cmi5 defined) statements.

* **cmi5\_9.4\_2** Assignable Unit (AU):  For all (cmi5 defined) statements issued by the AU, the Object&#39;s &quot;id&quot; property must match the activityId defined in the launch URL.

* **cmi5\_9.4.\_3** Learning Management System (LMS): The LMS must provide an object in all (cmi5 defined) statements.

* **cmi5\_9.4.\_4** Learning Management System (LMS):  For launched (cmi5 defined) statements issued by the LMS, the Object&#39;s &quot;id&quot; property must match the ActivityId provided by the LMS for the AU launched.

* **cmi5\_9.4.\_5** Learning Management System (LMS):  For abandoned (cmi5 defined) statements issued by the LMS, the Object&#39;s &quot;id&quot; property must match the ActivityId provided by the LMS for the AU abandoned.

* **cmi5\_9.4.\_6** Learning Management System (LMS):  For waived (cmi5 defined) statements issued by the LMS, the Object&#39;s &quot;id&quot; property for must match the ActivityId provided by the LMS for the AU waived.

* **cmi5\_9.4.\_7** Learning Management System (LMS):  For satisfied (cmi5 defined) statements for blocks issued by the LMS, the Object&#39;s &quot;id&quot; property must match the LMS generated block id.

* **cmi5\_9.4.\_8** Learning Management System (LMS):  For satisfied (cmi5 defined) statements for blocks issued by the LMS, the Object&#39;s &quot;id&quot; property must match the LMS generated course id.

9.5 Result

9.5.1 Score

* **cmi5\_9.5.1\_1** Assignable Unit (AU):  The AU must not report a score for (cmi5 defined) statements other than passed or failed.

* **cmi5\_9.5.1\_2** Assignable Unit (AU):  If the AU provides a &quot;raw&quot; value  for score it MUST also provide the &quot;min&quot; and &quot;max&quot; values for score.

(Other score requirements are covered in passed, failed, and MasteryScore)

9.5.2 Success

* **cmi5\_9.5.2\_1** Assignable Unit (AU):  The AU must set the &quot;success&quot; property of the result to true  for passed (cmi5 defined) statements.

* **cmi5\_9.5.2\_2** Assignable Unit (AU):  The AU must set the &quot;success&quot; property of the result to false  for failed (cmi5 defined) statements.

* **cmi5\_9.5.2\_3** Assignable Unit (AU):  The AU must not include the success property for  (cmi5 defined) statements other passed and failed.

* **cmi5\_9.5.2\_4** Learning Management System (LMS):  The LMS must set the &quot;success&quot; property of the result to true  for waived (cmi5 defined) statements.

* **cmi5\_9.5.2\_5** Learning Management System (LMS):  The LMS must not include the success property for  (cmi5 defined) statements other waived.

9.5.3 Completion

* **cmi5\_9.5.3\_1** Assignable Unit (AU):  The AU must set the &quot;completion&quot; property of the result to true  for passed (cmi5 defined) statements.

* **cmi5\_9.5.3\_2** Assignable Unit (AU):  The AU must not include the &quot;completion&quot; property for  (cmi5 defined) statements other completed.

* **cmi5\_9.5.3\_3** Learning Management System (LMS):  The LMS must set the &quot;completion&quot; property of the result to true for waived (cmi5 defined) statements.

* **cmi5\_9.5.3\_4** Learning Management System (LMS):  The LMS must not include the &quot; completion&quot; property for  (cmi5 defined) statements other waived.

* **cmi5_9.5.3_5** Assignable Unit (AU): The AU must set the "completion" property of the result to true for completed (cmi5 defined) statements.

9.5.4 Duration

9.5.4.1 AU statements that include duration

* **cmi5\_9.5.4.1\_1** Assignable Unit (AU):  The AU MUST include the &quot;duration&quot; property in &quot;terminated&quot; statements.

* **cmi5\_9.5.4.1\_2** Assignable Unit (AU):  The AU MUST include the &quot;duration&quot; property in &quot;completed&quot; statements.

* **cmi5\_9.5.4.1\_3** Assignable Unit (AU):  The AU MUST include the &quot;duration&quot; property in &quot;passed&quot; statements.

* **cmi5\_9.5.4.1\_3** Assignable Unit (AU):  The AU MUST include the &quot;duration&quot; property in &quot;failed&quot; statements.



9.5.4.2 LMS statements that include duration

* **cmi5\_9.5.4.2\_1** Learning Management System (LMS): The duration property MUST be included in &quot;Abandoned&quot; statements.

* **cmi5\_9.5.4.2\_2** Learning Management System (LMS):  The duration property MUST be at least set to the total session time, calculated as the time between the &quot;Launched&quot; statement and the last statement (of any kind) issued by the AU.

9.5.5 Extensions

9.5.5.1 progress

* **cmi5\_9.5.5.1\_1** Assignable Unit (AU):  The progress extensions, if provided, must be an integer 0 to 100 inclusive.

9.5.5.2 reason

* **cmi5\_9.5.5.2\_1** Learning Management System (LMS): The LMS MUST set the &quot;reason&quot; extension value in &quot;waived&quot; statements.

9.6 Context

9.6.1 Registration

* **cmi5\_9.6.1\_1** Learning Management System (LMS):  At the time of registration, the LMS MUST evaluate moveOn criteria in the course structure and issue satisfied statements for AU with moveOn of &quot;Not Applicable&quot;.

* **cmi5\_9.6.1\_2** Learning Management System (LMS):  For all satisfied statements triggered outside of an AU launch session, the LMS MUST generate a unique session id and use it for those statements.

9.6.2 ContextActivities

9.6.2.1 cmi5 Category Activity

* **cmi5\_9.6.2.1\_1** Learning Management System (LMS):  The LMS must include An Activity object with an &quot;id&quot; of &quot;https://w3id.org/xapi/cmi5/context/categories/cmi5&quot; in the &quot;category&quot; context activities for all cmi5 defined statements it issues.

* **cmi5\_9.6.2.1\_2** Assignable Unit (AU):  The LMS must include An Activity object with an &quot;id&quot; of &quot;https://w3id.org/xapi/cmi5/context/categories/cmi5&quot; in the &quot;category&quot; context activities for all cmi5 defined statements it issues.

9.6.2.2 moveOn Category Activity

* **cmi5\_9.6.2.2\_1** Learning Management System (LMS):  Waived (cmi5 defined) statements issued by the LMS  MUST have an Activity object with an &quot;id&quot; of &quot;https://w3id.org/xapi/cmi5/context/categories/moveon&quot; in the &quot;category&quot; context activities list. Other statements issued by the LMS MUST NOT include this Activity.

* **cmi5\_9.6.2.2\_2** Assignable Unit (AU):  Passed and Completed (cmi5 defined) statements issued by the AU  MUST have an Activity object with an &quot;id&quot; of &quot;https://w3id.org/xapi/cmi5/context/categories/moveon&quot; in the &quot;category&quot; context activities list. Other statements issued by the AU MUST NOT include this Activity.

9.6.2.3 Publisher ID Grouping Activity

* **cmi5\_9.6.2.3\_1** Learning Management System (LMS):  The LMS MUST include an Activity object  in the &quot;grouping&quot; context activities list with an &quot;id&quot; property whose value matches the AU&#39;s id attribute from the course structure in the &quot;contextTemplate&quot; of the State API document LMS.launchdata.  (Written to the State API prior to launching the AU)

9.6.3 Extensions

9.6.3.1 session ID

* **cmi5\_9.6.3.1\_1** Learning Management System (LMS):  The LMS MUST generate a unique string identifier (&quot;session id&quot;) for  each AU launch session.

* **cmi5\_9.6.3.1\_2** Learning Management System (LMS):  The LMS MUST record the session ID in context template of LMS.launchdata in the State API (per Section 10) prior to launching an AU.

9.6.3.2 masteryScore

* **cmi5\_9.6.3.2\_1** Learning Management System (LMS):  LMS MUST add masteryScore as an extension of context in a &quot;Launched&quot; statement when masteryScore is provided in the LMS.launchdata.

* **cmi5\_9.6.3.2\_2** Assignable Unit (AU):  An AU MUST include the &quot;masteryScore&quot; value when provided in the LMS.launchdata as a context extension for &quot;passed&quot;/&quot;failed&quot; Statements.

9.6.3.3 launchMode

* **cmi5\_9.6.3.3\_1** Learning Management System (LMS):  LMS MUST add launchMode as an extension of context in a &quot;Launched&quot; statement when launchMode is provided in the LMS.launchdata.

9.6.3.4 launchURL

* **cmi5\_9.6.3.4\_1** Learning Management System (LMS):  The LMS MUST put a fully qualified URL equivalent to the one that the LMS used to launch the AU without the name/value pairs included as defined in section 8.1 as a context extension of the &quot;Launched&quot; statement.



9.6.3.5 publisherId

NA

9.6.3.6 moveOn

* **cmi5\_9.6.3.6\_1** Learning Management System (LMS):  LMS MUST add moveOn as an extension of context in a Launched statement provided in LMS.launchdata.

9.6.3.7 launchParameters

* **cmi5\_9.6.3.7\_1** Learning Management System (LMS):  LMS MUST add launchParametersas an extension of context in a Launched statement when launchParameters is provided in LMS.launchdata.

9.7 Timestamp

* **cmi5\_9.7\_1** Learning Management System (LMS):  All statements issued by the LMS  MUST include a timestamp property in UTC time.

* **cmi5\_9.7\_2** Assignable Unit (AU):  All statements issued by the AU  MUST include a timestamp property in UTC time.

10.0 xAPI State Data Model

* **cmi5_10_1**  Assignable Unit (AU):  The AU MUST NOT modify or delete the LMS.LaunchData State document.

* **cmi5_10_2**  Assignable Unit (AU):  The  AU MUST NOT overwrite any values provided by the LMS in the contextTemplate.

* **cmi5_10_3**  Learning Management System (LMS):  LMS MUST include a value for launchMode in LMS.LaunchData State document.

* **cmi5_10_4**  Assignable Unit (AU):  If the value for launchMode (provided in the LMS.LaunchData State document) is " Browse” or “Review”, then AU MUST NOT issue passed, failed, or completed (cmi5 defined) statements.

* **cmi5_10_5**  Learning Management System (LMS):  LMS MUST include a value for launchParameters in LMS.LaunchData State document.

* **cmi5_10_6**  Learning Management System (LMS):  LMS MUST include a value for masteryScore in LMS.LaunchData State 
document if a value for masteryScore is defined in the course structure. 

* **cmi5_10_7**  Learning Management System (LMS):  LMS MUST include a value for moveOn in LMS.LaunchData State document.

* **cmi5_10_8**  Assignable Unit (AU):  If the returnURL is provided in "LMS.LaunchData", the AU MUST redirect the current browser window to the returnURL when the AU is terminated.

* **cmi5_10_9**  Learning Management System (LMS):  LMS MUST provide an entitlementKey object in "LMS.LaunchData" if an entitlementKey value is present for the AU in the course structure.

* **cmi5_10_10**  Learning Management System (LMS):  LMS MUST set the entitlementKey object property “courseStructure” to the value of entitlementKey.courseStructure present for the AU in the course structure.

* **cmi5_10_11** Assignable Unit (AU): The AU MUST get the "contextTemplate" value from the "LMS.LaunchData" State document.

* **cmi5_10_12** Assignable Unit (AU): The AU MUST use the contextTemplate as a template for the "context" property in all xAPI statements it records to the LMS.

* **cmi5_10_13** Assignable Unit (AU): The AU MUST NOT overwrite any values provided in the contextTemplate.

11.0 xAPI Agent Profile Data Model

* **cmi5_11_1**  Assignable Unit (AU):  The AU MUST call the agent profile API to retrieve the “cmi5LearnerPreferences” document.

11.1 languagePreference

* **cmi5_11_1_1**  Assignable Unit (AU):  If the AU creates or updates the “cmi5LearnerPreferences” document, the languagePreference property value MUST be a comma-separated list of RFC 5646 Language Tags.

* **cmi5_11_1_2**  Learning Management System (LMS):  If the LMS creates or updates the “cmi5LearnerPreferences” document, the languagePreference property value MUST be a comma-separated list of RFC 5646 Language Tags.

11.2 audioPreference

* **cmi5_11_2_1**  Assignable Unit (AU):  If the AU creates or updates the “cmi5LearnerPreferences” document, the audioPreference property value MUST be either “on” or “off”.

* **cmi5_11_2_2**  Learning Management System (LMS):   If the LMS creates or updates the “cmi5LearnerPreferences” document, the audioPreference property value MUST be either “on” or “off”.

12.0 xAPI Activity Profile Data Model

13.0 Course Structure Data Requirements

13.1 Course Structure Data Model
* **cmi5_13_1_1**  Learning Management System (LMS):  All leading/trailing whitespace MUST be removed by the LMS on import of the course structure for all of the data elements defined in section 13.


13.1.1 Course Level Metadata
* **cmi5_13_1_1_1**  Course Structure (cmi5.xml):  The course must have an IRI value for the id attribute of the “course” element.
* **cmi5_13_1_1_2**  Course Structure (cmi5.xml):  The course must have an title element with at least one langstring element containing a descriptive title that identifies the course.
* **cmi5_13_1_1_3**  Course Structure (cmi5.xml):  The course must have an description element with at least one langstring element containing a verbal description of the course.

13.1.2 Block Metadata
* **cmi5_13_1_2_1**  Course Structure (cmi5.xml):  The course must have an IRI value for the id attribute of each “block” element. This id MUST be unique within the course structure.
* **cmi5_13_1_2_2**  Course Structure (cmi5.xml):  Each block element must have an title element with at least one langstring element containing a descriptive title that identifies the block.
* **cmi5_13_1_2_3**  Course Structure (cmi5.xml):  Each block element must have an description element with at least one langstring element containing a verbal description of the block.
* **cmi5_13_1_2_4**  Course Structure (cmi5.xml):  If objectives element is present in a block, each of its member objective elements must contain a idref attribute value referencing an objective id.


13.1.3 Objective Metadata

* **cmi5_13_1_3_1**  Course Structure (cmi5.xml):  The objectives element of the course (if present) must have at least one member “objective” element.
* **cmi5_13_1_3_2**  Course Structure (cmi5.xml):  Each objective element must have an IRI value for the id attribute.
* **cmi5_13_1_3_3**  Course Structure (cmi5.xml):  Each objective element must have an title element with at least one langstring element containing a descriptive title that identifies the objective.
* **cmi5_13_1_3_4**  Course Structure (cmi5.xml):  Each objective element must have an description element with at least one langstring element containing a verbal description of the objective.

13.1.4 AU Metadata

* **cmi5_13_1_4_1** Course Structure (cmi5.xml):  The course must have an IRI value for the id attribute of each “au” element.  This id MUST be unique within the course structure.
* **cmi5_13_1_4_2** Course Structure (cmi5.xml):  Each au element must have an title element with at least one langstring element containing a descriptive title that identifies the block.
* **cmi5_13_1_4_3** Course Structure (cmi5.xml):  Each au element must have an description element with at least one langstring element containing a verbal description of the block.
* **cmi5_13_1_4_4** Course Structure (cmi5.xml):  If objectives element is present in a au, each of its member objective elements must contain a idref attribute value referencing an objective id.
* **cmi5_13_1_4_5** Course Structure (cmi5.xml):  Each au element must have a launchMethod attribute with a value of either "OwnWindow" or "AnyWindow"
* **cmi5_13_1_4_6** Course Structure (cmi5.xml):  Each au element may have a masteryScore attribute.  If present, its value must be a decimal between 0 and 1.
* **cmi5_13_1_4_6** Course Structure (cmi5.xml):  Each au element may have a moveOn attribute.  If present, its value must be one of the following: "Passed"  "Completed","CompletedAndPassed",  "CompletedOrPassed", or “NotApplicable".
* **cmi5_13_1_4_7** Course Structure (cmi5.xml):  Each au element must have a url element URL that references the launch point of the AU.  The URL may be either fully qualified or relative. 

13.1.5 Vendor Specific Metadata (Extensions)

13.2 Course Structure XSD
* **cmi5_13_2_1** Course Structure (cmi5.xml):  Course Structures must conform to the following XSD: https://w3id.org/xapi/profiles/cmi5/v1/CourseStructure.xsd. 
* **cmi5_13_2_2** Course Structure (cmi5.xml):  The course structure must be placed in a file called cmi5.xml 

14.0 Course Package
* **cmi5_14_0_1** Learning Management System (LMS):  The LMS MUST be able to import a course structure from a cmi5.xml file.
* **cmi5_14_0_2** Learning Management System (LMS):  The LMS MUST be able to import a course structure from a Zip64 file (containing a cmi5.xml file).
* **cmi5_14_0_3** Learning Management System (LMS):  The LMS MUST be able to import a course structure from a Zip32 file (containing a cmi5.xml file).


14.1 Course Packages in ZIP Format

* **cmi5_14_1_1** Course Package: The course package (ZIP file) MUST contain the course structure XML file (cmi5.xml) at its root directory
* **cmi5_14_1_2** Course Package:  Any media not included in a ZIP course package MUST use fully qualified URL references in the Course Structure XML (cmi5.xml)
* **cmi5_14_1_3** Course Package:  The course package ZIP file format MUST follow the specification defined at https://www.pkware.com/support/zip-app-note (for either Zip 64 or Zip 32).
* **cmi5_14_1_4** Course Package: Any media included in a ZIP course package MUST use relative URL references in the Course Structure XML (cmi5.xml)

14.2 Course Structure XML Without a ZIP File Package

* **cmi5_14_2_1** Course Structure (cmi5.xml):  When a course structure XML (cmi5.xml) file is provided without a ZIP file package, all URL references MUST be fully qualified.
