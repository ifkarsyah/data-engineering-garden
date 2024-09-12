---
title: Data Freshness
synonym: How often data is updated?
---
- **Why it matters**: How current the data is when it's served to end users is crucial for many use cases, especially for real-time analytics or decision-making.
- **Metrics**:
    - Time-to-data availability (from ingestion to querying)
    - Maximum supported data refresh intervals
- **Example**: A streaming platform like Apache Flink can provide near-instant data freshness, whereas batch processing might introduce delays in data availability.