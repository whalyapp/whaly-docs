# Webhook

## Why using the Webhook action?

With the Webhook action anybody in your organization can send data directly to popular services like [Zapier](https://zapier.com/), [N8N](https://n8n.io/), or [Integromat](https://www.integromat.com) (now [make](https://www.make.com/en)). This allow you to trigger complex workflow with your data.

## What does it look like?

{% hint style="info" %}
This action is only compatible with **Questions**.
{% endhint %}

This action will **a POST API call** with your chart data.

## Configuring Webhooks

In order to use the webhook action, all you need is a Webhook URL. Whaly will `POST` on this URL with a payload that looks like the following.

```json
{
  "fields": {
    "<KEY>": {
      "name": "<KEY>",
      "label": "<Label>",
      "label_short": "<Label_Short>"
    }
  },
  "data": [
    {
      "<KEY>": {
        "value": 19147
      }
    }
  ]
}
```
