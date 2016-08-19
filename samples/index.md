---
---

# JSON Samples

------

## Scenarios

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

### Typical No Credit Session

[View](scenarios/01-typical-non_credit_session)

{% include scenarios/descriptions/01-typical-non_credit_session.md %}

### Completed or Passed Move On - Passed

[View](scenarios/03-completed_or_passed-passed)

{% include scenarios/descriptions/03-completed_or_passed-passed.md %}

### Completed or Passed Move On - Completed

[View](scenarios/04-completed_or_passed-completed)

{% include scenarios/descriptions/04-completed_or_passed-completed.md %}

### Completed or Passed Move On - Failed But Completed

[View](scenarios/05-completed_or_passed-failed_completed)

{% include scenarios/descriptions/05-completed_or_passed-failed_completed.md %}

### Completed Move On - Completed

[View](scenarios/06-completed-completed)

{% include scenarios/descriptions/06-completed-completed.md %}

### Passed Move On - Passed

[View](scenarios/07-passed-passed)

{% include scenarios/descriptions/07-passed-passed.md %}

### Passed Move On with Mastery Score - Passed

[View](scenarios/08-passed-masteryScore-passed)

{% include scenarios/descriptions/08-passed-masteryScore-passed.md %}

### Completed and Passed Move On

[View](scenarios/09-completed_and_passed)

{% include scenarios/descriptions/09-completed_and_passed.md %}

### Completed and Passed Move On with Mastery Score

[View](scenarios/10-completed_and_passed-masteryScore)

{% include scenarios/descriptions/10-completed_and_passed-masteryScore.md %}

### Completed and Passed Move On with Mastery Score - Initial Failure

[View](scenarios/11-completed_and_passed-masteryScore-failed_first)

{% include scenarios/descriptions/11-completed_and_passed-masteryScore-failed_first.md %}

### "cmi5 allowed" Statements

[View](scenarios/12-allowed_statement)

{% include scenarios/descriptions/12-allowed_statement.md %}

### Usage of Progress Extension

[View](scenarios/13-progress_usage)

{% include scenarios/descriptions/13-progress_usage.md %}

### Completed and Passed - Multiple Session to Satisfy

[View](scenarios/14-completed_and_passed-multiple_sessions)

{% include scenarios/descriptions/14-completed_and_passed-multiple_sessions.md %}

### Review Launch Mode

[View](scenarios/15-review_mode)

{% include scenarios/descriptions/15-review_mode.md %}

### Non-Applicable Move On - No Launch Session

[View](scenarios/16-not_applicable-no_launch)

{% include scenarios/descriptions/16-not_applicable-no_launch.md %}

### Abandoned Session

[View](scenarios/17-abandoned_session)

{% include scenarios/descriptions/17-abandoned_session.md %}

-------

## License Agreement

Copyright 2012-2016 Advanced Distributed Learning (ADL) Initiative, U.S. Department of Defense

Licensed under the Apache License, Version 2.0 (the "License"). You may not use this file except in compliance with the License.
You may obtain a copy of the License at http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed
on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for
the specific language governing permissions and limitations under the License.

-------
