# OGC API - Discrete Global Grid Systems

This GitHub repository contains the draft [OGC API - Discrete Global Grid Systems](https://ogcapi.ogc.org/dggs/) standard, as well as supporting information.

[OGC API standards](https://ogcapi.ogc.org/) define modular API building blocks to spatially enable Web APIs
in a consistent way. [OpenAPI](https://openapis.org) is used to define the reusable
API building blocks with responses in JSON and HTML.

The OGC API family of standards is organized by resource type. **OGC API - DGGS** specifies an API for accessing data organised according to a Discrete Global Grid System (DGGS). A DGGS is a spatial reference system that uses a hierarchical tessellation of cells to partition and address the globe. DGGS are characterized by the properties of their cell structure, geo-encoding, quantization strategy and associated mathematical functions.

## Overview

**OGC API - DGGS** provides access to data organised according to one or more DGGS.

```
GET /dggs
```

List of DGGS Resource Instances

```
GET /dggs/{dggsRSID}
```

Structural definition and links to OGC API Resources implemented on this server for the selected DGGS Reference System. This describes the key parameters and structure of the selected DGGS Reference System as specified by [OGC Abstract Specification Topic 21 v2.0 - Part 1 (ISO/19170-1)](https://docs.ogc.org/as/20-040r3/20-040r3.html).

```
GET /dggs/{dggsRSID}/zones
```

Access the list of zones defined by the selected DGGS_RS. This can list either all the zones of the DGGS_RS (not advisable without the use of Limits and Offsets), or a particular subset based on a range of refinement Levels, a WGS84 bounding box or a <still to be defined> polygon search area.

```
GET /dggs/{dggsRSID}/zone/{ZonalID}
```

Access the definition of a particular zone

## Using the draft standard

The draft standard can be accessed [here](https://opengeospatial.github.io/ogcna-auto-review/21-038.html).

The example **OpenAPI** definition document for the draft OGC API - DGGS standard is on SwaggerHub [here](https://app.swaggerhub.com/apis/geofizzydrink/ogc_api_dggs/0.0.6).

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
