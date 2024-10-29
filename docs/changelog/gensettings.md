# General Settings
**Destination S3 bucket:** hbcd-main-staging    
**Mounted Directory:** `/loris/loris_server/volumes/data/loris/data/stg_s3_data/`     
**Data Structure:**    
```
root_bids_directory/ 
└─── participants.tsv
└─── participants.json 
└─── assembly_bids
└─── phenotype/  
    └─── visit_data.tsv
    └─── visit_data.json
    └─── sed_basic_demographics.tsv
    └─── sed_basic_demographics.json
    └─── biosample_urine.tsv 
    └─── biosample_urine.json
    └─── <instrument_name_1>.tsv    
    └─── <instrument_name_1>.json
    └─── <instrument_name_2>.tsv   
    └─── <instrument_name_2>.json ...
```

**Additional File Descriptions**    
The participant list and associated metadata are contained in `participants.tsv` and `participants.json`, respectively. Within the `phenotype/` folder:

 * `visit_data.tsv`: contains fields associated to visit-level data
 * `sed_basic_demographics.tsv`: contains derived fields pertaining to demographic data
 * `<instrument_name_1>.tsv`: Data Table for each instrument *(Participant GUID & 'Visit Label' in first two columns)* 
 * `<instrument_name_1>.json`: Data Dictionary for each instrument

**[Data Release Detailed settings](https://docs.google.com/spreadsheets/d/15Ne_q8-1dyTW3MWtUTfLp3nobRLIBaiYxV6k1_nL8EA/edit?gid=589752985#gid=589752985)**

**[HBCD - BIDS Descriptions for Data Release](datacuration/bids.md)**
