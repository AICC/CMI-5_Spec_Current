## cmi5 Conformance Testing Procedures Document (Working Draft - June 29, 2018)

****Disclaimer: This is a working draft, do NOT implement systems based on this information.****

_Disclaimers/Limits_


> Because compliance cannot be verified – it does not mean that an LMS (or AU) is not cmi5 conformant.
> 
> 
> Test suite AU failure to execute due to software/environment conflicts…

**<span class="underline">LMS</span>**

  - (TestSuite) Create Test Course Structure(s)
    
      - Multiple course structures
        
          - ZIP Package vs XML only
        
          - Mix of Relative and Fully Qualified URLS
        
          - One for size test 1000 + AU’s
            
              - 
          - Smaller one for Completion (Satisfied Test)
            
              - Large enough to test all MoveOn Criteria
                
                  - Blocks, AU’s

  - (Human) Import that structure(s) into the LMS (admin user)

  - (Human) Register the learner (admin User)

  - (Human) Access the course as a learner
    
      - Selected AU’s (not all)

  - (Machine) AU’s (Testsuite) inspect LMS/LRS data

  - (Human) Procedure for learner to follow thru the course(s).
    
      - Initial entry
    
      - Re-entry of AU’s

  - (Human) Modify course structure (admin user) and verify effect as a learner
    
      - Eg, MasteryScore, MoveOn, etc

**<span class="underline">AU (Content) - Individually</span>**

  - (Human) add a reference (URL) to AU to inspect

  - (Human) Launch *<span class="underline">the</span>* AU and Interact with AU

  - (Human) Re-entry to AU’s
    
      - Launch in different modes
        
          - Review, Normal, Browse

  - (Machine) Testsuite will inspect AU xapi data

**<span class="underline">AU (Content) – Course Structure (on or more)</span>**

  - (Machine) Testsuite (LMS) – import/validate a course structure

  - (Human) Launch *<span class="underline">each</span>* AU in the course and Interact with AU

  - (Human) Re-entry to AU’s
    
      - Launch in different modes
        
          - Review, Normal, Browse

  - (Machine) Testsuite will inspect AU xapi data

**<span class="underline">Course Structure/Package</span>**

  - (Machine) Inspect XML
    
      - XSD validation
    
      - Relative pathing & Fully Qualified URL

  - (Machine) Inspect Package
    
      - Inspect ZIP
    
      - File existence validation (ZIP)
        
          - Content
        
          - XML file
    
      - ZIP format (32/64)

# Testing Procedures

