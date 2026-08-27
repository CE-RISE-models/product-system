# CE-RISE Data Model Template

[![DOI](https://zenodo.org/badge/DOI/TOBEOBTAINED.svg)](https://doi.org/TOBEOBTAINED) [![Schemas](https://img.shields.io/badge/Schema%20Files-LinkML%2C%20JSON%2C%20SHACL%2C%20OWL-32CD32)](https://ce-rise-models.codeberg.page/<repo-name>/)

This repository provides the **official template** for creating CE-RISE data models.  
It defines the standard structure, tooling, and workflow used across all model projects.


---

## Data Model Structure
Put here description of data model structure.

### Key Design Principles


### Core Hierarchy

```
JustAnExample (root)
├── 1. GeneralProductInformation
│   ├── LotBatchNumber
│   ├── GTIN14
│   ├── SerialNumber
│   ├── ProductImages
│   ├── ProductType
│   └── UniqueProductIdentifier

```

### Workflow Sequence

#### **Step 1: Just another example** 
Basic product identification with multiple identifier types:
- **LotBatchNumber**: Lot/batch tracking information
- **GTIN14**: Global Trade Item Number (14-digit format with GS1 integration)
- **SerialNumber**: Individual product serial numbers
- **ProductImages**: Product images for branding/visual identification (comma-separated URLs)
- **ProductType**: Product classification (3-digit GTIN prefix or alphanumeric code)
- **UniqueProductIdentifier**: Enables web link to product passport

### Data Properties

Each class has a corresponding value property (e.g., `name_value`, `company_id_value`) that holds the actual data. All value properties are string type except where specified otherwise.

#### SQL Identifiers

Every data point in the model includes a `sql_identifier` annotation that serves as a unique, machine-friendly database identifier. These identifiers follow a structured namespace pattern to ensure uniqueness across the entire data model:

**Pattern**: `MODEL_[category]_[specific_name]`

**Features:**
- **Product Profile Prefix**: All identifiers start, for instance, with `pro_` to clearly identify them as belonging to the Product Profile data model
- **Hierarchical Namespacing**: Uses category prefixes (`gen_info_`, `mfr_info_`, `imp_info_`, `spec_info_`) to provide context and prevent naming conflicts
- **Database-Friendly**: Uses underscores and avoids special characters for SQL compatibility
- **Unique Across Model**: No duplicate identifiers, even when similar concepts appear in different parts of the hierarchy
- **Reasonable Length**: Abbreviated but meaningful names that balance clarity with practical database usage

**Examples:**
- `pro_gen_info_gtin14` - GTIN-14 identifier in General Product Information
- `pro_mfr_info_facility` - Manufacturing facility in Manufacturer Information  
- `pro_imp_info_eori` - EORI number in Import/Export Information
- `pro_spec_info_materials` - Material composition in Product Specifications

This identifier system enables seamless integration with databases and ensures clear data model composition when combining with other CE-RISE data models.

---

## Development Roadmap

| Step | Component | Criticalities Identified | Solutions Implemented | Status | Missing/TODO |
|------|-----------|-------------------------|----------------------|--------|--------------|
| **1** | **ExampleExampleExample** | • Unique product identifier lacks precision and standards<br>• No reference integration with discoverability/registries<br>• Missing serial number and lot number storage<br>• No connection to standard product nomenclature<br>• No product description and branding<br>• No classification for grouping products | • Added GS1 prefix and ontology integration<br>• Implemented GTIN-14 + serial number approach<br>• Added Schema.org prefix<br>• Created GTIN-14, Serial number, Lot/batch number subclasses<br>• Added ProductImages (comma-separated image URLs with format validation)<br>• Added ProductType (3-digit GTIN prefix or alphanumeric classification)<br>• Referenced UNTP framework for discoverability | **COMPLETED** | • UNTP Identity Resolver integration 

### Integration Opportunities



---

## Publishing

Release artifacts for each version (`schema.json`, `shacl.ttl`, `model.owl`)  
are served directly from this URL:
```
https://ce-rise-models.codeberg.page/<repo-name>/
```


---

## Accessing Previous Releases

If you want to view the files published for version `v1.2.0`, open:

```
https://codeberg.org/CE-RISE-models/<repo-name>/src/tag/pages-v1.2.0/generated/
```

Files available in that directory typically include:

- schema.yaml
- schema.json
- shacl.ttl
- model.ttl
- index.html


---
<a href="https://europa.eu" target="_blank" rel="noopener noreferrer">
  <img src="https://ce-rise.eu/wp-content/uploads/2023/01/EN-Funded-by-the-EU-PANTONE-e1663585234561-1-1.png" alt="EU emblem" width="200"/>
</a>

Funded by the European Union under Grant Agreement No. 101092281 — CE-RISE.  
Views and opinions expressed are those of the author(s) only and do not necessarily reflect those of the European Union or the granting authority (HADEA).  
Neither the European Union nor the granting authority can be held responsible for them.

© 2026 CE-RISE consortium.  
Licensed under [Creative Commons Attribution–NonCommercial 4.0 International (CC BY-NC 4.0)](https://creativecommons.org/licenses/by-nc/4.0/).  
Attribution: CE-RISE project (Grant Agreement No. 101092281) and the individual authors/partners as indicated.

<a href="https://www.nilu.com" target="_blank" rel="noopener noreferrer">
  <img src="https://nilu.no/wp-content/uploads/2023/12/nilu-logo-seagreen-rgb-300px.png" alt="NILU logo" width="40"/>
</a>

Developed by NILU (Riccardo Boero — ribo@nilu.no) within the CE-RISE project.  



