# Adobe Analytics Reference Guide: Report Templates

## Summary

Common report templates for analysing The Australian's digital products. These SQL-based templates can be used to create standardised reports for feature performance, user journeys, and conversion funnels.

## Feature Performance Report

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

Usage: Track feature adoption and engagement rates across the platform.

## User Journey Report

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

Usage: Analyse user behaviour and navigation patterns through the product.

## Conversion Funnel Report

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

Usage: Track subscription funnel performance and conversion rates.