**Small course testing**

  - (Human) Import that structure(s) into the LMS (admin user)

  - (Human) Register multiple learners (admin User) – User 1, 2, 3….

  - (Human) Access the course as a learner 1
    
      - Launch AU's in order
        
          - Do Not Launch (AU5 – Not applicable)
    
      - Complete all AU's with minimum MoveOn Criterial
    
      - Single Entry
    
      - Final Check AU (Assess results)
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - AU x is a test suite specific tool (not Normal AU scenario)
        
          - Alternate Credentials to Access to LRS for LMS issued statements.
            
              - AUx may not have sufficient access to query the LRS for statements issued by other AU’s – So alternate credentials would need to be provided *(e.g. AUx will need to have a login form for alternate access- for “deep queries”)*

  - (Human) Access the course as a learner 2
    
      - Launch AU's in order
    
      - Complete all AU's with MoveOn Criteria
    
      - Multiple Entry
    
      - Final Check AU (Assess results
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

  - (Human) Access the course as a learner 3
    
      - Launch AU's in any order
    
      - Multiple Entry (Re-launching - Exiting and Re-entering AU)
    
      - Complete all AU's except AU6
        
          - Partially Complete AU6 and re-enter
        
          - Complete AU6
    
      - Final Check AU(Assess results
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

**Large course testing**

  - (Machine) AU's (Testsuite) inspect LMS/LRS data

  - (Human) Procedure for learner to follow thru the course(s).
    
      - Initial entry
    
      - Re-entry of AU's

  - (Human) Modify course structure (admin user) and verify effect as a learner
    
      - Eg, MasteryScore, MoveOn, etc

  - Final Check AU(Assess results)

\<?xml version="1.0" encoding="utf-8"?\>

\<courseStructure xmlns="https://w3id.org/xapi/profiles/cmi5/v1/CourseStructure.xsd"\>

\<course id="http://course-repository.example.edu/identifiers/courses/02baafcf"\>

\<title\>

\<langstring lang="en-US"\>Intro to Web Based Content\</langstring\>

\</title\>

\<description\>

\<langstring lang="en-US"\>

This course will introduce you into the basics integrating xAPI with web

based content.

\</langstring\>

\</description\>

\</course\>

\<block id="<http://www.example.com/identifiers/aublock/005430bf-b3ba-45e6-b47b-d629603d83d8>" \>

\<au id=<http://course-repository.example.edu/identifiers/courses/02baafcf/aus/4c07>

launchMethod="OwnWindow"

masteryScore="0.8501”

moveOn="Passed"

activityType="http://adlnet.gov/expapi/activities/media"

\>

\<title\>

\<langstring lang="en-US"\>Guess a Number\</langstring\>

\</title\>

\<description\>

\<langstring lang="en-US"\>

This game uses xAPI to track the start and stop as well as the player's

guesses.

\</langstring\>

\</description\>

\<url\>./game.html\</url\>

\<launchParameters\>xyz123\</launchParameters\>

\<entitlementKey\>xyz-123-9999\</entitlementKey\>

\</au\>

\</block\>

\</courseStructure\>

  - Rollup discussion – Blocks with Blocks only as children

**<span class="underline">Small Course Structure test (LMS)</span>**

  - Created by testsuite (Static or generated)

  - Zip File with content

  - Mix of relative and fully qualified URL’s

  - Nested Blocks

  - Mixed Blocks - Blocks with AU’s and Block Children

  - Blocks with Block children only

**<span class="underline">Block1</span>**

> <span class="underline">AU0</span>

  - launchMethod="OwnWindow"

  - moveOn=" Completed "

  - \<Fully Qualified url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> **<span class="underline">Block1.1</span>**
> 
> <span class="underline">AU1</span>

  - launchMethod="OwnWindow"

  - masteryScore="0.8501”

  - moveOn="Passed"

  - \<Relative url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> <span class="underline">AU2</span>

  - launchMethod="OwnWindow"

  - moveOn=" Completed "

  - \<Relative url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> <span class="underline">AU3</span>

  - launchMethod="OwnWindow"

  - masteryScore="0.8501”

  - moveOn="CompletedAndPassed "

  - \<Relative url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> <span class="underline">AU4</span>

  - launchMethod="OwnWindow"

  - masteryScore="0.8501”

  - moveOn="CompletedOrPassed "

  - \<Relative url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> <span class="underline">AU5</span>

  - launchMethod="OwnWindow"

  - moveOn="NotApplicable"

  - \<Relative url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> **<span class="underline">Block1.1.1</span>**
> 
> **<span class="underline">Block1.1.1.1</span>**
> 
> <span class="underline">AU6</span>

  - launchMethod="OwnWindow"

  - moveOn=" Completed"

  - \<Fully Qualified url\>

  - \<launchParameters\>

  - \<entitlementKey\>

**<span class="underline">AUx</span>**

  - launchMethod="OwnWindow"

  - moveOn="NotApplicable"

  - \<Relative url\>

  - \<launchParameters\>

  - \<entitlementKey\>

**<span class="underline">Large Course Structure test (LMS) Test</span>**

  - Created by testsuite (Static or generated)

  - Has 1001 AU’s

  - Fully Qualified URL

  - Zipped and XML only

**<span class="underline">Block1</span>**

> <span class="underline">AU1</span>

  - launchMethod="OwnWindow"

  - moveOn=" Completed "

  - \<url\>

  - \<launchParameters\>

  - \<entitlementKey\>

> …
> 
> <span class="underline">AU1 1001</span>

  - launchMethod="OwnWindow"

  - moveOn=" Completed "

  - \<url\>

  - \<launchParameters\>

  - \<entitlementKey\>

  - 
# Testing Procedures

**<span class="underline">Small course testing</span>**

  - TestSuite Generates a test course structure (XML)
    
      - (Initially) Static one to start
    
      - *(Later)* a parameter driven generation of course structure.

  - (Human) Import that structure(s) into the LMS (admin user)

  - (Human) Register multiple learners (admin User) – User 1, 2, 3….

  - (Human) Access the course as a learner 1
    
      - Launch AU’s in order
        
          - Do Not Launch (AU5 – Not applicable)
    
      - Complete all AU’s with minimum MoveOn Criterial
    
      - Single Entry
    
      - Final Check AU
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

  - (Human) Access the course as a learner 2
    
      - Launch AU’s in order
    
      - Complete all AU’s with MoveOn Criterial
    
      - Multiple Entry
    
      - Final Check AU
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

  - (Human) Access the course as a learner 3
    
      - Launch AU’s in any order
    
      - Multiple Entry (Re-launching - Exiting and Re-entering AU)
    
      - Complete all AU’s except AU6
        
          - Partially Complete AU6 and re-enter
        
          - Complete AU6
    
      - Final Check AU
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

**<span class="underline">Large course testing</span>**

  - TestSuite Generates a test course structure (XML)
    
      - (Initially) Static one to start
    
      - *(Later)* a parameter driven generation of course structure.

  - (Machine) AU's (Testsuite) inspect LMS/LRS data

  - (Human) Procedure for learner to follow thru the course(s).
    
      - Initial entry
    
      - Re-entry of AU's

  - (Human) Modify course structure (admin user) and verify effect as a learner
    
      - Eg, MasteryScore, MoveOn, etc

# Detail Procedure

**<span class="underline">Small course testing</span>**

  - TestSuite Generates a test course structure (XML)
    
      - (Initially) Static one to start
    
      - *(Later)* a parameter driven generation of course structure.

  - (Human) Import that structure(s) into the LMS (admin user)

  - (Human) Register multiple learners (admin User) – User 1, 2, 3….

  - (Human) Access the course as a learner 1
    
      - Launch AU0
        
          - *Inspect URL (for all N/V pairs)*
        
          - *Get Auth Token (fetch)*
        
          - *Inspect State API*
        
          - *Issue Initialized Statement*
        
          - Send Complete Statement
        
          - 
          - Do Not Launch (AU5 – Not applicable)
    
      - Complete all AU’s with minimum MoveOn Criterial
    
      - Single Entry
    
      - Final Check AU
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

  - (Human) Access the course as a learner 2
    
      - Launch AU’s in order
    
      - Complete all AU’s with MoveOn Criterial
    
      - Multiple Entry
    
      - Final Check AU
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

  - (Human) Access the course as a learner 3
    
      - Launch AU’s in any order
    
      - Multiple Entry (Re-launching - Exiting and Re-entering AU)
    
      - Complete all AU’s except AU6
        
          - Partially Complete AU6 and re-enter
        
          - Complete AU6
    
      - Final Check AU
        
          - Run AU x after course complete (check for all satisfied)
        
          - A wait period should be established
        
          - AU x is Not Applicable
        
          - Alternate Credentials to Access to LRS for LMS issued statements.

# LMS Test Scenarios

1.  Individual AU Test (Simple) Simple Launch (Initial and re-entrant) (completed)

2.  Individual AU Test (One Entrance - Passed) - Simple Launch (one launch pass)

3.  Individual AU Test (Abandoned – AU crash After Launch) Simple Launch (Abandoned – Single AU crash After Launch)

4.  Individual AU Test (2 AU Course - Abandoned) - Simple Launch (abandoned 2AU’s)

5.  Individual AU Test (Terminate – Then write more)

6.  Block of AU’s Test (Satisfaction Roll-up) - A course with a single block (at Root) with 2 AU’s

7.  9 Blocks of AU’s - MoveOn Default Mixed with Completion/Passed MoveOn (Roll-up at course)

8.  2 Blocks of AU’s - Default MoveOn Criteria (entire Course) – Satisfied at Registration Time

9.  MasteryScore Test

## (Scenario \#1) Individual AU Test (Simple)

Scope:

  - Simple Launch (Initial and re-entrant)

Setup:

  - Course Structure (cmi5.xml, no media, not zipped)

  - Fully qualified URL to content

  - LaunchData= AU specific parameters

  - Moveon=Completed

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course, etc.*

3.  ***Action: Launch AU***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
            
              - *Verify ActivityID \<\> PublisherID from course structure*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
              - *Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
              - *OK/Failed list*

4.  **Action: Exit AU (Button)**
    
      - *Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)*
    
      - *Write Terminated Statement (Success)*
    
      - *Return To LMS (Use Return URL if provided or Close The AU window)*

5.  **Action: *(re) Launch AU***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
              - *Verify Launch Data Parameters from course structure are the same*
        
          - *Write Initialized Statement (success)*
        
          - *Read AU-Specific State API Document. (Verify contents same)*
        
          - *Present AU UI to learner (with results of checks)*
            
              - *OK/Failed list*
            
              - *Previous Statements*

6.  **Action: Send “Completed” (Button)**
    
      - *Result: AU*
        
          - *Write Completed Statement (Success)*

7.  **Action: Attempt to Void a Statement (Button)**
    
      - *Result: AU*
        
          - *Write Voided Statement for Completed (Failure)*
    
      - *Result: LaunchConsole (LMS*
        
          - *The LMS Rejects the Voiding Statement – as Unauthorized – See xAPI spec*

8.  **Action: Exit AU (Button)**
    
      - *Result: AU*
        
          - *Write Terminated Statement (Success)*
        
          - *Return To LMS (Use Return URL if provided or Close The AU window)*
    
      - *Result: LaunchConsole (LMS)*
        
          - *Satisfied Statement Issued – At Course Level*

9.  **Action: Post processing verification:**
    
      - *Result: Console (LMS)*
        
          - *Query LRS for all launch statements made during this scenario and verify that none have the same session id.*
        
          - *Query LRS for all cmi5 defined statements in this scenario excluding completed (or waived) statements. Verify that completion property is NOT included*
        
          - *Query LRS for all statements made by the LMS in this scenario. Verify that timestamps are in UTC time.*
        
          - 
## (Scenario \#2) Individual AU Test (One Entrance - Passed)

Scope:

  - Simple Launch (one launch pass)

Setup:

  - Course Structure (cmi5.xml, no media, Zip32)

  - Fully qualified URL to content

  - LaunchData= AU specific parameters

  - Moveon=Passed

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Ingest Zip32 file*
    
      - *extract*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course, etc.*

3.  ***Action: Launch AU***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
              - *~~Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued~~*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
            
              - 
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
              - *OK/Failed list*

4.  **Action: Send “Pass” (Button)**
    
      - *Result: AU*
        
          - *Write Passed Statement (Success)*

5.  **Action: Exit AU (Button)**
    
      - *Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)*
    
      - *Write Terminated Statement (Success)*
    
      - *Return To LMS (Use Return URL if provided or Close The AU window)*
    
    <!-- end list -->
    
      - *Result: LaunchConsole (LMS)*
        
          - *Satisfied Statement Issued – At Course Level*
        
          - *Verify Abandon Statement not issued for each session*
            
              - *After a reasonable period of time*

## (Scenario \#3) Individual AU Test (Abandoned – AU crash After Launch)

Scope:

  - Simple Launch (Abandoned – AU crash After Launch)

Setup:

  - Course Structure (cmi5.xml, no media, Zip64)

  - Fully qualified URL to content

  - LaunchData= AU specific parameters

  - Moveon=Completed

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Ingest Zip64 file*
    
      - *extract*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course, etc.*

3.  ***Action: Launch AU***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
              - *~~Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued~~*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
              - *OK/Failed list*

4.  **Action: Close AU (Abnormally Exit)**

5.  ***Action: Re-Launch AU (new session)***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Abandoned Statement Issued*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
              - *~~Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued~~*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
              - *OK/Failed list*
        
          - 
6.  **Action: Exit AU (Button)**
    
      - *Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)*
    
      - *Write Terminated Statement (Success)*
    
      - *Return To LMS (Use Return URL if provided or Close The AU window)*
    
    <!-- end list -->
    
      - *Result: LaunchConsole (LMS)*
        
          - *Verify No Satisfied Statement*
        
          - *~~Verify Abandon Statement not issued for second session~~*
            
              - *~~After a reasonable period of time~~*

