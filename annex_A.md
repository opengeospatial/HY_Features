## ANNEX A - Abstract Test Suite (normative)

### A.1 Introduction
These test suites ascertain the compliance of the conformance targets for the HY_Features specification with the specification itself. Each instance of hydrologic feature data is encoded according to a specific interchange schema, so the role of conformance with the abstract specification is that such an implementation schema can be related to the common definitions of HY_Features.

### A.2 Conformance class: HY_HydroFeature application schema equivalence

| **Conformance Class** | [/spec/hydrology/hydrofeature/1.0/conf/hy_ hydrofeature] (/spec/hydrology/hydrofeature/1.0/conf/hy_ hydrofeature) | 
| --- | --- | 
| Test | [/conf/uml_hydrofeature/namedfeature/*] (/conf/uml_hydrofeature/namedfeature/*) | |
| Test | [/conf/uml_hydrofeature/catchment/*] (/conf/uml_hydrofeature/catchment/*) | |
| Test | [/conf/uml_hydrofeature/network/*] (/conf/uml_hydrofeature/network/*) | |
| Test | [/conf/uml_hydrofeature/positioning/*] (//conf/uml_hydrofeature/positioning/*) | |
| Test | [/conf/uml_hydrofeature/storage/*] (/conf/uml_hydrofeature/storage/*) | |
| Requirement | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test purpose | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test method | Inspect the mapping between the data exchange schema and the HY_Features model to determine that all relevant schema elements are mapped to HY_Features equivalents. |
| Test type | Capability | 

### A.3 Conformance class: HY_SurfaceHydroFeature application schema equivalence

| **Conformance Class** | [/ spec/hydrology/surfacehydrofeature/1.0/conf/hy_ surfacehydrofeature] (/ spec/hydrology/surfacehydrofeature/1.0/conf/hy_ surfacehydrofeature) | 
| --- | --- |
| Test | [/conf/uml_surfacehydrofeature/surfacewater/*] (/conf/uml_surfacehydrofeature/surfacewater/*) |
| Test | [/conf/uml_surfacehydrofeature/surfacewaterconfines/*] (/conf/uml_surfacehydrofeature/surfacewaterconfines/*) |
| Requirement | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test purpose | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test method | Inspect the mapping between the data exchange schema and the HY_Features model to determine that all relevant schema elements are mapped to HY_Features equivalents. |
| Test type | Capability | 

### A.4 Conformance class: HY_HydrometricFeature application schema equivalence

| **Conformance Class** | [/ spec/hydrology/hydrometricfeature/1.0/conf/hy_ hydrometricfeature] (/ spec/hydrology/hydrometricfeature/1.0/conf/hy_ hydrometricfeature) | 
| --- | --- |
| Test | [/conf/uml_ hydrometricfeature /surfacewater/*] (/conf/uml_hydrometricfeature /surfacewater/*) |
| Requirement | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test purpose | All relevant elements of a data exchange schema including hydrologic features are mapped to equivalent HY_Features elements. |
| Test method | Inspect the mapping between the data exchange schema and the HY_Features model to determine that all relevant schema elements are mapped to HY_Features equivalents. |
| Test type | Capability | 

