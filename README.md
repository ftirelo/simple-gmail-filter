# simple-gmail-filter

Very simple tool to manage gmail filters.

## How to write a client

- Create a new github repo, downstream from this one
  - Suggested reading: https://www.atlassian.com/git/tutorials/git-forks-and-upstreams
- Generate credentials file and save somewhere safe (prefer locally)
- Folder `example` contains:
  - `personal_filters.py`
    - Example of some personal filters to adapt from
  - `update_gmail_filters.py`:
    - Reads `personal_filters`
    - Sets `credentials_path` and `token_path`
    - Authenticates to Gmail
    - Updates labels and filters
    - Applies filters
- Make a copy of the `examples` folder
- Edit `personal_filters.py`
- Edit `main` to set the variables `credentials_path` and `token_path`
- Run `update_gmail_filters.py`
- Upload changes to downstream repo
- Contribute to the library if you have an idea on how to improve it

## Overall design

- Modules:
  - Gmail connector
  - Filters and actions
  - Filter updater

### Gmail connector

- class GmailConnector:
  - Holds `service_`
  - Init gets: `credentials_path`, `token_path`
  - Methods:
    - `GetCurrentLabels`
    - `CreateLabel`
    - `GetCurrentFilters`
    - `CreateFilter`
    - `DeleteFilter`
    - `SearchMessages`
    - `ApplyFilterToMessages`

### Filters and actions

- class `Action`
- class `Filter`
- class `FilterList`

- Builder functions:
  - `ArchiveForQuery`
  - `ArchiveForSenders`
  - `AddLabelForQuery`
  - `AddLabelForSenders`
  - `SendToSpam`

### Filter updater

- Most of the function in private's `main`
