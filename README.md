## Task 1: Data Integration & Reflection
* **Pipeline Summary:** An SQL `LEFT JOIN` combined `members` and `checkouts` from `LibraryDB.db` to pair members with their borrowing histories[cite: 2]. Pandas `merge()` linked this data with `Book Catalog.json` via `book_id` to add book metadata[cite: 1]. Finally, BeautifulSoup extracted offline summer checkouts from `Reading Kickoff Signups.html`[cite: 3], which were concatenated using `pd.concat()` to ensure complete borrowing records across all platforms.
* **API vs. Web Scraping:** Using an API is preferred over web scraping because APIs deliver structured, machine-readable data through stable, versioned endpoints. Web scraping relies on parsing HTML layout markup, making it fragile and prone to breaking whenever a site's visual structure changes.

## Task 2: Data Integrity Report
* **Missing Values:** Blank `return_date` entries represent active checkouts or summer loans that have not yet been returned[cite: 3]. Deleting these rows would artificially lower reading counts, so they are preserved.
* **Duplicate Records:** Duplicate checkouts were identified and removed using `drop_duplicates()` to ensure activity metrics are accurate.
* **Inconsistent Formatting:** Capitalization and spacing errors (e.g., "HELIOPOLIS", "Nasr  City") in `neighborhood` and `membership_status` were standardized using `.str.strip()`, `.str.title()`, and explicit dictionary mapping.
* **Orphan Records:** Checkouts linked to `member_id`s absent from the primary database are retained to ensure total book usage counts remain accurate while flagging missing member profiles.

## Task 3: Data Fairness Reflection
* **Neighborhood Analysis:** Grouping total checkouts by `neighborhood` highlights unequal distribution in library program participation. Lower engagement in specific districts (such as Shubra or Zamalek) indicates potential accessibility barriers, including physical distance to branches or lack of local outreach[cite: 2].
* **Action Plan:** To achieve fair representation next summer, the library should organize mobile library pop-ups, partner with local neighborhood schools for enrollment drives, and expand digital borrowing access for underrepresented areas.
