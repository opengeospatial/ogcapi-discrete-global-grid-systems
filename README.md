# OGC API - Discrete Global Grid Systems

This GitHub repository contains the draft [OGC API - Discrete Global Grid Systems](https://ogcapi.ogc.org/dggs/) standard, as well as supporting information.

The latest draft candidate standard can be accessed [here in HTML](https://docs.ogc.org/DRAFTS/21-038.html) and [here in PDF](https://docs.ogc.org/DRAFTS/21-038.pdf).

The OpenAPI building blocks defined by the specification as well as complete bundled example API definition are [available here](https://github.com/opengeospatial/ogcapi-discrete-global-grid-systems/tree/master/openapi), and can also be visualized and experimented with an example implementation [with SwaggerUI here](https://petstore.swagger.io/?url=https://raw.githubusercontent.com/opengeospatial/ogcapi-discrete-global-grid-systems/master/openapi/ogcapi-dggs-1.bundled.json).

[OGC API standards](https://ogcapi.ogc.org/) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](https://openapis.org) can be used to describe and document the reusable API building blocks (resource paths, query parameters, responses supporting different representations such as JSON and HTML, schemas for both request payload and responses).

The OGC API family of standards is organized by resource type. **OGC API - DGGS** specifies an API for accessing data organised according to Discrete Global Grid Reference Systems (DGGRS).
A DGGRS is a spatial reference system combining a discrete global grid hierarchy (DGGH, a hierarchical tessellation of the globe into zones at successive refinement levels) with a zone identifier reference system (ZIRS) to uniquely address these zones.
Additionally, to enable DGGS-optimized data encodings, a DGGRS defines a deterministic order for sub-zones whose geometry is at least partially contained within a parent zone of a lower refinement level.
A Discrete Global Grid System (DGGS) is an integrated system implementing one or more DGGRS together with functionality for quantization, zonal query, and interoperability.
DGGS are characterized by the properties of the zone structure of their DGGHs, geo-encoding, quantization strategy and associated mathematical functions.

## Overview

**OGC API - DGGS** provides access to data organised according to one or more Discrete Global Grid Reference System (DGGRS).

The following transportable end-point resources can be attached either to an OGC API dataset (as defined by [OGC API - Common - Part 1: Core](http://docs.ogc.org/DRAFTS/19-072.html)) or to an OGC API collection (as defined by [OGC API - Common - Part 2: Geospatial data](http://docs.ogc.org/DRAFTS/20-024.html)).

```
GET .../dggs
```

[List](https://docs.ogc.org/DRAFTS/21-038.html#_listing_available_dggrs_dggs) of Discrete Global Grid Reference Systems (DGGRS)

```
GET .../dggs/{dggrsId}
```

[Description](https://docs.ogc.org/DRAFTS/21-038.html#_discrete_global_grid_reference_system_information_dggsdggrsid) of the DGGRS, providing links to the [definition of the DGGRS it implements](https://github.com/opengeospatial/ogcapi-discrete-global-grid-systems/blob/master/core/schemas/dggrs-definition/dggrs-definition-proposed.json), which consists of a specific hierarchy of Discrete Global Grids, a Zone Indexing Reference System (ZIRS) and a deterministic ordering of sub-zones.
The description also includes links to the data retrieval mechanism and zone query end-points.
The DGGRS definition describes the parameters and structure of its DGGH and ZIRS as specified by [OGC Abstract Specification Topic 21 v2.0 - Part 1 (ISO/19170-1)](https://docs.ogc.org/as/20-040r3/20-040r3.html),
as well as a deterministic sub-zone order.

```
GET .../dggs/{dggrsId}/zones
```

[Query the list of zones](https://docs.ogc.org/DRAFTS/21-038.html#_requirement_class_zone_query) where data is available and/or match certain query criteria (e.g., [a bounding box](https://docs.ogc.org/DRAFTS/21-038.html#_parameter_bbox), a [CQL2](http://docs.ogc.org/DRAFTS/21-065.html) [`filter`](https://docs.ogc.org/DRAFTS/21-038.html#_requirement_class_filtering_zone_queries_with_cql2)), for a selected DGGRS, optionally specifying a [particular DGGS hierarchy level](https://docs.ogc.org/DRAFTS/21-038.html#_parameter_zone_level) (`zone-level`).
This end-point supports a [compact representation](https://docs.ogc.org/DRAFTS/21-038.html#_parameter_compact_zones) based on zone hierarchy (`compact-zones=true`, the default), as well a [`parent-zone` parameter](https://docs.ogc.org/DRAFTS/21-038.html#_parameter_parent_zone_for_hierarchical_exploration) allowing to progressively explore the hierarchy to avoid potentially large responses.
In addition to a simple [JSON response](https://docs.ogc.org/DRAFTS/21-038.html#rc_zone-json), implementations can also support others such as a [64-bit integer binary response](https://docs.ogc.org/DRAFTS/21-038.html#rc_zone-binary64bit).

```
GET .../dggs/{dggrsId}/zones/{zoneId}
```

[Information](https://docs.ogc.org/DRAFTS/21-038.html#_retrieving_zone_information_dggsdggrsidzoneszoneid) about a specific zone for a specific DGGRS, such as its geometry and area.

```
GET .../dggs/{dggrsId}/zones/{zoneId}/data
```

[Retrieve the data](https://docs.ogc.org/DRAFTS/21-038.html#_requirement_class_data_retrieval) for a specific zone of a particular DGGRS, at a resolution corresponding to the DGGS hierarchy level of that zone, in one or more available data packet encodings.
Typically, the data packet would include values for descendent zones at a number of levels deeper than the [requested zone's level](https://docs.ogc.org/DRAFTS/21-038.html#_requirement_class_data_custom_depths) (`zone-depth` parameter), as opposed to a single value for the requested zone.
See the [DGGS-JSON](https://docs.ogc.org/DRAFTS/21-038.html#rc_data-json) schema in particular as well as the associated [UB-JSON encoding requirement class](https://docs.ogc.org/DRAFTS/21-038.html#rc_data-ubjson).

## Server and client implementations

[Overview of tools implementing OGC API - DGGS](implementations/README.adoc)

## Communication

Join the [SWG mailing list (Private)](https://lists.ogc.org/mailman/listinfo/dggs.swg) or the [DWG mailing list (Public)](https://lists.ogc.org/mailman/listinfo/dggs.dwg).

Most of all work on the specification takes place in [GitHub issues](https://github.com/opengeospatial/ogcapi-discrete-global-grid-systems/issues),
so browse there to get a good idea of what is happening, as well as past decisions.


## Additional information

The draft **OGC API - DGGS** standard references the [OGC Abstract Specification Topic 21 v2.0 - Part 1 (ISO/19170-1)](https://docs.ogc.org/as/20-040r3/20-040r3.html).

## Building

Document Initialisation and Compilation instructions are [here](https://github.com/opengeospatial/ogcapi-discrete-global-grid-systems/blob/master/building.adoc).

## [Contributing](CONTRIBUTING.md)

The contributor understands that any contributions, if accepted by the OGC Membership and ISO/TC 211, shall be incorporated into OGC and ISO/TC 211 Standards documents and that all copyright and intellectual property shall be vested to the OGC.

The Discrete Global Grid Systems (DGGS) Standards Working Group (SWG) is the group at OGC responsible for the stewardship of the standard, but is working to do as much work in public as possible.

* [DGGS Standards Working Group Charter](https://www.ogc.org/projects/groups/dggsswg)
* [Open issues](https://github.com/opengeospatial/ogcapi-discrete-global-grid-systems/issues)
* [Copy of License Language](https://raw.githubusercontent.com/opengeospatial/ogcapi-discrete-global-grid-systems/master/LICENSE)

Pull Requests from contributors are welcomed. However, please note that by sending a Pull Request or Commit to this GitHub repository, you are agreeing to the terms in the Observer Agreement https://portal.ogc.org/files/?artifact_id=92169
