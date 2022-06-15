---
description: >-
  This section describes how to embed a report in your website or your webapp.
  In order to do so you need to be able to modify your app's code as well as
  having admin access to Whaly.
---

# 👩💻 Embed a report

## Setting up your report for embedding

First of all go to setting > org admin > general settings for your org and copy your client secret as well as org slug you'll need to for later.

![Getting your client secret](<../../.gitbook/assets/image (215).png>)

Then you need to get your embed token on the report you want to share. In order to do so you need to open the report you wish to embed and click on the share button. Once you see the drawer you can copy your embed token you'll need it for later.

![Get your embed token](<../../.gitbook/assets/image (183).png>)

Now you are all set, we can start writing code 🤓

## Embed the report in your app

In order to secure your embed and to make sure that nobody can use your embed on their website we require you to generate and sign a JSON Web Token that you will pass as a query string parameter in the iframe that you embed. This way we ensure that only you who owns the client secret can create short live token that give your user access to your embed.

In order to do so you can check the following code:

```javascript
import jwt from 'jsonwebtoken';

// this routine must happen on server side as your secret should remain secret
const embedToken = "<MY_EMBED_TOKEN>";
const clientSecret = "<MY_CLIENT_SECRET>";
const orgSlug = "<MY_ORG_SLUG>";

// we require you to generate a payload with the default filters you want to pass
// if you don't want to pass filters just input an empty object {}
// the filter payload is an object which keys are the apiName of the filter
// and the value is the value that you want to pass

const payload = {
    filters: { 
        myFilter: 1 
    }, 
    expiration_date: Date.now() + 24 * 60 * 60 * 1000 // valid for 24h
};

// generate and sign your JWT, please use the HS256 algorithm
const myToken = jwt.sign(payload, clientSecret);

// generate the embed url
const embed_url = `https://app.whaly.io/${orgSlug}/embed/report/${embedToken}?token=${myToken}`
```

You can then render your iframe using the templating system you want

```html
<iframe src="<%= embed_url %>" 
  frameborder="0" 
  style="width: 100%;height: 600px" 
  allowfullscreen>
</iframe>
```

## Access your filters API Name

In order to set and retrieve your filters API Name you can edit your filter and click on the developer tab and set your apiName. Please note that filters API Name must be unique for a given report and are not set by default.

![Setting an API Name](<../../.gitbook/assets/image (179).png>)
