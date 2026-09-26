# Enterprise IT Asset Catalog Generation Prompt

Copy the prompt below into another AI when the entire repository must be generated or rebuilt in one execution.

---

## Role

Act as a Global Enterprise IT Asset Architect, Principal Data Engineer and specialist in ITAM, CMDB, governance, compliance and multinational inventory management.

Generate a complete synthetic enterprise asset catalog in one uninterrupted execution. Do not ask intermediate questions. Create the files, organize the folders and validate the result before responding.

## Objective

Create JSON records for corporate assets, product references, cloud services, software, SaaS, contracts, governance records, maintenance, warranty, disposal and compliance.

Cover these operating areas:

- End-user computing, remote work, mobility and controlled BYOD
- Offices, branches, field operations and shared resources
- Corporate networks, wireless, WAN, SD-WAN, security and VoIP
- Data centers, colocation, racks, power, servers and storage
- Virtualization, containers, Kubernetes and private cloud
- AWS, Azure, OCI, IBM Cloud and Huawei Cloud
- SaaS, licenses, databases, middleware, AI and analytics
- Governance, contracts, warranties, maintenance, disposal and compliance

## Required Folder Structure

Every JSON must be placed below `assets/`:

```text
assets/<asset_class>/<asset_category>/<filename>.json
```

Allowed `asset_class` values:

- `hardware`
- `software`
- `cloud`
- `governance`

Use lowercase kebab-case folder names derived from `asset_category`.

Examples:

```text
assets/hardware/server/
assets/hardware/notebook/
assets/hardware/smartphone/
assets/cloud/cloud-compute/
assets/cloud/cloud-database/
assets/software/database/
assets/software/voip-service/
assets/governance/governance/
```

## Required Filename Convention

Every file must follow exactly:

```text
NNNN-category-manufacturer-model-type.json
```

Rules:

- `NNNN` is a four-digit numeric identifier beginning at `0001`.
- `category` comes from `asset_category`, converted to lowercase kebab-case.
- `manufacturer` comes from `manufacturer`, converted to lowercase kebab-case.
- `model` comes from `model`, converted to lowercase kebab-case.
- `type` is the lowercase value of `asset_class`: `hardware`, `software`, `cloud` or `governance`.
- Do not use spaces, accents, underscores or special characters in filenames.
- Do not use `product-catalog` in filenames or content.
- Derive the filename from the actual JSON fields; never create a name that disagrees with the record.

Examples:

```text
0001-workstation-lenovo-thinkpad-p1-gen-6-hardware.json
0214-notebook-hp-zbook-power-16-g11-hardware.json
0305-cloud-compute-azure-virtual-machines-cloud.json
0443-server-ibm-power-s1022-hardware.json
```

## Mandatory JSON Schema

Every record must include at least:

```json
{
  "asset_id": "ASSET-REF-0001",
  "asset_tag": "REF-AMER-0001",
  "inventory_id": "REFERENCE-2026-0001",
  "serial_number": "MOCK-VENDOR-0001",
  "manufacturer": "Vendor",
  "model": "Product Model",
  "asset_class": "HARDWARE",
  "asset_category": "SERVER",
  "record_type": "ASSET",
  "lifecycle_status": "DEPLOYED",
  "operational_status": "ACTIVE",
  "active": true,
  "global_allocation": {
    "region": "AMER",
    "country": "United States",
    "corporate_entity": "Example Global Technology Inc.",
    "business_unit": "Global Technology",
    "department": "Infrastructure",
    "cost_center": "CC-INFRA-US-0001",
    "assigned_user": "USER-MOCK-0001",
    "shared_resource": null,
    "site_code": "AMER-US-01",
    "location": "Example Enterprise Site",
    "data_center": "DC-AMER-01"
  },
  "data_classification": "INTERNAL",
  "compliance_matrix": {
    "ISO27001": {
      "applicable": true,
      "status": "COMPLIANT",
      "evidence_reference": "EVIDENCE-ISO27001-0001"
    },
    "SOC2_Type2": {
      "applicable": true,
      "status": "REVIEW_REQUIRED",
      "evidence_reference": "EVIDENCE-SOC2-0001"
    },
    "PCI-DSS_v4": {
      "applicable": false,
      "status": "NOT_APPLICABLE",
      "evidence_reference": null
    },
    "vendor_security_review": {
      "applicable": true,
      "status": "PENDING",
      "review_reference": "VENDOR-REVIEW-0001"
    }
  },
  "technical_identity": {
    "hostname": "MOCK-ASSET-0001",
    "ip_address": "198.51.100.10",
    "mac_address": "02:00:5E:00:00:01",
    "network_segment": "CORPORATE-ASSETS",
    "vlan_id": 210
  },
  "procurement": {
    "purchase_order": "PO-MOCK-2026-0001",
    "vendor": "Mock Vendor",
    "acquisition_date": "2026-01-15",
    "deployment_date": "2026-02-01",
    "purchase_price": 1000,
    "currency": "USD",
    "lease_or_owned": "OWNED"
  },
  "warranty_and_support": {
    "support_contract": "SUPPORT-MOCK-0001",
    "support_provider": "Mock Vendor",
    "support_level": "PREMIUM",
    "support_expiration_date": "2029-02-01"
  },
  "maintenance": {
    "maintenance_status": "SCHEDULED",
    "maintenance_frequency": "QUARTERLY",
    "last_maintenance_date": "2026-08-01",
    "next_maintenance_date": "2026-11-01",
    "open_incidents": 0,
    "maintenance_history": []
  },
  "service_management": {
    "business_service": "Technology Service",
    "environment": "PRODUCTION",
    "service_owner": "OWNER-MOCK-0001",
    "support_queue": "QUEUE-INFRASTRUCTURE",
    "contract_reference": "CONTRACT-MOCK-0001"
  },
  "tags": ["mock-data"],
  "notes": "Synthetic enterprise record."
}
```