## (Scenario \#4) Individual AU Test (2 AU Course - Abandoned)

Scope:

  - Simple Launch (abandoned)

Setup:

  - Course Structure (cmi5.xml, with media, Zip32)

  - Course Structure – 2 AUs
    
      - AU 1 – LaunchMethod = AnyWindow
    
      - AU 2 – LaunchMethod = OwnWindow

  - Fully qualified URL to content

  - LaunchData= AU specific parameters

  - Moveon=Completed, Completed

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Ingest Zip32 file*
    
      - *extract cmi5.xml*
    
      - *extract media*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course, etc.*

3.  ***Action: Launch AU 1***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *LMS launches AU with **<span class="underline">any</span>** of the following:*
            
            1.  *Redirect Browser to AU URL +cmi5 Query string*
            
            2.  *Spawn new Browser window to AU URL +cmi5 Query string*
            
            3.  *Direct to “component” in the LMS’s window to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
            4.  *~~Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued~~*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
            5.  *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
            6.  *OK/Failed list*

4.  **Action: Close AU 1 (Abnormally Exit)**

5.  **Action: Launch AU2 (new session)**
    
      - *Result: LaunchConsole (LMS)*
        
          - *Abandoned Statement Issued (for AU1 session)*
        
          - *Launched Statement Issued (AU2 Session)*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
        
          - *LMS launches AU with **<span class="underline">any</span>** of the following:*
            
            7.  *Redirect Browser to AU URL +cmi5 Query string*
            
            8.  *Spawn new Browser window to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
            9.  *~~Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued~~*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
            10. *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
            11. *OK/Failed list*
        
          - 
6.  **Action: AU 2 (Simulate Post Abandoned AU1 - button )**
    
      - Issue Completed Statement for the <span class="underline">previous</span> AU1 session ID
    
      - *Result: LMS*
        
          - *Either the LMS Rejects the Completed Statement OR Voids it*
            
            12. *REJECTED:* LMS/LRS Issues a HTTP 400 Bad Request
            
            13. *VOIDED:* LMS/LRS Records Completed Statement, Then issues a Voiding Statement for the Completed Statement.
    
      - *Result: AU (UI)*
        
          - Present AU UI to learner (with results of Failure)
        
          - If Statement not rejected:
            
            14. Get Completed Statement ID with voidedStatementId
            
            15. Verify Accompanied Voided Statement is present

7.  **Action: Exit AU 2 (Button)**
    
      - *Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)*
    
      - *Write Terminated Statement (Success)*
    
      - *Return To LMS (Use Return URL if provided or Close The AU window)*
    
    <!-- end list -->
    
      - *Result: LaunchConsole (LMS)*
        
          - *Verify No Satisfied Statement*
        
          - *Verify Abandon Statement not issued for second session*
            
            16. *After a reasonable period of time*

## (Scenario \#5) Individual AU Test (Terminate – Then write more)

Scope:

  - Single AU, terminated.

Setup:

  - Course Structure (cmi5.xml, with media, Zip64)

  - Course Structure (1 AU)

  - Fully qualified URL to content

  - LaunchData= AU specific parameters

  - Moveon=Completed

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Ingest Zip64 file*
    
      - *extract cmi5.xml*
    
      - *extract media*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course, etc.*

3.  ***Action: Launch AU***
    
      - *Result: LaunchConsole (LMS)*
        
          - *Launched Statement Issued*
        
          - *Write State API Document LMS.launchdata*
        
          - *Redirect Browser to AU URL +cmi5 Query string*
    
      - *Result: AU*
        
          - *Parse Query String*
        
          - *Call Fetch URL – Retrieve Authentication Token*
            
              - *~~Call Fetch URL 2<sup>nd</sup>Time to verify Error Issued~~*
        
          - *Read State API Document LMS.launchdata (verify structure)*
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - *Write Initialized Statement (success)*
        
          - *Present AU UI to learner (with results of checks)*
            
              - *OK/Failed list*

4.  **Action: AU Terminate Statement Button (Issue Terminate but do not close)**
    
      - *Result: AU*
        
          - *Issue Terminate Statement*

**  
**

5.  **Action: AU Issue Statement Button (Issue Terminate but do not close)**
    
      - *Result: AU*
        
          - *Issue Completed Statement*
        
          - 
      - *Result: LMS*
        
          - *Either the LMS Rejects the Completed Statement OR Voids it*
            
              - *REJECTED:* LMS/LRS Issues a HTTP 400 Bad Request
            
              - *VOIDED:* LMS/LRS Records Completed Statement, Then issues a Voiding Statement for the Completed Statement.
    
      - *Result: AU (UI)*
        
          - Present AU UI to learner (with results of Failure)
        
          - If Statement not rejected:
            
              - Get Completed Statement ID with voidedStatementId
            
              - Verify Accompanied Voided Statement is present

## (Scenario \#6) Block of AU’s Test (Satisfaction Roll-up)

Scope:

  - A course with a single block (at Root) with 2 AU’s

Setup:

  - Course Structure

  - Course Structure (cmi5.xml, no media, not zipped)

  - Fully qualified URLs to content

  - LaunchData= AU specific parameters

  - Moveon=Completed

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course, etc.*

3.  ***Action: Launch AU 1***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

4.  **Action: Exit/Close AU 1 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

5.  ***Action: Launch AU 2***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

6.  **Action: Exit/Close AU 2 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)
    
      - Result: LaunchConsole (LMS)
        
          - Verify Satisfied Statement Issued – At Block Level
        
          - Verify Satisfied Statement Issued – At Course Level

## (Scenario \#7) MoveOn Default Mixed with Completed MoveOn 

Scope:

  - A course with AU’s in blocks with mixed MoveOn Criteria

