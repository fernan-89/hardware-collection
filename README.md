# Enterprise Hardware Collection

Synthetic enterprise IT asset inventory for testing asset-management workflows, data pipelines, compliance controls, lifecycle reporting and catalog integrations.

## Repository Contents

The repository contains 503 JSON examples organized by asset type and category:

```text
assets/
  hardware/
    server/
    workstation/
    notebook/
    storage/
    network/
    mobile/
    ...
  cloud/
    cloud-compute/
    cloud-database/
    cloud-storage/
    cloud-network/
    ...
  software/
    operating-system/
    database/
    security-platform/
    voip-service/
    ...
  governance/
    governance/
```

Each filename follows this convention:

```text
NNNN-categoria-fabricante-modelo-tipo.json
```

Examples:

- `assets/hardware/workstation/0001-workstation-lenovo-thinkpad-p1-gen-6-hardware.json`
- `assets/hardware/notebook/0214-notebook-hp-zbook-power-16-g11-hardware.json`
- `assets/cloud/cloud-compute/0305-cloud-compute-azure-virtual-machines-cloud.json`
- `assets/software/database/0479-database-ibm-db2-11-5-software.json`

## Included Examples

The mock catalog covers enterprise technology used in global organizations:

- Endpoints: notebooks, desktops, workstations, tablets, smartphones, monitors, keyboards, mice, docks and conference devices.
- Data center: bare-metal servers, GPU servers, mainframes, LinuxONE, racks, UPS, storage arrays, tape libraries and storage adapters.
- Networking: switches, routers, firewalls, access points, wireless controllers, SD-WAN, Fibre Channel and session border controllers.
- Cloud: AWS, Azure, OCI, IBM Cloud and Huawei Cloud compute, databases, containers, storage, networking, security and observability.
- Software: operating systems, databases, virtualization, development tools, identity, security, analytics, middleware and enterprise platforms.
- Mobile: Nokia, Samsung, Huawei and Microsoft endpoint examples with mobile-management and security services.
- VoIP: Teams Phone, Webex Calling, Avaya, Mitel, 3CX, Asterisk, FreePBX, Grandstream, Yealink, Poly, AudioCodes, Ribbon and Zoom Phone.
- Manufacturers and platforms: Lenovo, Dell, HPE, HP, Cisco, Microsoft, Azure, AWS, OCI, Huawei, Linux, JetBrains, IBM, Nokia and Samsung.
- Governance: corporate entities, cost centers, cloud accounts, vendor contracts, entitlements, warranty, maintenance and disposal records.

## Common Data Model

Each record is a synthetic asset or product reference with a common enterprise structure. Depending on the asset, it may include:

- Identity: `asset_id`, `asset_tag`, `inventory_id`, `serial_number`, `manufacturer`, `model` and `record_type`.
- Lifecycle: `lifecycle_status`, `operational_status` and `active`.
- Allocation: `region`, `corporate_entity`, `department`, `cost_center`, `assigned_user`, `shared_resource`, site and data-center information.
- Compliance: `data_classification` and `compliance_matrix` entries for ISO 27001, SOC 2 Type II, PCI-DSS v4 and vendor security review.
- Operations: technical identity, network placement, environment, business service, ownership and support queue.
- Commercial controls: procurement, vendor, contract, warranty, support and reference-only status.
- Maintenance: maintenance state, frequency, dates, incidents and maintenance history.

## Data Safety

All records are mock data. Serial numbers, asset tags, hostnames, MAC addresses, IP addresses, contract references, users, vendors, prices and identifiers are fictional. Documentation-only IP ranges are used where network values are present. No production credentials, secrets or personal data are included.

Product-family references represent synthetic examples for inventory modeling. They are not purchase entitlements, warranties, licenses or confirmation of current vendor availability.

## Usage

The files can be consumed directly by scripts, test fixtures, ETL jobs or schema-validation pipelines. A typical workflow is:

1. Enumerate JSON files recursively under `assets/`.
2. Parse each document as UTF-8 JSON.
3. Route records using `asset_class` and `asset_category`.
4. Validate `compliance_matrix`, lifecycle and allocation fields.
5. Use `record_type` to distinguish deployed assets from product references and governance records.

## License

Licensed under the [PolyForm Strict License 1.0.0](LICENSE): you may read and use this software for noncommercial purposes only. Modifying it, creating derivative works, redistributing it and any commercial use are not permitted without a separate written license. This software is not open source.

## One-Shot Generation Prompt

The reusable English generation instructions are available in [CATALOG_GENERATION_PROMPT.md](CATALOG_GENERATION_PROMPT.md). They describe the schema, naming convention, folder layout, manufacturers, anonymization rules and validation gates for rebuilding the catalog in one execution.
