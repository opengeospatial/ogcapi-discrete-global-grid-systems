# OGC API - Discrete Global Grid Systems

This GitHub repository contains the draft [OGC API - Discrete Global Grid Systems](https://ogcapi.ogc.org/dggs/) standard, as well as supporting information.

The latest draft candidate standard can be accessed [here in HTML](https://opengeospatial.github.io/ogcna-auto-review/21-038.html) and [here in PDF](https://opengeospatial.github.io/ogcna-auto-review/21-038.pdf).

The OpenAPI building blocks defined by the specification as well as complete bundled example API definition are [available here](https://github.com/opengeospatial/ogcapi-discrete-global-grid-systems/tree/master/openapi), and can also be visualized and experimented with an example implementation [with SwaggerUI here](https://petstore.swagger.io/?url=https://raw.githubusercontent.com/opengeospatial/ogcapi-discrete-global-grid-systems/master/openapi/ogcapi-dggs-1.bundled.json).

[OGC API standards](https://ogcapi.ogc.org/) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](https://openapis.org) can be used to describe and document the reusable API building blocks (resource paths, query parameters, responses supporting different representations such as JSON and HTML, schemas for both request payload and responses).

The OGC API family of standards is organized by resource type. **OGC API - DGGS** specifies an API for accessing data organised according to a Discrete Global Grid System (DGGS). A DGGS is a spatial reference system that uses a hierarchical tessellation of zones to partition and address the globe. DGGS are characterized by the properties of their zone structure, geo-encoding, quantization strategy and associated mathematical functions.

## Overview

**OGC API - DGGS** provides access to data organised according to one or more DGGS.

```
GET .../dggs
```

List of DGGS Resource Instances

```
GET .../dggs/{dggsRSID}
```

Description of the DGGS instance, providing links to the definition of the DGGS and indexing scheme it implements, as well as links to the data retrieval mechanism and zone query end-points. The DGGS definition describes the parameters and structure of the selected DGGS Reference System as specified by [OGC Abstract Specification Topic 21 v2.0 - Part 1 (ISO/19170-1)](https://docs.ogc.org/as/20-040r3/20-040r3.html).

```
GET .../dggs/{dggsRSID}/zones
```

Query the list of zones where data is available and/or match certain query criteria (e.g., a bounding box, a [CQL2](http://docs.ogc.org/DRAFTS/21-065.html) filter), for a selected DGGS_RS, optionally specifying a particular DGGS hierarchy level. This end-point supports a compact representation based on zone hierarchy, as well as paging in order to handle potentially large responses.

```
GET /dggs/{dggsRSID}/zones/{ZonalID}
```

Information about a specific zone for a specific DGGS instance, such as its geometry and area.

```
GET /dggs/{dggsRSID}/zones/{ZonalID}/data
```

Retrieve the data for a specific zone of a particular DGGS instance, at a resolution corresponding to the DGGS hierarchy level of that zone, in one or more available data packet encodings.
Typically, the data packet would include values for descendent zones at a number of levels deeper than the requested zone's level, as opposed to a single value for the requested zone zone.

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
