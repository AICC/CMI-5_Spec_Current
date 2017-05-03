<p align=center><img src="https://cloud.githubusercontent.com/assets/1656316/9965238/bc9deb2c-5de9-11e5-9954-63aa03873f88.png" align=center></p>

#cmi5 JSON Samples

------

##Scenarios

These samples represent various scenarios possible when running content using the cmi5 runtime definitions. Most of these scenarios are based on the "Simple" Course Structure Example from Section 15.1 of the specification.

Some common attributes about all samples:

* They use the same "actor" in all statements, normally the `account.name` property would be unique to the learner and the `account.homePage` unique to the LMS
* They represent the statement as constructed before sending to the LRS, therefore they do not include properties set by the LRS such as "stored", "authority" and "version"
* A single registration is used in each separate scenario and files are numbered in request order
* LMS Launch Data for a session is included in the samples, and for scenarios with multiple sessions is included for each session
* Launch Mode is `Normal` unless specified
* Fetch URL request response is only shown in the simple session, but is necessary for every session
* Duration property values are included where required but are all very short in nature because of how the sessions were generated, in practice durations are likely to be substantially longer
* Statements represent the minimum requirements per the cmi5 specification, in practice additional properties will be common, particularly in the context

Discrepancies with the above are pointed out where necessary.

###Simple Session

[01-simple_session](01-simple_session)

Session that includes the minimum data, and is associated with a `NotApplicable` Move On criteria which results in immediate satisfaction of the course upon registration creation. Includes Satisfied Statement, Launched Statement, Fetch URL response, LMS.LaunchData State content, Initialized Statement, and Terminated Statement.

###Abandoned Session

[02-simple_abandoned_session](02-simple_abandoned_session)

Session that is abandoned, essentially a session without a Terminated Statement. Includes Satisfied Statement (from `NotApplicable` Move On), Launched Statement, LMS.LaunchData State content, Initialized Statement, and Abandoned Statement.

###Completed or Passed Move On - Passed

[03-completed_or_passed-passed](03-completed_or_passed-passed)

Session from an AU that has its Move On criteria set to `CompletedOrPassed` that has a Passed Statement recorded. LMS.LaunchData content shows `CompletedOrPassed` Move On criteria as does the Launched Statement context extensions. Note that the Satisfied Statement is issued immediately following the Passed Statement.

###Completed or Passed Move On - Completed

[04-completed_or_passed-completed](04-completed_or_passed-completed)

Session from an AU that has its Move On criteria set to `CompletedOrPassed` that has a Completed Statement recorded. LMS.LaunchData content shows `CompletedOrPassed` Move On criteria as does the Launched Statement context extensions. Note that the Satisfied Statement is issued immediately following the Completed Statement.

###Completed or Passed Move On - Failed But Completed

[05-completed_or_passed-failed_completed](05-completed_or_passed-failed_completed)

Session from an AU that has its Move On criteria set to `CompletedOrPassed` that has a Failed Statement recorded followed by a Completed Statement. Note that the Satisfied Statement is issued immediately after the Completed Statement, regardless of the Failed Statement's existence.

###Completed Move On - Completed

[06-completed-completed](06-completed-completed)

Session from an AU that has its Move On criteria set to `Completed` that has a Completed Statement recorded. LMS.LaunchData content shows `Completed` Move On criteria as does the Launched Statement context extensions. Note that the Satisfied Statement is issued immediately following the Completed Statement.

###Passed Move On - Passed

[07-passed-passed](07-passed-passed)

Session from an AU that has its Move On criteria set to `Passed` that has a Passed Statement recorded. LMS.LaunchData content shows `Passed` Move On criteria as does the Launched Statement context extensions. Note that the Satisfied Statement is issued immediately following the Passed Statement.

###Passed Move On with Mastery Score - Passed

[08-passed-masteryScore-passed](08-passed-masteryScore-passed)

Session from an AU that has its Move On criteria set to `Passed` and includes a Mastery Score that has a Passed Statement with score recorded. LMS.LaunchData content shows `Passed` Move On criteria and `0.9` Mastery Score as does the Launched Statement context extensions.

###Completed and Passed Move On

[09-completed_and_passed](09-completed_and_passed)

Session from an AU that has its Move On criteria set to `CompletedAndPassed` that has both a Passed Statement and a Completed Statement recorded. LMS.LaunchData content shows `CompletedAndPassed` Move On criteria as does the Launched Statement context extensions. Note that the Satisfied Statement is issued following the Completed Statement and not after the earlier Passed Statement.

###Completed and Passed Move On with Mastery Score

[10-completed_and_passed-masteryScore](10-completed_and_passed-masteryScore)

Same as the Completed and Passed Move On scenario but with a passing score recorded. Note Passed statement includes `result.score.scaled` of `0.88` which is greater than the Mastery Score of `0.86` as defined in the LMS.LaunchData, Launched Statement, and Passed Statement.

###Completed and Passed Move On with Mastery Score - Initial Failure

[11-completed_and_passed-masteryScore-failed_first](11-completed_and_passed-masteryScore-failed_first)

Same as the Completed and Passed Move On with Mastery Score scenario but with an initial Failed Statement. Note Failed statement includes `result.score.scaled` of `0.82` which is less than the Mastery Score of `0.86` as defined in the LMS.LaunchData, Launched Statement, and Failed Statement. The following Passed statement includes a `result.score.scaled` of `0.91` which is greater than the Mastery Score of `0.86` which is also included in the Passed Statement.

###"cmi5 allowed" Statements

[12-allowed_statement](12-allowed_statement)

Session showing the use of "cmi5 allowed" Statements. Includes a single "cmi5 allowed" Statement using the "experienced" verb. Note the statement must happen between the Initialized and Terminated statements and uses the context template from the LMS.LaunchData.

###Usage of Progress Extension

[13-progress_usage](13-progress_usage)

Session showing the use of the "progress" extension. Includes 4 "cmi5 allowed" Statements that have an increasing progress of 25% (`25`), 50% (`50`), 75% (`75`) and 100% (`100`) followed by a Completed Statement. Note the "progress" extension is not included in the Completed Statement.

###Completed and Passed - Multiple Session to Satisfy

[14-completed_and_passed-multiple_sessions](14-completed_and_passed-multiple_sessions)

Multiple session scenario showing a `CompletedAndPassed` Move On criteria where the Passed and Completed Statements occur in separate sessions. Note LMS.LaunchData differs between the two because the session identifier is contained therein. Each session includes distinct Launched, Initialized, and Terminated Statements which include distinct context because of the distinct sessions.

###Review Launch Mode

[15-review_mode](15-review_mode)

Session with a Launch Mode of `Review`. Likely a previous session has recorded completion and pass or waived. Note the Launch Mode value in the Launched Statement context extensions and the LMS.LaunchData.

-------

<a id="license_agreement"></a>
#License Agreement

Copyright 2012-2016 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defense

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License.
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed
on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for
the specific language governing permissions and limitations under the License.

-------
