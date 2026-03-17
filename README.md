# congress-committees
A data pipeline for collecting and storing congressional committee/subcommittee information and their activities.

## Repo Structure
```
.
├── notebooks/
│   ├── congressapi.ipynb   # Committee metadata (listings, membership, leadership, etc.)
│   ├── reports.ipynb       # Committee reports (active)
│   ├── print.ipynb         # Committee print collection
│   └── mtgs.ipynb          # Committee meetings
└── README.md
```

## Data Source
- Main: GovInfo, 
- Validation Check: Stewart et al (2021), Replication Data (Hearings; Ban et al 2025)

## 1. Historical Committee Structure (congress - committee level)
```
- Source: GovInfo 
- Variables: congress, chamber(House/Senate), thomas_id, type (standing, select/special, joint, conference), cmt_id, cmt_name, subcmt_id, subcmt_name
```

## 2. Committee Membership
```
biogiudeID, congress, chamber, party, gender, district, seniority, party_rank, ym_cmt_assn, ym_cmt_term, cmt_name, cmt_code, subcmt_name, subcmt_code
```

## 3. Committee Markups and Hearings
```
- Source: Hearings (Ban et al 2023)
```

## 4. Committee Reports
- Primary Keys: `congress`, `reportNumber`
- Variables: TBD
- Pipeline: Collect `congress`, `type`, `number` and `part` from the `/committee-report` listing, fetches the URL from the `/text` sub-endpoint, extracts the body text via BeautifulSoup, and stores the result in MongoDB.


## Current Progress
- [x] Retrieve `/committee-report` listing and confirm field names
- [x] Confirm `/text` endpoint structure (returns HTM/PDF URLs)
- [x] Fetch HTM and extract plain text
- [ ] Determine congress range
- [ ] Implement full MongoDB storage pipeline
- [ ] Build `print` and `mtgs` pipelines
