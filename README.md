# Orpheus Engine (orpheus-engine) Archive (April 8, 2026)

>[!CAUTION]
>
>**TECHNICAL AUDIT NOTICE**
>
>This repository is a static archive preserved for forensic auditing and youth safeguarding oversight. The source code contained herein implements automated data harvesting, third-party profiling, and programmatic surveillance of minors.
>
>All technical liability, privacy inquiries, or complaints regarding these operations must be directed to the original authors via the contact information in the repository metadata or on the official [Hack Club website](https://hackclub.com).

> [!IMPORTANT]
> 
> **LEGAL NOTICE & ARCHIVE PROTOCOL**
>
> * No Support of Content: The archiver **does not support, endorse, or condone** any viewpoints, ideologies, or organizational practices expressed, implied, or implemented within this repository.
>
> * No Warranties: This archive is **provided "as-is" for transparency and forensic purposes**; no warranties of any kind are provided regarding the functionality, safety, or legality of the contained code.
>
> * Non-Production Warning: **The archiver strictly does not condone the use of this software in a production environment and/or with real-world user data.** This code implements surveillance and profiling mechanisms that may violate international privacy standards and youth safeguarding regulations.
>
> * Purpose of Archive: **This repository is maintained strictly for security and privacy audits, legal documentation, historical archival, and forensic research using simulated/synthetic data.** It serves as a public interest case study in the degradation of nonprofit transparency and as a technical reference for the ethical failures of centralized youth surveillance infrastructure.
>
> * Non-Affiliation: The archiver (the owner of this fork) **is not a contributor to this project**, has **no affiliation with the original authors** (including but not limited to [@]24c02, Hack Club, or the Hack Foundation), and **assumes no responsibility for the function or deployment of this code.**
>
> * Trademark Notice: All third-party trademarks mentioned (including but not limited to Hack Club, The Hack Foundation, GitHub, Google, Dagster, OpenAI, Genderize, and Bright Data) are the property of their respective owners. **The archiver claims no ownership rights over any third-party trademarks mentioned herein.**

## Audit Summary

This fork preserves the repository state as of **April 8, 2026**. This snapshot was captured **one week after the merge of Pull Request \#18**, ensuring that the archived code reflects the stable production version of the data warehouse replication logic. This archive ensures a permanent public record of the internal data-mining infrastructure currently in operation.

## Documented Functional Constraints

The following operations are hard-coded into this suite and are executed without explicit, per-event disclosure to participants:

  * **Database Mirroring (PR \#18):** Implements "Full-Refresh" logic to replicate private interaction databases and student "reviews" into a centralized, permanent PostgreSQL Data Warehouse.
  * **Programmatic Gender Identification:** Utilizes the **Genderize API** to assign gender markers to students based on name-string analysis rather than self-reporting.
  * **Geospatial Tracking:** Converts physical residential addresses into latitude and longitude coordinates via the **Google Maps API** for permanent mapping and regional tracking.
  * **Automated Social Surveillance:** Employs **Bright Data** (a commercial web-scraping and proxy service) to monitor and archive student social media mentions and project "virality" across Reddit, Hacker News, and other public forums.
  * **Shadow Infrastructure:** Configured for deployment via private **Coolify** instances, removing the data pipeline from standard cloud compliance and transparency protocols.

-----

## Original Project Documentation (Unchanged)

This is a set of Python scripts that generates dashboards and reporting across Hack Club.
Most nonprofits / organizations / companies don’t have the code for their data pipelines public. All of Hack Club's data scripts are open source in this repo.

Some other tasks it does are:

  * Calculates sign-up counts and HCB spend for YSWS programs
  * Downloads our email list and backs it up in Postgres
  * Syncs Airtables to Postgres for reporting

To illustrate, here’s what happens when you submit a project that gets approved for YSWS:

1.  **Gender Assignment:** If we don’t already have a gender on file for you, we use the Genderize API to try and guess your gender using the name you provided. We use this to try and understand how many girls are shipping projects, since we don’t want to have to ask for gender across every form and care about helping more girls make projects. If you have self-reported gender before, we always default to your self reported gender (male / female / or nonbinary).

2.  **Geocoding:** We geocode your address using the Google Maps API to convert it into a latitude and longitude. We use this for map visualizations and also to understand how many Hack Clubbers are participating from different regions (ex. USA vs. Europe).

3.  **Viral Monitoring:** We use the GitHub API to get the current number of stars from your GitHub repo. If your repo has more than 5 GitHub stars, we then use the Bright Data API to try and find places your project has gone viral on the internet (ex. reddit / Hacker News / etc). We do this as one way of understanding quality of projects across YSWS programs.

4.  **Archival:** We use archive.hackclub.com (Arker) to archive the public deployed page for your project and your git repo. This is used for historical records and fraud detection. It only pulls public information from your public git repo and your public deployed page.
---
This is a set of Python scripts that generates dashboards and reporting across Hack Club. 

Most nonprofits / organizations / companies don’t have the code for their data pipelines public. I’ve actually never seen anyone publicize it before besides Dagster’s sample project. All of Hack Club's data scripts are open source in this repo.

Some other tasks it does are:

- Calculates sign-up counts and HCB spend for YSWS programs
- Downloads our email list and backs it up in Postgres
- Syncs Airtables to Postgres for reporting

To illustrate, here’s what happens when you submit a project that gets approved for YSWS:

- If we don’t already have a gender on file for you, we use the Genderize API to try and guess your gender using the name you provided. We use this to try and understand how many girls are shipping projects, since we don’t want to have to ask for gender across every form and care about helping more girls make projects. If you have self-reported gender before, we always default to your self reported gender (male / female / or nonbinary)

- We geocode your address using the Google Maps API to convert it into a latitude and longitude. We use this for map visualizations and also to understand how many Hack Clubbers are participating from different regions (ex. USA vs. Europe).

- We use the GitHub API to get the current number of stars from your GitHub repo. If your repo has more than 5 GitHub stars, we then use the Bright Data API to try and find places your project has gone viral on the internet (ex. reddit / Hacker News / etc). We do this as one way of understanding quality of projects across YSWS programs. For example, if a YSWS program has 1,000 projects made for it and none went viral - that’s a red flag. Or, if a smaller YSWS program has a lot of projects that went viral, then something amazing happened and we need to understand what worked so we can do it more. This is new and an attempt to start measuring quality of projects instead of just quantity. I think it’d be cool if this could be shared with project authors too (ex. “your project just went viral!” or a place where you can see all the places your projects went viral)

- We use archive.hackclub.com (https://github.com/hackclub/arker) to archive the public deployed page for your project and your git repo. Occasionally this is helpful for fraud detection (sometimes people ship a project, get approved, them immediately private their repo because they did fraud and we can’t retroactively go and check to see what was in their repo once it’s gone). It’s also for generally a historic record - some of the coolest projects made years ago in Hack Club are sadly no longer online and it’s sad that we can no longer see them. This only pulls public information from your public git repo and your public deployed page. I’m planning to add Wayback Machine support for this too.

