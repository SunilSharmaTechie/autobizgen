# AutoBizGen: AI-Powered Business Profile Generator with API Enrichment

## Description

AutoBizGen is a production-grade solution that automates the end-to-end workflow of transforming raw business listings into enriched, insight-driven content.

It ingests structured .xlsx files containing business names, addresses, and contact details, integrates with trusted APIs such as Google Maps to retrieve metadata (e.g., ratings, websites), and generates high-quality, AI-written business descriptions tailored for real-world applications.

Designed with modularity, reliability, and compliance in mind, AutoBizGen features:
• Scalable batch processing via CLI
• API usage compliance and data privacy safeguards
• Integrated retry logic and failure handling
• Structured multi-format export (Markdown, Excel, CSV)

Ideal for marketing automation teams, SaaS platforms, CRM enrichment pipelines, and consulting workflows, this system enables organizations to accelerate content operations, improve data quality, and drive meaningful automation at scale.

Table of Contents
- [AutoBizGen: AI-Powered Business Profile Generator with API Enrichment](#autobizgen-ai-powered-business-profile-generator-with-api-enrichment)
  - [Description](#description)
    - [Key Features](#key-features)
  - [Problem Statement](#problem-statement)
    - [AutoBizGen Solves This By:](#autobizgen-solves-this-by)
  - [Who This Is For](#who-this-is-for)
    - [Ideal Users:](#ideal-users)
  - [Architecture Overview](#architecture-overview)
    - [System Flow Diagram](#system-flow-diagram)
    - [Detailed Component Breakdown](#detailed-component-breakdown)
      - [1. Data Ingestion \& Preprocessing](#1-data-ingestion--preprocessing)
      - [2. API Enrichment Layer](#2-api-enrichment-layer)
      - [3. AI Content Generation Engine](#3-ai-content-generation-engine)
      - [4. Output \& Export Engine](#4-output--export-engine)
      - [5. Execution Layer (CLI Interface)](#5-execution-layer-cli-interface)
    - [Cross-Cutting Concerns](#cross-cutting-concerns)
  - [Tech Stack \& Dependencies](#tech-stack--dependencies)
    - [Core Programming Language](#core-programming-language)
    - [Primary Python Libraries](#primary-python-libraries)
      - [Data Handling](#data-handling)
      - [API Integration](#api-integration)
      - [AI Content Generation](#ai-content-generation)
      - [Output \& Export](#output--export)
      - [Logging \& Execution](#logging--execution)
    - [System Requirements](#system-requirements)
    - [Optional Tools for Extension](#optional-tools-for-extension)
  - [Tech Stack \& Dependencies](#tech-stack--dependencies-1)
    - [Core Programming Language](#core-programming-language-1)
    - [Primary Python Libraries](#primary-python-libraries-1)
      - [Data Handling](#data-handling-1)
      - [API Integration](#api-integration-1)
      - [AI Content Generation](#ai-content-generation-1)
      - [Output \& Export](#output--export-1)
      - [Logging \& Execution](#logging--execution-1)
    - [System Requirements](#system-requirements-1)
    - [Optional Tools for Extension](#optional-tools-for-extension-1)
  - [Input Format Examples](#input-format-examples)
    - [Required Input Format (.xlsx)](#required-input-format-xlsx)
    - [Accepted File Type \& Sheet Handling](#accepted-file-type--sheet-handling)
    - [Example Record](#example-record)
    - [Folder Structure (Recommended)](#folder-structure-recommended)
    - [Data Validation Rules](#data-validation-rules)
    - [Prompt Templates (Optional)](#prompt-templates-optional)
  - [Output Samples (Markdown + Excel)](#output-samples-markdown--excel)
    - [Output Formats](#output-formats)
    - [Sample Output Table (Excel \& CSV)](#sample-output-table-excel--csv)
    - [Sample Markdown Output (USA)](#sample-markdown-output-usa)
    - [Folder Structure (Dynamic Output)](#folder-structure-dynamic-output)
    - [How to Use Dynamic Country Filtering](#how-to-use-dynamic-country-filtering)
  - [Core Code Modules](#core-code-modules)
    - [Professional-Grade Module Structure](#professional-grade-module-structure)
    - [Enterprise Practices Implemented](#enterprise-practices-implemented)
  - [CLI \& GUI Usage Examples](#cli--gui-usage-examples)
    - [CLI Usage (Command Line Interface)](#-cli-usage-command-line-interface)
      - [Basic Command](#basic-command)
      - [Full CLI Options](#full-cli-options)
      - [Example Command with All Options](#example-command-with-all-options)
      - [Environment Variable Support (.env)](#environment-variable-support-env)
      - [Scheduler \& Automation Friendly](#scheduler--automation-friendly)
    - [🔹 GUI Usage (Streamlit Web Interface)](#-gui-usage-streamlit-web-interface)
      - [Launch Streamlit App](#launch-streamlit-app)
      - [Features of the Web GUI](#features-of-the-web-gui)
      - [Sample GUI URL (after launch)](#sample-gui-url-after-launch)
      - [Ideal For:](#ideal-for)
  - [CLI and GUI Usage Examples](#cli-and-gui-usage-examples)
    - [CLI Usage (Enterprise Automation Standard)](#cli-usage-enterprise-automation-standard)
      - [Minimal Execution](#minimal-execution)
      - [Advanced Execution with All Options](#advanced-execution-with-all-options)
      - [CLI Option Matrix](#cli-option-matrix)
      - [Environment Variable Support (.env)](#environment-variable-support-env-1)
      - [Automation Compatibility](#automation-compatibility)
    - [GUI Usage (Streamlit-Based Interface)](#gui-usage-streamlit-based-interface)
      - [Launch the Web Interface](#launch-the-web-interface)
      - [Key Capabilities](#key-capabilities)
      - [Typical Access URL](#typical-access-url)
      - [Target User Scenarios](#target-user-scenarios)
  - [Compliance and Limitations](#compliance-and-limitations)
    - [API Usage and Terms of Service](#api-usage-and-terms-of-service)
    - [AI Content Guidelines](#ai-content-guidelines)
    - [Data Privacy and Security](#data-privacy-and-security)
    - [System Limitations](#system-limitations)
    - [Legal Disclaimer](#legal-disclaimer)
  - [Enhancements and Roadmap](#enhancements-and-roadmap)
    - [Planned Enhancements](#planned-enhancements)
      - [1. Streamlit GUI Upgrade (Advanced Mode)](#1-streamlit-gui-upgrade-advanced-mode)
      - [2. API-First Deployment (FastAPI/Flask Service Layer)](#2-api-first-deployment-fastapiflask-service-layer)
      - [3. Live Dashboard \& Monitoring Tools](#3-live-dashboard--monitoring-tools)
      - [4. Advanced Prompt Engineering System](#4-advanced-prompt-engineering-system)
      - [5. Multi-Language Output Support](#5-multi-language-output-support)
      - [6. Model Routing and Cost Optimization](#6-model-routing-and-cost-optimization)
      - [7. Report Versioning and Audit Trails](#7-report-versioning-and-audit-trails)
      - [8. Third-Party Integration Modules](#8-third-party-integration-modules)
      - [9. Enhanced Data Quality Layer](#9-enhanced-data-quality-layer)
    - [Roadmap Timeline (Indicative)](#roadmap-timeline-indicative)
  - [License](#license)
    - [Permissions](#permissions)
    - [Limitations](#limitations)
    - [Conditions](#conditions)
    - [File Reference](#file-reference)
  - [Demo Output (Optional Preview)](#demo-output-optional-preview)
    - [Sample Excel Output (`.xlsx`)](#sample-excel-output-xlsx)
    - [Sample Markdown Output (`.md`)](#sample-markdown-output-md)
    - [Folder Example](#folder-example)
    - [Screenshot or GIF (Coming Soon)](#screenshot-or-gif-coming-soon)


### Key Features
- Upload business records via Excel
- Fetch additional details using APIs like Google Maps (e.g., ratings, websites)
- Generate original descriptions using GPT, Claude, or open-source LLMs
- Export results in `.xlsx`, `.csv`, and `.md` formats
- Handle API retries, invalid records, and AI prompt customization
- Built for compliance, traceability, and extension

## Problem Statement

Marketing teams, business owners, and data operators often face repetitive, manual processes when it comes to enriching business records and creating professional descriptions.

These challenges include:

- Manually searching for business details like websites, Google ratings, or review counts
- Copy-pasting and formatting data from Excel sheets
- Writing custom business descriptions repeatedly, leading to inconsistency and wasted time
- Lacking a centralized system for batch automation, data accuracy, and content quality

This fragmentation results in missed opportunities, inconsistent branding, and slow execution.

### AutoBizGen Solves This By:
- Reading structured Excel files containing core business data
- Enriching records using APIs like Google Maps Places
- Generating tailored, high-quality business content using LLMs (GPT, Claude, or LLaMA)
- Exporting results in multiple formats, ready for downstream workflows
- Enabling full automation with CLI, batch processing, and prompt customization

With AutoBizGen, teams can scale their business profiling operations with minimal manual input, reduced error rates, and professional output ready for websites, platforms, and CRMs.

## Who This Is For

AutoBizGen is designed for professionals and teams responsible for business profiling, content generation, and data enhancement. It serves as a powerful automation tool for anyone working with business records and needing fast, scalable, and AI-enhanced output.

### Ideal Users:

- **Marketing Teams**
  - Generate consistent and professional business descriptions for websites, brochures, and campaigns
  - Enrich datasets for segmentation, outreach, or SEO efforts

- **Founders & Business Owners**
  - Quickly create polished "About Us" sections for multiple locations or service lines
  - Keep digital presence up-to-date across listings and directories

- **Data Analysts & Operators**
  - Automate repetitive tasks like address validation, review tracking, and source attribution
  - Export clean and enriched datasets ready for BI tools or CRM import

- **Agencies & Freelancers**
  - Deliver high-volume business content or onboarding packages for multiple clients
  - Improve consistency and turnaround with automated enrichment and writing

- **Product & Content Teams**
  - Integrate AutoBizGen into internal platforms for on-demand content generation
  - Use CLI or scheduled runs for regular profile updates at scale

Whether you are managing hundreds of business records or building a content pipeline for a platform, AutoBizGen helps you automate intelligently, reduce manual work, and generate outputs that are both accurate and valuable.

## Architecture Overview

AutoBizGen is built with a production-grade, enterprise-ready architecture that embraces modularity, extensibility, and compliance from the ground up. It seamlessly bridges structured business data with API-driven enrichment and LLM-based content generation, all in a maintainable and testable pipeline.

### System Flow Diagram

```plaintext
┌────────────────────┐
│  Input Spreadsheet │
│  (Excel .xlsx)     │
└─────────┬──────────┘
          ↓
┌────────────────────────────┐
│ Data Validator & Normalizer│
└─────────┬──────────────────┘
          ↓
┌────────────────────────────┐
│   API Enrichment Layer     │
│ (Google Maps, Caching, etc.) │
└─────────┬──────────────────┘
          ↓
┌────────────────────────────┐
│  AI Generation Engine      │
│ (GPT-4, Claude, LLaMA)     │
└─────────┬──────────────────┘
          ↓
┌────────────────────────────┐
│ Export Engine              │
│ (.xlsx, .csv, .md Formats) │
└─────────┬──────────────────┘
          ↓
┌────────────────────────────┐
│ Audit Logging & CLI Output │
└────────────────────────────┘
```

### Detailed Component Breakdown

#### 1. Data Ingestion & Preprocessing
- Accepts `.xlsx` files as input
- Validates columns: Business Name, Address, Phone Number (and optionally Email, Website)
- Cleans invalid formats:
  - Normalizes phone number and address formats
  - Removes null or placeholder entries
  - Logs skipped rows for auditing
- Handles batch files and large datasets with chunked processing

#### 2. API Enrichment Layer
- **Primary API:** Google Maps Places API (others can be plugged in)
- Fetches structured business metadata:
  - Official website
  - Business category/type
  - Rating and review count
  - Geo-coordinates (lat/lng)
- Implements retry logic with exponential backoff
- API responses cached with SQLite (or optionally Redis/JSON flat file)
- Handles API quota limits, 403s, and malformed responses

#### 3. AI Content Generation Engine
- LLM selection is configurable: GPT-4 (OpenAI), Claude, or LLaMA (local or HuggingFace)
- Each business record is passed through a structured prompt with:
  - Name, Address, Category, Website, Reviews
- Prompts are modular and support chaining:
  - Context injection
  - Tone control (e.g., professional, friendly, technical)
  - Style configuration (length, target audience)
- Generation results are validated and optionally rewritten for grammar/tone control

#### 4. Output & Export Engine
- **Excel Output:** Multi-sheet `.xlsx` with enriched + generated content
- **CSV Output:** For bulk imports or downstream pipelines
- **Markdown Output:** For human-readable summaries or publishing
- Supports optional template headers, footers, and disclaimers
- Each output row contains:
  - Input Fields
  - API Enrichment Fields
  - AI-Generated "About" Section

#### 5. Execution Layer (CLI Interface)
- Executable via command line for local or automated runs
- CLI options:
  - Input path
  - Output format and directory
  - AI model choice
  - Retry and timeout configs
  - Verbose logging
- Compatible with:
  - `cron` jobs
  - GitHub Actions
  - Cloud run environments

### Cross-Cutting Concerns

- **Security & Compliance**
  - API key stored via `.env` or vault integration
  - Complies with OpenAI and Google API usage policies
  - Option to append AI disclaimer to generated text

- **Observability**
  - JSON-based logs per execution
  - Errors, skipped rows, API stats, and generation time tracked

- **Extensibility**
  - Easily add new data sources (e.g., Yelp API)
  - Swap or add LLM providers without changing pipeline logic
  - Future-ready for web frontend or GUI (e.g., Streamlit)

This architecture empowers marketing and data teams to reliably scale their content generation workflows while ensuring full transparency, legal compliance, and developer control. It is designed to perform in real-world enterprise-grade scenarios with minimal human intervention.

## Tech Stack & Dependencies

AutoBizGen is built using modern, battle-tested Python libraries and cloud APIs to ensure a production-ready experience that’s easy to maintain, extend, and deploy. Below is a breakdown of the primary technologies used, along with their role in the system.

### Core Programming Language
- **Python 3.10+**
  - Chosen for strong ecosystem, readability, and native async support

### Primary Python Libraries

#### Data Handling
- **pandas** → Read, clean, and manipulate Excel and tabular data
- **openpyxl** → Read/write `.xlsx` files and manage Excel formatting
- **python-dotenv** → Load API keys and environment variables securely
- **phonenumbers** → Normalize and validate phone formats

#### API Integration
- **requests** → HTTP client for calling APIs (Google Maps, future integrations)
- **tenacity** → Retry logic and exponential backoff for unstable responses
- **sqlite3** (built-in) → Lightweight cache for API enrichment results

#### AI Content Generation
- **openai** → GPT-3.5/GPT-4 integration
- **anthropic** (optional) → Claude API integration
- **transformers / llama-cpp-python** → Local or Hugging Face-hosted LLaMA models

#### Output & Export
- **csv** (standard library) → CSV writer for raw and enriched exports
- **markdownify / markdown-it-py** → Markdown generation for AI output
- **jinja2** (optional) → Use template-based exports or rich formatting

#### Logging & Execution
- **logging** → Centralized logger with multiple levels (INFO, WARNING, ERROR)
- **argparse** → Robust command-line parsing for custom CLI workflows
- **uuid** / **datetime** → For unique report IDs and timestamping

### System Requirements
- Python 3.10+
- `.env` file for managing API keys (OpenAI, Google Maps)
- Internet access for live API enrichment and remote LLMs (unless using local models)

### Optional Tools for Extension
- **Redis / JSON flat file** → Alternate cache store for high-scale workloads
- **Streamlit / Flask** → Web interface integration for GUI-based workflows
- **Docker** → Containerized deployment for CI/CD pipelines

This tech stack balances rapid development, reliable automation, and future extensibility — making AutoBizGen ideal for both startups and enterprise-level adoption.


## Tech Stack & Dependencies

AutoBizGen is built using modern, battle-tested Python libraries and cloud APIs to ensure a production-ready experience that’s easy to maintain, extend, and deploy. Below is a breakdown of the primary technologies used, along with their role in the system.

### Core Programming Language
- **Python 3.10+**
  - Chosen for strong ecosystem, readability, and native async support

### Primary Python Libraries

#### Data Handling
- **pandas** → Read, clean, and manipulate Excel and tabular data
- **openpyxl** → Read/write `.xlsx` files and manage Excel formatting
- **python-dotenv** → Load API keys and environment variables securely
- **phonenumbers** → Normalize and validate phone formats

#### API Integration
- **requests** → HTTP client for calling APIs (Google Maps, future integrations)
- **tenacity** → Retry logic and exponential backoff for unstable responses
- **sqlite3** (built-in) → Lightweight cache for API enrichment results

#### AI Content Generation
- **openai** → GPT-3.5/GPT-4 integration
- **anthropic** (optional) → Claude API integration
- **transformers / llama-cpp-python** → Local or Hugging Face-hosted LLaMA models

#### Output & Export
- **csv** (standard library) → CSV writer for raw and enriched exports
- **markdownify / markdown-it-py** → Markdown generation for AI output
- **jinja2** (optional) → Use template-based exports or rich formatting

#### Logging & Execution
- **logging** → Centralized logger with multiple levels (INFO, WARNING, ERROR)
- **argparse** → Robust command-line parsing for custom CLI workflows
- **uuid** / **datetime** → For unique report IDs and timestamping

### System Requirements
- Python 3.10+
- `.env` file for managing API keys (OpenAI, Google Maps)
- Internet access for live API enrichment and remote LLMs (unless using local models)

### Optional Tools for Extension
- **Redis / JSON flat file** → Alternate cache store for high-scale workloads
- **Streamlit / Flask** → Web interface integration for GUI-based workflows
- **Docker** → Containerized deployment for CI/CD pipelines

This tech stack balances rapid development, reliable automation, and future extensibility — making AutoBizGen ideal for both startups and enterprise-level adoption.


## Input Format Examples

AutoBizGen expects a structured Excel file (`.xlsx`) as input, containing essential business information that will be validated, enriched, and used for AI-generated content creation. Below is a detailed explanation of the required structure, supported data points, folder organization, and best practices.

### Required Input Format (.xlsx)

Each row should represent a single business record. The input file must include the following columns:

| Column Name       | Required | Description                                                   |
|------------------|----------|---------------------------------------------------------------|
| Business Name     | ✅       | The official name of the business                             |
| Address           | ✅       | Full business address (street, city, state, zip code)         |
| Phone Number      | ✅       | Business contact number (E.164 international format preferred)|
| Email (Optional)  | ❌       | Email address (used for reference only, not enriched)         |
| Website (Optional)| ❌       | If known, used for consistency check during enrichment        |

### Accepted File Type & Sheet Handling
- Only `.xlsx` files are supported at this stage (not `.xls`, `.csv`, or Google Sheets)
- The first worksheet in the Excel file will be processed by default
- Optional future support for named sheet selection via CLI (`--sheet-name`)

### Example Record

| Business Name | Address                     | Phone Number   | Email                | Website               |
|---------------|-----------------------------|----------------|----------------------|------------------------|
| Zen Spa       | 123 Elm St, Austin, TX 73301 | +1 512-555-7890 | contact@zenspa.com   | https://www.zenspa.com |

### Folder Structure (Recommended)

```plaintext
/input/
  └── businesses_mar_2025.xlsx

/prompts/
  └── business_about_template.txt
```

### Data Validation Rules
- All required fields must be non-empty and properly formatted
- Phone numbers are normalized using the `phonenumbers` library
- Addresses must include at least street, city, and postal code
- Invalid, duplicate, or incomplete rows are skipped and logged in `/logs/`
- Recommended maximum: 5,000 rows per file for stability (dependent on API quotas)

### Prompt Templates (Optional)
Users can place a `.txt` file in `/prompts/` to define how the AI generates business descriptions.

**Example prompt (business_about_template.txt):**
```text
Write a professional and friendly "About" section for the following business:

Business Name: {{business_name}}
Category: {{category}}
Rating: {{rating}}
Address: {{address}}
Website: {{website}}
```

Prompt variables will be dynamically replaced at runtime.


This structured input format ensures the system has all the context needed to reliably enrich and describe each business in a consistent, scalable, and professional manner. For best performance, keep datasets clean, de-duplicated, and aligned with the template structure.


## Output Samples (Markdown + Excel)

AutoBizGen produces clean, multi-format output files that combine the original input, API-enriched metadata, and AI-generated descriptions. The formats are structured for downstream use in content platforms, CRMs, business directories, or internal analytics.

AutoBizGen supports **dynamic output generation** based on location — including city, region, or country. By passing a `--country` flag or configuring via `.env`, the final output files are automatically labeled and filtered accordingly.

### Output Formats

1. **Excel (.xlsx)**
   - Multi-sheet format (if needed)
   - Recommended for internal users and audit-ready delivery
   - Easily importable into Google Sheets, CRMs, or BI dashboards

2. **CSV (.csv)**
   - Lightweight format for bulk imports or data pipelines
   - Ideal for integrations with Airtable, Notion, SQL, or marketing tools

3. **Markdown (.md)**
   - Human-readable summaries suitable for GitHub repos, static sites, and client previews
   - Optionally rendered as clean HTML in web previews


### Sample Output Table (Excel & CSV)

| Business Name | Website               | Rating | Reviews | Category   | Country  | Description (AI-generated)                       |
|---------------|------------------------|--------|---------|------------|----------|--------------------------------------------------|
| Zen Spa       | https://zenspa.com     | 4.6    | 124     | Wellness    | USA      | Zen Spa is a tranquil space offering holistic... |


### Sample Markdown Output (USA)

```markdown
### Zen Spa

- **Website:** [zenspa.com](https://zenspa.com)
- **Category:** Wellness
- **Rating:** 4.6 (124 reviews)
- **Country:** USA

**About**
Zen Spa is a tranquil space offering holistic treatments, massage therapy, and aromatherapy in the heart of Austin, Texas. Known for its warm ambiance and attentive staff, it provides a relaxing escape for clients seeking balance and renewal. Visit their website to explore seasonal offers and service menus.
```

### Folder Structure (Dynamic Output)

```plaintext
/output/
  ├── usa/
  │   ├── businesses_mar_2025.xlsx
  │   ├── businesses_mar_2025.csv
  │   └── businesses_mar_2025.md
  ├── canada/
  │   └── businesses_mar_2025.xlsx
  └── logs/
      └── export_log.json
```

### How to Use Dynamic Country Filtering

- **CLI**: `python main.py --input data.xlsx --country usa`
- **Environment Variable**: `COUNTRY=usa`

Each format provides value for a different team:
- **Marketing** → Use `.md` for website copy
- **Ops & CRM** → Use `.xlsx` or `.csv` for uploads and tracking
- **Founders/Clients** → Easy snapshot view via `.md`

This dynamic, country-specific output structure ensures your enriched business content is regionally organized and ready to use across localized platforms — clean, compliant, and scalable.


## Core Code Modules

AutoBizGen is structured as a modular, enterprise-grade Python application, following clean architecture principles and best practices for scalable, testable automation pipelines. Each module is crafted with single responsibility, fault tolerance, and future extensibility in mind — supporting real-world data processing and AI workflows across marketing, analytics, and operations.

### Professional-Grade Module Structure

```plaintext
├── main.py
│   └── Central pipeline orchestrator. Coordinates CLI input, module invocation,
│       exception routing, and audit logging.
│
├── ingest.py
│   └── Data ingestion and validation engine.
│       - Reads Excel (.xlsx) using `openpyxl`
│       - Enforces schema constraints (e.g., business name, address, phone)
│       - Performs cleaning, normalization, and validation
│       - Streams data in batches for memory efficiency
│
├── enrich.py
│   └── Enrichment layer for integrating external APIs.
│       - Uses Google Maps Places API to fetch: ratings, categories, websites
│       - Retry-safe and rate-limit aware (via `tenacity`)
│       - Optional local caching via SQLite for repeated runs
│
├── generate.py
│   └── AI content generation engine.
│       - Loads structured prompt templates from `prompts/`
│       - Supports multiple LLMs (OpenAI GPT, Claude, LLaMA)
│       - Dynamic prompt injection with business metadata
│       - Post-processes AI output for tone, grammar, and length control
│
├── export.py
│   └── Multi-format export service.
│       - Outputs to .xlsx (Excel), .csv, and .md (Markdown)
│       - Handles column ordering, formatting, disclaimers, and footers
│       - Supports dynamic pathing by country/date/context
│
├── utils/
│   ├── logger.py       # Configurable logging (INFO, ERROR, DEBUG) with file/stream support
│   ├── cache.py        # Encapsulates local SQLite-based result caching layer
│   └── config.py       # Loads .env and CLI overrides with conflict resolution
│
├── prompts/
│   └── business_about_template.txt  # Customizable LLM prompt templates (Jinja-style optional)
```

### Enterprise Practices Implemented
- **Single Responsibility Per Module** → Enables isolated unit testing and refactoring
- **Plug-and-Play Providers** → Swap out APIs or AI models via config or environment variables
- **Resilient by Design** → All network-dependent layers have retry logic and logging
- **Production Traceability** → Structured JSON logs are emitted at each stage

This robust, modular structure ensures that AutoBizGen is ready for enterprise-scale use across different regions, clients, or brands — and is fully prepared for CI/CD workflows, versioning, or cloud deployments.


## CLI & GUI Usage Examples

AutoBizGen is designed for seamless execution via both Command-Line Interface (CLI) and an optional Web GUI (powered by Streamlit). This dual-mode interface makes it ideal for developers, analysts, and non-technical users alike.

---

###  CLI Usage (Command Line Interface)

The CLI offers full flexibility for input selection, country-specific filtering, output formats, AI model choice, logging verbosity, and more — all through environment variables or direct flags.

#### Basic Command
```bash
python main.py --input ./input/businesses_mar_2025.xlsx --country usa
```

#### Full CLI Options

| Flag                  | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `--input`             | Path to input Excel file (`.xlsx`)                                          |
| `--country`           | Filter records and organize output by country (e.g., `usa`, `canada`)       |
| `--output-dir`        | Path to export output files (default is `./output/`)                         |
| `--prompt-file`       | Path to custom prompt template (`.txt`) in `prompts/`                        |
| `--model`             | AI model to use (`gpt-4`, `claude-2`, `llama-2`)                             |
| `--max-retries`       | Max retries for API calls (default: 3)                                       |
| `--cache-enabled`     | Enable/disable API caching (`true`/`false`)                                  |
| `--output-formats`    | Comma-separated formats: `xlsx`, `csv`, `md` (e.g., `--output-formats xlsx,md`)|
| `--log-level`         | Logging level: `INFO`, `DEBUG`, `ERROR`                                     |

#### Example Command with All Options
```bash
python main.py \
  --input ./input/businesses_mar_2025.xlsx \
  --country canada \
  --prompt-file ./prompts/business_about_template.txt \
  --model gpt-4 \
  --output-formats xlsx,csv,md \
  --output-dir ./output/ \
  --cache-enabled true \
  --max-retries 5 \
  --log-level INFO
```

#### Environment Variable Support (.env)
```dotenv
INPUT=./input/businesses_mar_2025.xlsx
COUNTRY=usa
MODEL=gpt-4
OUTPUT_FORMATS=xlsx,md
OUTPUT_DIR=./output/
CACHE_ENABLED=true
MAX_RETRIES=3
LOG_LEVEL=DEBUG
```

#### Scheduler & Automation Friendly
- **Cron Jobs** for periodic execution
- **CI/CD** pipelines for hands-free reporting
- **Cloud Functions** or serverless job triggers

---

### 🔹 GUI Usage (Streamlit Web Interface)

The GUI interface makes AutoBizGen accessible to non-technical users. Built using Streamlit, it allows users to upload files, configure settings, trigger generation, and download results from a web browser.

#### Launch Streamlit App
```bash
streamlit run app.py
```

#### Features of the Web GUI
- Drag-and-drop Excel upload
- Dropdown to select country or region
- Input fields for API keys, prompt customization, and model selection
- Real-time status updates
- Download links for `.xlsx`, `.csv`, and `.md` outputs
- Error messages and logs shown in-app

#### Sample GUI URL (after launch)
```
http://localhost:8501
```

#### Ideal For:
- Internal marketing teams
- Non-technical founders
- Content managers and clients

The combination of CLI and GUI ensures AutoBizGen is usable across technical and non-technical teams — whether integrated into pipelines or operated via browser with zero code.


## CLI and GUI Usage Examples

AutoBizGen supports both command-line and browser-based interfaces, making it adaptable for enterprise-grade automation pipelines and fully accessible to non-technical stakeholders. This dual-mode interaction ensures end-to-end usability across engineering, content, marketing, and operations teams.


### CLI Usage (Enterprise Automation Standard)

The Command-Line Interface (CLI) is designed for robust execution in professional environments. It supports full customization via CLI flags or environment variables, and integrates seamlessly with CI/CD systems, cron schedulers, or job orchestrators.

#### Minimal Execution
```bash
python main.py --input ./input/businesses_mar_2025.xlsx --country usa
```

#### Advanced Execution with All Options
```bash
python main.py \
  --input ./input/businesses_mar_2025.xlsx \
  --country canada \
  --prompt-file ./prompts/business_about_template.txt \
  --model gpt-4 \
  --output-formats xlsx,csv,md \
  --output-dir ./output/ \
  --cache-enabled true \
  --max-retries 5 \
  --log-level DEBUG
```

#### CLI Option Matrix

| Flag                  | Description                                                                 |
|-----------------------|-----------------------------------------------------------------------------|
| `--input`             | Required: Path to `.xlsx` input containing business records                 |
| `--country`           | Filters data and organizes output by region or country                      |
| `--output-dir`        | Directory for all exported report files                                     |
| `--prompt-file`       | Custom `.txt` prompt used for LLM generation                                |
| `--model`             | AI model selection (`gpt-4`, `claude`, `llama`)                             |
| `--output-formats`    | Export format options: `xlsx`, `csv`, `md`                                  |
| `--cache-enabled`     | Enables local result caching for repeat lookups                            |
| `--max-retries`       | Retry threshold for API fault tolerance                                     |
| `--log-level`         | Logging granularity: `INFO`, `DEBUG`, or `ERROR`                           |

#### Environment Variable Support (.env)
```dotenv
INPUT=./input/businesses_mar_2025.xlsx
COUNTRY=usa
MODEL=gpt-4
OUTPUT_FORMATS=xlsx,md
OUTPUT_DIR=./output/
CACHE_ENABLED=true
MAX_RETRIES=3
LOG_LEVEL=DEBUG
```

#### Automation Compatibility
- Fully compatible with cron-based scheduling systems
- Easily integrated into GitHub Actions, GitLab CI, or Jenkins pipelines
- Ideal for orchestration tools like Airflow, Prefect, or Dagster
- Serverless compatible via AWS Lambda, Cloud Run, or containerized execution


### GUI Usage (Streamlit-Based Interface)

AutoBizGen also offers a modern browser-based interface powered by Streamlit. The GUI is ideal for business analysts, marketing teams, or clients without coding experience. It allows users to execute the full enrichment and content generation process via intuitive controls.

#### Launch the Web Interface
```bash
streamlit run app.py
```

#### Key Capabilities
- Drag-and-drop Excel input upload
- Dropdown selectors for country, model, and output format
- Input fields for prompt customization and log level
- Real-time processing updates with error transparency
- Output download buttons for Excel, CSV, and Markdown files
- Inline console-style logs and status traces

#### Typical Access URL
```
http://localhost:8501
```

#### Target User Scenarios
- Marketing managers preparing large-scale location listings
- Freelancers delivering business summaries in client templates
- Internal QA or editorial teams verifying output consistency

The Streamlit GUI enables easy onboarding of non-technical users while maintaining full fidelity of functionality. It also serves as a controlled demo interface during stakeholder reviews or client onboarding.


Whether through programmatic automation or point-and-click execution, AutoBizGen delivers high-quality, structured output with minimal configuration overhead. This dual interface strategy ensures adaptability across technical, operational, and strategic roles in modern enterprise settings.

## Compliance and Limitations

AutoBizGen is engineered with attention to compliance, legal safety, and responsible AI usage. This ensures that deployments across regulated industries, client-facing environments, and production-grade infrastructures remain secure, ethical, and reliable.

### API Usage and Terms of Service
- **Google Maps API**: Data fetched (e.g., ratings, websites, place details) must adhere to Google’s [Terms of Service](https://cloud.google.com/maps-platform/terms/). AutoBizGen does not scrape or store proprietary data beyond documented API usage.
- **OpenAI and Anthropic APIs**: All usage of GPT and Claude models must align with respective API providers' content generation guidelines. Users are responsible for adhering to quota, rate limits, and regional compliance policies.
- **Caching**: Local caching of API results (optional) is used only for optimization and never for unauthorized data replication.

### AI Content Guidelines
- **Originality**: All AI-generated content is original, synthesized from input metadata and context. No scraping, copying, or derivative content is created.
- **Plagiarism Control**: Prompts are engineered to minimize common phrasing or templated output. Generated text is customizable for further post-editing or brand tone alignment.
- **Disclaimer Support**: AutoBizGen can append an optional disclaimer such as "This content was generated using AI" in Markdown or Excel exports.

### Data Privacy and Security
- No personal or sensitive data is stored persistently unless explicitly configured
- Files are processed locally unless cloud deployment is configured by the user
- API keys are stored in `.env` and never exposed in code or logs
- Logging avoids PII and focuses on metadata, process status, and exceptions

### System Limitations
- **API Dependency**: Output accuracy relies on the completeness and freshness of third-party API responses (e.g., outdated ratings)
- **Quota and Rate Limits**: Users must monitor and manage API keys with respect to request thresholds
- **LLM Interpretation Variability**: While prompt engineering improves consistency, tone and language may still vary slightly across generations
- **Maximum Scale**: Recommended batch size is 5,000 records per execution to balance performance and API cost

### Legal Disclaimer
AutoBizGen is provided as an open-source tool. It is the responsibility of the deploying organization or user to ensure:
- That API access rights are valid and maintained
- That AI-generated content meets branding, factual, and legal requirements
- That local jurisdictional laws around AI disclosures and data access are followed

AutoBizGen does not guarantee compliance out-of-the-box for regulated sectors like finance, healthcare, or government unless explicitly configured and reviewed by domain professionals.

This safeguards-first architecture ensures AutoBizGen can be deployed confidently in environments requiring legal oversight, transparency, and traceability.


## Enhancements and Roadmap

AutoBizGen is architected for evolution. While the current version covers end-to-end ingestion, enrichment, generation, and export, several enterprise-ready features are in the planning and prototyping stages. These enhancements are designed to make the system even more scalable, intelligent, and flexible across a wide range of real-world business environments.

### Planned Enhancements

#### 1. Streamlit GUI Upgrade (Advanced Mode)
- Role-based access controls (RBAC)
- Session tracking and report history by user
- AI prompt preview and live-edit with context injection

#### 2. API-First Deployment (FastAPI/Flask Service Layer)
- Convert CLI pipeline into secure API endpoints
- Suitable for embedding in SaaS tools or dashboards
- Token-based authentication and rate limiting

#### 3. Live Dashboard & Monitoring Tools
- Real-time token usage, error trends, and report generation stats
- Admin dashboard for queued jobs, retries, and cache hit analysis

#### 4. Advanced Prompt Engineering System
- Jinja2-based templating with field-level overrides
- Custom personas, tones, and industries via metadata triggers
- Support for prompt chaining and iterative AI refinement

#### 5. Multi-Language Output Support
- LLM-generated summaries in multiple languages using translation APIs
- Language selector available via CLI and GUI
- Localized tone adjustments for regional campaigns

#### 6. Model Routing and Cost Optimization
- Configure hybrid inference (use GPT for summaries, LLaMA for intros)
- Load balancing between OpenAI and local LLMs for cost-sensitive clients
- Intelligent fallback when rate limits are reached

#### 7. Report Versioning and Audit Trails
- Maintain timestamped version history of generated content
- Compare changes between previous and current report iterations
- Useful for compliance audits and editorial reviews

#### 8. Third-Party Integration Modules
- Native export to Notion, Airtable, and Google Sheets
- Webhooks and callback URLs for automation chaining
- Slack or Teams alert for completion or failure events

#### 9. Enhanced Data Quality Layer
- ML-based anomaly detection in business data before processing
- Enrichment result scoring and confidence metrics
- Auto-flagging incomplete or low-trust records

### Roadmap Timeline (Indicative)
- Q2 2025: Streamlit GUI v2, prompt engineering toolkit
- Q3 2025: API-first backend, multi-language generation, dashboard beta
- Q4 2025: Third-party integrations, report versioning, audit controls

AutoBizGen’s roadmap is focused on elevating automation, configurability, and content reliability. These features are being designed in collaboration with early adopters, and contributions are welcome via GitHub.


## License

AutoBizGen is released under the MIT License, a permissive open-source license that supports both individual and commercial use. This license ensures transparency, flexibility, and adoption in both private and public codebases.

### Permissions
- Commercial use
- Modification and distribution
- Private use and white-label integration
- Embedding into closed-source enterprise workflows

### Limitations
- No warranty provided
- No liability assumed by maintainers or contributors

### Conditions
- Must include a copy of the license in all distributions
- Any significant modifications must be documented
- Original authorship attribution must be retained in derived works

### File Reference
The complete MIT License text is included in the `LICENSE` file at the root of the repository.

For organizations interested in dual licensing, enterprise support, or commercial partnerships, please reach out via the GitHub repository's contact information or discussion board.

This licensing model ensures that AutoBizGen remains freely usable and extensible while maintaining clarity and protection for both maintainers and users.


## Demo Output (Optional Preview)

AutoBizGen produces structured, enriched, and AI-augmented business reports in `.xlsx`, `.csv`, and `.md` formats. This section provides a visual and textual snapshot of expected outputs to help contributors and adopters understand the result quality and formatting standards.

### Sample Excel Output (`.xlsx`)
- Sheet 1: Raw input business records
- Sheet 2: Enriched data (websites, ratings, categories)
- Sheet 3: AI-generated descriptions with branding tone

**Preview (Tabular):**
| Business Name | Category   | Rating | Reviews | Country | Description                          |
|---------------|------------|--------|---------|---------|--------------------------------------|
| Zen Spa       | Wellness   | 4.6    | 124     | USA     | Zen Spa is a modern wellness studio...|

### Sample Markdown Output (`.md`)
```markdown
### Zen Spa
- Website: [zenspa.com](https://zenspa.com)
- Category: Wellness
- Rating: 4.6 (124 reviews)
- Country: USA

Zen Spa is a modern wellness studio based in Austin, Texas. Known for its tranquil design and attentive staff, it offers a broad range of aromatherapy and massage services. The business consistently earns positive reviews and serves both local residents and tourists.
```

### Folder Example
```plaintext
/output/
  ├── usa/
  │   ├── businesses_report.xlsx
  │   ├── businesses_report.csv
  │   └── businesses_report.md
  └── logs/
      └── generation_log_2025-03-31.json
```

### Screenshot or GIF (Coming Soon)
You may include a screenshot of the GUI or Excel output in the GitHub README or documentation site to demonstrate formatting, layout, and visual clarity. Suggested location: `/docs/assets/demo_preview.png`

This sample output section provides guidance to users preparing to validate functionality, replicate behavior, or demo results to clients and stakeholders.