Setup:

  - Course Structure (cmi5.xml, no media, not zipped)

  - Course Structure
    
      - 8 Block’s at root level
    
      - 2 AU’s in 7 blocks
    
      - 1 AU in 1 Block
    
      - Block Structure as follows:
        
          - Block1
            
              - AU1 – default moveOn
            
              - AU2 - Passed moveOn
        
          - Block2
            
              - AU 3 – Completed moveOn
            
              - AU 4 – default moveOn
        
          - Block3
            
              - AU 5 – CompletedAndPassed moveOn
            
              - AU 6 - default moveOn
        
          - Block4
            
              - AU 7- default moveOn
            
              - AU 8 – CompletedAndPassed moveOn (Change sequence)
        
          - Block5
            
              - AU 9- default moveOn
            
              - AU 10 – CompletedAndPassed moveOn (both statements in on session)
        
          - Block 6
            
              - AU 11 - default moveOn
            
              - AU 12 – CompletedOrPassed moveOn
        
          - Block 7
            
              - AU 13 - default moveOn
            
              - AU 14 – CompletedOrPassed moveOn (sequence)
        
          - Block 8
            
              - AU 15 - default moveOn

  - Fully qualified URLs to content

  - LaunchData= AU specific parameters

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course*
    
      - Result: LaunchConsole (LMS)
        
          - Satisfied Statement Issued by the LMS for Block8
        
          - Verify activity ID is unique across structure (and in test) – at end
        
          - Verify activity ID does not match publisher ID

3.  ***Action: Launch AU 2***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

4.  **Action: Exit/Close AU 2 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

5.  ***Action: (re)Launch AU 2***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement is NOT issued for Block1
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

6.  **Action: Exit/Close AU 2 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)
    
      - Result: LaunchConsole (LMS)
        
          - Verify Satisfied Statement Issued for Block1
        
          - Verify activity ID is unique across structure (and in test) – at end
        
          - Verify activity ID does not match publisher ID

7.  ***Action: (re)Launch AU 2***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

8.  **Action: Exit/Close AU 2 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)
    
      - *Result: LMS*
        
          - *Either the LMS Rejects the Passed Statement OR Voids it*
            
              - *REJECTED:* LMS/LRS Issues a HTTP 400 Bad Request
            
              - *VOIDED:* LMS/LRS Records Passed Statement, Then issues a Voiding Statement for the Passed Statement.
    
      - *Result: AU (UI)*
        
          - Present AU UI to learner (with results of Failure)
        
          - If Statement not rejected:
            
              - Get Passed Statement ID with voidedStatementId
            
              - Verify Accompanied Voided Statement is present

9.  ***Action: Launch AU 3***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

10. **Action: Exit/Close AU 3 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

11. ***Action: (re)Launch AU 3***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement is NOT issued for Block2
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

12. **Action: Exit/Close AU 3 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

13. 
14. ***Action: (re)Launch AU 3***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

15. **Action: Exit/Close AU 3 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)
    
      - *Result: LMS*
        
          - *Either the LMS Rejects the Completed Statement OR Voids it*
            
              - *REJECTED:* LMS/LRS Issues a HTTP 400 Bad Request
            
              - *VOIDED:* LMS/LRS Records Passed Statement, Then issues a Voiding Statement for the Passed Statement.
    
      - *Result: AU (UI)*
        
          - Present AU UI to learner (with results of Failure)
        
          - If Statement not rejected:
            
              - Get Passed Statement ID with voidedStatementId
            
              - Verify Accompanied Voided Statement is present

16. ***Action: Launch AU 5***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement is issued for Block2
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

17. **Action: Exit/Close AU 5 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

18. ***Action: (re)Launch AU 5***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement is NOT issued for Block3
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

19. **Action: Exit/Close AU 5 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

20. ***Action: Launch AU 8***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement <span class="underline">is</span> issued for Block3
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

21. **Action: Exit/Close AU 8 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

22. ***Action: (re)Launch AU 8***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement is NOT issued for Block4
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

23. **Action: Exit/Close AU 8 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

24. ***Action: Launch AU 10***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement <span class="underline">is</span> issued for Block4
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
        
          - OK/Failed list

25. **Action: Exit/Close AU 10 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

26. ***Action: Launch AU 12***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement <span class="underline">is</span> issued for Block5
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
        
          - OK/Failed list

27. **Action: Exit/Close AU 12 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Completed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU

28. ***Action: Launch AU 14***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Verify that Satisfied Statement is issued for Block6
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

29. **Action: Exit/Close AU 14 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Passed Statement (Success)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU
    
      - Result: LaunchConsole (LMS)
        
          - Verify that Satisfied Statement is issued for Block7
        
          - Verify that Satisfied Statement is issued for the Course

## (Scenario \#8) Default MoveOn (entire Course) 

Scope:

  - A course with AU’s in blocks with all default MoveOn Criteria (issues satisfied statements)

Setup:

  - Course Structure (cmi5.xml, no media, not zipped)

  - Course Structure
    
      - 2 Block’s at root level
    
      - 2 AU’s in each block
    
      - Course Structure as follows:
        
          - Block1
            
              - AU1 – moveOn=default
            
              - AU2 – moveOn not specified (will default to default)
        
          - Block2
            
              - AU3 – moveOn not specified (will default to default)
            
              - AU4 – moveOn=default

  - Fully qualified URLs to content

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course*
    
      - Result: LaunchConsole (LMS)
        
          - Verify Satisfied statements are issued for Block1, Block2, and entire course
        
          - Verify activity ID’s is unique across structure (and in test) – at end
        
          - Verify activity ID’s does not match publisher ID

3.  *Register Learner in course*

4.  **Action: Post processing verification:**
    
      - *Result: Console (LMS)*
        
          - *Query LRS for all cmi5 defined statements in this scenario excluding completed (or waived) statements. Verify that completion property is NOT included*
        
          - *Query LRS for all statements made by the LMS in this scenario. Verify that timestamps are in UTC time.*

## (Scenario \#9) MasteryScore Test 

Scope:

  - A course with an AU that has a MasteryScore as part of its moveOn Criteria (MasteryScore as imported)

Setup:

  - Course Structure (cmi5.xml, no media, not zipped)

  - Course Structure
    
      - 1 Block’s at root level
    
      - 1 AU’s a block
    
      - Block Structure as follows:
        
          - Block1
            
              - AU1 – Passed moveOn, MasteryScore = 0.80

  - Fully qualified URLs to content

  - LaunchData= AU specific parameters

<!-- end list -->

1.  *Add setup data – import course Structure*
    
      - *Read cmi5.xml and load course structure data*

2.  *Register Learner in course*
    
      - Result: LaunchConsole (LMS)
        
          - Verify activity ID is unique across structure (and in test) – at end
        
          - Verify activity ID does not match publisher ID

3.  ***Action: Launch AU 1***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

4.  **Action: AU Issue Statement Button**
    
      - *Result: AU*
        
          - Set Result.Score.ScaledScore = 0.75 (Less than MasteryScore)
        
          - *Issue Passed Statement*
    
      - *Result: LMS*
        
          - *Either the LMS Rejects the Passed Statement OR Voids it*
            
              - *REJECTED:* LMS/LRS Issues a HTTP 400 Bad Request
            
              - *VOIDED:* LMS/LRS Records Passed Statement, Then issues a Voiding Statement for the Passed Statement.
    
      - *Result: AU (UI)*
        
          - Present AU UI to learner (with results of Failure)
        
          - If Statement not rejected:
            
              - Get Passed Statement ID with voidedStatementId
            
              - Verify Accompanied Voided Statement is present

5.  **Action: Exit/Close AU 1 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)

