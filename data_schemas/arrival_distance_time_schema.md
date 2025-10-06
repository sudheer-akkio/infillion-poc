# Table Name: ARRIVAL-DISTANCE-TIME

## Table Description
This table contains campaign- and creative-level visit attribution records that link advertising metadata (advertiser, agency, campaign, creative, strategy) to measured visitor behaviors such as distance_traveled, average dwell time, time elapsed, and projected/verified visits by visit_date. It is used to measure and optimize in‑store visit attribution and campaign performance and can be used to build behavioral audiences for targeting and segmentation. | :ui-name:Arrival Distance & Time: :short-name:arr_dist_time: |<

## Data Dictionary

### Fields:

- `advertiser_id` (INTEGER): Numeric identifier for the advertiser used in the dataset. Business purpose: join and roll up metrics to the advertiser level for reporting and billing. Relational note: acts as a foreign key to advertiser master/reference tables.
- `advertiser_name` (STRING): Human-readable advertiser name. Business purpose: display label for reporting and dashboards and to validate advertiser_id.
- `agency_id` (INTEGER): Numeric identifier for the agency handling the advertiser or campaign. Business purpose: link performance to agency for billing and agency-level analytics. Relational note: foreign key to agency reference.
- `agency_name` (STRING): Agency display name associated with the campaign. Business purpose: present agency ownership in reports and reconcile agency-level activity.
- `avg_dwell_time_min` (FLOAT): Average dwell time in minutes per visit/event. Business purpose: measures how long visitors spent on-site or near a location — useful for engagement metrics and quality assessment.
- `campaign_id` (INTEGER): Numeric identifier for the campaign. Business purpose: primary key to group creatives and measure campaign-level performance. Relational note: foreign key to campaign reference or metadata.
- `campaign_name` (STRING): Readable campaign title used for reporting and selection in UI. Business purpose: identify marketing programs and match to budgets/briefs.
- `creative_id` (INTEGER): Numeric identifier for an individual creative (ad/asset). Business purpose: link metrics to specific creatives for performance comparison and optimization. Relational note: acts as foreign key to creative metadata.
- `creative_name` (STRING): Descriptive name of the creative or ad unit. Business purpose: human-friendly label to identify creative formats, sizes, or targeting characteristics in reports.
- `distance_traveled` (FLOAT): Distance traveled (units implied by system) associated with the visit or user movement. Business purpose: measure reach, travel behavior, or attribution radius for visit qualification; may require unit clarification in downstream use.
- `frequency` (STRING): Reported frequency metric (e.g., exposures per user). Business purpose: indicates how many times an audience or device saw an ad.
- `multiplier` (FLOAT): Numeric multiplier or weighting applied to the row (e.g., scaling factor or adjustment). Business purpose: apply weighting when projecting or aggregating metrics.
- `organization_id` (INTEGER): Identifier for the owning organization (top-level account). Business purpose: anchor dataset to a single organization for access control and enterprise reporting. Relational note: acts as a foreign key to organization master.
- `organization_name` (STRING): Name of the owning organization for the dataset. Business purpose: display and filter at the enterprise/account level.
- `projected_visits` (INTEGER): Projected number of visits attributed to the creative/campaign for the row. Business purpose: planning and forecasting visit volume for campaign performance expectations.
- `projected_unique_visits` (INTEGER): Projected count of unique visitors for the creative/campaign. Business purpose: estimate unique reach for planning and ROI calculations.
- `time_elapsed` (STRING): Time elapsed metric (e.g., seconds) related to the event. Business purpose: provides session or event duration data.
- `strategy_id` (INTEGER): Numeric identifier for the targeting or media strategy applied. Business purpose: group lines and creatives by strategy for optimization and reporting. Relational note: acts as foreign key to strategy metadata.
- `strategy_name` (STRING): Name or description of the media/targeting strategy. Business purpose: explain targeting/tactic used (e.g., tier, audience) for analysis and creative assignment.
- `verified_unique_visits` (INTEGER): Count of verified (quality-checked) unique visits for the row. Business purpose: primary quality metric for unique conversions or store visits after verification.
- `verified_visits` (INTEGER): Count of verified visits (total visit events) after validation. Business purpose: used for billing, attribution and performance reporting when only verified visits are billable.
- `visit_date` (STRING): Date of the visit or event (stored as text). Business purpose: time-series analyses, daily reporting and trend comparisons; should be parsed to a date type for time-based calculations.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

