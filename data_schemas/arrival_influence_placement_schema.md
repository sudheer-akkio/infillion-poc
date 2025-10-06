# Table Name: ARRIVAL-INFLUENCE-PLACEMENT

## Table Description
Daily placement-level performance records that link advertisers, agencies, campaigns, creatives and strategies to influence placements and report projected vs verified site visits, verified unique visits, average dwell time and multipliers by visit_date. This table is used to evaluate and reconcile placement effectiveness, optimize media delivery and generate audience segments for targeting. | :ui-name:Arrival Influence Placement Metrics: :short-name:arr_infl_placement: |<

## Data Dictionary

### Fields:

- `advertiser_id` (INTEGER): Numeric identifier for the advertiser associated with the row; used to join back to advertiser master data and aggregate metrics by advertiser. Foreign key to advertiser entity.
- `advertiser_name` (STRING): Display name of the advertiser/brand presented in reports; provides human-readable context for advertiser_id and is used in dashboards and client-facing reports. | :lower: |<
- `agency_id` (INTEGER): Numeric identifier for the agency responsible for the campaign; used to join to agency tables and filter performance by agency. Foreign key to agency entity.
- `agency_name` (STRING): Full agency name associated with the media activity; used for reporting, billing reconciliation, and agency-level performance views. | :lower: |<
- `avg_dwell_time_min` (FLOAT): Average time (in minutes) that visitors spent on the placement or creative during the visit; used as an engagement metric to evaluate creative and placement effectiveness.
- `campaign_id` (INTEGER): Identifier for the advertising campaign grouping this activity; used to aggregate budget, goals and performance across creatives and strategies. Foreign key to campaign entity.
- `campaign_name` (STRING): Human-readable campaign title used for reporting and campaign-level analysis; maps to campaign_id and helps stakeholders find campaign context. | :lower: |<
- `creative_id` (INTEGER): Identifier for the specific creative/asset used in the placement; used to link creative metadata and measure creative-level performance. Foreign key to creative entity.
- `creative_name` (STRING): Descriptive name or encoded metadata for the creative (size, format, targeting tags); used to identify specific creatives in performance and QA. | :lower: |<
- `frequency` (STRING): Planned or reported frequency metric (how many times an audience sees the creative); used to measure ad exposure frequency for reach analysis.
- `multiplier` (FLOAT): Scaling factor applied to projections or conversions for the placement (e.g., audience or inventory multiplier); used to adjust projected metrics.
- `organization_id` (INTEGER): Identifier for the parent organization or client account under which activity is tracked; used for account-level segmentation and access control. Foreign key to organization entity.
- `organization_name` (STRING): Name of the client organization or account; used in multi-client reporting and labeling. | :lower: |<
- `influence_placement_name` (STRING): Name or label of the influence placement or site where the creative ran (site, app, section); used to tie performance to specific inventory. | :lower: |<
- `influence_placement_type` (STRING): Type/category of the placement (e.g., site, app, channel) used to group inventory types for analysis. | :lower: |<
- `projected_visits` (INTEGER): Projected total visits (non-unique) expected from the placement or plan; used for forecasting, pacing and goal-setting.
- `projected_unique_visits` (INTEGER): Projected unique visitors expected from the placement or plan; used for reach planning and unique audience forecasting.
- `strategy_id` (INTEGER): Identifier for the targeting or delivery strategy configuration (e.g., line-item/strategy level); used to map to strategy-level settings and reporting. Foreign key to strategy entity.
- `strategy_name` (STRING): Readable name of the strategy or line item used for delivery (often includes tier/format/targeting); used to filter and analyze performance at the strategy level. | :lower: |<
- `verified_unique_visits` (INTEGER): Count of verified unique visits measured (post-verification) for the placement; used to validate projection accuracy and measure real audience reach.
- `verified_visits` (INTEGER): Count of verified total visits measured (post-verification) for the placement; used for reporting actual performance and reconciliation against projections.
- `visit_date` (STRING): Date of the visit or reporting date for the row (YYYY-MM-DD); used for time-series reporting, trend analysis and joins to calendar tables.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

