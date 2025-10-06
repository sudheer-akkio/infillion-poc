# Table Name: ALL-DIMENSIONS-AND-METRICS

## Table Description
Aggregated advertising performance data containing impressions, clicks, conversions, revenue, viewability and video metrics broken down by timestamp, campaign, creative, publisher/app, device, geo, agency and other dimensions; used for campaign reporting, attribution, optimization and audience segmentation. | :ui-name:All Dimensions and Metrics (Ad Performance): :short-name:all_dims_metrics: |<

## Data Dictionary

### Fields:

- `agg_timestamp` (STRING): Aggregation date for the row (date the metrics were rolled up). Used to group and filter reporting by aggregation period.
- `advertiser_id` (STRING): Unique identifier for the advertiser (relational key to advertiser dimension). Used to join or filter metrics by advertiser.
- `advertiser_name` (STRING): Advertiser display name used in reports and labels; helps identify the advertiser for business reporting. | :lower: |<
- `agency_id` (STRING): Unique identifier for the agency (relational key to agency dimension). Used for agency-level aggregation and joins.
- `agency_name` (STRING): Agency display name used for reporting and attribution. | :lower: |<
- `app_id` (STRING): Identifier for the mobile app (relational key to app/catalog). Used to attribute metrics to specific apps.
- `app_name` (STRING): App display name used in reporting and grouping; helps identify the application where inventory ran. | :lower: |<
- `app_store` (STRING): Source/store type for the app (e.g., app store or in-app indicator). Used to segment inventory by distribution channel. | :lower: |<
- `browser` (STRING): Browser name used to segment web inventory and user agents. Useful for troubleshooting rendering/compatibility. | :lower: |<
- `browser_version` (STRING): Browser version string to further segment by client capabilities. Useful for debugging and compatibility analysis.
- `campaign_id` (STRING): Unique identifier for the campaign (relational key to campaign dimension). Used to join campaign settings and aggregate campaign performance.
- `campaign_name` (STRING): Campaign display name used for reporting and to identify marketing initiatives. | :lower: |<
- `city_code` (STRING): Internal city code used for geographic grouping (relational key to city dimension). Used for location-based reporting and joins.
- `city_name` (STRING): Readable city name for geographic reporting and segmentation. | :lower: |<
- `content_title` (STRING): Title of the content or placement where the ad appeared. Used for contextual reporting and content-level analysis. | :lower: |<
- `creative_id` (STRING): Unique identifier for the creative (relational key to creative/media asset). Used to attribute impressions/clicks to specific creatives.
- `creative_name` (STRING): Creative display name used in creative-level reporting and optimization. | :lower: |<
- `creative_size` (STRING): Creative dimension (e.g., 300x250) that identifies ad format/size. Used to segment performance by ad format.
- `device_make` (STRING): Device manufacturer (e.g., Samsung, Apple) for device-level segmentation. Useful for hardware-specific analysis. | :lower: |<
- `device_model` (STRING): Device model name used to segment by specific device hardware. Helpful for debugging and audience insights. | :lower: |<
- `exchange_id` (STRING): Identifier for the ad exchange or supply source (relational key). Used to join exchange metadata and filter by exchange.
- `exchange_name` (STRING): Name of the ad exchange or supply partner used to segment inventory and analyze partner performance. | :lower: |<
- `inventory_browser_type` (STRING): Type of inventory by browser context (e.g., Web, In-App). Used to segment inventory by delivery environment. | :lower: |<
- `inventory_market_type` (STRING): Market classification for inventory (e.g., Exchange, Direct). Used to analyze marketplace vs direct-sold inventory. | :lower: |<
- `metro_code` (INTEGER): Metropolitan area code (geographic reference) used to group markets (DMA/metropolitan areas). Useful for geo-targeting and lookup. | :all-unique-vals: |<
- `metro_name` (STRING): Human-readable metropolitan area name used for market-level reporting and segmentation. | :lower: |<
- `openrtb_device_type` (STRING): OpenRTB device type classification (e.g., Phone, Tablet, Personal Computer). Used to segment by device category for bidding and reporting. | :lower: |<
- `organization_id` (INTEGER): Identifier for the owning organization or account (relational key). Used for multi-organization filtering and joins.
- `organization_name` (STRING): Organization display name for account-level reporting and access control. | :lower: |<
- `os_type` (STRING): Operating system family (e.g., Android, iOS, Windows) used to segment inventory and target by OS. | :lower: |<
- `os_version` (STRING): Operating system version string to further segment by OS release. Used for compatibility or audience analysis.
- `postal_code_name` (STRING): Postal code label used for fine-grained geographic targeting (e.g., ZIP or postal code). Serves as a geographic lookup/reference. | :lower: :all-unique-vals: |<
- `publisher_id` (STRING): Identifier for the publisher or site owner (relational key to publisher dimension). Used to join publisher metadata and aggregate publisher performance.
- `publisher_name` (STRING): Publisher or site owner name used in reporting and publisher-level analysis. | :lower: |<
- `region` (INTEGER): Region code (state/region reference) used to group geographic data (e.g., state FIPS or internal region code). Useful for geographic lookups and aggregation. | :all-unique-vals: |<
- `region_name` (STRING): Readable region or state name for geographic reporting and segmentation. | :lower: |<
- `site_domain` (STRING): Domain of the site where the ad served. Used to identify placements and analyze site-level performance. | :lower: |<
- `strategy_id` (INTEGER): Identifier for the delivery strategy or line item (relational key). Used to map metrics to campaign/strategy configurations.
- `strategy_name` (STRING): Delivery strategy or line item name used for pacing, targeting and optimization reporting. | :lower: |<
- `zip` (STRING): ZIP/postal code value used for geographic aggregation and targeting. Serves as a geographic reference key; stored as string to preserve leading zeros for northeastern US ZIP codes. | :all-unique-vals: |<
- `clicks` (INTEGER): Count of clicks recorded for the row. Used to measure engagement and calculate downstream metrics like CTR and conversions.
- `ctc` (FLOAT): Click-to-conversion metric indicator (business-specific metric). Used in conversion attribution or quality calculations.
- `ctr` (FLOAT): Click-through rate (CTR) used to evaluate ad responsiveness; calculated metric used for performance evaluation.
- `impressions` (INTEGER): Number of ad impressions served. Core volume metric used for reach and CPM calculations.
- `in_view` (INTEGER): Count of impressions measured as viewable (partial viewability). Used to assess viewability performance.
- `in_view_100_percent` (INTEGER): Count of impressions that were 100% viewable. Used for strict viewability assessments and guarantees.
- `measurable` (INTEGER): Count of impressions that were measurable by viewability/measurement vendors. Used to determine valid measurement base.
- `post_click_conversions` (INTEGER): Conversions attributed within the post-click attribution window. Used to measure conversion impact of clicks.
- `post_click_revenue` (FLOAT): Revenue attributed to post-click conversions. Used for revenue and ROI calculations from click-attributed actions.
- `post_view_conversions` (INTEGER): Conversions attributed within the post-view attribution window. Used to measure view-through conversion impact.
- `post_view_revenue` (FLOAT): Revenue attributed to post-view conversions. Used for revenue and ROI calculations from view-attributed actions.
- `total_conversions` (INTEGER): Total conversions (post-click + post-view or aggregated conversion metric). Used as the primary conversion metric for performance.
- `total_revenue` (FLOAT): Total revenue attributed to the row (aggregate revenue from conversion windows). Used for financial performance and ROAS.
- `video_complete` (INTEGER): Count of video impressions that reached completion. Used to evaluate video engagement and completion volume.
- `video_complete_rate` (FLOAT): Rate of video completions relative to eligible plays; used to measure video creative effectiveness.
- `video_complete_rate_impression_based` (FLOAT): Video completion rate computed against impressions (impression-based denominator). Used for alternate completion measurement.
- `video_first_quartile` (INTEGER): Count of viewers reaching the first quartile of a video. Used for video engagement funnel analysis.
- `video_midpoint` (INTEGER): Count of viewers reaching the midpoint (50%) of a video. Used to gauge mid-funnel video engagement.
- `video_start` (INTEGER): Count of video starts (impressions that initiated playback). Used to measure initial engagement with video creatives.
- `video_third_quartile` (INTEGER): Count of viewers reaching the third quartile (75%) of a video. Used to assess deeper video engagement.
- `viewability_rate` (FLOAT): Percentage of impressions that were viewable per measurement standards. Used to measure quality of served inventory.
- `viewability_rate_100_percent` (FLOAT): Percentage of impressions that were 100% viewable. Used for strict viewability reporting and guarantees.
- `kiwi_results_count` (INTEGER): Internal or partner-specific results counter (single-value indicator). Used for internal QA or partner integration checks.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

