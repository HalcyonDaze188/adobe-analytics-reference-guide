# The Australian - Product Analytics Guide

## Feature Tracking Matrix

### 1. Authentication Features

| Feature | Event | Variable | Success Metric | Description |
| ---|---|---|---|---|
| Login Button | event65 | eVar23='login-button' | Click-through rate | Track login initiation |
| Login Method | event65 | eVar23='login-method' | Method distribution | Track auth preference |
| Login Success | event18 | eVar46='logged_in' | Success rate | Track completion |
| Login Error | event65 | eVar23='login-error' | Error rate | Track failures |
| Session State | event1 | eVar14='subscriber' | Login retention | Track session status |

### 2. Content Engagement Features

| Feature | Event | Variable | Success Metric | Description |
| ---|---|---|---|---|
| Article View | event8 | pageName | View count | Track content access |
| Scroll Depth | event17 | prop45 | Reading depth % | Track content consumption |
| Time Spent | event63 | prop30 | Average time | Track engagement duration |
| Social Share | event65 | eVar23='share' | Share rate | Track content distribution |
| Bookmark | event65 | eVar23='save' | Save rate | Track content saving |
| Comment | event65 | eVar23='comment' | Engagement rate | Track discussion participation |

### 3. Subscription Features

| Feature | Event | Variable | Success Metric | Description |
| ---|---|---|---|---|
| Paywall View | event1 | eVar23='paywall' | View rate | Track conversion opportunity |
| Subscribe CTA | event65 | eVar23='sub-cta' | Click-through rate | Track intent |
| Plan Select | event65 | eVar23='plan-select' | Selection rate | Track preference |
| Payment Start | event65 | eVar23='payment-start' | Funnel entry | Track conversion start |
| Payment Complete | event18 | eVar14='subscriber' | Conversion rate | Track success |

## Report Generation Guide

### Adobe Analytics Access

```text
URL: analytics.adobe.com
Report Suite: newscorpau-tausweb
Access Level: Product Manager
```

### Standard Report Creation Steps

1. Basic Report Setup
   * Log into Adobe Analytics
   * Select "Workspace" tab
   * Click "Create New Project"
   * Choose "Blank Project"

2. Data Configuration
   * Set date range
   * Select report suite
   * Add primary metrics
   * Configure segments

3. Visualization Selection
   * Add data tables
   * Include trend graphs
   * Add summary metrics
   * Configure breakdowns

4. Report Export Steps
   * Click "Project" menu
   * Select "Download CSV"
   * Choose full or selected data
   * Save to local system

### Common Report Templates

#### 1. Feature Performance Report

```sql
SELECT 
    'Feature_Performance' as report_type,
    DATE_FORMAT(date, '%Y-%m-%d') as date,
    eVar23 as feature_name,
    COUNT(DISTINCT visitor_id) as unique_users,
    SUM(event65) as interactions,
    SUM(event65)/COUNT(DISTINCT visitor_id) as interaction_rate
FROM report_suite
GROUP BY date, eVar23
ORDER BY date DESC, interactions DESC
```

#### 2. User Journey Report

```sql
SELECT 
    'User_Journey' as report_type,
    DATE_FORMAT(date, '%Y-%m-%d') as date,
    eVar14 as user_type,
    eVar23 as journey_step,
    COUNT(DISTINCT visitor_id) as users,
    SUM(event1) as page_views,
    SUM(event63) as engagement_time
FROM report_suite
GROUP BY date, eVar14, eVar23
ORDER BY date DESC, users DESC
```

#### 3. Conversion Funnel Report

```sql
SELECT 
    'Conversion_Funnel' as report_type,
    DATE_FORMAT(date, '%Y-%m-%d') as date,
    eVar23 as funnel_stage,
    COUNT(DISTINCT visitor_id) as unique_users,
    SUM(event65) as stage_interactions,
    SUM(CASE WHEN event18 > 0 THEN 1 ELSE 0 END) as conversions
FROM report_suite
GROUP BY date, eVar23
ORDER BY date DESC, funnel_stage
```

### Report Distribution Settings

| Setting | Value | Purpose | Frequency |
| ---|---|---|---|
| Format | CSV | Data analysis | As needed |
| Schedule | Daily | Automation | Daily 9am |
| Recipients | Team Email | Distribution | Automated |
| Metrics | All | Complete data | N/A |

### Report Naming Convention

| Report Type | Format | Example |
| ---|---|---|
| Feature Performance | YYYYMMDD_Feature_Performance | 20240424_Feature_Performance |
| User Journey | YYYYMMDD_User_Journey | 20240424_User_Journey |
| Conversion Funnel | YYYYMMDD_Conversion_Funnel | 20240424_Conversion_Funnel |

## Data Validation Checklist

1. Basic Validation
   * Check date ranges
   * Verify metrics
   * Confirm segments
   * Validate totals

2. Quality Checks
   * Compare to historical data
   * Check for anomalies
   * Verify calculations
   * Cross-reference sources

3. Export Validation
   * Confirm all columns
   * Check data formatting
   * Verify calculations
   * Validate filters
