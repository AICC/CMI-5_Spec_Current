## cmi5 client library 

A cmi5 client library is available for enabling cmi5 support in content to work with a cmi5 conformant LMS (Learning Management System).  The library is available at the following gitHub site:

* <https://github.com/adlnet/cmi5-Client-Library>

Here are 3 common examples for using the cmi5 client library.
-   Hello World
-   Simple Completed
-   Passed/Failed

### **Example #1 Hello world**

In this scenario, we will implement the bare minimum for a cmi5 enabled AU (content).  Launch and exit.

1.  **Include a reference to the ADL wrapper library.** This is
    available from the ADL Github site
    * See <https://github.com/adlnet/xAPIWrapper/tree/master/dist> ).

           <script src="Scripts/xapiwrapper.min.js"></script>

2.  **Include a reference to cmi5Controller.js.** This is available from
    the ADL Github site
    * See  <https://github.com/adlnet/cmi5-Client-Library/tree/master/Examples/Scripts>

           <script src="Scripts/cmi5Controller.js"></script>

3.  **Include a reference to cmi5Wrapper.js.**
    * See  <https://github.com/adlnet/cmi5-Client-Library/tree/master/Examples/Scripts>

           <script src="Scripts/cmi5Wrapper.js"></script>

4.  **Parse launch parameters passed on the URL Launch line and set
    properties of the cmi5 controller**.

           cmi5Controller.setEndPoint(parse("endpoint"));<BR> 
           cmi5Controller.setFetchUrl(parse("fetch"));<BR> 
           cmi5Controller.setRegistration(parse("registration"));<BR> 
           cmi5Controller.setActivityId(parse("activityid"));<BR> 
           cmi5Controller.setActor(parse("actor"));<BR> 


5.  **Call the *cmi5Controller.startUp()* method.** Two call back functions are passed:

    1. **cmi5Ready**... This function is called once the controller has fetched the authorization token, read the State document, and the agent Profile.

    2. **startUpError**...This function is called if the *startUp()* method detects an error.

6.  **Create the "cmi5Ready" function.**

    1. Set Object Identifiers for your AU with *cmi5Controller.setObjectProperties(*langstring, actitityType, name, description*)*
          - The langstring used by the AU ( Example: "en-US" )
          - The actitityType (Example: "http://adlnet.gov/expapi/activities/assessment")
          - The name of the AU (Example: "ADL AU Example 1")
          - The description of the AU (Example : "This is a simple of an AU.")

    1. Issue the initialized Statement

           SendStatement("Initialized");

7.  **Create the "startUpError" function**.

    1. Set your error handling according to your preferences (console, alert, etc)

8.  **Add reference to FinishAU() in your UI for learner exit event.**

### **Example #2 Simple Completed**

In this scenario, the learner views or does all of the relevant activities in an AU presentation and exits.
 
***Steps 1 thru  7 (Same as Example #1)***

    8. When learner finishes all activities - Send Completed Statement --

           SendStatement("Completed");

    9. Add reference to FinishAU() in your UI for learner exit event.

### **Example #3 Passed/Failed**

In this scenario, the learner will be assessed in a scored activity. The
activity has a MasteryScore associated with it from the course
structure.

***Steps 1 thru 7 (Same as Example #1)***

    8.  Get the MasteryScore

           var score = cmi5Controller.getMasteryScore();

    9.  Assess Learner (Learner performs assessment activity)

    10. Judge Score -- Based on Score , Send Statement:

           if (score >= cmi5Controller.getMasteryScore()) {
               SendStatement("Passed", score);
           } else {
               SendStatement("Failed", score);
           }

    11. Add reference to FinishAU() in your UI for learner exit event.
