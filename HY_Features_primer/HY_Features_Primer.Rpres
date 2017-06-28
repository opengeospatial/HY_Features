<style>
.br {
    position: fixed;
    top: 80%;
    left: 100%;
}

.iu {
    position: fixed;
    top: 150px;
}
.footer {
    color: black;
    position: fixed;
    top: 90%;
    text-align:right;
    width:5%;
}
.footer2 {
    color: black;
    position: fixed;
    top: 90%;
    text-align:right;
    width:5%;
}
</style>

WaterML2 Part 3: Surface Hydrology Features (HY_Features)
========================================================
author: David L. Blodgett
date: 06-2017
width: 1440
height: 900
A conceptual feature model for surface hydrology.

For more info, visit the [SWG home page.](http://www.opengeospatial.org/projects/groups/hydrofeatswg)

If you are an OGC member, [get the latest spec on pending docs.](https://portal.opengeospatial.org/files/?artifact_id=74219&version=2)

<div class="br" style="margin-left:-300px; margin-top:-300px;">
  <img src="catchmentNetwork.png"></img>
</div>

========================================================
left: 60%

**What is HY_Features?**

<div class="footer2">1</div>

HY_Features is a conceptual model describing hydrology features and their relationships

- The model describes hydrology specific feature types, e.g. catchments, drainage networks, rivers, lakes and waterbodies.
- Defined in the Unified Modeling Language (UML).
- All features specialize the General Feature of the ISO / OGC General Feature Model.
- Most features "specialize" a general HY_HydroFeature providing multilingual naming.
- HY_Features models hydrologic units and surface waterbodies.
- Focus is on surface water features and the networks they form.

***
<div class="iu">
<img src="intro_uml.png">
</div>

========================================================

**What is HY_Features for?**

HY_Features provides a common conceptual basis for
identification of hydrologic features.

This should help provide:

1. shared feature types defined for use in the hydrology domain,
2. a common language for documenting datasets,
3. a standard conceptual model for data and software,
4. a means to unify hydrologic feature identities across data products.

<div class="br" style="margin-left:-300px; margin-top:-300px;">
  <img src="catchmentNetwork.png"></img>
</div>

<div class="footer">2</div>

========================================================

**What kinds of features are in HY_Features?**

HY_Features includes: hydrologic units,
the junction features that join them, and the waterbody
features that drain them. The core feature concepts are:

- **catchment**: a holistic and abstract hydrologic unit concept, that links inflow and outflow.
- **hydro nexus**: a holistic and abstract junction concept, that connects interacting catchments.
- **realization**: a hydrology-specific way of interpreting a holistic feature.
- **waterbody**: an identified body of water, that accumulates runoff in a catchment.
- **container**: a depression or channel that may hold a waterbody, that drains a catchment.
- **hydro network**: a network of catchments that forms a larger, containing catchment. 

Note: Catchment and nexus are not modeled as abstract classes in UML. Abstract 
is used to describe that these are meant to represent the abstract notion 
of a hydrologic unit or junction.

<div class="footer">3</div>

========================================================

**What is a catchment?**

Catchment is a holistic abstract notion of a hydrologic unit (a feature type).

It is a physiographic unit defined by a common outlet (and
potentially an upstream inlet.)

In other words a catchment is...
- the basic unit of study in hydrology and water resources management
- a hydrologic system that drains to a defined outlet
- an area in which hydrologic processes take place
- the link from one inlet hydro nexus to one outlet hydro nexus

<div class="footer">4</div>

========================================================

**What is a Hydro Nexus?**

A hydro nexus is a place where two or more catchments interact.

Theoretically, there is a hydro nexus anywhere on the landscape.

However, we usually identify significant places to break up our catchments.

A hydro nexus...
- can act as a pour point at the boundary of a catchment
- can act as an inlet to or an outlet from a catchment
- can receive flow from and give flow to multiple catchments

Note: Typically, a hydro nexus is a location at the end of a flow path, but other
realizations, such as areas of infiltration, could be introduced in future work. 

<div class="footer">5</div>

========================================================

**What is hydrologic realization?**

Catchment and hydro nexus are meant to be holistic and
have several hydrology-specific interpretations.

HY_Features deals with this by saying they can be **realized** in a number of ways.

<div align="center">
<img src="fig5.png" height=420>
</div>

<small>_Note that "realization" and "realized" are UML class association names between a holistic feature (the realized feature) and a specific feature (the realization feature)._</small>

<div class="footer">6</div>

========================================================

**What is hydrologic realization?**

As shown in this figure, a catchment can be
realized as a divide (A.), an area (B.), a main flowpath (C.), a network
of catchments (D.), a network of waterbodies (E.), a dendritic topologic network (F.),
a complex feature network (G.), or a collection of monitoring sites (H.).

<div align="center">
<img src="fig5.png" height=420>
</div>

<small>_Note that these realizations are meant to be conceptual.
The graphics are only meant to illustrate the concept._</small>

<div class="footer">7</div>

========================================================

**How do waterbodies work in HY_Features?**

- First, consider a main flowpath waterbody of a catchment. 
- Zoom out to a network of sub-catchments and their flowpaths. 
- Now we have a network of waterbodies, each of which is a realization of a sub-catchment.

<div align="center">
<img src="singleFlowpath.png" height=500><img src="catchmentNetwork.png" height=500><img src="base.png" height=500>
</div>

<div class="footer">8</div>

========================================================
left: 70%

<div class="footer2">9</div>

**How do waterbodies work in HY_Features?**

- A main flowpath or network of waterbodies realizes a catchment.

- A main flowpath or network delivers a catchment's flow to a hydro nexus.

- A hydro nexus is realized by a hydro location on the waterbody network.

***

![img](hydrographicNetwork.png)

========================================================
left: 70%

<div class="footer2">10</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.

***

![](sequence_1.png)

========================================================
left: 70%

<div class="footer2">11</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, you have two **hydrologic locations**.

***

![](sequence_2.png)

========================================================
left: 70%

<div class="footer2">12</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, you have two **hydrologic locations**.
3. Delineate the **divide** around the area that drains to the blue line.

***

![](sequence_3.png)

========================================================
left: 70%

<div class="footer2">13</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, you have two **hydrologic locations**.
3. Delineate the **divide** around the **area** that contributes to the blue line between the two hydro locations.

***

![](sequence_4.png)

========================================================
left: 70%

<div class="footer2">14</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, you have two **hydrologic locations**.
3. Delineate the **divide** around the **area** that drains to the blue line.
4. Give the delineated hydrologic unit a name and ID. This is your **catchment**.

***

![](sequence_5.png)

========================================================
left: 70%

<div class="footer2">15</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, you have two **hydrologic locations**.
3. Delineate the **divide** around the **area** that drains to the blue line.
4. Give the delineated hydrologic unit a name and ID. This is your **catchment**.
5. Now that you have identified your catchment, you can consider your hydrologic locations to be realizations of **hydrologic nexuses** of your catchment.

***

![](sequence_6.png)

========================================================
left: 70%

<div class="footer2">16</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

Now we have catchment *12* with inflow hydro nexus *34* and
outflow hydro nexus *56*.

Catchment *12* is realized as a linear *divide* polygon, a planar *area*
and a main *flowpath* line.

Hydro nexuses *34*, and *56* are realized as hydro locations.

***

![](sequence_6.png)

========================================================
left: 70%

<div class="footer2">17</div>

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

Imagine that there are alternate data or geometric representations 
of the catchment between Hydro Nexus *34* and *56*. These may be:

- for mapping at a different spatial scale
- from a different data processing method
- defined by a different originating organization
- representative of a different process such as surface 
water contributing or groundwater contributing catchment

As long as various data products represent the same 
hydrology-specific catchment realization and identify 
the same realized catchment, they can be associated directly 
or related data and reports can also be unambiguously linked.

***

![](sequence_7.png)

========================================================
left: 70%

<div class="footer2">18</div>

**Networks of Waterbodies or Channels and Catchment Interactions**

A catchment can be realized as a network of waterbodies, 
shown here as a simple network of blue lines meant to represent
waterbodies. 

A catchment can also be realized as the network of its channels, 
shown here as a network of orange lines that may contain the waterbodies.

Also illustrated here, two catchments and their associated waterbodies/channels
interact at a hydrologic location that is referenced to the waterbody/channel 
network that realizes the whole catchment.


***

![](sequence_8.png)

========================================================
left: 75%

<div class="footer2">19</div>

**Networks of Waterbodies or Channels and Catchment Interactions**

If we create hydro locations at junctions in the waterbody network 
and associate them with hydro nexuses and catchments, it becomes clear 
that a waterbody or catchment (boundary) network is also be a 
network of many individual catchment realizations.

If we connect water bodies with hydro locations at 
their inlets and outlets, we get a network of catchments interacting at 
their hydro nexuses. By using consistent identifiers for the hydro 
nexuses and the associated catchments, datasets representing 
waterbodies/channels that are built at different scales can be 
tied together.

The ability to both tie datasets together accross scales and to 
support linking various data sets that represent the same real-world 
features, is the primary goal of HY_Features conceptual model. Future 
work will be able to build on this conceptual basis, adding formal 
encodings for linking data together and encoding hydrographic data 
directly.

***

![](sequence_9.png)

========================================================
left: 75%

<div class="footer2">20</div>

**Ways of Conforming to HY_Features -- Conformance Classes**

**1) Data Model Mapping**  
HY_Features can be useful in describing the characteristics of an existing data 
model. In this case, conformance is accomplished by recording how a given dataset 
"maps" onto HY_Features. Note that the actual level of coorespondence can be low. 
As long as the mapping itself considers all mandatory elements of HY_Features, it 
would be considered conformant. 

**2) Implementation of an Encoding of HY_Features**  
In this case, all mandatory properties, associations, and default values are 
required in the implementation for one or more HY_Features feature type. Implementations 
would necessarily extend and profile the HY_Features conceptual model, adding specific 
geometric representations and specifying which HY_Features featuretypes are to be included.

***

<div class="br" style="margin-left:-300px; margin-top:-300px;">
  <img src="catchmentNetwork.png"></img>
</div>


