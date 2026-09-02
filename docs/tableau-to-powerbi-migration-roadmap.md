# 🔄 Roadmap: Migrating a Tableau Report to Power BI

This document outlines a general roadmap for migrating a single Tableau report to Power BI. It is intended as reference documentation and is not tied to any specific report currently in this repository.

## 1. Discovery & Inventory
- Document the Tableau report's purpose, audience, and refresh cadence.
- Catalog all data sources (databases, extracts, files, APIs) and connection types used.
- List every sheet, dashboard, calculated field, parameter, filter, and table calculation.
- Note any Tableau-specific features in use (LOD expressions, sets, actions, dashboard extensions).

## 2. Requirements & Gap Analysis
- Map each Tableau feature to its closest Power BI equivalent (e.g., LOD expressions → DAX `CALCULATE`/`ALLEXCEPT`, Tableau Sets → DAX/Power Query filters or What-If parameters, dashboard actions → Power BI bookmarks/drill-through).
- Identify features with no direct Power BI equivalent and decide on workarounds or acceptable deviations.
- Confirm licensing (Power BI Pro/Premium) and data connectivity requirements (Import vs. DirectQuery vs. Live Connection).

## 3. Data Layer Migration
- Recreate data connections in Power Query (or dataflows), replicating any Tableau data-source joins/blends.
- Rebuild the data model in Power BI's model view (relationships, cardinality, cross-filter direction) to mirror Tableau's data model/blend logic.
- Migrate calculated fields to DAX measures/calculated columns, validating logic differences (row context vs. Tableau's LOD).

## 4. Visual & Layout Reconstruction
- Rebuild each worksheet as a Power BI visual, choosing the closest native or certified custom visual when Tableau chart types aren't native.
- Recreate dashboard layout, filters (slicers), parameters, and interactivity (drill-through, tooltips, actions/bookmarks).
- Apply consistent theming/branding to match the original report's look and feel.

## 5. Validation & Testing
- Perform side-by-side data validation: compare totals, KPIs, and filtered views between Tableau and Power BI for the same inputs.
- Test performance (query/render times) and refresh schedules.
- Conduct UAT with report stakeholders to confirm functional parity.

## 6. Deployment & Cutover
- Publish to the appropriate Power BI workspace, configure gateway/data refresh, and set up row-level security if the Tableau report had user filters.
- Set up distribution (apps, subscriptions) to replace Tableau's sharing/scheduling.
- Run both reports in parallel briefly, then decommission the Tableau report once sign-off is received.

## 7. Documentation & Handover
- Document the new data model, DAX measures, and any deviations from the original Tableau logic.
- Train report owners/users on Power BI-specific navigation and features.