6.  ***Action: Re-Launch AU 1***
    
      - Result: LaunchConsole (LMS)
        
          - Launched Statement Issued
        
          - Write State API Document LMS.launchdata
        
          - Redirect Browser to AU URL +cmi5 Query string
    
      - Result: AU
        
          - Parse Query String
        
          - Call Fetch URL – Retrieve Authentication Token
        
          - Read State API Document LMS.launchdata (verify structure)
            
              - *Verify Launch Data Parameters from course structure are the same for the AU*
                
                  - *Launch Mode*
                
                  - *Launch Parameters*
                
                  - *Mastery Score*
                
                  - *EntitlementKey*
                
                  - *MoveOn*
        
          - Write Initialized Statement (success)
        
          - Present AU UI to learner (with results of checks)
            
              - OK/Failed list

7.  **Action: AU Issue Statement Button**
    
      - *Result: AU*
        
          - Set Result.Score.ScaledScore = 0.80 (equal to MasteryScore)
        
          - *Issue Passed Statement (success)*

8.  **Action: Exit/Close AU 1 (Button)**
    
      - Result: AU
        
          - Write AU specific State API Document (state Id = AUtest, Registration, ActivityId, Actor)
        
          - Write Terminated Statement (Success)
        
          - Return To LMS (Use Return URL if provided or Close The AU window)
    
      - *Result: LMS (console)*
        
          - *LMS issues Satisfied Statement(s) for Block1 and entire course*

**<span class="underline">  
</span>**

<span id="_Toc509556428" class="anchor"></span>

**<span class="underline">  
</span>**

## **<span class="underline">LMS Test Scenarios</span>** (requirements mapped)

1.  **Individual AU Test (Simple) Simple Launch (Initial and re-entrant) (completed)**

<!-- end list -->

  - cmi5\_6.1\_1 Learning Management System (LMS): The LMS MUST be able to import and process course structures containing more than 1000 AU's.

  - **cmi5\_8.1\_1** Learning Management System (LMS): The AU MUST be launched by the LMS using either a new browser window or redirecting the existing browser window to a new location.

  - **cmi5\_8.1\_3** Learning Management System (LMS): The AU MUST be launched by the LMS with a launch URL containing query string parameters (endpoint, fetch, actor, registration, and activityId).

  - **cmi5\_8.1\_4** endpoint - Learning Management System (LMS): The AU MUST be launched by the LMS with a launch URL containing a "endpoint" name/value pair in the query string containing the endpoint to the LRS.

  - **cmi5\_8.1\_6** fetch - Learning Management System (LMS): the LMS MUST place the *fetch*name/value pair in the query string.

  - **cmi5\_8.1\_8** actor - Learning Management System (LMS): The LMS MUST populate the actor with a valid value.

  - **cmi5\_8.1\_10** registration - Learning Management System (LMS): The LMS MUST place a UUID value for registration id in the query string.

  - **cmi5\_8.1\_12** activityId- Learning Management System (LMS): The LMS MUST generate an activityId for the AU and place its value in the query string.

  - **cmi5\_8.1\_13** activityId- Learning Management System (LMS): The activityId generated MUST NOT match the AU's id (publisher id) from the course structure

  - **cmi5\_8.2.1\_1** Learning Management System (LMS): The LMS MUST include a \_ fetch \_ name/value pair in the launch URL.

  - **cmi5\_8.2.1\_5** Learning Management System (LMS): The LMS must return an auth token in a the JSON structure specified from a valid fetch URL call.

  - **cmi5\_9.2\_1** Learning Management System (LMS): The LMS MUST provide an actor object with an objectType of "Agent" and MUST contain an "account" as defined in the xAPI specification.

  - **cmi5\_9.3.1\_2** Learning Management System (LMS): The LMS MUST NOT issue multiple Launched (cmi5 defined) statements for given a session id.

  - **cmi5\_9.5.3\_4** Learning Management System (LMS): The LMS must not include the " completion" property for (cmi5 defined) statements other waived.

  - **cmi5\_9.6.3.4\_1** Learning Management System (LMS): The LMS MUST put a fully qualified URL equivalent to the one that the LMS used to launch the AU without the name/value pairs included as defined in section 8.1 as a context extension of the "Launched" statement.

  - **cmi5\_9.6.3.1\_1** Learning Management System (LMS): The LMS MUST generate a unique string identifier ("session id") for each AU launch session.

  - **cmi5\_9.6.3.1\_2** Learning Management System (LMS): The LMS MUST record the session ID in context template of LMS.launchdata in the State API (per Section 10) prior to launching an AU.

  - **cmi5\_9.6.3.7\_1** Learning Management System (LMS): LMS MUST add launchParameters as an extension of context in a Launched statement when launchParameters is provided in LMS.launchdata.

  - **cmi5\_9.6.3.6\_1** Learning Management System (LMS): LMS MUST add moveOn as an extension of context in a Launched statement when moveOn is provided in LMS.launchdata.

  - cmi5\_9.7\_1 Learning Management System (LMS): All statements issued by the LMS MUST include a timestamp property in UTC time.

  - **cmi5\_10\_5** Learning Management System (LMS): LMS MUST include a value for launchParameters in LMS.LaunchData State document.

  - **cmi5\_10\_3** Learning Management System (LMS)**: LMS MUST include a value for launchMode in LMS.LaunchData State document.**

  - **cmi5\_10\_5** Learning Management System (LMS)**: LMS MUST include a value for launchParameters in LMS.LaunchData State document.**

  - **cmi5\_10\_6** Learning Management System (LMS)**: LMS MUST include a value for masteryScore in LMS.LaunchData State document if a value for masteryScore is defined in the course structure.**

  - **cmi5\_10\_7** Learning Management System (LMS)**: LMS MUST include a value for moveOn in LMS.LaunchData State document.**

  - **cmi5\_10\_9** Learning Management System (LMS)**: LMS MUST provide an entitlementKey object in "LMS.LaunchData" if an entitlementKey value is present for the AU in the course structure.**

  - **cmi5\_10\_10** Learning Management System (LMS)**: LMS MUST set the entitlementKey object property “courseStructure” to the value of entitlementKey.courseStructure present for the AU in the course structure.**

  - **cmi5\_13\_1\_1** Learning Management System (LMS)**: All leading/trailing whitespace MUST be removed by the LMS on import of the course structure for all of the data elements defined in section 13.**

  - **cmi5\_14\_0\_1** Learning Management System (LMS)**: The LMS MUST be able to import a course structure from a cmi5.xml file.**

  - **cmi5\_14\_0\_2** Learning Management System (LMS)**: The LMS MUST be able to import a course structure from a Zip64 file (containing a cmi5.xml file).**

  - **cmi5\_14\_0\_3** Learning Management System (LMS)**: The LMS MUST be able to import a course structure from a Zip32 file (containing a cmi5.xml file).**

<!-- end list -->

2.  **Individual AU Test (One Entrance - Passed) - Simple Launch (one launch pass)**

