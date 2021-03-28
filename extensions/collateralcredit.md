
### collateralCredit

**Required:** No

**Data type:** collateralCreditReference

**Description:** The purpose of this optional property is to communicate the intention of the course author to the LMS how to approach scenarios such as "testing out" or instances for use of waived regarding this AU (or Block). The LMS MAY choose to implement the author’s recommendations. If implemented, this property defines a List of AUs (that MUST be in the course structure) that the LMS MUST issue Waived statements for when this AU (or Block) is Satisfied.  LMS should use reason of "Tested Out" or "Equivalent AU".   LMS's MAY provide additional information (such as the AU/Block id) within the "waived" Statement as an LMS defined extension.

**Value space:** List of ids from other AU’s in the course

**Sample value:**


```xml
<collateralCredits>
  <collateralCredit idref ="example.com/xyz123"></collateralCredit>
  <collateralCredit idref ="example.com/xyz456"></collateralCredit>
  <collateralCredit idref ="example.com/abc123"></collateralCredit>
</collateralCredits>
```

 
