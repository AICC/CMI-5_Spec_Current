#### 1.0 terminatedReason

<table>
    <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/terminatedReason</td></tr>
    <tr><th align="right" nowrap>Description:</th><td>Indicates the reason why an AU was "terminated"</td></tr>
    <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS SHOULD use this value to determine why the session was terminated. </td></tr>
    <tr><th align="right" nowrap>AU Usage:</th><td>The AU SHOULD set this value in statements it makes with the verb "Terminated". </td></tr>
    <tr><th align="right" nowrap>AU Obligation:</th><td>Optional</td></tr>
    <tr><th align="right" nowrap>LMS Obligation:</th><td>None</td></tr>
    <tr><th align="right" nowrap>Data type:</th><td>Object</td></tr>
    <tr><th align="right" nowrap>Value space:</th><td>An object containing a code and a message.  See sections 1.1, 1.2</td></tr>
    <tr><th align="right" nowrap>Sample value:</th><td>{ "code":206, "reason":{ "en":"Maximum number of attempts exceeded.", "fr":"Nombre maximum de tentatives dépassé" } }</td></tr>
</table>

#### 1.1 terminatedReason – code  

<table>
    <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/terminatedReason</td></tr>
    <tr><th align="right" nowrap>Description:</th><td>Specifies a code for a condition why an AU was "terminated" </td></tr>
    <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS SHOULD use this value to determine why the session was terminated. </td></tr>
    <tr><th align="right" nowrap>AU Usage:</th><td>The AU should set this value based one of the following conditions:
* 0 – Normal Termination
* These codes indicate that LMS admin intervention is not required 
* 101 - Prerequisites not met (another course)
* 102 - Time Bounds – Operating Hours of Business
* 103 - Location Restriction
* 104 - Payment Required
* 105 - User not Qualified (Regulatory and/or user profile related)
* 106 - Dependencies not Available (Browser, OS, hardware, Systems etc.)
* 107 - Assets not Available (Can’t reach a Video, etc.) 
* For all other conditions: 100 – LMS admin intervention is not required 
* These codes indicate that LMS admin intervention is required 
* 201 - MoveOn Incorrectly (Incompatible with AU) – Passed, Completed, etc. 
* 202 - MasteryScore – Can’t be obtainable value or lower than 
* 204 – LaunchParameters (Missing or Incorrect)
* 205 – EntitlementKey (Missing or Invalid)
* 206 - Too Many Attempts
* 207 - Max Duration Exceeded
* 208 - Cheating Suspected (Invalid User Behavior)
* 209 - Assets not Available (e.g. Can’t reach a Video, etc.)
* For all other conditions: 200 - Does Requires LMS admin intervention</td></tr>
    <tr><th align="right" nowrap>AU Obligation:</th><td>Required (if terminatedReason extension is used)</td></tr>
    <tr><th align="right" nowrap>LMS Obligation:</th><td>None</td></tr>
    <tr><th align="right" nowrap>Data type:</th><td>Integer</td></tr>
    <tr><th align="right" nowrap>Value space:</th><td>0, 100-107, 200-209</td></tr>
    <tr><th align="right" nowrap>Sample value:</th><td>200</td></tr>
</table>

#### 1.2 terminatedReason – message  

<table>
    <tr><th align="right" nowrap>ID:</th><td>https://w3id.org/xapi/cmi5/result/extensions/terminatedReason</td></tr>
    <tr><th align="right" nowrap>Description:</th><td>A human readable message explaining why an AU was "terminated" </td></tr>
    <tr><th align="right" nowrap>LMS Usage:</th><td>The LMS MAY use this value to report why the AU session was terminated. </td></tr>
    <tr><th align="right" nowrap>AU Usage:</th><td>If the terminatedReason extension is provided by the AU in a Terminated Statement, the AU MUST provide a human readable message describing the reason why the AU terminated.  The description SHOULD provide additional information about the cause and possible resolutions (e.g. LMS administrator intervention required). </td></tr>
    <tr><th align="right" nowrap>AU Obligation:</th><td>Required (if terminatedReason extension is used)</td></tr>
    <tr><th align="right" nowrap>LMS Obligation:</th><td>None</td></tr>
    <tr><th align="right" nowrap>Data type:</th><td>JSON Object</td></tr>
    <tr><th align="right" nowrap>Value space:</th><td>JSON Object in the following object structure:
* Key: "reason"
* Value: Object with the following at least one of the following name/value pairs:
    * Key: RFC 5646 Language Tags
    * Value: String</td></tr>
    <tr><th align="right" nowrap>Sample value:</th><td>{"reason":  { "en":"Maximum number of attempts exceeded.", "fr":"Nombre maximum de tentatives dépassé" } }</td></tr>
</table>
