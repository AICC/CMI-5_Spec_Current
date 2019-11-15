# xAPI/TinCan Package vs. cmi5 Comparison

## Executive Summary

*The most commonly used mechanism for deploying xAPI-based learning content with an LMS does not have interoperability beyond launch and access to the LRS by the content –more is needed for any* *practical implementation.* The cmi5 specification addresses this need and is therefore recommended by the US Dept. of Defense *(See DoDI 1322.26 - <https://adlnet.gov/dodi/dodi-xapi>*)

The xAPI specification makes no mention of an LMS as it was intended to track training activities beyond the LMS. In the absence of a defined specification for packaging and launching xAPI activities from an LMS, early in life cycle of xAPI (2013), a quasi-de facto mechanism was created to fill the void. This mechanism is based on a document titled “Incorporating a TinCan LRS into an LMS” (<https://github.com/RusticiSoftware/launch/blob/master/lms_lrs.md>). While the TinCan packaging mechanism is very thinly defined and is not an ADL specification, it has, unfortunately, been widely adopted in the Learning industry.

To address this, the ADL Initiative and the Aviation Industry Computer-Based Training Committee (AICC) jointly created the cmi5 specification. ADL actively maintains cmi5 as an xAPI profile that defines the “LMS launches content" use case. cmi5 is implemented using the Experience API (xAPI) as the content-to-LMS communication layer. cmi5 provides many elements that the TinCan package does not support:

  - ***<span class="underline">Consistent</span>* rules that define completion criteria, such as a mastery score.**
  - **Defined tracking of results.**
  - **Defined method to launch content without a pop-up window.**
  - **Multi-lesson packages.**
  - **Nested blocks of lessons.**
  - **Complete course definition, including title and objectives.**
  - **Built-in mechanism for support of distributed content.**

Note: There has been some confusion on the use of the terms “xAPI” vs. “TinCan” with relation to the packaging of xAPI content for an LMS. This “TinCan package” is not defined in the xAPI Specification and the only known documentation is in the document discussed above. Therefore, for the remainder of this document we will refer to that package as “TinCan”.

## xAPI/TinCan Package vs. cmi5 Comparison for L&D Professionals

The following table provides a high level comparison of TinCan to cmi5 for learning & development professionals who develop/deliver TinCan content.

<table>
<thead>
<tr class="header">
<th><strong><br />
Feature</strong></th>
<th><strong>xAPI/TinCan<br />
Package</strong></th>
<th><strong><br />
cmi5</strong></th>
<th><strong><br />
Description</strong></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td>Normalized Criteria For Completion</td>
<td>No</td>
<td>Yes</td>
<td><p>cmi5 establishes interoperable rules for determining completion/mastery of learning activities. TinCan has no completion criteria defined.</p>
<p>Establishing completion/mastery consistency between systems implementing TinCan requires custom effort and does not provide interoperability.</p></td>
</tr>
<tr class="even">
<td>Normalized Reporting</td>
<td>No</td>
<td>Yes</td>
<td>cmi5 establishes rules for records (statements) to include identifiers for learner session so that records can be more easily grouped for normalized reports. TinCan has no features to provide this functionality.</td>
</tr>
<tr class="odd">
<td>Multiple Lesson Support</td>
<td>No</td>
<td>Yes</td>
<td>cmi5 packages allow for multiple launchable presentations in a defined hierarchy with criteria for progression. TinCan allows for only one launchable presentation.</td>
</tr>
</tbody>
</table>

## xAPI/TinCan Package vs. cmi5 Detailed Comparison

The TinCan package specification does not have any normalizing rules for xAPI usage. The TinCan package only normalizes the launch, LRS connect information, and XML metadata describing statements that the learning activity makes.

<table>
<thead>
<tr class="header">
<th><strong><br />
Feature</strong></th>
<th><strong>xAPI/TinCan<br />
Package</strong></th>
<th><strong><br />
cmi5</strong></th>
<th><strong><br />
Description</strong></th>
</tr>
</thead>
<tbody>
<tr >
<td>Content Package</td>
<td>Yes</td>
<td>Yes</td>
<td>TinCan has a package containing remote (or local) content and a manifest that specifies content entry point, activity definitions, and interactions. cmi5 has an XML course structure that can reference remote (or local) content entry point. Both have a ZIP file for transferring content (locally).</td>
</tr>
<tr >
<td>Mastery Score</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 course structure can include a mastery score for each lesson. The mastery score may be set by the LMS administrator.</td>
</tr>
<tr >
<td>Completion Criteria</td>
<td>No</td>
<td>Yes</td>
<td>cmi5 includes a “move on” criteria that defines specific verb patterns that must be received in order to receive credit for a lesson.</td>
</tr>
<tr >
<td>Is an ADL Initiative or standards organization specification</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification was jointly developed by ADL and AICC.</td>
</tr>
<tr >
<td>Defined use of the xAPI “Result.Score” property.</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines rules for specific verbs related to the Result.Score including scaled, raw, min, and max values.</td>
</tr>
<tr >
<td>Defined use of the xAPI “Result.Success” property</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines rules for defined verbs allowed to use the Result.Success property.</td>
</tr>
<tr >
<td>Defined use of xAPI “Result.Duration” property.</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines rules for that require defined verbs to include the Result.Duration property and guidance for time calculation.</td>
</tr>
<tr >
<td>Defined use of the xAPI “Result.Completion” property.</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines rules for defined verbs allowed to use the Result.Completion property.</td>
</tr>
<tr >
<td>Ability to “waive” lessons.</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines a standard verb that indicates that an AU has been satisfied by alternative means such as manual override (e.g. instructor discretion)</td>
</tr>
<tr >
<td>Requires use of the xAPI “Context.registration” property</td>
<td>No</td>
<td>Yes</td>
<td>Although the TinCan package passes a registration in the launch command, it does not require Context.registration to be set in xAPI statements.</td>
</tr>
<tr >
<td>Sequencing of statements</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines a predicable sequence of verb statements in an AU session.</td>
</tr>
<tr >
<td>Session management</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification defines rules for managing session data and identifying statement association with a given session.</td>
</tr>
<tr >
<td>Authentication management</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification provides for a “fetch URL” service that supplies an authentication token to the AU. This method reduces the risk of token reuse by unauthorized actors.</td>
</tr>
<tr >
<td>Allows launching and tracking of multiple AUs in a course</td>
<td>No</td>
<td>Yes</td>
<td>The cmi5 specification allows a course to contain from 1 to 1000 AUs</td>
</tr>
<tr >
<td>Is conformant to the xAPI Specification</td>
<td>No</td>
<td>Yes</td>
<td>The TinCan package, by adding additional parameters in calls to the xAPI Statement API, will fail LRS Conformance unless a specific "allow list" exception is made. In addition, the LRS action expected based on these parameters is not thoroughly defined.</td>
</tr>
</tbody>
</table>

### Content Package

TinCan has a package containing remote (or local) content and a manifest that specifies content entry point, activity definitions, and interactions. cmi5 has an XML course structure that can reference remote (or local) content entry point. Both have a ZIP file for transferring content (locally)

  - **Both have:** packages, remote and local content

  - **TinCan does not have**: objectives, completion criteria, block hierarchy, and a Zip 64 option.

### Mastery Score

The cmi5 course structure can include a mastery score for each AU. Depending on the LMS feature set, the mastery score can be overridden/modified by the LMS administrator after the course structure is imported. The TinCan package does not have definition for mastery score. The ability to set Mastery Score allows the LMS to determine passing or failure of judged activity in the AU (if the AU has scoring).

### Completion Criteria

cmi5 includes a “move on” criteria that defines specific verb patterns that must be received in order to receive credit for a lesson. For example, the course structure could define that a given AU requirement is satisfied if a Completed or Passed verb is sent by the AU. It is also possible to define an AU as being “optional” to the completion of a course. The TinCan package has no defined completion criteria.

### Is an ADL Initiative or standards organization specification.

The cmi5 specification was jointly developed by the ADL Initiative, the AICC, and other industry experts. The spec was developed through a series of open meetings and reviews over a period of several years. The cmi5 specification is a xAPI profile that is fully integrated with launch and packaging rules for LMS delivery of content.

The TinCan package is an informal proposal document that was created at the initial release of the xAPI specification. It has not had formal reviews and extensive community/industry input.

### Defined use of the xAPI “Result.Score” property.

The cmi5 specification is a xAPI profile that defines usage of Result.Score for specific verbs including scaled, raw, min, and max values. Result.Score important for judging mastery or comprehension.

The TinCan package has no rules defined for Result.Score usage.

### Defined use of the xAPI “Result.Success” property.

The cmi5 specification is a xAPI profile that defines usage of Result.Success for specific verbs. Result.Success important for judging mastery or comprehension.

The TinCan package has no rules defined for Result.Success usage.

### Defined use of xAPI “Result.Duration” property.

The cmi5 specification is a xAPI profile that defines usage of Result.Duration property for specific verbs and guidance for time calculation. Result.Duration is important for calculating time spent in learning activities.

The TinCan package has no rules defined for Result.Duration usage.

### Defined use of the xAPI “Result.Completion” property.

The cmi5 specification is a xAPI profile that defines usage of Result.Completion for specific verbs. Result.Completion is important for determining if the learner has viewed all relevant materials in an AU.

The TinCan package has no rules defined for Result.Completion usage.

### Ability to "waive" lessons.

The cmi5 specification defines a standard verb that indicates that an AU has been satisfied by alternative means such as manual override (e.g. instructor discretion). This is very a useful feature for defining “testing out” scenarios in the LMS to skip AU’s in a course. It can also be used if the instructor has other reasons to believe (such as documentation) that the learner has already mastered the content.

The TinCan package has definition of “waive” features.

### Requires use of the xAPI “Context.registration” property

Although the TinCan package passes a registration in the launch command, it does not require Context.registration to be set in xAPI statements. With cmi5 the LMS defines the Context.registration property value and provides it to the AU for it to include in its statements. This ensures that Context.registration is included in statements providing better normalization of data for reporting and managing enrollment records.

### Sequencing of statements

The TinCan package specification has activity definitions but no defined sequence of verb statements. The cmi5 specification defines rules for a predicable sequence of verb statements in an AU session. All AU’s must have defined statements for the start and end of a session. Statements for completion or mastery must be provided before session ending statements.

### Session management

TinCan has no features for managing sessions and identifying statements from a given session. The cmi5 specification defines rules for managing session state data and identifying statement association with a given session. This enables reporting based on each individual launch of an AU.

### Authentication management

The cmi5 specification provides for a “fetch URL” service that supplies an authentication token to the AU. The fetch URL is “one time” use URL that the AU uses to retrieve the authentication token. Additional calls to the fetch URL are rejected. This method reduces the risk of token reuse by unauthorized actors.

### Allows launching and tracking of multiple AUs in a course

The cmi5 specification requires the LMS to support courses with 1 to (at least) 1000 AU’s. This allows for a large, hierarchical structure of course elements (AUs) that can be reused and recombined in other structures in an interoperable manner. The TinCan package only allows for one launchable activity.

### Is conformant to the xAPI Specification

The TinCan package, by adding additional parameters in calls to the xAPI Statement API, will fail LRS Conformance unless a specific “allow list” exception is made. In addition, the LRS action expected based on these parameters is not thoroughly defined. This creates many interoperability issues. cmi5 has no features (or requirements) that conflict with the xAPI specification. LRS’s that support cmi5 can pass the xAPI conformance test without such conflicts.
