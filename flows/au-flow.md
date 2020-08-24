## cmi5 Implementation Flow for an AU

The chart below provide a high-level description of the execution flow for an implementing cmi5 in an AU (Assignable Unit) - i.e. learning content.  Each of the shapes in the chart are further explained (below the chart).

![](./au-flow-chart.png?raw=true)

**LMS Launches AU**

AU parses Launch URL for connect information:

  - Fetch URL
  - Actor
  - Registration
  - Activity ID

*See Sections:*

  - 8.1 Launch Method

**<span class="underline">Get Authorization Token</span>**

AU uses the fetch URL to get the LRS access authorization token. The fetch URL can only be used once. The retrieved token must be used for all subsequent xAPI calls in the AU launch session.

*See Sections:*

  - 8.2 Authorization Token Fetch URL

**<span class="underline">Get State Document</span>**

The AU retrieves the state document *LMS.LaunchData* using the current registration id

The AU retrieves the following data from *LMS.LaunchData:*

  - **contextTemplate** – the AU must use this template all xAPI statement it makes (cmi5 allowed statements must omit the cmi5 category id)
  - **launchMode** – AU must provide behavior as described for Normal, Browse, or Review modes.
  - **launchParameters** -
      - MasteryScore
      - moveOn
      - returnURL
     - entitlementKey

*See Sections:*

  - 13.1.4 AU Metadata - moveOn
  - 9.3.9 Satisfied

**<span class="underline">Get Agent Profile</span>**

The AU retrieves the “cmi5LearnerPreferences” document from the Agent Profile using the Actor provided from the Launching URL.

The AU checks for “languagePreference" and "audioPreference" values.
  - If the AU supports multiple languages it should set the language indicated in “languagePreference" as the default language.
  - If the AU has audio, it should set whether the audio is on or off based on the value indicated in “audioPreference"

*See Sections:*
  - 11.0 xAPI Agent Profile Data Model

**<span class="underline">Perform AU Setup</span>**

The AU performs it is internal setup activities prior to being for learner interaction.

This includes activities such as:

  - Retrieving AU’s previous state from LRS
  - Loading resources/media
  - Processing data from cmi provided documents *LMS.LaunchData* and *cmi5LearnerPreferences*

**<span class="underline">Send Initialized Statement</span>**

To indicate that the AU is ready for learner interaction, the AU sends a Statement to the LRS using the “initialized” verb and the other “cmi5 defined” statement required data elements (i.e. object requirements, context template, extensions, etc.).

*See Sections:*

  - 9.1 Statement ID
  - 9.2 Actor
  - 9.3 Verbs
  - 9.3.2 Initialized
  - 9.4 Object
  - 9.6.2.1 cmi5 Category Activity
  - 9.6.3.1 session ID
  - 10.0 xAPI State Data Model (Context Template)

**<span class="underline">Deliver Learning Experience</span>**

The AU delivers the learning experience to the learner. As the AU processes its events, it may

  - Send xAPI Statements specifically defined for cmi5 completion and/or mastery. (see following sections) Each of these statements are only written once during a registration  
      - Completed
      - Failed 
      - Passed

  - Send custom xAPI statements provided they follow cmi5 “allowed rules” (i.e. object requirements, context template, extensions, etc.). The AU can send as many of these as desired during a session.

*See Sections:*
  - 7.1.3 Types of Statements
  - 9.3 Verbs
  - 9.4 Object
  - 9.6.3.1 session ID
  - 10.0 xAPI State Data Model (Context Template)

**<span class="underline">Write Completed Statement</span>**

When the learner views or performs all of the relevant activities, the AU sends a Statement to the LRS using the “completed” verb and the other “cmi5 defined” statement required data elements (i.e. object requirements, context template, extensions, etc.).

*See Sections:*
  - 9.1 Statement ID
  - 9.2 Actor
  - 9.3 Verbs
  - 9.3.3 Completed
  - 9.4 Object
  - 9.6.2.1 cmi5 Category Activity
  - 9.6.3.1 session ID
  - 10.0 xAPI State Data Model (Context Template)

**<span class="underline">Write Failed Statement</span>**

If the AU is designed to have a judged activity and the learner fails to meet the minimum criteria (e.g. passing a quiz), the AU sends a Statement to the LRS using the “failed” verb and the other “cmi5 defined” statement required data elements (i.e. object requirements, context template, extensions, etc.).

*See Sections:*
  - 9.1 Statement ID
  - 9.2 Actor
  - 9.3 Verbs
  - 9.3.5 Failed
  - 9.4 Object
  - 9.6.2.1 cmi5 Category Activity
  - 9.6.3.1 session ID
  - 10.0 xAPI State Data Model (Context Template)

**<span class="underline">Write Passed Statement</span>**

If the AU is designed to have a judged activity and the learner successfully to meets or exceeds the minimum criteria (e.g. passing a quiz), the AU sends a Statement to the LRS using the “passed” verb and the other “cmi5 defined” statement required data elements (i.e. object requirements, context template, extensions, etc.).

*See Sections:*
  - 9.1 Statement ID
  - 9.2 Actor
  - 9.3 Verbs
  - 9.3.4 Passed
  - 9.4 Object
  - 9.6.2.1 cmi5 Category Activity
  - 9.6.3.1 session ID
  - 10.0 xAPI State Data Model (Context Template)

**<span class="underline">Exit AU</span>**

Depending on the AU design, the learner may take an action to exit from the presentation or the AU may start its exit process based on some other criteria.

**<span class="underline">Terminate</span>**

When the AU was terminated by the Learner and that the AU will not be sending any more statements for the session, it sends a Statement to the LRS using the “terminated” verb and the other “cmi5 defined” statement required data elements (i.e. object requirements, context template, extensions, etc.).

*See Sections:*
  - 9.1 Statement ID
  - 9.2 Actor
  - 9.3 Verbs
  - 9.3.8 Terminated
  - 9.4 Object
  - 9.6.2.1 cmi5 Category Activity
  - 9.6.3.1 session ID
  - 10.0 xAPI State Data Model (Context Template)

**<span class="underline">Redirect or Close Window</span>**

After the AU has finished all processing, it will one of the following things:
  - Nothing (no redirection)
  - Close the Browser Window
  - Redirect to another URL

*See Sections:*
  - 10.0 xAPI State Data Model – returnURL
  - 13.1.4 AU Metadata - launchMethod
