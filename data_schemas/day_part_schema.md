# Table Name: DAY-PART

## Table Description
Ad performance aggregated at the day-part and weekday level with campaign/strategy/advertiser/agency/exchange metadata, containing impressions, clicks, CTR, conversions and detailed video completion metrics. It is used to evaluate and optimize time-of-day targeting, pacing, budget allocation and audience segmentation and can support audience generation. | :ui-name:Day Part Performance: :short-name:day_part: |<

## Data Dictionary

### Fields:

- `agg_timestamp` (STRING): UTC-aligned aggregation timestamp (ISO 8601) representing the row's reporting interval; used to group and time-series metrics for analysis
- `advertiser_id` (INTEGER): Numeric identifier linking each row to an advertiser; used as a foreign key to join advertiser master data and aggregate advertiser-level metrics | (relational key)
- `advertiser_name` (STRING): Advertiser display name for reporting and labeling; used to present human-readable advertiser context in dashboards and reports | :lower: |<
- `agency_id` (INTEGER): Numeric identifier for the agency responsible for the advertiser or campaign; used to join agency-level details and roll up performance | (relational key)
- `agency_name` (STRING): Agency display name for reporting and stakeholder attribution; used to label agency-level performance and client-service relationships | :lower: |<
- `campaign_end_date_tz` (STRING): Campaign scheduled end date/time (timezone-aware) indicating when campaign delivery should stop; used for filtering active vs ended campaigns and campaign lifecycle reporting
- `campaign_frequency_amount` (INTEGER): Numeric frequency cap value indicating how many times the targeting rule allows an action in the campaign's frequency interval; used for pacing and cap calculations
- `campaign_frequency_interval` (STRING): Unit for campaign frequency (e.g., hour, day) that pairs with frequency amount to define the cap window; small set of categorical values used for frequency logic | :lower: :all-unique-vals: |<
- `campaign_frequency_optimization` (INTEGER): Numeric flag/setting for campaign-level frequency optimization behavior; used to understand if/what optimization is applied when delivering impressions
- `campaign_frequency_type` (STRING): Text label describing the campaign's frequency enforcement type (e.g., asap); used to interpret how frequency caps are applied | :lower: |<
- `campaign_goal_category` (FLOAT): Campaign goal category code (currently empty in this dataset); reserved for classifying campaign objectives where populated
- `campaign_goal_type` (STRING): High-level campaign objective metric type (e.g., ctr, conversions) used to interpret goal_value and optimization targets; small categorical set for business KPIs | :lower: :all-unique-vals: |<
- `campaign_goal_value` (FLOAT): Numeric value associated with the campaign goal (e.g., target CTR or goal amount); used to evaluate performance vs objectives and optimization targets
- `campaign_id` (INTEGER): Numeric campaign identifier used to link rows to campaign-level metadata and aggregate campaign performance | (relational key)
- `campaign_impression_cap_amount` (INTEGER): Total impression cap applied to the campaign (numeric); used to limit delivery and compute remaining budgeted impressions
- `campaign_merit_pixel_id` (FLOAT): Identifier for the campaign's merit/conversion pixel (often null); used to map conversion tracking pixels to campaigns when available | (relational key)
- `campaign_name` (STRING): Human-readable campaign name used in reports and dashboards to identify the campaign; helpful for business context and filtering | :lower: |<
- `campaign_pc_window_minutes` (FLOAT): Post-click attribution lookback window in minutes (when present); used to calculate post-click conversions and attribution windows
- `campaign_pv_pct` (INTEGER): Percentage parameter related to post-view attribution or delivery (integer); used in attribution or delivery logic when applicable
- `campaign_pv_window_minutes` (FLOAT): Post-view attribution lookback window in minutes (when present); used to calculate post-view conversions and attribution windows
- `campaign_start_date_tz` (STRING): Campaign scheduled start date/time (timezone-aware); used to filter for in-flight campaigns and establish campaign reporting windows
- `campaign_status` (BOOLEAN): Boolean flag indicating whether the campaign is active (true) or inactive/paused (false); used to quickly filter current delivery vs stopped campaigns
- `campaign_total_impression_budget` (INTEGER): Total impression budget allocated to the campaign; used for pacing, forecasting and budget utilization reporting
- `day_part_id` (INTEGER): Numeric identifier for the day-part/time bucket corresponding to this row; used to join to day-part reference and roll up time-of-day performance | (relational key)
- `day_part_name` (STRING): Named day-part/time window (e.g., Night (7pm-11pm)) used to attribute performance to specific time-of-day segments; small set of reference buckets for scheduling analysis | :lower: :space-to-hyphen: :all-unique-vals: |<
- `exchange_id` (INTEGER): Numeric identifier for the ad exchange supplying the inventory; used to join exchange reference data and analyze exchange-level delivery | (relational key)
- `exchange_name` (STRING): Exchange or supply partner display name (e.g., PubMatic, OpenX) used for supply-source reporting and troubleshooting; consistent categorical values for exchange-level analysis | :lower: |<
- `organization_id` (INTEGER): Numeric identifier for the owning organization (single value in this dataset); used for top-level tenancy or account-level joins | (relational key)
- `organization_name` (STRING): Organization or account name used for labeling and top-level reporting; single consistent value across rows in this dataset | :lower: |<
- `strategy_end_date_raw` (STRING): Raw strategy-level end date/time field (may be null) indicating when the strategy was scheduled to finish; useful for matching strategy lifecycle when present
- `strategy_frequency_amount` (INTEGER): Frequency cap amount defined at the strategy level; used for strategy pacing and delivery constraints
- `strategy_frequency_optimization` (BOOLEAN): Boolean indicator if frequency optimization is enabled for the strategy; used to determine whether the strategy actively manages frequency delivery
- `strategy_goal_type` (STRING): Strategy-level goal metric type (categorical) that defines what the strategy is optimizing toward; used to interpret strategy_goal_value and performance evaluation | :lower: :all-unique-vals: |<
- `strategy_goal_value` (FLOAT): Numeric target or threshold for the strategy's goal metric; used to measure how close delivery comes to the strategy objective
- `strategy_id` (INTEGER): Numeric identifier for the strategy (line-item / targeting configuration); used to join strategy metadata and aggregate strategy-level performance | (relational key)
- `strategy_impression_pacing_amount` (FLOAT): Configured impression pacing amount at the strategy level (often null); used for pacing delivery over the chosen pacing interval when populated
- `strategy_impression_pacing_interval` (STRING): Unit for impression pacing (e.g., day) used to interpret the pacing amount and schedule delivery | :lower: |<
- `strategy_impression_pacing_type` (STRING): Type of impression pacing used by the strategy (categorical); small set of values describing pacing behavior | :lower: :all-unique-vals: |<
- `strategy_media_type` (STRING): Media format targeted by the strategy (e.g., display, video); used to segment metrics and apply media-specific KPIs and reporting | :lower: :all-unique-vals: |<
- `strategy_name` (STRING): Strategy (line item) display name used for human-readable reporting and to connect line item performance to campaign structure | :lower: |<
- `strategy_pacing_amount` (FLOAT): Numeric pacing amount for the strategy (used with pacing_type) to control delivery rate; used in forecasting and pacing logic
- `strategy_pacing_type` (STRING): Pacing mode or cadence (e.g., asap) that determines how the strategy spends its budget/pacing amount; categorical value used in delivery logic | :lower: |<
- `strategy_roi_target` (FLOAT): Reserved field for a strategy ROI or efficiency target (all null in this dataset); used to store ROI targets when supplied
- `strategy_run_on_display` (BOOLEAN): Boolean flag indicating whether the strategy is allowed to run on display inventory; used for channel eligibility filtering
- `strategy_run_on_mobile` (BOOLEAN): Boolean flag indicating whether the strategy is allowed to run on mobile inventory; used for channel eligibility filtering
- `strategy_run_on_streaming` (BOOLEAN): Boolean flag indicating whether the strategy is allowed to run on streaming inventory; used for channel eligibility filtering
- `strategy_status` (BOOLEAN): Boolean indicator of whether the strategy is active (true) or paused/disabled (false); used to filter active line items for analysis
- `strategy_supply_type` (STRING): Supply classification for the strategy (e.g., RTB); used to understand delivery method and partner routing | :upper: |<
- `strategy_type` (STRING): Strategy classification or currency/format code (single value in dataset); used to group similar strategy types for reporting | :upper: |<
- `week_day_id` (INTEGER): Integer code for the day of week (reference mapping to week_day_name); used to group and filter performance by weekday | :all-unique-vals: |<
- `week_day_name` (STRING): Weekday name (e.g., Monday) for day-of-week segmentation and reporting; small stable set of categorical values used for time-based analysis | :lower: :all-unique-vals: |<
- `clicks` (INTEGER): Count of recorded clicks in the row's aggregation window; used to compute CTR, cost-per-click and other engagement metrics (sparse / many nulls where not applicable)
- `ctc` (FLOAT): Click-through contribution or cost-to-click metric (context-specific) used for efficiency analysis; often null or sparse depending on reporting scope
- `ctr` (FLOAT): Click-through rate (clicks / impressions) used as a primary engagement KPI; sparse across rows where impressions or clicks are missing
- `impressions` (INTEGER): Number of ad impressions served in the aggregation window; core delivery metric used for reach, frequency and CPM calculations
- `post_click_conversions` (INTEGER): Conversions attributed within the post-click lookback window; used for direct response attribution and conversion rate calculations
- `post_view_conversions` (INTEGER): Conversions attributed within the post-view lookback window; used for view-through attribution and incremental measurement
- `total_conversions` (INTEGER): Aggregate conversions (post-click + post-view or total reported conversions) used to evaluate campaign effectiveness
- `video_complete` (INTEGER): Count of completed video views; used to measure creative completion performance for video inventory (sparse where non-video)
- `video_complete_rate` (FLOAT): Proportion of video starts that reached completion (video completions / video starts); key KPI for video engagement, often null for non-video strategies
- `video_first_quartile` (INTEGER): Count of first-quartile video views used to analyze early view engagement for video creatives
- `video_midpoint` (INTEGER): Count of midpoint (50%) video views used to measure mid-play engagement for video creatives
- `video_start` (INTEGER): Count of video starts (initial plays) used as the denominator for video completion and quartile rates
- `video_third_quartile` (INTEGER): Count of third-quartile (75%) video views used to evaluate later-stage engagement in video playback

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

