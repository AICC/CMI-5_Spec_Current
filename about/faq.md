---
---

# cmi5 FAQ (Frequently Asked Questions)

------


1.  **Why was cmi5 created?** The cmi5 project was started as a result of efforts by the ADL and the AICC to harmonize the AICC and SCORM specifications which diverged and were no longer compatible. It soon became obvious that the effort would be better served by a complete replacement with more features and better technology (restful web services). The AICC started the effort in 2010 with SOAP and then redesigned the effort to leverage xAPI in 2012.

2.  **What does cmi5 mean?** The name came from the original AICC (Aviation Industry Computer-Based Training Committee) specification for "cmi" (Computer Managed Instruction) interoperability. The AICC developed multiple versions of this spec and then decided to completely redesign "cmi" -- since the last version was "4" the project was called "cmi5". Now "cmi5" is actually the name of the specification, not an acronym. The "5" in cmi5 does not represent a version (i.e. there will not be a "cmi6"). cmi5 is versioned by release name, e.g. "cmi5 -- Quartz" -- [see spec for versioning] - )

3.  **Who created cmi5?** cmi5 was originally a project created by the AICC (Aviation Industry Computer-based Training Committee) in 2010. When the AICC dissolved in 2014, the cmi5 project was transferred to the ADL (Advanced Distributed Learning) Initiative. The ADL currently stewards and hosts the community effort for supporting/developing the cmi5 specification.

4.  **Who is using cmi5? The following organizations are using cmi5:**

     -   **US DoD (Dept. of Defense)** - Through DoD policy, the ADL (Advanced Distributed Learning Initiative) is recommending the use of cmi5 in its distributed learning solutions. Additionally, the ADL is developing tools/templates to provide support for cmi5 adopters inside and outside of the DoD.

     -   **LMS Vendors** -- See [this link] for LMS vendors currently supporting cmi5

     -   **Authoring Tool Vendors** -- See [this link] for Authoring Tool vendors currently supporting cmi5

5.  **Why are you using Basic Auth?** Basic Auth is not being used as a username/password encoding scheme in cmi5.  Basic Auth (RFC 7235) was selected because it was the most widely used scheme at the time the xAPI specification was created.  Basic Auth is used to provide a temporary “authorization” to the LRS (not authentication to the LRS).  Authentication to the LRS is expected to be managed by the LMS or some other mechanism.  With cmi5, a Basic Auth token is used in the HTTP header of xAPI requests made by the Learning Activity.  Actual learner authentication is outside the scope of cmi5.   

6.  **Can there be more than one launchable module in a cmi5 package?** Yes. In the cmi5 specification, a "Course" is a collection of separately launchable learning activities called AUs (Assignable Units). cmi5 requires that the LMS support at least 1,000 AUs in a course. AUs in a course can be grouped in a hierarchy of "Blocks".

7.  **Do I need an LMS to use cmi5 in my Learning content?** Yes. You cannot use cmi5 learning content without a cmi5 enabled LMS (or similar system). The system used to manage the learning content (LMS or otherwise) must have either a built-in LRS or provide integration with an LRS. In cmi5, the LMS provides special launch parameters that the learning content must use to connect to the correct LRS.

8.  **How do I make my Learning Content cmi5 compliant?** The easiest way to make your learning content cmi5 compliant is to use an authoring tool that can generate a cmi5 package. If you have existing SCORM content (the source material), implementing cmi5 could be as easy as republishing the content as cmi5 from your authoring tool. If your Authoring tool does not support cmi5, contact your vendor and ask if cmi5 support is on their product roadmap! You can also can develop cmi5 capabilities yourself if you have the technical expertise to do so. There is an example runtime library available that makes implementation relatively easy for tool developers ([see this link]).

  [see spec for versioning]: https://github.com/AICC/CMI-5_Spec_Current/blob/quartz/cmi5_spec.md#revhistory
  [this link]: https://aicc.github.io/CMI-5_Spec_Current/adoption/
  [see this link]: https://aicc.github.io/CMI-5_Spec_Current/client/
