## requires

**Required:** No

**Data type:** requiresReference

**Description:** The purpose of this optional property is to communicate the intention of the course author to the LMS that a specified list of AU’s must have met their moveOn criteria before this AU (or Block) is accessible by the learner.  The LMS MAY choose to implement the author’s recommendations.  If implemented, this property defines a List of AUs (that MUST be in the course structure) that MUST have met their moveOn criteria before the LMS allows the learner to access this AU (or Block). 

**Value space:** List of ids from other AU’s in the course

**Sample value:**

```xml
<requires>
      <require idref ="example.com/xyz123"></require>
      <require idref ="example.com/xyz456"></require>
      <require idref ="example.com/abc123"></require>
</requires>
```

**XSD – for requires**

(additional) cmi5 XSD definition for AU Type:
```xml
<xs:element name=" requires" type=" requiresReferenceType " minOccurs="0"/>
```

(additional) cmi5 XSD definition for Block Type:
```xml
<xs:element name=" requires" type="requiresReferenceType " minOccurs="0"/>
```

XSD definition for requiresType:

```xml
<xs:complexType name="requiresReferenceType"> <xs:sequence>
<xs:element name=" require" maxOccurs="unbounded">
<xs:complexType>
<xs:attribute name="idref" type="xs:anyURI"></xs:attribute>
</xs:complexType>
</xs:element>
<xs:group ref="anyElement"/>
</xs:sequence>
<xs:attributeGroup ref="anyAttribute"/>
</xs:complexType>
```
