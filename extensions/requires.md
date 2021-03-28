## requires

**Required:** No

**Data type:** requiresReference

**Description:** The purpose of this optional property is to communicate the intention of the course author to the LMS that a specified list of AU’s must have met their moveOn criteria before this AU (or Block) is accessible by the learner.  The LMS MAY choose to implement the author’s recommendations.  If implemented, this property defines a List of AUs (that MUST be in the course structure) that MUST have met their moveOn criteria before the LMS allows the learner to access this AU (or Block).> Value space: List of ids from other AU’s in the course

**Sample value:**

<requires>
      <require idref ="example.com/xyz123"></require>
      <require idref ="example.com/xyz456"></require>
      <require idref ="example.com/abc123"></require>
</requires>
  
