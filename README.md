
> [!IMPORTANT]
> On June 26 2024, Linux Foundation announced the merger of its financial services umbrella, the Fintech Open Source Foundation ([FINOS](https://finos.org)), with OS-Climate, an open source community dedicated to building data technologies, modeling, and analytic tools that will drive global capital flows into climate change mitigation and resilience; OS-Climate projects are in the process of transitioning to the [FINOS governance framework](https://community.finos.org/docs/governance); read more on [finos.org/press/finos-join-forces-os-open-source-climate-sustainability-esg](https://finos.org/press/finos-join-forces-os-open-source-climate-sustainability-esg)

# bgs-dm-samples-dat - Ecosystem Platform Sample Data

This repo contains Ecosystem Platform sample data products, including:
- RMI: Uility Transition Hub data created and operated by
[RMI](https://rmi.org/)
- PUDL: Public Utility Data Library created and operated by
[Catalyst Cooperative](https://catalyst.coop/)

These sample data products are used to demonstrate Ecosystem
Platform capabilities

Soon, there will be many more sample data products available!

Full documentation is available in in the
[bgs-dm-mesh-doc](https://github.com/brodagroupsoftware/bgs-dm-mesh-doc)
repo.

## About Data Products

A data product is stored in its own directory under
the "dataproducts" directory.  There are two sample
data products as mentioned earlier, and they
are stored under "rmi" and "pudl" directory.

Data products represents groups of data. Data products have
the following characteristics:
- Is identified by a unique UUID which is assigned
when the data product is registered (see our CLI for information
about registering a data product)
- Contain have one or more artifacts which represent specific data
- Resides in a namespace, and a namespace can have
one or more data products.  Each data product in a namespace has
a unique name (any string)
- Has tags which may make it easier to find when users
search for data products in the Marketplace
- Is published at which point it is
made available in the Marketplace.  Each publisher must be registered
before they can register a data product

A data product is defined by its "product.yaml".
~~~~
product:
    namespace: brodagroupsoftware.com
    name: rmi.dataproduct
    description: US Utility data provided by RMI
    tags: ["utilities", "emissions"]
    publisher: publisher.user@brodagroupsoftware.com
    endpoints:
        discovery: http://localhost:9999/discovery
        observability: http://localhost:9999/observability
        administration: http://localhost:9999/administration
~~~~

## About Artifacts

Data products has one or more artifacts associated with them.
Artifacts for a data product are in the product's "artifacts"
directory.

Artifacts represent data in a data product.  The important thing to know
about artifacts is that they DO NOT contain actual data, but rather
only reference data that exists elsewhere, identified by links (URLs).

Artifacts can represent data in any form as long as it
can be accessed as a URL (either public or private URL, as
long as the entity has rights to access the data).  Artifacts
can represent databases or tables in a database,
CSV files, Parquet files, images, audio, document, or text - there
is no limitation as to what a publisher may deem to be data.

Artifacts have the following characteristics:
- Is identified by a unique UUID which is assigned
when the data product is registered (see our CLI for information
about registering a data product)
- Has a unique name
- Has a license (by default it is: CDLA 2.0, Permissive, Version 2.0)
- Has a secrity policy that governs access to it
- Has links (URL) to actual data, metadata, and sample data

An artifact is in the "artifacts" directory and is defined
in an artifact YAML file:
~~~~
artifact:
  name: Assets Earnings Investments
  description: |
    Detailed breakdown of utility assets in electric rate base, earnings
    on these assets, and annual investments (capital additions) by technology.
  tags: ["utilities", "emissions"]
  license: CDLA 2.0, Permissive, Version 2.0
  securitypolicy: public
  links:
    - relationship: artifact
      mimetype: text/csv
      url: https://utilitytransitionhub.rmi.org/static/data_download/assets_earnings_investments.csv
    - relationship: sample
      mimetype: text/csv
      url: placeholder-sample.csv
    - relationship: metadata
      mimetype: application/json
      url: placeholder-metadata.json
~~~~

## License

Use of this source code is governed by an MIT-style
license that can be found in the LICENSE file or at
https://opensource.org/licenses/MIT.