3.  (Same Scenario \#1)

4.  **Individual AU Test (Abandoned – AU crash After Launch) Simple Launch (Abandoned – Single AU crash After Launch)**

5.  (See scenario \#1)

6.  **cmi5\_9.4.\_5** Learning Management System (LMS): For abandoned (cmi5 defined) statements issued by the LMS, the Object's "id" property must match the ActivityId provided by the LMS for the AU abandoned.

7.  **cmi5\_9.5.4.2\_1** Learning Management System (LMS): The duration property MUST be included in "Abandoned" statements.

8.  cmi5\_9.5.4.2\_2 Learning Management System (LMS): The duration property MUST be at least set to the total session time, calculated as the time between the "Launched" statement and the last statement (of any kind) issued by the AU.

9.  **cmi5\_9.3\_9** Learning Management System (LMS): LMS MUST NOT issue more than one abandoned (cmi5 defined) statement for a session id.

10. **cmi5\_9.3.6\_1** Learning Management System (LMS): The LMS MUST record an "abandoned" (cmi5 defined) statement on behalf of an given AU if the previous session (with the same learner/course registration) of that AU did not include a "terminated" statement(cmi5 defined).

11. **cmi5\_9.3\_9** Learning Management System (LMS): LMS MUST NOT issue more than one abandoned (cmi5 defined) statement for a session id.

12. Individual AU Test (2 AU Course - Abandoned) - Simple Launch (abandoned 2AU’s)

13. (See scenario \#3)

14. **cmi5\_9.3.6\_2** Learning Management System (LMS): After recording an "abandoned" (cmi5 defined) statement for a given session, the LMS MUST NOT allow any additional statements to be recorded for that session.

15. **cmi5\_8.1\_2 Learning Management System (LMS)**: The AU MUST be launched by the LMS using the method specified in the course structure metadata. (new window, redirect existing window, or any window)

16. **cmi5\_14\_1\_4 Course Package:** Any media included in a ZIP course package MUST use relative URL references in the Course Structure XML (cmi5.xml)

17. Individual AU Test (Terminate – Then write more)

18. (See scenario \#1)

19. **cmi5\_9.3.8\_2** Learning Management System (LMS): Upon receiving a (cmi5 defined) "terminated" statement, the LMS MUST reject statements (of any kind) for the AU session received after its (LMS defined) specified period of time.

20. Block of AU’s Test (Satisfaction Roll-up) - A course with a single block (at Root) with 2 AU’s

21. (See scenario \#1)

22. **cmi5\_9.3.9 \_1** Learning Management System (LMS): The LMS MUST generate a unique block id for each block in the course structure.

23. **cmi5\_9.3.9 \_2** Learning Management System (LMS):The generated Block id MUST NOT match the publisher's ID from the course structure.

24. **cmi5\_9.3.9 \_3** Learning Management System (LMS): The LMS MUST issue a (cmi5 defined) "satisfied" statement when the learner has met the moveOn criteria of all AU's in a (course structure) block. The "satisfied" statement must include the block id generated by the LMS and use "<https://w3id.org/xapi/cmi5/activitytype/block>" as the value of the "type" property in the Object's Definition.

25. **cmi5\_9.3.9 \_4** Learning Management System (LMS): The LMS MUST generate a unique course id for the course structure.

26. **cmi5\_9.3.9 \_5** Learning Management System (LMS):The generated course id MUST NOT match the publisher's ID from the course structure.

27. **cmi5\_9.3.9 \_6** Learning Management System (LMS): The LMS MUST issue a (cmi5 defined) "satisfied" statement when the learner has met the moveOn criteria of all AU's in a course. The "satisfied" statement must include the course id generated by the LMS and use "<https://w3id.org/xapi/cmi5/activitytype/block>" as the value of the "type" property in the Object's Definition.

28. **cmi5\_9.3.9 \_7** Learning Management System (LMS): For all "satisfied" statements triggered as a result of an AU launch session, the LMS MUST use the session id from the AU launch in the statements.

29. 9 Blocks of AU’s - MoveOn Default Mixed with Completion/Passed MoveOn (Roll-up at course)

30. See Scenario 6

31. **cmi5\_9.6.1\_1** Learning Management System (LMS): At the time of registration, the LMS MUST evaluate moveOn criteria in the course structure and issue satisfied statements for AU with moveOn of "Not Applicable".

32. **cmi5\_9.6.1\_2** Learning Management System (LMS): For all satisfied statements triggered outside of an AU launch session, the LMS MUST generate a unique session id and use it for those statements.

33. **cmi5\_6.3\_2** The LMS MUST Void statements that are NOT rejected AND conflict with the "Statement API" requirements as defined in Section 9

34. 2 Blocks of AU’s - Default MoveOn Criteria (entire Course) – Satisfied at Registration Time

35. **cmi5\_9.3.9 \_1** Learning Management System (LMS): The LMS MUST generate a unique block id for each block in the course structure.

36. **cmi5\_9.3.9 \_2** Learning Management System (LMS):The generated Block id MUST NOT match the publisher's ID from the course structure.

37. **cmi5\_9.3.9 \_3** Learning Management System (LMS): The LMS MUST issue a (cmi5 defined) "satisfied" statement when the learner has met the moveOn criteria of all AU's in a (course structure) block. The "satisfied" statement must include the block id generated by the LMS and use "<https://w3id.org/xapi/cmi5/activitytype/block>" as the value of the "type" property in the Object's Definition.

38. **cmi5\_9.3.9 \_4** Learning Management System (LMS): The LMS MUST generate a unique course id for the course structure.

39. **cmi5\_9.3.9 \_5** Learning Management System (LMS):The generated course id MUST NOT match the publisher's ID from the course structure.

40. **cmi5\_9.3.9 \_6** Learning Management System (LMS): The LMS MUST issue a (cmi5 defined) "satisfied" statement when the learner has met the moveOn criteria of all AU's in a course. The "satisfied" statement must include the course id generated by the LMS and use "<https://w3id.org/xapi/cmi5/activitytype/block>" as the value of the "type" property in the Object's Definition.

41. 
42. **cmi5\_9.6.1\_1** Learning Management System (LMS): At the time of registration, the LMS MUST evaluate moveOn criteria in the course structure and issue satisfied statements for AU with moveOn of "Not Applicable".

43. **cmi5\_9.6.1\_2** Learning Management System (LMS): For all satisfied statements triggered outside of an AU launch session, the LMS MUST generate a unique session id and use it for those statements.

44. **cmi5\_9.7\_1 Learning Management System (LMS)**: All statements issued by the LMS MUST include a timestamp property in UTC time.

45. 
46. **MasteryScore Test**

47. (Same Scenario \#6)

48. **cmi5\_9.6.3.2\_1** Learning Management System (LMS): LMS MUST add masteryScore as an extension of context in a "Launched" statement when masteryScore is provided in the LMS.launchdata.

49. **cmi5\_10\_6** Learning Management System (LMS): LMS MUST include a value for masteryScore in LMS.LaunchData State document if a value for masteryScore is defined in the course structure.

50. # Contents

51. [Testing Procedures 1](#testing-procedures)

52. [Testing Procedures 1](#testing-procedures-1)

53. [Detail Procedure 1](#detail-procedure)

54. [(Scenario \#) Individual AU Test (Simple) 1](#lms-test-scenarios)

55. [(Scenario \#2) Individual AU Test (One Entrance - Passed) 1](#scenario-2-individual-au-test-one-entrance---passed)

56. [(Scenario \#3) Individual AU Test (Abandoned – AU crash After Launch) 1](#scenario-3-individual-au-test-abandoned-au-crash-after-launch)

57. [(Scenario \#4) Individual AU Test (2 AU Course - Abandoned) 1](#scenario-4-individual-au-test-2-au-course---abandoned)

58. [(Scenario \#5) Individual AU Test (Terminate – Then write more) 1](#scenario-5-individual-au-test-terminate-then-write-more)

59. [(Scenario \#6) Block of AU’s Test (Satisfaction Roll-up) 1](#scenario-6-block-of-aus-test-satisfaction-roll-up)

60. [(Scenario \#7) MoveOn Default Mixed with Completed MoveOn 1](#scenario-7-moveon-default-mixed-with-completed-moveon)

61. [(Scenario \#8) Default MoveOn (entire Course) 1](#scenario-8-default-moveon-entire-course)

62. [(Scenario \#9) MasteryScore Test 1](#scenario-9-masteryscore-test)

63. [\_Disclaimers/Limits/Assumptions\_ 1](#_Toc509556428)

64. [LMS Test Scenarios 1](#_Toc509556429)

65. [**LMS Test Scenarios** (requirements mapped) 1](#lms-test-scenarios-requirements-mapped)

66. Fix this…

67. **cmi5\_9.5.3\_4 Learning Management System (LMS)**: The LMS must not include the " completion" property for (cmi5 defined) statements other than waived and completed

68. ***<span class="underline">ADD THIS</span>***

69. **cmi5\_14\_1\_4** Course Package: Any media included in a ZIP course package MUST use relative URL references in the Course Structure XML (cmi5.xml)

# AU Test Scenarios

Already Built AU (Content Provider)

1.  AU Test (Launch and Exit) – Initialize and Terminate

2.  AU Test (MoveOn)

3.  
Authoring Tool

## **<span class="underline">AU Test Scenarios</span>** (requirements mapped)

Really only one scenario…

  - Launch each AU in course and re-enter.

  - AU Vendor/provider will provide instructions to exercise the AU features to generate enough data to verify them with AU test suite.
    
      - Number of times and circumstances to Re-enter

  - The suite will detect features with Success/Failure of each feature (Statement, data element, etc.)

  - *Test suite will apply rules to all of the data generated in LRS (all requirements)*

  - Test suite will verify returnURL behavior at launch time.
    
    **<span class="underline">Steps with new scenario:</span>**

<!-- end list -->

1.  Load AUs/Course into the TestSuite

2.  Verify Course Structure

3.  Simple Launch and Exit of each AU

4.  Verify returnURL behavior

5.  Re-set/Re-enroll

6.  Follow Vendor-provided script to test all course features
    
    1.  Exercise Content based on vendor instructions (Since AU designs will vary)

7.  TestSuite will **<span class="underline">inspect</span>** the LRS data to detect which features were implemented and verify their conformance

8.  TestSuite will generate a report
    
    2.  Feature Detected (LRS data)
    
    3.  Feature Compliance determined by
        
        1.  LRS data
        
        2.  HTTP error logs

AU tests are “course tests”. Each Course will go thru the following steps….

**<span class="underline">STEP \#1</span> (**Launch and Exit each AU in the course – Initialize and Terminate**)**

  - cmi5\_8.1\_5** endpoint - Assignable Unit (AU):** The AU MUST get the endpoint value from the query string and use the endpoint value as the Base Endpoint for xAPI requests.

  - cmi5\_8.1\_7** fetch - Assignable Unit (AU):** The AU MUST retrieve the fetch value from the query string.

  - **cmi5\_8.1\_9** **actor - Assignable Unit (AU):** The AU MUST get the actor value from the query string. The AU MUST use the actor value in API calls that require an "actor" property when sending xAPI requests.

  - **cmi5\_8.1\_11** **registration - Assignable Unit (AU):** The AU MUST use the registration id provided query string in API calls that require a "registration id" when sending xAPI requests.

  - **cmi5\_8.1\_13 activityId- Assignable Unit (AU):** The AU MUST get the activityId value from the query string and use the activityId value in API calls that require an "activity id" when issuing cmi5 defined statements. **cmi5\_8.2.1\_3** Assignable Unit (AU): The AU MUST issue only one request to the \_ **fetch** \_ URL.

  - **cmi5\_8.2.1\_4** **Assignable Unit (AU):** The AU MUST NOT issue any type of HTTP requests other than POST to the \_ **fetch** \_ URL.

  - **cmi5\_8.2.2\_2** **Assignable Unit (AU):** The AU MUST place the authorization token returned from the fetch URL in the Authorization headers of all HTTP requests made to the LRS endpoint.

  - **cmi5\_9.1\_1** **Assignable Unit (AU):** The AU MUST assign a statement id property in UUID format for all statements it issues.

  - **cmi5\_9.2\_3** **Assignable Unit (AU):** The Actor object defined by the LMS must be used as the actor in all cmi5 defined statements made by the AU.

  - **cmi5\_9.3\_4** **Assignable Unit (AU):** The AU MUST issue a Terminated (cmi5 defined) statement as its last statement in a session.

  - **cmi5\_9.3\_1** Assignable Unit (AU): The AU MUST NOT issue duplicate verbs (in cmi5 defined statements) within an AU session. (see cmi5 verbs…)

  - **cmi5\_9.3.2\_1** **Assignable Unit (AU):** The AU MUST issue a Initialized (cmi5 defined) statement as its first statement in a session.

  - **cmi5\_9.3.2\_2** **Assignable Unit (AU):** The AU MUST NOT issue more than one Initialized (cmi5 defined) statement in a session.

  - **cmi5\_10\_1** Assignable Unit (AU): The AU MUST NOT modify or delete the LMS.LaunchData State document.

  - **cmi5\_10\_8** Assignable Unit (AU): If the returnURL is provided in "LMS.LaunchData", the AU MUST redirect the current browser window to the returnURL when the AU is terminated.

  - **cmi5\_10\_2** Assignable Unit (AU): The AU MUST NOT overwrite any values provided by the LMS in the contextTemplate.

  - **cmi5\_10\_11 Assignable Unit (AU)** : AU MUST get the "contextTemplate" value from the "LMS.LaunchData" State document.

  - **cmi5\_10\_12 Assignable Unit (AU)** : The AU MUST use the contextTemplate as a template for the "context" property in all xAPI statements it records to the LMS.

  - **cmi5\_10\_13 Assignable Unit (AU)** : The AU MUST NOT overwrite any values provided in the contextTemplate.

  - **cmi5\_9.5.4.1\_1** Assignable Unit (AU): The AU MUST include the "duration" property in "terminated" statements.

  - **cmi5\_9.3.2\_1** Assignable Unit (AU): The AU MUST issue a Initialized (cmi5 defined) statement as its first statement in a session.

  - **cmi5\_9.3.2\_2** Assignable Unit (AU): The AU MUST NOT issue more than one Initialized (cmi5 defined) statement in a session.

  - **cmi5\_9.3.8\_1** Assignable Unit (AU): The AU MUST record a (cmi5 defined) statement containing the "terminated" verb as the last statement in a session.

  - **cmi5\_9.4\_1** Assignable Unit (AU): The AU must provide an object in all (cmi5 defined) statements.

  - **cmi5\_9.4\_2** Assignable Unit (AU): For all (cmi5 defined) statements issued by the AU, the Object's "id" property must match the activityId defined in the launch URL.

  - **cmi5\_9.5.2\_3** Assignable Unit (AU): The AU must not include the success property for (cmi5 defined) statements other passed and failed.

  - **cmi5\_9.5.3\_2** Assignable Unit (AU): The AU must not include the "completion" property for (cmi5 defined) statements other completed.

  - **cmi5\_9.6.2.1\_2** Assignable Unit (AU): The LMS must include An Activity object with an "id" of "<https://w3id.org/xapi/cmi5/context/categories/cmi5>" in the "category" context activities for all cmi5 defined statements it issues.

  - **cmi5\_9.7\_2** Assignable Unit (AU): All statements issued by the AU MUST include a timestamp property in UTC time.

  - **cmi5\_11\_1** Assignable Unit (AU): The AU MUST call the agent profile API to retrieve the “cmi5LearnerPreferences” document.

  - **cmi5\_9.5.1\_1** Assignable Unit (AU): The AU must not report a score for (cmi5 defined) statements other than passed or failed.

  - **cmi5\_9.3.3\_1** Assignable Unit (AU): The AU MUST issue only one Completed (cmi5 defined) statement per ActivityId per registration.

  - **cmi5\_9.5.3\_4** Assignable Unit (AU): The AU must set the "completion" property of the result to true for **completed** (cmi5 defined) statements.

  - **cmi5\_9.3\_2** Assignable Unit (AU): The AU MUST NOT use a Passed and a Failed verb (in cmi5 defined statements) within an AU session.

  - **cmi5\_9.3\_6** Assignable Unit (AU): The AU MUST issue only one Passed (cmi5 defined) statement per ActivityId per registration.

  - **cmi5\_9.3\_7** Assignable Unit (AU): The AU MUST NOT issue a Failed (cmi5 defined) statement following a Passed (cmi5 defined) statement per ActivityId per registration.

  - **cmi5\_9.5.1\_1** Assignable Unit (AU): The AU must not report a score for (cmi5 defined) statements other than passed or failed.

  - **cmi5\_9.5.1\_2** Assignable Unit (AU): If the AU provides a "raw" value for score it MUST also provide the "min" and "max" values for score.

  - **cmi5\_9.5.2\_1** Assignable Unit (AU): The AU must set the "success" property of the result to true for passed (cmi5 defined) statements.

  - **cmi5\_9.5.2\_2** Assignable Unit (AU): The AU must set the "success" property of the result to false for failed (cmi5 defined) statements.

  - **cmi5\_9.5.3\_1** Assignable Unit (AU): The AU must set the "completion" property of the result to true for passed (cmi5 defined) statements.

  - **cmi5\_9.5.4.1\_2** Assignable Unit (AU): The AU MUST include the "duration" property in "completed" statements.

  - **cmi5\_9.5.4.1\_3** Assignable Unit (AU): The AU MUST include the "duration" property in "passed" statements.

  - **cmi5\_9.5.4.1\_3** Assignable Unit (AU): The AU MUST include the "duration" property in "failed" statements.

  - **cmi5\_9.5.5.1\_1** Assignable Unit (AU): The progress extensions, if provided, must be an integer 0 to 100 inclusive.

  - **cmi5\_9.6.2.2\_2** Assignable Unit (AU): Passed and Completed (cmi5 defined) statements issued by the AU MUST have an Activity object with an "id" of "<https://w3id.org/xapi/cmi5/context/categories/moveon>" in the "category" context activities list. Other statements issued by the AU MUST NOT include this Activity.

  - **cmi5\_9.6.3.2\_2** Assignable Unit (AU): An AU MUST include the "masteryScore" value when provided in the LMS.launchdata as a context extension for "passed"/"failed" Statements.

  - **cmi5\_10\_4** Assignable Unit (AU): If the value for launchMode (provided in the LMS.LaunchData State document) is " Browse” or “Review”, then AU MUST NOT issue passed, failed, or completed (cmi5 defined) statements.

  - **cmi5\_11\_1\_1** Assignable Unit (AU): If the AU creates or updates the “cmi5LearnerPreferences” document, the languagePreference property value MUST be a comma-separated list of RFC 5646 Language Tags.

  - **cmi5\_11\_2\_1** Assignable Unit (AU): If the AU creates or updates the “cmi5LearnerPreferences” document, the audioPreference property value MUST be either “on” or “off”.

# \_Disclaimers/Limits/Assumptions\_

1.  Because compliance cannot be verified – it does not mean that an LMS (or AU) is not cmi5 conformant.

2.  Test suite AU failure to execute due to software/environment conflicts…

3.  **“Reasonable Time” set by TestSuite parameters. (Procedure will specify)**
    
      - Rationale: How long a learner user would expect to wait for LMS corrective action due to AU failure - up to 3 seconds
    
      - Satisfied vs Error Scenario (same)
    
      - Reasonable time (see vendor instructions…)

4.  Checks and verification may actually occur after all testing steps have occurred by post processing logs and statements. The testing procedure will show sequence of events (not necessary when determinations are made by the software)

5.  The LMS may have features that are beyond the scope of the cmi5 specification which will not be tested for conformance (e.g, editing course structures, etc.)

6.  Course Structures are created with the AU authoring tools (most cases)

7.  AU’s issuing LMS Specific Verb/Statements – will generate warnings in test suite – make pull request for future version with explicit prohibition.

# ADD TO REQUIREMENTS

  - **cmi5\_10\_11 Assignable Unit (AU)** : AU MUST get the "contextTemplate" value from the "LMS.LaunchData" State document.

  - **cmi5\_10\_12 Assignable Unit (AU)** : The AU MUST use the contextTemplate as a template for the "context" property in all xAPI statements it records to the LMS.

  - **cmi5\_10\_13 Assignable Unit (AU)** : The AU MUST NOT overwrite any values provided in the contextTemplate.

# ADD TO REQUIREMENTS (5-11)

**cmi5\_9.5.3\_4** Learning Management System (AU): The AU must set the "completion" property of the result to true for **completed** (cmi5 defined) statements.

**PULL – REQUEST for AU prohibitions**

AU’s issuing LMS Specific Verb/Statements – will generate warnings in test suite – make pull request for future version with explicit prohibition.

ERRATA

|                   |                                                                |
| ----------------- | -------------------------------------------------------------- |
| **Sample Value:** | {courseStructure: "xyz-123-9999"", alternate: "abc-456-1111""} |

Examples – Rename to Actual Document Names,,,

LMS.LaunchData

Options for test suite development:

1.  Open Source - Rip-Tide Scenario – they just do one, put it out there as open source

2.  BAA funded work

3.  Internal ADL project

4.  Hybrid – ADL project that enhances an open source or BAA project.
    
    BAA – Expected this summer. Scope of the BAA will be broad enough to for cmi5 test suite proposals.
    
    We should host BAA information sessions to explain the BAA process and encourage vendors to send in proposals for cmi5 test suites.
    
    Reach out to communities for potential vendors to develop test suite
    
    Next Steps for group:

<!-- end list -->

  - Iterate on the cmi5 testing procedures/scenario documents

  - Work on high level “scope of work” for test suite

  - Update JSON samples

# Errata

***Pull request – change the sample to a simple string***

<table>
<thead>
<tr class="header">
<th><h3 id="launchparameters">launchParameters</h3></th>
<th></th>
</tr>
</thead>
<tbody>
<tr class="odd">
<td><strong>Required:</strong> No<br />
<strong>Data type: </strong>string</td>
<td><p><strong>Description:</strong><br />
Static launch parameters defined by the course designer.</p>
<p><strong>Value space:</strong><br />
Values are defined by the course designer.</p>
<p><strong>Sample value:</strong><br />
&lt;launchParameters&gt;<br />
{"param1": "Lorem ipsum dolor sit amet", "param2": [1,2,3,4,5],"param3": {"a": 1,"b": 2}}<br />
&lt;/launchParameters&gt;</p></td>
</tr>
</tbody>
</table>

JSON examples

  - launchParameters in State Documents (several)

  - entitlementKey (alternate key) in state documents (both scenarios)

  - languagePreference, audioPreference in Agent Profile (one or two)
    
    "launchParameters":"param1=abc456,param2=xyz123",
    
    "launchParameters":"param1=abc456\&param2=xyz123",
    
    "launchParameters":"\\"value\\",\\"value2\\"",
    
    "launchParameters":"param1,Param2,",
    
    "launchParameters":"{\\"stuff1\\":1,\\"stuff2\\":\\"some string value\\",\\"stuff3\\":5.6}",
    
    Cmi5 implementor’s list – permissions – Lectora -& Brainer
    
    TestSuite development not likely for “free”
    
    AU Test Suite and LMS testsuite that can test each other – likely – possibly an ADL internal development only
