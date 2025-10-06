# Table Name: ARRIVAL-STANDARD

## Table Description
Row-level records of campaign and creative visit metrics tied to points-of-interest (POIs), containing projected and verified visit counts, average dwell time, visit_date, POI details, and campaign/strategy metadata. The table also captures device attributes (visit_device, visit_model, visit_os) to support attribution, campaign performance measurement, location-level optimization, and audience segmentation for targeting. | :ui-name:Arrival Standard - POI Visit Metrics: :short-name:arrival_std: |<

## Data Dictionary

### Fields:

- `advertiser_id` (INTEGER): Numeric identifier for the advertiser associated with the record. Used to link metrics to the advertiser for reporting and billing. Serves as a foreign key to advertiser master data.
- `advertiser_name` (STRING): Readable name of the advertiser. Business-facing label for reports and dashboards. | :lower: |<
- `agency_id` (INTEGER): Numeric identifier for the agency responsible for the campaign. Used to group and filter performance by agency; acts as a foreign key to agency records.
- `agency_name` (STRING): Readable name of the agency managing the campaign. Used for reporting and client communication. | :lower: |<
- `avg_dwell_time_min` (FLOAT): Average dwell time at the point of interest in minutes. Measures on-site engagement per visit for campaign effectiveness and audience quality.
- `campaign_id` (INTEGER): Numeric identifier for the campaign tied to these metrics. Used to join to campaign-level configuration and budget data; acts as a foreign key.
- `campaign_name` (STRING): Human-readable campaign label. Used in reporting, filtering, and creative attribution. | :lower: |<
- `creative_id` (INTEGER): Numeric identifier for the creative/line item variant. Links records to creative metadata (format, size); acts as a foreign key to creative-level tables.
- `creative_name` (STRING): Descriptive name of the creative or line item. Used to identify ad format/asset in reports. | :lower: |<
- `frequency` (STRING): Measured ad frequency (impressions per user/period). Used to measure ad exposure frequency for reach analysis.
- `multiplier` (FLOAT): Scaling or weighting factor applied to projected metrics (e.g., geographic or audience multiplier). Used to adjust projections or model outputs in calculations.
- `organization_id` (INTEGER): Numeric identifier for the owning organization/account for these campaigns. Used to scope access and aggregate at the organization level; acts as a foreign key.
- `organization_name` (STRING): Readable name of the owning organization/account. Used for top-level reporting and labeling. | :lower: |<
- `poi_address` (STRING): Full postal address of the point of interest (POI). Used to map visits to physical locations and for geospatial analysis. | :lower: |<
- `poi_name` (STRING): Name of the point of interest (store/location). Used to attribute visits to specific business locations and to group location-level performance. | :lower: |<
- `projected_visits` (INTEGER): Modeled or projected total visits to the POI in the measurement window. Used for planning and forecasting campaign reach.
- `projected_unique_visits` (INTEGER): Modeled or projected count of unique visitors expected. Used to estimate reach and avoid double-counting in planning.
- `strategy_id` (INTEGER): Numeric identifier for the targeting/measurement strategy applied to the campaign. Used to join to strategy metadata and settings; acts as a foreign key.
- `strategy_name` (STRING): Descriptive name of the targeting or measurement strategy. Used in analysis to compare approaches (e.g., geo, audience strategy). | :lower: |<
- `visit_date` (STRING): Date of the recorded/attributed visit (string format YYYY-MM-DD). Used to trend performance over time and aggregate by day.
- `visit_device` (STRING): Device category for the visit (e.g., smartphone, tablet). Used to segment performance by device type. | :lower: |<
- `visit_make` (STRING): Device manufacturer name for the visiting device (e.g., Apple, Samsung). Used for device manufacturer-level segmentation and analysis. | :lower: |<
- `visit_model` (STRING): Device model string for the visiting device (e.g., iPhone, SM-A356U). Useful for device-level segmentation and quality checks. | :lower: |<
- `visit_os` (STRING): Operating system name/version for the visiting device (e.g., Android, iOS). Used to segment by platform. | :lower: |<
- `verified_unique_visits` (INTEGER): Count of verified unique visits (deduplicated) attributed to the campaign/POI. Used as a primary effectiveness metric for unique reach.
- `verified_visits` (INTEGER): Count of verified total visits (non-unique) attributed to the campaign/POI. Used as a primary engagement metric for footfall.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

