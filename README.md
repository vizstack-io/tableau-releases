# tableau-releases
This repository provides information about Tableau releases in a machine-readable format.

## files
- known-versions.json: Contains a sorted list of known release versions, starting at 2020.4.0. The last element is the most current release of the newest major/minor.
- \<release-version\>.json: Contains a dict with details about the release and its respective download files.
  - files: a list of dicts for each download included in this version.
    - bytes: file size in bytes (int)
    - download_link: published download link for file (string/uri)
    - expected_md5sum: the md5sum provided by Tableau for file (string) — null if value provided by Tableau is invalid or missing
    - expected_sha1sum: the sha1sum provided by Tableau for file (string) — null if value provided by Tableau is invalid or missing
    - expected_sha256sum: the sha256sum provided by Tableau for file (string) — null if value provided by Tableau is invalid or missing
    - file_md5sum: the md5sum provided by Akamai for file (string) — this is provided for every file still available to be downloaded, and retained if known before a file is removed from Akamai's servers
    - name: the file name (string)
    - present: false when the file is known to be missing, such as if removed by Tableau (boolean)
    - uploaded_at: Unix timestamp (seconds) for when file was uploaded to Akamai (number/float)
  - release_date: date version was released (string: mm/dd/yyyy)
  - present: false when the release is known to be absent, such as if removed by Tableau (boolean)
  - version: version number associated with this release. (string)
- release.jsonschema: jsonschema used for validating the format of each release file.
