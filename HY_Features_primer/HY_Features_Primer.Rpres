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
</style>

WaterML2 Part 3: Surface Hydrology Features (HY_Features)
========================================================
author: David L. Blodgett
date: 06-2017
width: 1440
height: 900

<div class="br" style="margin-left:-300px; margin-top:-300px;">
  <img src="catchmentNetwork.png"></img>
</div>

========================================================
left: 50%

**What is HY_Features?**

HY_Features is a conceptual model defined in the Unified
Modeling Language (UML).

- The model describes hydrology specific feature types.
- All features "specialize" a general HY_HydroFeature.
- HY_Features models hydrologic units and waterbodies.

***

<div class="iu">
<img src="intro_uml.png">
</div>

========================================================

**What is HY_Features for?**

HY_Features provides a common conceptual basis for
identification of hydrologic features.

This should help provide:

1. a shared set of hydrologic feature types,
2. a common language for documenting datasets,
3. a standard conceptual model for data and software.

========================================================

**What kinds of features are in HY_Features?**

HY_Features includes: hydrologic units,
the junction features that join them, and the waterbody
features that drain them. The core feature concepts are:

- **catchment**: a holistic and abstract hydrologic unit feature.
- **hydro nexus**: a holistic and abstract junction or node feature.
- **realization**: a feature that is a distinct perspective of
an holistic feature.
- **waterbody**: a distinct named or otherwise identified body of water.
- **container**: a depression or channel that may hold a waterbody.

========================================================

**What is a catchment?**

Catchment is a holistic and abstract featuretype.

It is a physiographic unit defined by a common outlet (and
potentially an upstream inlet.)

In other words a catchment is...
- the basic unit of study in hydrology and water resources management
- a hydrologic system that drains to a defined outlet
- an area in which hydrologic processes take place
- the link from one inlet hydro nexus to one outlet hydro nexus

========================================================

**What is a Hydro Nexus?**

A hydro nexus is a place where two or more catchments interact.

Theoretically, there is a hydro nexus anywhere on the landscape.

However, we usually identify significant places to break up our catchments.

A hydro nexus...
- is a node at the boundary of a catchment
- can act as an inlet to or an outlet from a catchment
- can recieve flow from and give flow to multiple catchments

========================================================

**What is hydrologic realization?**

Catchment and hydro nexus are meant to be holistic and
have several hydrology-specific interpretations.

HY_Features deals with this by saying they can be **realized** in a number of ways.

<div align="center">
<img src="fig5.png" height=600>
</div>

<small>_Note that "realization" and "realized" are UML class association names between a holistic feature (the realized feature) and a specific feature (the realization feature)._</small>

========================================================

**What is hydrologic realization?**

As shown in this figure, a catchment can be
realized as a divide, an area, a main flowpath, a network
of catchments, a network of waterbodies, a topologogy,
a complex network, or a collection of monitoring sites.

<div align="center">
<img src="fig5.png" height=600>
</div>

<small>_Note that these realizations are meant to be conceptual.
The graphics are only meant to illustrate the concept._</small>

========================================================

**How do waterbodies work in HY_Features?**

First, consider a main flowpath waterbody of a catchment. Zoom out to a network of catchments and their flowpaths. Now we have a network of waterbodies, each of which is a realization of a catchment.

<div align="center">
<img src="singleFlowpath.png" height=600><img src="catchmentNetwork.png" height=600><img src="base.png" height=600>
</div>

========================================================
left: 70%

**How do waterbodies work in HY_Features?**

A main flowpath or network of waterbodies realizes a catchment.

A main flowpath or network delivers a catchment's flow to a hydro nexus.

A hydro nexus is realized by a hydro location on the waterbody network.

***

![img](hydrographicNetwork.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.

***

![](sequence_1.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, call them **hydrologic locations**.

***

![](sequence_2.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, call them **hydrologic locations**.
3. Delineate the **divide** around the area that drains to the blue line.

***

![](sequence_3.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, call them **hydrologic locations**.
3. Delineate the **divide** around the **area** that drains to the blue line.

***

![](sequence_4.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, call them **hydrologic locations**.
3. Delineate the **divide** around the **area** that drains to the blue line.
4. Give the delineated hydrologic unit a name and ID and call it a **catchment**.

***

![](sequence_5.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

The relationship between these four types of features, is
best illustrated as a sequence of steps.

1. Given a **waterbody** feature, lets say it's a line.
2. Choose two locations on that line, call them **hydrologic locations**.
3. Delineate the **divide** around the **area** that drains to the blue line.
4. Give the delineated hydrologic unit a name and ID and call it a **catchment**.
5. Now call the hydrologic locations **hydrologic nexuses**.

***

![](sequence_6.png)

========================================================
left: 70%

**Waterbody -- Hydro Location and Catchment -- Hydro Nexus**

Now we have catchment *12* with inflow hydro nexus *34* and
outflow hydro nexus *56*.

Catchment *12* is realized as a linear *divide* polygon, a planar *area*,
and a main *flowpath* line.

Hydro nexuses *34*, and *56* are realized as hydro locations.

***

![](sequence_6.png)



