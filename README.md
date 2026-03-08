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
- Main: Congress.gov API (v3)
- Supplementary: TBD

## 1. Committee/Subcommittee Membership and Leadership
- Primary Keys: bioguideID, Chamber, congress
- Variables: TBD


## 2. Committee Markups and Hearings
- Primary Keys: TBD
- Variables: TBD


## 3. Committee Reports
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
