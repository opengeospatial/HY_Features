## ANNEX B - The Utilities application schema (informative)


The informative Utilities schema introduces utility classes for common patterns required by the HY_Features domain model, that are not hydrology-specific. These classes are intended to identify feature characteristics which are usually understood as the 'core' or 'master' metadata, and which are not observed in the narrower sense through using a distinct sampling feature or applying a certain procedure. The concepts proposed here are primarily defined to support the named hydrologic feature named differently within cultural, political or historical context, and to which specific characteristcs are assigned in the perspective of a contextually related domain. However, they may be generally applicable to domains where features are named in multilingual and cross-jurisdiction contexts,  where features are recognised differently in space and time and categorized under a particular perspective.

The EXT_LocalisedName class is intended to expand the comparable concept of a *localised character string*, defined in the 'Cultural and linguistic adaptability' informative package of ISO19139(2007):Metadata XML Implementation, for the information about the mode of a name's usage, and about the standard used for romanisation, transcription or transliteration of characters of another alphabet into Latin characters. This may support internationally acting information services to resolve conventionally used names to local names, and to improve the interoperability with national data providing systems across languages and scripts.

The EXT_SpatialContext class provides a means to describe the spatial 'overlap' of a source feature, especially a hydrologic feature, with a target spatial feature in another domain, e.g. the number of countries or WMO regions sharing the catchment, or the rock or soil types characterising it. Spatial context is identified by the domain within which a spatial overlap exists, the number of specified features in the target domain that the source feature overlaps, an identifier and a (keyword) characterisation of the source (hydrologic) feature in related domain. This characterisation may be specialised to simplify the nature of this information, such as a single numeric value. 

The EXT_TemporalContext class provides a means to describe the existance or behaviour in time of a source feature, especially a hydrologic feature, e.g. the lifespan of reservoir. Temporal context is identified by (keyword) characterisation of the source (hydrologic) feature in time, the temporal extent of the characteristc and the status whether a characteristic applies or not. This characterisation may be specialised to simplify the nature of this information, such as a single numeric value. 

The EXT_ClassifcationContext class provides a means to desribe the classification used to arrange a feature or feature property according to agreed criteria. Classification context is identified by keyword expressing the position or rank in a classification system, the name of the classifcation system applied, and an expression of the high-level topic or theme the related classification system refers to. 

The EXT_MultilingualKeyword class provides a simple means to describe a multilingual keyword used in cross-jurisdiction context to describes the contextual relationships of the hydrologic feature by identifying the keyword as a localised character string as defined in this utilities package, and by a keyowrd role using a domain specific term. Recognising the wide range of context-related listings of  keywords in the domain, an 'empty' EXT_KeywordRole container is defined, that supports the use of keyword grouping agreed in the domain instead of the keyword type list given in the ISO metadata model. It is intended that an implementation will reference a domain-specific keyword typing. 

![Figure 30: Utilities required for the hydrologic feature model (UML class diagram)](figs/fig30.png) 
Figure 30: Utilities required for the hydrologic feature model (UML class diagram) 