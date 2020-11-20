
## Conceptual Overview of cmi5

**<u>Introduction</u>**

cmi5 is a "profile" for using the xAPI specification with traditional learning management (LMS) systems.

Since the xAPI specification is highly generalized to support many different use cases, a set of "extra rules" (called a "profile") is needed to ensure interoperability for a given use case. The cmi5 profile ensures plug and play interoperability between learning content and LMS systems.

The use case that the cmi5 profile is specifically designed for is one where the learner launches the learning content/activity from the LMS user interface.

<p align="center"> <img width="720" src="https://raw.githubusercontent.com/AICC/CMI-5_Spec_Current/gh-pages/images/cmi5-concept-overview-11-20-2020.png"></p>

**<u>Components</u>**

**Course Package** - a course structure (see below) optionally packaged in ZIP with optional learning content media files.

**Course Structure** - A list of assignable units (see below) and their launch parameters, with an implied sequence, representing a course.

**LMS** - Learning Management System. A system that includes the capabilities to register learners, launch learning presentations, analyze and report learner performance, and track learners\' progress.

**LRS** - Learning Record Store. A web service that receives, stores, and retrieves xAPI statements.

**AU --** Assignable Unit. A separately launchable learning content presentation. The AU is the unit of tracking and management. The AU collects data on the learner and sends it to the LMS.

**<u>Roles</u>**

**Learner** - The user who is interacting with the learning content with the purpose of acquiring knowledge, skills, or abilities.

**Author** - A user who assembles assignable units into a course package for consumption in the LMS. The author may also create the Assignable Units or reference them from other sources.

**Administrator** - A user who ingests the course package into the LMS and provides access to the course for learners.

**<u>Process</u>**

1.  Author creates one or more units of separately launchable learning content presentations (AU's) that can communicate using cmi5.
2.  Author creates a course structure XML file that references the AU's URI location and provides Metadata for launch, description, and identification. The author also provides completion requirements rules.
3.  The AU's resources may be referenced from an external host or be placed in a ZIP file along with the course structure XML.
4.  Once the course package is completed, it is ready to be ingested into the LMS.
5.  The administrator imports the course package either as a XML file or a ZIP file containing the XML and media files if any. (LMS copies stuff)
6.  The administrator enrolls Learner(s) in the course associated with the imported course package. The enrollment is recorded in the LMS as a registration.
7.  The learner initiates the launch of an AU by interacting with the LMS.
8.  The LMS prepares launch data and records the launch in the LRS.
9.  The LMS redirects the learner to the AU presentation.
10. The learner interacts with the AU and the AU records activities, scores, mastery, and completion to the LRS

**<u>Key cmi5 features</u>**

**Launch Mechanism** - The Content (AU) is launched by LMS using a cmi defined Launch URL. The Launch URL is a URL to content with Query String Parameters which provides connectivity and authorization to the LRS. The Query String parameters provide the following:

-   LRS location (end point)
-   Learner Identifier (provided by the LMS)
-   Activity ID (provided by the LMS to identify the AU)
-   Registration (Provide by the LMS to indicate enrollment in a course)
-   A "Fetch URL" for the AU to retrieve an authorization token for accessing the LRS

Example:

> http://www.example.com/LA1/Start.html  
> ?endpoint=http://lrs.example.com/lrslistener/   
> &fetch=http://lms.example.com/tokenGen.htm?k=2390289x0   
> &actor={\"objectType\": \"Agent\",\"account\":   
> {\"homePage\": \"http://www.example.com\",\"name\": \"1625378\"}    
> &registration=760e3480-ba55-4991-94b0-01820dbd23a2   
> &activityId=http://www.example.com/LA1/001/intro

**Fetch URL** - The AU must retrieve an authorization token using the Fetch URL provided in the query string parameters in order to access the LRS. The Fetch URL may only be called once.

**Session Management** - A session is a period of time marked by the launch of an AU (Learning Activity) until its termination. All statements made by the AU and the LMS during a session are identified with a Session ID. The LMS manages the creation of sessions. cmi5 has rules for specific statements that must be sent to the LRS in a session.

**Extensibility** - cmi5 has statements specifically defined for completion, mastery, and session start/termination. However, AU's are not solely restricted to these statements. AU's may send additional statements for any other purpose as long those statements contain cmi5 session identification and are issued within an session.
