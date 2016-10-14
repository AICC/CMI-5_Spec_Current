---
---

# Best Practices

------

### Best Practice #1 – Use of Objectives

(Since Objectives usage outside of course structure is not defined.)

Objectives are defined for the course structure, but there is no language in the specification concerning their usage in statements. If using Objectives in statements (as Activities) the best practice is to use the Activity Definition type (http://adlnet.gov/expapi/activities/objective) from the ADL vocabulary.

The same Objective can be referenced by multiple AU or Blocks. There are 2 ways to interpret meeting an Objective. The two expected practices are:

1. All elements referencing the Objective need to be Satisfied (or met moveOn criteria)
1. Only one element referencing the Objective needs to be Satisfied (or met moveOn criteria).

It is recommended that LMS developers document how they do this and allow for an extension (in the course structure) to indicate what method should be used.

------

### Best Practice #2 – Resolvable IRI's**

All IRI’s must be unique in the cmi5 spec. However, The Best practice to ensure a unique IRI should include a valid domain/host name and be resolvable.

Per XAPI specification:

> Internationalized Resource Locator (IRL): In the context of this document, an IRL is an IRI that when translated into a URI (per the IRI to URI rules), is a URL. Some communities of practice simply use URL even if they use IRIs, which isn't as technically correct within xAPI.

The resolution of an IRI should return a description of the IRI’s purpose/origin.

### Best Practice #3 – LMS resolution of relative course ID IRI’s.**

If the LMS imports a course with relative IRI’s it should prepend a valid protocol (http://, ftp://, or relative protocol // etc. ), domain, and path.

If other course elements have relative IRI’s, the LMS should prepend the course IRI to the relative course element IRI


> (Course IRI)(AU relative IRI) 
