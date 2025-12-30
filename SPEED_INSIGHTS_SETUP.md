# Vercel Speed Insights Setup Guide

This document outlines the Vercel Speed Insights implementation for the Grass Studio website.

## Overview

Vercel Speed Insights has been integrated into the Grass Studio website to help monitor and analyze page performance metrics. This allows us to track Core Web Vitals and other important performance indicators.

## What is Vercel Speed Insights?

Vercel Speed Insights is a performance monitoring tool that tracks real user metrics (RUM) from your website visitors. It helps you understand:

- **Core Web Vitals**: LCP (Largest Contentful Paint), FID (First Input Delay), CLS (Cumulative Layout Shift)
- **Web Vitals**: Additional metrics like TTFB (Time to First Byte)
- **Navigation Timing**: Page load and performance data
- **Custom Metrics**: Ability to track business-specific metrics

## Implementation Details

### What Was Added

The Speed Insights tracking script has been added to all HTML pages in the project:

- `index.html`
- `games.html`
- `books.html`
- `contact.html`
- `mountain-tales.html`
- `heartfall.html`

### Script Integration

For static HTML sites, the following code was added before the closing `</body>` tag on each page:

```html
<!-- Vercel Speed Insights -->
<script>
  window.si = window.si || function () { (window.siq = window.siq || []).push(arguments); };
</script>
<script defer src="/_vercel/speed-insights/script.js"></script>
```

This implementation:
- Creates a queue for Speed Insights calls
- Loads the Speed Insights tracking script asynchronously using the `defer` attribute
- Ensures minimal impact on page load performance

## Prerequisites for Full Functionality

To enable Speed Insights tracking and view data:

1. **Vercel Account**: Required to access the Vercel dashboard and view metrics
2. **Speed Insights Enabled**: Enable Speed Insights in the Vercel project dashboard
3. **Deployment to Vercel**: Deploy the site to Vercel using `vercel deploy` or by connecting your Git repository
4. **Active Traffic**: Data collection begins after deployment, and metrics become available as users visit the site

### Enabling Speed Insights

1. Go to your [Vercel Dashboard](https://vercel.com/dashboard)
2. Select the Grass Studio project
3. Navigate to the **Speed Insights** tab
4. Click **Enable** in the dialog that appears

> **Note**: After enabling Speed Insights, the new routes (`/_vercel/speed-insights/*`) will be available after your next deployment.

## Deployment Instructions

To deploy the updated site to Vercel:

```bash
# Using Vercel CLI
vercel deploy

# Or for production deployment
vercel deploy --prod
```

### Alternative: Git Integration

Connect your GitHub repository to Vercel for automatic deployments:

1. Go to [Vercel Dashboard](https://vercel.com/dashboard)
2. Click "Add New Project"
3. Select "Import Git Repository"
4. Choose the Grass-Studio repository
5. Click "Deploy"

Vercel will automatically deploy your site whenever you push to the main branch.

## Viewing Performance Data

Once deployed and enabled:

1. Navigate to your [Vercel Dashboard](https://vercel.com/dashboard)
2. Select the Grass Studio project
3. Click the **Speed Insights** tab
4. After a few days of visitor traffic, performance metrics will be available

### Metrics Available

Speed Insights provides:
- Real User Monitoring (RUM) data from actual visitors
- Breakdown by page, browser, device type, and connection
- Core Web Vitals scores
- Performance trends over time

## Privacy and Data Compliance

Speed Insights respects user privacy and complies with major privacy standards:

- GDPR compliant data handling
- No sensitive user data collection
- Optional URL parameter filtering (for removing sensitive query strings)

For more information, see the [Privacy and Compliance documentation](https://vercel.com/docs/speed-insights/privacy-policy).

## Next Steps

- Monitor performance metrics in the Vercel dashboard
- Review [Using Speed Insights](https://vercel.com/docs/speed-insights/using-speed-insights) for detailed metric interpretation
- Check [Speed Insights Troubleshooting](https://vercel.com/docs/speed-insights/troubleshooting) if you encounter any issues

## Helpful Resources

- [Vercel Speed Insights Documentation](https://vercel.com/docs/speed-insights)
- [Core Web Vitals Guide](https://web.dev/vitals/)
- [Vercel Deployment Guide](https://vercel.com/docs/concepts/deployments)
- [Performance Optimization Best Practices](https://web.dev/performance/)
