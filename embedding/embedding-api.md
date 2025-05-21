---
description: >-
  This section describes how to embed a report in your website or your webapp.
  In order to do so you need to be able to modify your app's code as well as
  having admin access to Whaly.
---

# 👩‍💻 Embedding API

## Setting up your report for embedding

The above steps will show you how to generate "**Signed URLs**" that are a secure way to embed your dashboards into your applications to share data with your customers!

First of all go to **Setting > Org admin > General Settings** for your org and copy your **Client Secret** as well as **Org Slug** you'll need it later.

![Getting your client secret](<../.gitbook/assets/image (218).png>)

Then you need to get your E**mbed Token** on the report you want to embed.&#x20;

In order to do so you need to open the report you wish to embed and click on the **share** button. Once you see the drawer, you can copy your **Embed Token,** you'll need it later.

![Get your embed token](<../.gitbook/assets/image (184).png>)

Now you are all set, we can start writing code 🤓

## Embed reports in your app

In order to secure your dashboards and to make sure that nobody can use your embed on their own website, we require you to generate and sign a **JSON Web Token.**

This JWT token will be used to generate your **Signed URL.** This way we ensure that only the owner of the **Client Secret** can create **Signed URLs**.

{% hint style="info" %}
In order to avoid leaking your **Client Secret**, the JWT generation need to be done on your **server side applications**.

If you include your Client Secret in your Web App, you expose it to anyone reading the code of your webpage, which is very dangerous!
{% endhint %}

In order to create a **signed JWT token**, you can check the following code example:

```javascript
// Example for a webserver running in Node.js
// The same algorithm and JWT librairies needs to be ported in your backend programming language (PHP, Python, Go, ...))

import jwt from 'jsonwebtoken';

// This routine must happen on server side as your secret should remain secret
const embedToken = "<MY_EMBED_TOKEN>";
const clientSecret = "<MY_CLIENT_SECRET>";
const orgSlug = "<MY_ORG_SLUG>";

// We require you to generate a payload with the default filters you want to pass
// if you don't want to pass filters just input an empty object {}
// the filter payload is an object which keys are the apiName of the filter
// and the value is the value that you want to pass

const payload = {
    filters: { 
        myFilter: 1 
    }, // Optional
    userEmail: "joe@lucky.com", // Email of the user doing the request
    expiration_date: Date.now() + 24 * 60 * 60 * 1000 // valid for 24h
};

// Generate and sign your JWT, please use the HS256 algorithm
const myToken = jwt.sign(payload, clientSecret);

// Generate the embed url
const embed_url = `https://app.whaly.io/${orgSlug}/embed/report/${embedToken}?token=${myToken}`
```

You can then render your iFrame using the templating system you want (React / Vue.js / ...)

```html
<iframe src="<%= embed_url %>" 
  frameborder="0" 
  style="width: 100%;height: 600px" 
  allowfullscreen>
</iframe>
```

## Access your filters API Name

In order to set and retrieve your filters API Name you can edit your filter and click on the developer tab and set your apiName. Please note that filters API Name must be unique for a given report and are not set by default.

![Setting an API Name](<../.gitbook/assets/image (180).png>)

## JWT Params

You can encode several parameters in your JWT such as

<table><thead><tr><th>Name</th><th>Is Required</th><th>Value</th><th width="187">Description</th></tr></thead><tbody><tr><td>filters</td><td>true</td><td>FilterPayload</td><td>You can control any filter values through this payload </td></tr><tr><td>expiration_date</td><td>true</td><td>Timestamp</td><td>This value indicates when your token will stop be accepted</td></tr><tr><td>disable_drills</td><td>true</td><td>Boolean</td><td>This value helps you disable all drills by default on the dashboard</td></tr></tbody></table>

#### FilterPayload

The filter payload is an object that takes for keys the filter api name and as value depending on the filter type.

```javascript
{
    <filterApiName>: FilterValuePayload
}
```

#### FilterValuePayload

For numeric filters you can pass one numeric (float or int) or an array of numerics

```javascript
{
    myNumeric: 1.2,
    myNumericArray: [4.21, 1,337]
}
```

For string filters you can pass on string or an array of string

<pre class="language-javascript"><code class="lang-javascript"><strong>{
</strong>    myString: "rick",
    myStringArray: ["rick", "morty"]
}
</code></pre>

For dates, you can either pass an array of 2 dates or a more complex object to describe your operation.&#x20;

{% hint style="warning" %}
Carefull dates must be passed as per the [ISO8601](https://en.wikipedia.org/wiki/ISO_8601) standard.
{% endhint %}

Passing dates as an array

```javascript
 {
    myDate: ["2021-01-01T00:00:00.000Z", "2021-12-01T00:00:00.000Z"] 
 }
```

