#Environmental Sample Data Standard
###Introduction
The Environmental Investigations Division (EID) Environmental Sample Data Standard provides a standard way to represent information associated with environmental samples collected as part of environmental investigations and monitoring. The standard provides a consistent view of sample information and defines a minimum set of attributes necessary to document a sample within BES programs.

This standard does not purport to address all of the information necessary to support specific programs. However, the standard should be adequate to document the identity and the minimum set of attributes necessary to generally describe a sample. In addition, the standard provides a way to associate arbitrary properties with locations in a standard way.

###Entities

The Standard has three entities associated with an environmental sample. The entities, along with their cardinality, are:

1. Environmental Sample Identification (1)
2. Environmental Sample Relation (n)
3. Environmental Sample Property (n)

###Environmental Sample Identification

The Environmental Sample Identification section is the core of the standard. This contains the minimum information necessary to identify and describe an environmental sample. The necessary attributes are:

Attribute Name | Description | Examples
---------------|--------------|----------
Namespace	  | The Namespace provides the domain or authority from which the identifier comes. It may be a project, an agency that assigned the identifier, or an information system (e.g., STORET or WPCL ELEMENT). For example, if the monitoring is to be conducted from the existing USGS monitoring station on Fanno Creek at 56th Ave  then the Namespace would be ‘USGS’ and the Identifier would be 142069000. |	USGS,WPCL Element,Tryon Creek Water Quality Project
Identifier  | An identifier used to identify a monitoring location. It is not expected to be human readable. It should be unique within the Namespace.	
Description	| A description of the sample which can be used to convey additional information not easily captured with other fields.	
Collection Date | The date-time that sample collection was completed.
Medium	        | Webster: a surrounding or enveloping substance. Gold book: the phase (and composition of the phase) in which chemical species and their reactions are studied in a particular investigation.	| [USGS Medium Codes](http://help.waterdata.usgs.gov/medium_cd)<br>[EPA WQX Media](http://cdx.epa.gov/wqx/download/DomainValues/ActivityMedia.zip)<br>[EPA WQX Media Subdivision](http://cdx.epa.gov/wqx/download/DomainValues/ActivityMediaSubdivision.zip)
SampleType      | The type of the sample being collected: often conveys information about how and for what purpose the sample was collected. |Duplicate<br>Trip Blank<br>Equipment Blank
IsQC            | Is the sample being collected for Quality Control purposes?	
IsCompliance              | Is the sample being collected to comply with a regulatory requirement?	|
SampleCollectionProcedure	| A reference to a procedure used to collect the sample. |
SampleHandlingProcedure  	| A reference to a procedure applied to the sample prior to being submitted for analysis. If the handling is part of the SampleCollectionProcedure, then this does need to be recorded separately.	Field filtering, sieving, grinding are all commonly used. |
LaboratoryIdentifier      | An identifier given to the sample by the laboratory receiving it.|

###Environmental Sample Relation

Environmental samples and monitoring locations are related to each other in sampling complexes. Often, the relationship is simple (e.g., a sample is collected from a monitoring location). However, sometimes there are complex relationships between and among samples and locations. Composite samples, split samples, duplicate samples, and trip blanks all imply more complex relationship between and among samples and locations. The required attributes for Environmental Sample Relation are:

Attribute Name |	Description |	Example
---------------|--------------|----------
ToNamespace  |	The namespace of the sample or monitoring location on which the sample depends. |
ToIdentifier | The identifier of the sample or monitoring location on which the sample depends. |
Relationship |	The name of the relationship between the sample and the sample/location on which it depends. |


Samples can depend either on samples or locations. For example, a *composite sample* whose parent samples are given identifiers and persisted will have relationships with all of the parent samples. A *composite sample* whose parent samples are not given identifiers and persisted will have relationships with the monitoring locations from which the parent samples were obtained. A *duplicate sample* will have a relationship with both the location that it was collected from and the sample for which it serves as a duplicate. Figure 1 illustrates common relationships in EID sampling programs.

![Examples of the relationships among samples and locations.](https://github.com/jasonelaw/eid-sample/img/RelationExamples.png "Figure 1: Examples of the relationships among samples and between samples and locations.")

###Environmental Sample Property

All monitoring programs and projects have different requirements and different designs. These differences result in differences in information requirements across projects and programs. The Environmental Sample Identification section above allows for information about environmental samples to be recorded in a consistent way across programs and projects. Project or program specific information about environmental samples can be represented by Environmental Sample Property. The attributes necessary to describe an Environmental Sample Property:

Attribute Name | Description | Example
---------------|-------------|----------
PropertyName | The name of the property of the environmental sample. |	
PropertyValue | The value of the property of the environmental sample. |

