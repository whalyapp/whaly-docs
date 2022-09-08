# Table of contents

* [👏 Welcome to Whaly 🐳](README.md)

## Organization

* [🏫 What is an organization ?](organization/what-is-an-organization.md)
* [🔑 Manage Access to your org](organization/manage-access-to-your-org.md)
* [❓ Understanding Licences](organization/understanding-licences.md)
* [👮 Understanding User Roles](organization/manage-access-control.md)

## Warehouse

* [🏦 Connect your Warehouse](warehouse/connect-your-warehouse.md)
* [🔷 BigQuery](warehouse/bigquery/README.md)
  * [🔗 Connect your BigQuery](warehouse/bigquery/connect-your-bigquery.md)
  * [🧹 Configure a Cloud Storage cleaning rule](warehouse/bigquery/configure-a-cloud-storage-cleaning-rule.md)
* [❄ Snowflake](warehouse/snowflake/README.md)
  * [🔗 Connect your Snowflake](warehouse/snowflake/connect-your-snowflake.md)
  * [🗝 Giving access to Snowflake data](warehouse/snowflake/giving-access-to-snowflake-data.md)

## Platform

* [💫 Caching](technical-deep-dive/caching.md)

## Workspace

* [✏ Workspace](workspace/workspace.md)
* [📗 Catalog](workspace/catalog.md)
* [⚙ Settings](workspace/settings.md)

## Sources

* [🔌 Connect your Sources](sources/how-sources-work.md)
* [🧙 Source monitoring](sources/source-monitoring.md)
* [🎁 Source catalog](sources/source-catalog/README.md)
  * [Community](sources/source-catalog/community/README.md)
    * [Github Stars](sources/source-catalog/community/github-stars.md)
    * [Slack](sources/source-catalog/community/slack.md)
    * [Orbit](sources/source-catalog/community/orbit.md)
  * [Database](sources/source-catalog/database/README.md)
    * [MongoDb](sources/source-catalog/database/mongodb.md)
    * [PostgreSQL / Postgres](sources/source-catalog/database/postgres/README.md)
      * [💡 Tip: Extracting the relationships](sources/source-catalog/database/postgres/tip-extracting-the-relationships.md)
  * [eCommerce](sources/source-catalog/ecommerce/README.md)
    * [WooCommerce](sources/source-catalog/ecommerce/woocommerce.md)
  * [Engineering](sources/source-catalog/engineering/README.md)
    * [Github](sources/source-catalog/engineering/github.md)
  * [Finance](sources/source-catalog/finance/README.md)
    * [Brex](sources/source-catalog/finance/brex.md)
    * [Pennylane](sources/source-catalog/finance/pennylane/README.md)
      * [Pennylane (Redshift) - General Ledger & Trial Balance](sources/source-catalog/finance/pennylane/pennylane-redshift-general-ledger-and-trial-balance.md)
      * [Pennylane API - Customer Invoices](sources/source-catalog/finance/pennylane/pennylane-api-customer-invoices.md)
    * [Qonto](sources/source-catalog/finance/qonto.md)
    * [Stripe](sources/source-catalog/finance/stripe.md)
    * [QuickBooks](sources/source-catalog/finance/quickbooks.md)
  * [Marketing / Growth](sources/source-catalog/marketing-growth/README.md)
    * [Facebook Ads](sources/source-catalog/marketing-growth/facebook-ads.md)
    * [Google Ads](sources/source-catalog/marketing-growth/google-ads.md)
    * [Google Analytics](sources/source-catalog/marketing-growth/google-analytics/README.md)
      * [Google Analytics (V4)](sources/source-catalog/marketing-growth/google-analytics/google-analytics-v4.md)
      * [Google Analytics (Universal Analytics)](sources/source-catalog/marketing-growth/google-analytics/google-analytics.md)
    * [LaGrowthMachine](sources/source-catalog/marketing-growth/lagrowthmachine.md)
    * [lemlist](sources/source-catalog/marketing-growth/lemlist.md)
    * [LinkedIn Ads](sources/source-catalog/marketing-growth/linkedin-ads.md)
    * [Salesloft](sources/source-catalog/marketing-growth/salesloft.md)
  * [No-Code](sources/source-catalog/no-code/README.md)
    * [Airtable](sources/source-catalog/no-code/airtable.md)
    * [Bubble](sources/source-catalog/no-code/bubble.md)
    * [Google Sheets](sources/source-catalog/no-code/google-sheets.md)
  * [Support](sources/source-catalog/support/README.md)
    * [Intercom](sources/source-catalog/support/intercom.md)
  * [Product](sources/source-catalog/product/README.md)
    * [Amplitude](sources/source-catalog/product/amplitude.md)
    * [MixPanel](sources/source-catalog/product/mixpanel.md)
    * [Segment](sources/source-catalog/product/segment.md)
  * [Sales](sources/source-catalog/sales/README.md)
    * [Aircall](sources/source-catalog/sales/aircall.md)
    * [Pipedrive](sources/source-catalog/sales/pipedrive.md)
    * [Hubspot](sources/source-catalog/sales/hubspot.md)
    * [Recruit CRM](sources/source-catalog/sales/recruit-crm.md)
    * [Salesforce](sources/source-catalog/sales/salesforce.md)
* [💭 Whitelisting Whaly IPs](sources/whitelisting-whaly-ips.md)

## Data Management

