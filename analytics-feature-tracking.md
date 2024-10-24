# Adobe Analytics Reference Guide: Feature Tracking Matrix

## Summary
This guide outlines the key features to track across The Australian's digital products, including authentication, content engagement, and subscription features. Use this reference to understand what metrics are available and how to track product performance.

## Authentication Features

| Feature | Event | Variable | Success Metric | Description |
| ---|---|---|---|---|
| Login Button | event65 | eVar23='login-button' | Click-through rate | Track login initiation |
| Login Method | event65 | eVar23='login-method' | Method distribution | Track authentication preference |
| Login Success | event18 | eVar46='logged_in' | Success rate | Track completion |
| Login Error | event65 | eVar23='login-error' | Error rate | Track failures |
| Session State | event1 | eVar14='subscriber' | Login retention | Track session status |

## Content Engagement Features

| Feature | Event | Variable | Success Metric | Description |
| ---|---|---|---|---|
| Article View | event8 | pageName | View count | Track content access |
| Scroll Depth | event17 | prop45 | Reading depth % | Track content consumption |
| Time Spent | event63 | prop30 | Average time | Track engagement duration |
| Social Share | event65 | eVar23='share' | Share rate | Track content distribution |
| Bookmark | event65 | eVar23='save' | Save rate | Track content saving |
| Comment | event65 | eVar23='comment' | Engagement rate | Track discussion participation |

## Subscription Features

| Feature | Event | Variable | Success Metric | Description |
| ---|---|---|---|---|
| Paywall View | event1 | eVar23='paywall' | View rate | Track conversion opportunity |
| Subscribe CTA | event65 | eVar23='sub-cta' | Click-through rate | Track intent |
| Plan Select | event65 | eVar23='plan-select' | Selection rate | Track preference |
| Payment Start | event65 | eVar23='payment-start' | Funnel entry | Track conversion start |
| Payment Complete | event18 | eVar14='subscriber' | Conversion rate | Track success |