## Lifecycle and Classification

Use these lifecycle states:

- `PROCURED`
- `DEPLOYED`
- `IN_MAINTENANCE`
- `END_OF_LIFE`
- `DISPOSED`

For a product-family reference that is not deployed, use `record_type` `PRODUCT_REFERENCE`, `lifecycle_status` `PROCURED`, `operational_status` `NOT_DEPLOYED` and `lease_or_owned` `REFERENCE_ONLY`.

Use only these data classifications:

- `PUBLIC`
- `INTERNAL`
- `CONFIDENTIAL`
- `RESTRICTED`

## Required Manufacturers and Platforms

Include representative families from these groups:

- Lenovo: ThinkPad, ThinkCentre, ThinkStation, ThinkSystem, ThinkAgile, ThinkVision, XClarity and TruScale.
- Dell: PowerEdge, PowerStore, PowerScale, PowerSwitch, Precision, Latitude, OptiPlex, Wyse, UltraSharp and APEX.
- HPE: ProLiant, Superdome Flex, NonStop, Alletra, StoreOnce, Aruba, Synergy, Apollo and GreenLake.
- HP: EliteBook, ProBook, ProDesk, ZBook, Z workstations, monitors, printers, scanners, keyboards, mice, docks, Poly, Wolf Security and Anyware.
- Cisco: Catalyst, Nexus, UCS, Meraki, ISR, ASR, Secure Firewall, Webex Calling and CUBE.
- Microsoft and Azure: Surface, Windows, Windows Server, SQL Server, Entra, Intune, Defender, Teams, Teams Phone, Azure VMs, AKS, SQL, Storage, Functions and Key Vault.
- AWS: EC2, ECS, EKS, Fargate, Lambda, RDS, DynamoDB, Redshift, S3, VPC, Direct Connect, CloudFront, IAM, KMS and CloudWatch.
- OCI: Compute, OKE, Functions, Autonomous Database, MySQL HeatWave, Object Storage, VCN, FastConnect, Load Balancer, Cloud Guard and Vault.
- Huawei: MateBook, MatePad, smartphones, FusionServer, Atlas, OceanStor, CloudEngine, AirEngine, USG, Huawei Cloud ECS, OBS, CCE and RDS.
- Linux: Ubuntu, RHEL, Fedora, Debian, SUSE, Rocky, AlmaLinux, Linux Kernel LTS, Kubernetes, OpenShift, Docker and RHEL for Edge.
- JetBrains: IntelliJ IDEA, PyCharm, WebStorm, PhpStorm, GoLand, Rider, CLion, RustRover, DataSpell, TeamCity and YouTrack.
- IBM: Power, z16, LinuxONE, z/OS, z/VM, CICS, IMS, FlashSystem, DS8000, TS4300, Spectrum Virtualize, IBM Cloud, Db2, MQ, WebSphere, API Connect, QRadar, Guardium, watsonx, Maximo, FileNet and IBM Quantum.
- Nokia and Samsung: smartphones, rugged smartphones, tablets, 5G gateways, private wireless, Galaxy, Knox, Galaxy Book, Galaxy Tab and mobile storage.
- VoIP: Avaya, Mitel, 3CX, Asterisk, FreePBX, Grandstream, Yealink, Poly, AudioCodes, Ribbon, Zoom Phone, Teams Phone, Webex Calling, SBC, PBX and IP phones.

## Anonymization Rules

Use synthetic data only:

- Users must use `USER-MOCK-*` identifiers.
- Serial numbers must use `MOCK-*` identifiers.
- MAC addresses must use the locally administered `02:*` range.
- IP addresses must use documentation ranges `192.0.2.0/24`, `198.51.100.0/24` or `203.0.113.0/24`.
- Domains must use `example.test`.
- Never include passwords, tokens, private keys, real certificates or personal data.

## One-Shot Execution

1. Inspect the destination directory.
2. Generate all JSON files in batch.
3. Create `assets/<asset_class>/<asset_category>/` automatically.
4. Derive every filename from the actual JSON fields.
5. Remove or replace duplicates by `manufacturer + model`.
6. Generate or update `README.md`; keep the existing `LICENSE` (PolyForm Strict License 1.0.0) unchanged.
7. Recursively validate every JSON file.
8. Do not leave generation scripts in the final repository.

## Completion Gates

The task is complete only when:

- Every file is valid JSON.
- Every record contains the mandatory fields.
- Every name matches `NNNN-category-manufacturer-model-type.json`.
- Every prefix has four digits.
- The filename suffix matches `asset_class`.
- The path matches `asset_class` and `asset_category`.
- No asset IDs are duplicated.
- No unexplained `manufacturer + model` duplicates exist.
- No file or field is named `product-catalog`.
- No temporary generation scripts remain.
- The README describes the actual repository contents.

At the end, report the total file count, counts by `asset_class`, included manufacturers, VoIP record count and all validations performed.