* [🛠 Workbench](data-management/workbench/README.md)
  * [🪄 Formulas](data-management/workbench/formulas.md)
  * [🪟 Views](data-management/workbench/views.md)
  * [🗝 Configuring Primary Key of Datasets](data-management/workbench/configuring-primary-key-of-datasets.md)
  * [🔎 Drills](data-management/workbench/drills.md)
  * [🧙♀ SQL Datasets](data-management/workbench/sql-datasets.md)
  * [🧞♂ Import Tables from your Data Warehouse](data-management/workbench/import-tables-from-your-data-warehouse.md)
* [🧭 Explorations](data-management/explorations/README.md)
  * [🆕 Create an exploration](data-management/explorations/create-an-exploration.md)
  * [🪄 Exploration Templates](data-management/explorations/exploration-templates.md)
  * [🔢 Add metrics](data-management/explorations/add-metrics/README.md)
    * [💯 Using custom format](data-management/explorations/add-metrics/using-custom-format.md)
  * [🎲 Add dimensions](data-management/explorations/add-dimensions.md)
  * [🔗 Add related data](data-management/explorations/add-related-data.md)
  * [📈 Create a chart](data-management/explorations/create-a-chart/README.md)
    * [Metric chart](data-management/explorations/create-a-chart/metric-chart.md)
    * [Gauge chart](data-management/explorations/create-a-chart/gauge-chart.md)
    * [Line chart](data-management/explorations/create-a-chart/line-chart.md)
    * [Bar chart](data-management/explorations/create-a-chart/bar-chart.md)
    * [Pie chart](data-management/explorations/create-a-chart/pie-chart.md)
    * [Table chart](data-management/explorations/create-a-chart/table-chart.md)
    * [Funnel chart](data-management/explorations/create-a-chart/funnel-chart.md)
    * [Waterfall chart](data-management/explorations/create-a-chart/waterfall-chart.md)
    * [Heatmap chart](data-management/explorations/create-a-chart/heatmap-chart.md)
    * [Map chart](data-management/explorations/create-a-chart/map-chart.md)
    * [Worldmap chart](data-management/explorations/create-a-chart/worldmap-chart.md)
    * [Custom time format in time series](data-management/explorations/create-a-chart/custom-time-format-in-time-series.md)
  * [🔮 Forecasting](data-management/explorations/forecasting.md)

## Data consumption

* [📊 Dashboards](content-management/dashboards/README.md)
  * [🆕 Create a dashboard](content-management/dashboards/create-a-dashboard.md)
  * [🟦 Manage tiles](content-management/dashboards/manage-tiles/README.md)
    * [📈 Add chart tiles](content-management/dashboards/manage-tiles/add-chart-tiles.md)
    * [🔠 Add text tiles](content-management/dashboards/manage-tiles/add-text-tiles.md)
    * [➡ Add navigation tiles](content-management/dashboards/manage-tiles/add-navigation-tiles.md)
    * [🏗 Arranging tiles](content-management/dashboards/manage-tiles/arranging-tiles.md)
  * [ℹ Add a description](content-management/dashboards/add-a-description.md)
  * [🔎 Filter a dashboard](content-management/dashboards/filter-a-dashboard.md)
  * [🔗 Share a report by link](content-management/dashboards/share-a-report-by-link.md)
  * [⚡ Push dashboard](content-management/dashboards/push-dashboard.md)
  * [🗑 Delete a report](content-management/dashboards/delete-a-report.md)
* [📈 Questions](content-management/questions/README.md)
  * [🆕 Create a question](content-management/questions/create-a-question.md)
  * [ℹ Add a description](content-management/questions/add-a-description.md)
  * [🔗 Share a question by link](content-management/questions/share-a-question-by-link.md)
  * [⚡ Push question data](content-management/questions/push-question-data.md)
  * [🗑 Delete a question](content-management/questions/delete-a-question.md)

## Content management

* [📂 Folders](content-management/folders.md)
* [⭐ Explorations Section](content-management/explorations-section.md)
* [✂ Bulk Content Management](content-management/bulk-content-management.md)

## Embedding

* [📌 Embed in Business apps](embedding/embed-in-business-apps/README.md)
  * [Notion](embedding/embed-in-business-apps/notion.md)
  * [Clickup](embedding/embed-in-business-apps/clickup.md)
  * [Hubspot](embedding/embed-in-business-apps/hubspot.md)
  * [Google Chrome](embedding/embed-in-business-apps/google-chrome/README.md)
    * [🌱 Install](embedding/embed-in-business-apps/google-chrome/install-preview-release.md)
    * [⚙ Configure the Chrome extension](embedding/embed-in-business-apps/google-chrome/configure-the-chrome-extension.md)
* [👩💻 Embedding API](embedding/embedding-api.md)

## Workflows

* [🚀 Push](workflows/push.md)
  * [Configure a Push](workflows/push/configure-a-push.md)
  * [Manage Push](workflows/push/manage-push.md)
* [💼 Manage Installed Actions](workflows/manage-installed-actions.md)
* [⚡ Actions catalog](workflows/actions-catalog/README.md)
  * [Airtable](workflows/actions-catalog/airtable.md)
  * [Google Sheets](workflows/actions-catalog/google-sheets.md)
  * [Slack](workflows/actions-catalog/slack.md)
  * [Sendgrid](workflows/actions-catalog/sendgrid.md)
  * [Webhook](workflows/actions-catalog/webhook.md)

## Guides

* [⛑ Support](guides/support.md)
