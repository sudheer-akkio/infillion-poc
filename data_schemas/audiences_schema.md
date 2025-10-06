# Table Name: AUDIENCES

## Table Description
Daily ad delivery and spend dataset broken down by organization, agency, advertiser, campaign, strategy, inventory, vendor and audience segment, containing impressions, clicks, video-start/quarter/completion metrics, conversion counts, and detailed cost/fee/spend fields. Used for campaign performance reporting, billing reconciliation, and audience generation/segmentation and optimization. | :ui-name:Audience delivery & spend metrics: :short-name:audiences: |<

## Data Dictionary

### Fields:

- `mm_date` (STRING): Measurement date for the row (YYYY-MM-DD). | Used to track metrics and costs by day for reporting and time-series analysis; serves as the primary time dimension for aggregations.
- `organization_id` (INTEGER): Internal organization identifier (foreign key). | Maps every row to a single parent organization for billing and governance. Relational mapping: organization-level key.
- `organization_name` (STRING): Organization display name. | Human-readable name of the organization for reports and dashboards. | :lower: |<
- `agency_id` (INTEGER): Agency identifier (foreign key). | Links rows to the agency responsible for the campaign/strategy for attribution and reporting. Relational mapping: agency key.
- `agency_name` (STRING): Agency display name. | Human-friendly agency label used in client deliverables and filters. | :lower: |<
- `advertiser_id` (INTEGER): Advertiser identifier (foreign key). | Maps each row to the advertiser (brand) paying for the campaign; used for billing and segmentation. Relational mapping: advertiser key.
- `advertiser_name` (STRING): Advertiser display name. | Human-readable advertiser name for reporting and segmentation. | :lower: |<
- `campaign_id` (INTEGER): Campaign identifier (foreign key). | Associates metrics and costs with a specific campaign for performance analysis and budget reconciliation. Relational mapping: campaign key.
- `campaign_name` (STRING): Campaign display name. | Descriptive campaign label used in dashboards, client reports and budget tracking. | :lower: |<
- `total_budget_usd` (FLOAT): Total budget allocated to the campaign in USD. | Used for pacing, budget remaining calculations and campaign-level ROI.
- `strategy_id` (INTEGER): Strategy / line-item identifier (foreign key). | Identifies the specific strategy or line item that delivered the inventory; key to link to targeting and bidding rules. Relational mapping: strategy key.
- `strategy_name` (STRING): Strategy / line-item descriptive name. | Human-readable line-item or tactic label used to filter and explain performance differences across strategies. | :lower: |<
- `strategy_goal_type` (STRING): Primary optimization goal for the strategy (e.g., ctr). | Explains the objective guiding bidding/measurement (used to interpret KPIs and success metrics). | :lower: :all-unique-vals: |<
- `device_type` (STRING): Device category (e.g., mobile, desktop). | Used to segment performance, apply device-specific targeting and billing rules. | :lower: :all-unique-vals: |<
- `environment_type` (STRING): Execution environment (e.g., in-app vs browser). | Indicates where the ad was served to evaluate environment-specific performance and policies. | :lower: :all-unique-vals: |<
- `media_type` (STRING): Media channel type (e.g., display, video). | Classifies creative/inventory type for reporting, attribution and cost grouping. | :lower: :all-unique-vals: |<
- `form_factor` (STRING): Device form factor (e.g., Smartphone, Feature Phone). | Enables finer segmentation by device form factor for creative and targeting optimizations. | :lower: :all-unique-vals: |<
- `inventory_id` (INTEGER): Inventory placement identifier (foreign key). | Maps rows to a specific inventory package or placement used for delivery and reconciliation. Relational mapping: inventory key.
- `video_placement` (STRING): Video placement descriptor (where video ad appeared). | Describes the video-specific placement for measuring video completion and viewability. | :lower: :all-unique-vals: |<
- `video_skippability` (BOOLEAN): Whether the video ad was skippable (True/False). | Important for CPM/cost models and interpreting completion metrics; affects billing and expected viewability.
- `deal_id` (INTEGER): Deal identifier (private marketplace/guaranteed deal) (foreign key). | Links to contract-level deals for preferential pricing and reporting. Relational mapping: deal key.
- `deal_name` (STRING): Deal descriptive name (often empty). | Human-readable deal label when available for contract-level reconciliation.
- `vendor_type` (STRING): Type of vendor/service (e.g., contextual, measurement). | Categorizes the role of the vendor to attribute costs and results to service types. | :lower: :all-unique-vals: |<
- `vendor_id` (INTEGER): Vendor identifier (foreign key). | Links costs/flags to a particular third-party vendor for fee allocation and vendor-level reporting. Relational mapping: vendor key.
- `vendor_name` (STRING): Vendor display name. | Vendor label used for cost breakout, partner reporting and troubleshooting. | :lower: |<
- `parent_vendor_name` (STRING): Parent vendor or vendor group name. | Higher-level vendor grouping used to roll up vendor costs and simplify partner reporting. | :lower: |<
- `segment_id` (INTEGER): Targeting segment identifier (foreign key). | Maps the row to a specific audience or measurement segment used for targeting or exclusions. Relational mapping: segment key.
- `segment_name` (STRING): Audience/segment descriptive name. | Human-readable label of the audience or safety/quality segment used for reporting and targeting logic. | :lower: |<
- `retail_cpm` (FLOAT): Retail CPM (cost-per-thousand) in USD. | Represents the displayed/retail price for the inventory used for client-facing billing and benchmarks.
- `wholesale_cpm` (FLOAT): Wholesale CPM in USD. | Represents the platform's or supply-side CPM before retail markup; used to compute margins.
- `impressions` (INTEGER): Number of impressions delivered. | Core delivery metric for reach, frequency and cost-per-impression calculations.
- `clicks` (INTEGER): Number of clicks recorded. | Engagement metric used for CTR calculation and performance evaluation.
- `total_pc_conversions` (INTEGER): Pixel/conversion count (PC) total. | Aggregated conversion metric used for performance and CPA calculations.
- `total_pv_conversions` (INTEGER): Post-view conversion count (PV) total. | Tracks conversions attributed to views (view-through) for cross-channel attribution.
- `video_start` (INTEGER): Count of video starts. | Video engagement metric used to measure initial engagement with video creatives.
- `video_q1` (INTEGER): Count of video plays reaching 25% (Q1). | Measures partial consumption of video to inform creative performance.
- `video_q2` (INTEGER): Count of video plays reaching 50% (Q2). | Mid-point video engagement metric for quality assessments.
- `video_q3` (INTEGER): Count of video plays reaching 75% (Q3). | Advanced video engagement metric before completion.
- `video_complete` (INTEGER): Count of video completions. | Measures full view-through success for video creatives and billing in some models.
- `revenue_usd` (FLOAT): Revenue recorded in USD (platform/line-level). | Revenue recognized for the row; used for financial reporting and margin analysis.
- `clear_price_usd` (FLOAT): Clear/clearing price paid to supply for the impression (USD). | Represents the winning auction price unit value used in cost computations.
- `media_cost_usd` (FLOAT): Media cost in USD (platform media expense). | Cost attributed to media buys before fees; used to compute margins and reconcile billing.
- `total_ad_cost_usd` (FLOAT): Total ad-related cost in USD (media + contextual/viewability fees etc). | Aggregated ad cost used in billing and margin calculations.
- `esupply_fee` (FLOAT): eSupply fee applied (USD). | Standard platform or supply fee applied to lines for billing.
- `mm_data_cost_usd` (FLOAT): Measurement/data cost in USD for measurement services. | Portion of spend allocated to measurement or data partners for reporting & cost allocation.
- `contextual_cost_usd` (FLOAT): Contextual targeting or verification cost in USD. | Fees for contextual classification/safety or related services charged against campaigns.
- `viewability_cost_usd` (FLOAT): Viewability verification cost in USD. | Fee for viewability-related services used to adjust billed amounts and assess quality.
- `edata_fee_usd` (FLOAT): edata fee in USD (platform fee). | Another platform-level fee component used in total fee calculations.
- `winning_amt_usd` (FLOAT): Winning bid amount in USD for the impression. | Core auction metric used to determine media_cost and reconcile clearing price.
- `billed_spend_usd` (FLOAT): Amount billed to the advertiser in USD. | Final billed spend used for invoicing and client billing reconciliation.
- `total_fee_usd` (FLOAT): Total fees charged (USD) across services. | Sum of platform, vendor and service fees used to calculate final client spend and margins.
- `total_spend_usd` (FLOAT): Total spend in USD (billed spend + fees or client-facing total). | Represents the advertiser-facing total spend metric used in reporting and ROI calculations.

## (OPTIONAL) Table Relationships

## (Optional) Business Context

## (Optional) Notes

