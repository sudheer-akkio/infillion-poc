# Table Name: ARRIVAL-INFLUENCE-GEO

## Table Description
Daily, geo-level attribution records linking campaigns, strategies and creatives to verified and projected in-person visits, with metrics such as verified_visits, verified_unique_visits, avg_dwell_time_min, multiplier, and influence_city/state. Used to evaluate local campaign performance, optimize creative targeting, and generate audiences for location-based marketing. | :ui-name:Arrival Influence by Geography: :short-name:arrival_influence_geo: |<

## Data Dictionary

### Fields:

- `visit_date` (STRING): Date when the visit was recorded; used as the primary time dimension for daily trend analysis, reporting, and time-based aggregations; serves as the main key for temporal joins.
- `organization_name` (STRING): Name of the organization that owns the measurement dataset; used to group and filter data by company for enterprise-level reporting.
- `organization_id` (INTEGER): Internal numeric identifier for the organization; used as a relational key to join to organization master/reference tables and enforce record ownership.
- `agency_name` (STRING): Name of the agency responsible for the campaign; used for agency-level attribution, billing, and performance comparisons.
- `agency_id` (INTEGER): Numeric identifier for the agency; relational key for joining to agency reference data and aggregating metrics by agency.
- `advertiser_name` (STRING): Name of the advertiser/brand for whom the campaign ran; used to group and report performance at the advertiser level.
- `advertiser_id` (INTEGER): Numeric identifier for the advertiser; relational key to advertiser master data for cross-dataset joins and reporting.
- `campaign_name` (STRING): Descriptive campaign name that identifies the specific marketing effort; used for campaign-level filtering and reporting.
- `campaign_id` (INTEGER): Numeric identifier for the campaign; relational mapping key for joining to campaign metadata and rolling up campaign-level metrics.
- `strategy_name` (STRING): Name of the strategy or line item within the campaign (e.g., targeting/placement tier); used to analyze performance by tactic and to map to strategy-level settings.
- `strategy_id` (INTEGER): Numeric identifier for the strategy/line item; relational key to strategy-level configuration and performance records.
- `creative_name` (STRING): Human-readable name of the creative/ad asset; used to attribute visits and engagement to specific creatives for A/B and creative-level analysis.
- `creative_id` (INTEGER): Numeric identifier for the creative asset; relational key for joining to creative metadata and tracking asset-level performance.
- `influence_city` (STRING): City associated with the influence attribution (where influenced visits occurred); used for city-level geographic analysis and geo-targeting validation.
- `influence_state` (STRING): State associated with the influence attribution (state/region for geo-level reporting); used for state-level aggregation and geographic segmentation. | :upper: :all-unique-vals: |<
- `verified_visits` (INTEGER): Count of verified (attributed) visits for the row's date, campaign/creative and geo; used as the primary measured metric for reach and footprint analysis.
- `verified_unique_visits` (INTEGER): Count of deduplicated unique visitors (verified) for the row's grouping; used to measure unique reach and avoid double-counting.
- `avg_dwell_time_min` (FLOAT): Average dwell time per visit in minutes for the row's grouping; used to assess engagement quality of influenced traffic.
- `frequency` (STRING): Measured frequency metric for the grouping (how often users were exposed); indicates ad exposure frequency for reach analysis.
- `multiplier` (FLOAT): Scaling or weighting factor applied to measured counts to produce projected values; used to adjust raw verification counts to estimated totals.
- `projected_visits` (INTEGER): Visits after applying multiplier/weighting (projected or scaled visits); used for forecasting and reported reach metrics when scaling measured counts.
- `projected_unique_visits` (INTEGER): Projected deduplicated unique visitors after applying weighting; used for reporting estimated unique reach and planning.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

