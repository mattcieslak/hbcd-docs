# Processing and Analytic Software Standards
HBCD pipeline developers, Workgroups, and community contributors who wish to integrate their tools into the HBCD release environment are expected to follow these guidelines to ensure standardization of HBCD software and documentation. These guidelines are rooted in principles and utilities developed by [NMIND](https://www.nmind.org/about) aimed at promoting reproducibility and standardization in neuroimaging tools ([Kiar et. al 2023](https://www.nature.com/articles/s41562-023-01647-0)). Among these is the [NMIND Coding Standards Checklist](https://www.nmind.org/standards-checklist/), a comprehensive framework for evaluating the quality of a tool's documentation, infrastructure, and testing capabilities.

To participate, developers must complete the checklist and submit a pull request to the [proceedings repository](https://github.com/nmind/proceedings), including the tool's exported JSON file for external review. Any issues or feature requests related to this utility should be reported as issues in the NMIND [GitHub repository](https://github.com/nmind/standards-checklist). 

At a minimum, tools must meet the standards equivalent to the Bronze badge in the rating system. Developers may bypass checklist items that are not applicable—for example, listing software dependencies is less critical since all HBCD software must be containerized.

## Documentation 
### NMIND Documentation Checklist
<input type="checkbox" [name] [value] [checked] [disabled]> Landing page (e.g., GitHub README, website) has provides a link to documentation and brief description of what program does<br>
<input type="checkbox" [name] [value] [checked] [disabled]> Documentation is up to date with version of software<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  Typical intended usage is described<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  An example of its usage is shown<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  Document functions intended for users (i.e., public function docstring/help coverage ≥ 10%)<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  Description of required input parameters for user-facing functions with reasonable description of inputs (i.e., "NIfTI of brain mask in MNI" vs. "An image file")<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  Description of output(s)<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  User installation instructions available<br>
<input type="checkbox" [name] [value] [checked] [disabled]>  Dependencies listed (i.e., external and within-language requirements)<br>

### Webpage For Documentation
In addition to the general guidelines outlined in the checklist, each pipeline must maintain living documentation accessible through a dedicated webpage. This ensures the information remains up-to-date, offering a more dynamic and easily navigable resource compared to static publications or standard GitHub README files. Given the complexity and depth of information typically required for image processing pipelines, a webpage provides a more effective platform for organizing and presenting the documentation. Developers can refer to the [fMRIPrep ReadtheDocs](https://fmriprep.org/en/stable/) as a guide for overall organization and what level of detail each section should ideally include. 

## Infrastructure
### NMIND Infrastructure Checklist
<input type="checkbox" [name] [value] [checked] [disabled]> Code is open source<br>
<input type="checkbox" [name] [value] [checked] [disabled]> Package is under version control<br>
<input type="checkbox" [name] [value] [checked] [disabled]> Readme is present<br>
<input type="checkbox" [name] [value] [checked] [disabled]> License is present (see more details in following section)<br>
<input type="checkbox" [name] [value] [checked] [disabled]> Issues tracking is enabled (i.e., either through GitHub or external site)<br>
<input type="checkbox" [name] [value] [checked] [disabled]> Digital Object Identifier (DOI) points to latest version (e.g., Zenodo)<br>
<input type="checkbox" [name] [value] [checked] [disabled]> All documented installation instructions can be successfully followed<br>

### Licensing and Obtaining a DOI
All included software must have a [license](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/adding-a-license-to-a-repository) and a DOI for publication as internal HBCD pipelines may be used for data releases prior to publication. For pipelines without a citable scientific article, developers can obtain a DOI by self-publishing on [Zenodo](https://cdnis-brain.readthedocs.io/zenodo/). Software from non-HBCD PIs included in HBCD releases must undergo NMIND peer review and be published with a DOI. Additionally, all software must be compatible with BIDS input data or the latest HBCD derivatives provided in the current release. The pipeline webpage should include a description of how to properly cite the pipeline (see [example](https://fmriprep.org/en/stable/#citation)).

### Versioning and New Release Policies
In addition to basic version control on GitHub, developers should tag new releases when significant updates or multiple changes are made. Each tagged release must include a changelog detailing the differences from the previous version. Developers are encouraged to establish a standard release cycle and define criteria for special releases, such as urgent bug fixes. Documentation should specify which versions will receive long-term support, which will be deprecated, and the timeline for deprecation.

## Testing Ability

### NMIND Testing Checklist
<input type="checkbox" [name] [value] [checked] [disabled]> Provide / generate / point to test data**<br>
<input type="checkbox" [name] [value] [checked] [disabled]> Provide instructions for users to run tests and evaluate for correct behavior

<i>**Standards for testing may not be applicable for all HBCD processing pipelines. For example, depending on how specialized a given application is for HBCD, openly sharing representative test data for the workflow may not be feasible.</i>
