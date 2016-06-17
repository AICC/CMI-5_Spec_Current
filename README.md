
----------

<p>
<p align=center><img src="https://cloud.githubusercontent.com/assets/1656316/9965238/bc9deb2c-5de9-11e5-9954-63aa03873f88.png" align=center></p>



# The cmi5 Project #

---

## What is cmi5 ? A set of "extra rules" for xAPI##


cmi5 is a "profile" for using the [xAPI specification](https://github.com/adlnet/xAPI-Spec) with traditional learning management (LMS) systems.  

Since the xAPI specification is highly generalized to support many different use cases, a set of "extra rules" (called a "profile") is needed to ensure interoperability for a given use case. The cmi5 profile ensures plug and play interoperability between learning content and LMS systems. 

The use case that the cmi5 profile is specifically designed for is one where the learner launches the learning content/activity from the LMS user interface.  

cmi5 defines specific interoperability rules for the following areas:

- Content Launch Mechanism
- Authentication
- Session Management
- Reporting
- Course Structure



## Goals

The mission of cmi5 is to provide a better alternative to current AICC/SCORM specifications with something considerably more flexible, robust, and adaptable to today's technologies. The specific goals of cmi5 are as follows:

#### 1 - A simplified tracking data model

SCORM and AICC data models were too complicated and had many optional data elements that were not used. The goal of simple data model is to only define the bare minimum data elements required that would work across most learning domains. (e.g. Score, status, and time).

#### 2 - The ability to record and report/retrieve content-defined data

Restricting data collection to a small set of required data elements was too limiting.  In most cases what was really needed was the just the ability to record the data from the content in the LMS and later retrieve it for analysis. The goal of allowing content defined data recording/retrieval allows content designers to add features and still be interoperable.

Content defined data can either be text or digital data. 

- Extensible Data Model (defined by the content text data)
- Digital Data attachments 

#### 3 - Support for content as a service (CaaS) model of delivery
Allow content to be stored on other domains (independent of the LMS server domain)

#### 4 - Device/OS/browser independence

Allow for content to be independent of a browser in order to communicate or be launched.

#### 5 - Share data between learning activities

Allow data to be shared between learning activities for multiple learners enrolled in the same course.


## History

The ***cmi5*** project was originally started in the AICC (Aviation Industry Computer-Based Training Committee) in 2010. ***cmi5*** was expected to replace both AICC and SCORM specifications with a more feature-rich and robust solution.  Both AICC and SCORM specifications had technical issues and constraints as well as significant overlap.

The AICC was nearing completion of SOAP-based communication mechanism for cmi5 in 2012 about the same time the Tin Can API research project (now called xAPI) was completed in the ADL. 

The AICC and ADL participants soon determined that there was significant overlap between the two specifications.  xAPI had broader application than ***cmi5***, so the ADL and AICC agreed to cooperate on an "xAPI profile" to meet the more specific use case needs of ***cmi5***. So the cmi5 project was "rebooted" in 2012 and the SOAP architecture was replaced with xAPI. The ***cmi5*** project is still guided by its original goals.
  
In 2014, the AICC  dissolved and formally transferred the ***cmi5*** project to the ADL.


## Versions

The versioning of cmi5 is as follows:

- Major versions change functionality or interoperability.
- Major versions of cmi5 are named by "rocks" (granite, basalt, etc.). 
- Minor versions correct errata (errors) only
- Minor versions of cmi5 are serialized by "edition"  (1st, 2nd 3rd, etc)

For example "Sandstone, 1st edition".

### Sandstone (released May 2015)

Sandstone is the first release of cmi5.  It is a "developer release" to collect feedback from learning technology developers.  It is not intended for actual implementation.  

- [Sandstone, 1st Edition](https://github.com/AICC/CMI-5_Spec_Current/tree/sandstone-release)

### Quartz (currently in work)

Quartz is currently in work and scheduled for release in June 2016.  The Quartz version will include developer feedback collected from Sandstone.  When completed, Quartz will be the first "production release" intended for implementation.

- [Quartz, Current Draft](https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md)


## cmi5 Articles ##

The following are articles that discuss cmi5 and explain its potential uses: 

- [Experience API, cmi5, and Future SCORM](http://bit.ly/1Pjad2W)
- [Time to Plugin to cmi5?](https://www.linkedin.com/pulse/time-plugin-cmi5-bill-mcdonald)
- [cmi5: The next generation SCORM](http://risc-inc.com/next-generation-scorm-cmi5/)
- [cmi5 Process Flow: An overview](http://risc-inc.com/blog/cmi5-overview-process-flow/)
- [cmi5: xAPI for LMSs](http://www.slideshare.net/BillMcDonald3/cmi5xapicamp-50890282)

(More will be added as they become available)

## Connect with the cmi5 community!

Please note that the cmi5 working group is a volunteer community effort and is open to all.  

We very much want to encourage people to share their thoughts about cmi5 and participate.  Please consider connecting with us in one or more of the following ways:

### cmi5 GitHub

All are welcome to raise issues/comments on this GitHub repository.

Also, [please see our wiki](https://github.com/AICC/CMI-5_Spec_Current/wiki) for a comprehensive set of meeting minutes.

### cmi5 Email Address
Please send questions for the working group to: [cmi5wg@adlnet.gov](mailto://cmi5wg@adlnet.gov)

### Weekly GotoMeeting Conferences

The cmi5 working group holds weekly Web Conferences that are open to all. The meeting are held every Friday at 10:30 am US Eastern Time. See link below to register:

- [Register For cmi5 Working Group Conferences](https://attendee.gotowebinar.com/register/834085493171125249)

### xAPI Spec Development Calls

The xAPI group meets the first 3 Wednesdays of each month from 2:30 - 3:30 EST. All are welcome.

- [Register For xAPI Working Group Meetings](https://attendee.gotowebinar.com/register/279276321478091778)

### Subscribe to cmi5 Mailing list

This list provides weekly meeting minutes and news about cmi5.

- [Subscribe to cmi5 Mailing list ](http://eepurl.com/bjlA01) (Managed by Mail Chimp).  

### The cmi5 LinkedIn Group

The cmi5 LinkedIn group was established to encourage discussion about cmi5 and answer your questions.  Please join at link below:

- [cmi5 LinkedIn Group](http://www.linkedin.com/grp/home?gid=3943740)

### Follow cmi5 on Twitter

Follow cmi5 on Twitter: [#cmi5](https://twitter.com/hashtag/cmi5), [@cmi5spec](https://twitter.com/cmi5spec)

### Join the cmi5 Slack Team

The cmi5 working group is currently testing Slack team communication. To join the slack group, please use the following link: [Add me to the cmi5 Slack Team](mailto:cmi5wg@adlnet.gov?subject=%5Bcmi5%20Slack%20Registration%5D&body=Please%20add%20me%20to%20the%20cmi5%20slack%20working%20group.)

----------
