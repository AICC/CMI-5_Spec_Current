---
---

# Common cmi5 Mistakes
{% capture mtmp %}{% increment MistakeCount %}{% endcapture %}

------

### Common Mistake #{% increment MistakeCount %} – Disregarding the returnURL

**Mistake:**  The content (AU) does not redirect the browser to the returnURL when exiting

**Consequence:**  Since the best practice for LMS systems is to use the returnURL, the consequence of this mistake is rather significant, as the learner cannot return to the LMS user interface after exit.  This is also a violation of the minimum conformance requirements of cmi5 and the AU is not conformant.

### Common Mistake #{% increment MistakeCount %} –  Using the Activity ID as Publisher ID

**Mistake:**  The content (AU) does not use the publisher ID provided in the State API in context activities of the statements it makes, incorrectly using the LMS generated Activity ID instead.

**Consequence:**	 The consequence of this mistake is that the data in statements are incorrectly documented.  This is also a violation of the minimum conformance requirements of cmi5 and the AU is not conformant.

### Common Mistake #{% increment MistakeCount %} –  Disregarding the masteryScore

**Mistake:** The content (AU) does not issue the proper statements (Passed) when the score is above the masteryScore (as provided in the State API by the LMS).  Instead it uses its own internally specified score threshold to determine mastery.

**Consequence:**	The consequence of this mistake is that the content is incorrectly issuing passed or failed statements.  The AU is ignoring the masteryScore as provided by the LMS administrator (or course structure as it currently exists).  This is also a violation of the minimum conformance requirements of cmi5 and the AU is not conformant.

### Common Mistake #{% increment MistakeCount %} –  Automatic Satisfaction (Course Completion) immediately on Course Registration

**Mistake:** A course structure has not included moveOn Criteria for ANY of its AU’s.

**Consequence:**	The consequence of this mistake is that the course is immediately satisfied on registration (without the learner launching ANY AUs in the course).  While this does technically conform to requirements of cmi5, it is likely NOT the intent of the course designer.

### Common Mistake #{% increment MistakeCount %} –  Not respecting Browse and Review Launch Modes

**Mistake:** Launch mode values (of Browse and Review) provided by the LMS in the State Document are ignored by the AU.  

**Consequence:** The consequence of this mistake is that the AU incorrectly issues cmi5 statements other than initialized and terminated.  This is a violation of the minimum conformance requirements of cmi5 and the AU is not conformant.



------
