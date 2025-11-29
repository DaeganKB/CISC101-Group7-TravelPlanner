Changelog (Nov 28th): Added missing data defualts, and numerics for budget. 

### Module 1 — Intake & Setup
## Collect essential details
* Destination(s)

  * Accept single or multiple destinations.

  * If missing: default to "unspecified" with flexibility_level = high.

* Dates or trip length

  * Normalize to ISO-8601 (start_date, end_date, length_days).

  * If missing: default to "unspecified"; assume length_days = 7 (one week).

  * If only length provided: infer end_date from start_date.

* Number of travelers

  * If missing: default to 1.

* Budget style (affordable, mid-range, luxury)

  * Normalize to both style and numeric range (per day, in user currency):

    * Affordable → 75–150/day

    * Mid-range → 150–300/day

    * Luxury → 300+/day

  * If missing: default to mid-range.

  * If numeric budget provided: store both style and range.

* Interests (food, culture, nature, etc.)

  * Normalize to taxonomy list.

  * If missing: default to ["general sightseeing"].

* Preferred pace (relaxed, balanced, fast)

  * Normalize to heuristics:

    * Relaxed → ≤2 activities/day

    * Balanced → 3/day

    * Fast → 4+/day

  * If missing: default to balanced.

* Key constraints (mobility, weather, diet)

  * Normalize into structured categories:

    * Personal (mobility, diet, allergies)

    * External (season, expected weather, holidays)

* If missing: default to "none".

## Normalize details
* Dates → ISO-8601 format, derive season.

* Budget → store both style and numeric range.

* Interests → map to controlled vocabulary + free text.

* Pace → map to activity heuristics.

* Constraints → structured into personal vs. external.
