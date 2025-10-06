# Table Name: PERFORMANCE

## Table Description
Aggregated campaign- and creative-level advertising performance data containing impressions, clicks, CTR/CTC, conversions and revenue, viewability and video metrics, plus campaign/strategy/creative/advertiser/agency identifiers and timestamps for reporting, billing and optimization of digital campaigns. | :ui-name:Campaign Performance: :short-name:perf: |<

## Data Dictionary

### Fields:

- `advertiser_id` (INTEGER): Unique identifier for the advertiser associated with the row; used to group performance by advertiser. Business purpose: link performance metrics to the advertiser record (FK to advertiser master).
- `advertiser_name` (STRING): Advertiser display name for reporting and user-friendly labels. Business purpose: readable identifier for dashboards and reports. | :lower: |<
- `agency_id` (INTEGER): Identifier for the agency managing the advertiser or campaign. Business purpose: relate performance to agency records for billing/ownership (FK to agency master).
- `agency_name` (STRING): Agency display name used for reporting and account ownership. Business purpose: show which agency manages the account or campaign. | :lower: |<
- `agg_timestamp` (STRING): Timestamp representing the aggregation period or report capture time. Business purpose: indicates the specific time bucket for the row's metrics.
- `campaign_conversion_type` (STRING): Primary conversion attribution type configured for the campaign (e.g., 'variable', 'click', 'view'). Business purpose: determines how conversions are attributed in reported metrics. | :lower: |<
- `campaign_end_date` (STRING): Campaign scheduled end date (display timezone). Business purpose: used to filter active vs ended campaigns and to compute pacing or time remaining.
- `campaign_end_date_tz` (STRING): Campaign end date with explicit timezone/offset. Business purpose: ensures accurate interpretation of campaign end relative to local time.
- `campaign_frequency_amount` (INTEGER): Numeric cap amount used for campaign frequency targeting (e.g., number of impressions). Business purpose: controls how often the same user may see ads within the configured interval.
- `campaign_frequency_interval` (STRING): Time interval unit for campaign frequency caps (e.g., 'hour', 'day'). Business purpose: defines the window over which the frequency_amount applies. | :lower: |<
- `campaign_frequency_optimization` (INTEGER): Flag/setting indicating optimization mode for campaign frequency (numeric code). Business purpose: internal configuration used to control frequency-based optimization behavior.
- `campaign_frequency_type` (STRING): Type of frequency enforcement (e.g., 'asap' / other modes). Business purpose: describes how frequency caps are applied to serving logic. | :lower: |<
- `campaign_goal_category` (FLOAT): High-level category for the campaign's goal. Business purpose: group campaigns by objective category for reporting/analysis.
- `campaign_goal_type` (STRING): Specific goal metric the campaign is optimizing towards (e.g., 'ctr', 'cpm', 'conversions'). Business purpose: informs optimization and KPI evaluation. | :lower: |<
- `campaign_goal_value` (FLOAT): Target numeric value for the campaign goal (e.g., target CTR). Business purpose: used to evaluate performance against the campaign objective.
- `campaign_id` (INTEGER): Unique campaign identifier. Business purpose: primary key for campaign-level mapping and joins to campaign metadata (FK to campaign master).
- `campaign_impression_cap_amount` (INTEGER): Impression cap amount set at campaign level (max impressions). Business purpose: limits total impressions delivered for a campaign.
- `campaign_impression_cap_type` (STRING): Mode/type of impression cap at campaign level (e.g., 'no-limit', numeric limit). Business purpose: clarifies how the impression cap amount is applied. | :lower: |<
- `campaign_initial_start_date_tz` (STRING): Campaign initial start date with timezone (original start). Business purpose: reference for campaign lifecycle and performance baselining.
- `campaign_name` (STRING): Human-readable campaign name used in reports. Business purpose: display label for campaign-level reporting and filtering. | :lower: |<
- `campaign_pc_window_minutes` (FLOAT): Post-click attribution window in minutes for the campaign. Business purpose: determines how long conversions are attributed to a click.
- `campaign_political` (BOOLEAN): Boolean flag indicating if a campaign is political in nature. Business purpose: regulatory/eligibility handling and special reporting.
- `campaign_pv_pct` (INTEGER): Post-view percentage or weighting used by campaign (numeric code). Business purpose: internal weighting used in attribution between post-view vs post-click.
- `campaign_pv_window_minutes` (FLOAT): Post-view attribution window in minutes for the campaign. Business purpose: determines how long conversions are attributed to views.
- `campaign_start_date_tz` (STRING): Campaign scheduled start date with timezone. Business purpose: used to compute active status and pacing.
- `campaign_status` (BOOLEAN): Boolean indicating whether the campaign is active (True) or not. Business purpose: filter active campaigns for serving and reporting.
- `clicks` (INTEGER): Count of clicks attributed to the row's creative/campaign/time bucket. Business purpose: engagement metric for performance and billing.
- `creative_id` (INTEGER): Identifier for the creative (ad) asset. Business purpose: link performance to the specific creative for creative-level analysis (FK to creative/master).
- `creative_name` (STRING): Display name of the creative asset. Business purpose: human-readable label for creative-level reporting and optimization. | :lower: |<
- `creative_rich_media` (BOOLEAN): Boolean flag indicating whether the creative is rich media. Business purpose: segment metrics by creative type for creative analysis and pricing.
- `creative_size` (STRING): Creative dimensions or size label (e.g., '320x480'). Business purpose: used to group creatives and analyze performance by ad size.
- `creative_tpas_placement_id` (STRING): Third-party ad server (TPAS) placement identifier for the creative. Business purpose: map to external placement records for reporting and reconciliation.
- `creative_tpas_placement_name` (STRING): Third-party placement name for the creative. Business purpose: human-friendly label for external placement mapping and reconciliation. | :lower: |<
- `ctc` (FLOAT): Cost-per-click (or related click-based cost metric) depending on configuration. Business purpose: used for cost analysis and CPA calculations.
- `ctr` (FLOAT): Click-through rate (clicks / impressions) for the row. Business purpose: measures engagement efficiency of the creative/campaign.
- `impressions` (INTEGER): Count of impressions served in the row's aggregation. Business purpose: primary delivery metric used for reach, CPM, and pacing.
- `in_view` (FLOAT): Number (or percent/count) of impressions considered 'in view' based on viewability measurement. Business purpose: assess viewable impressions for viewability-based billing and reporting.
- `in_view_100_percent` (FLOAT): Count of impressions that were 100% in-view. Business purpose: used to track fully viewed impressions for specific billing or KPIs.
- `measurable` (FLOAT): Count or indicator of impressions that were measurable by viewability or measurement partners. Business purpose: used to determine denominator for viewability and other measured metrics.
- `organization_id` (INTEGER): Identifier for the owning organization (top-level account). Business purpose: group advertisers and campaigns under a single organization for billing/permissions (FK).
- `organization_name` (STRING): Organization display name used across accounts. Business purpose: top-level label for reporting and access control. | :lower: |<
- `post_click_conversions` (INTEGER): Number of conversions attributed to a post-click window for the row. Business purpose: measures conversion performance attributable to clicks.
- `post_click_revenue` (FLOAT): Revenue attributed to post-click conversions. Business purpose: monetization metric for ROI and revenue analysis.
- `post_view_conversions` (INTEGER): Number of conversions attributed to a post-view window. Business purpose: measures view-attributed conversions for campaign evaluation.
- `post_view_revenue` (FLOAT): Revenue attributed to post-view conversions. Business purpose: helps quantify value from view-attributed conversions.
- `revenue` (FLOAT): Revenue attributed to the row (may represent intermediate revenue calculation). Business purpose: revenue metric for the row; used alongside total_revenue for financial reporting.
- `strategy_end_date_raw` (STRING): Raw strategy-level end date field (may be null). Business purpose: indicates when the bidding/strategy was scheduled to end.
- `strategy_frequency_amount` (INTEGER): Frequency cap amount configured at strategy level. Business purpose: controls delivery frequency at strategy granularity.
- `strategy_frequency_interval` (STRING): Interval unit for strategy-level frequency caps (e.g., 'hour', 'day'). Business purpose: defines the window for frequency enforcement at strategy level. | :lower: |<
- `strategy_frequency_optimization` (BOOLEAN): Boolean or flag indicating whether strategy-level frequency optimization is enabled. Business purpose: affects how the strategy enforces frequency in serving decisions.
- `strategy_frequency_type` (STRING): Type of frequency enforcement for the strategy (mode). Business purpose: clarifies enforcement behavior (e.g., strict vs soft). | :lower: |<
- `strategy_goal_type` (STRING): Goal metric the strategy is optimizing for (e.g., 'ctr', 'cpa', 'reach'). Business purpose: drives bidding and optimization logic for the strategy. | :lower: |<
- `strategy_goal_value` (FLOAT): Numeric target for the strategy's goal (e.g., target ROI or CTR). Business purpose: used to evaluate strategy performance and guide automated bidding.
- `strategy_id` (INTEGER): Unique identifier for the strategy (bidding/pacing configuration). Business purpose: join to strategy metadata and aggregate strategy-level performance (FK to strategy master).
- `strategy_impression_pacing_amount` (FLOAT): Impression pacing target amount for the strategy. Business purpose: used to pace delivery (e.g., impressions per interval) when pacing is configured.
- `strategy_impression_pacing_interval` (STRING): Interval unit for strategy impression pacing (e.g., 'day'). Business purpose: defines the time bucket used for impression pacing. | :lower: |<
- `strategy_impression_pacing_type` (STRING): Type of impression pacing applied (mode). Business purpose: indicates whether pacing is strict, even, front-loaded, etc. | :lower: |<
- `strategy_media_type` (STRING): Media channel targeted by the strategy (e.g., 'DISPLAY', 'VIDEO'). Business purpose: segment performance and apply media-specific logic.
- `strategy_name` (STRING): Human-readable name of the strategy used for reporting. Business purpose: label for strategy-level performance analysis and configuration tracking. | :lower: |<
- `strategy_pacing_optimization_type` (FLOAT): Pacing optimization numeric field (likely unused here). Business purpose: configuration for pacing algorithm; often null in this dataset.
- `strategy_pacing_type` (STRING): High-level pacing mode for the strategy. Business purpose: identifies how budget/impressions are paced across the campaign timeline. | :lower: |<
- `strategy_roi_target` (FLOAT): ROI target value for the strategy. Business purpose: guides bid adjustments to meet an ROI goal.
- `strategy_run_on_display` (BOOLEAN): Boolean flag indicating if the strategy runs on display inventory. Business purpose: shows whether strategy includes display placements.
- `strategy_run_on_mobile` (BOOLEAN): Boolean flag indicating if the strategy targets mobile inventory. Business purpose: used for device-level targeting and reporting.
- `strategy_run_on_streaming` (BOOLEAN): Boolean flag indicating if the strategy includes streaming inventory (connected TV, streaming). Business purpose: separates streaming delivery for measurement and billing.
- `strategy_start_date_raw` (STRING): Raw strategy-level start date (may be null). Business purpose: indicates when strategy began for timeline and pacing calculations.
- `strategy_status` (BOOLEAN): Boolean indicating whether the strategy is active. Business purpose: filter active vs paused/ended strategies for serving and reporting.
- `strategy_type` (STRING): Type/classification of the strategy (single category in sample). Business purpose: helps group strategies by operational type. | :lower: |<
- `total_conversions` (INTEGER): Total number of conversions attributed to the row (sum across attribution windows). Business purpose: primary conversion metric for performance and ROI.
- `total_revenue` (FLOAT): Total revenue attributed to the row (sum of revenue signals). Business purpose: used for ROI, LTV, and billing reconciliation.
- `tpa_conversions` (INTEGER): Third-party attribution conversions field (appears unused). Business purpose: placeholder for TPAs; not populated in this dataset.
- `uniques` (INTEGER): Unique user count (unique identifiers) for the row's impressions. Business purpose: measures reach distinct users for reach/frequency analysis.
- `video_complete` (INTEGER): Count of video completions for video creatives. Business purpose: video performance metric to track full views.
- `video_complete_rate` (FLOAT): Rate (percentage) of video completions out of starts or impressions. Business purpose: KPI for video engagement.
- `video_complete_rate_impression_based` (FLOAT): Video completion rate calculated relative to impressions (impression-based). Business purpose: alternate KPI for completion effectiveness vs impressions.
- `video_first_quartile` (INTEGER): Count of first-quartile video completions. Business purpose: video engagement funnel tracking.
- `video_midpoint` (INTEGER): Count of midpoint (50%) video completions. Business purpose: measures mid-funnel video engagement.
- `video_start` (INTEGER): Count of video starts (ad play initiations). Business purpose: baseline video engagement metric.
- `video_third_quartile` (INTEGER): Count of third-quartile (75%) video completions. Business purpose: advanced video engagement tracking.
- `viewability_rate` (FLOAT): Percentage of impressions that were viewable according to measurement standards. Business purpose: used for viewability reporting and viewable-based billing.
- `viewability_rate_100_percent` (FLOAT): Indicator or metric showing 100% viewability rate (specialized measurement). Business purpose: used in strict viewability reporting or SLA checks.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

