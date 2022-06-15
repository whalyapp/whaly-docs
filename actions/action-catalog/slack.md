# Slack

## Why using the Slack action?

With the Slack action anybody in your organisation can send data directly to any preselected Slack Channel. This is useful to quickly share with teammates any updates on current deadlines on vital informations based on data.

## What does it look like?

This action will **send a Slack message** with your Dashboard/Question screenshot or raw data as a file.

## Supported formats

Slack integration supports the following formats:

* PDF
* PNG
* CSV
* JSON

## Configuring Slack

### Generating a Bot User Token in a Private Slack Action Application

* Go to the Slack API app page at [https://api.slack.com](https://api.slack.com/apps).
* Click **Create New App**.

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.32.06.png>)

* In the popup that appears, click on "**From an app manifest**"

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.32.26.png>)

* Select your Workspace

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.33.27.png>)

* In the code editor that appears, copy paste the following snippet

```
display_information:
  name: Whaly Push App
  description: This app will allow Whaly to push data into your Slack workspace.
settings:
  org_deploy_enabled: false
  socket_mode_enabled: false
  is_hosted: false
  token_rotation_enabled: false
features:
  bot_user:
    display_name: Whaly Push
    always_online: true
oauth_config:
  scopes:
    bot:
      - channels:read
      - users:read
      - files:write
      - groups:read
      - im:read
      - mpim:read
      - chat:write
```

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.34.34.png>)

* Click on "**Create**" in the next popup

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.34.45.png>)

* On the page on which you are redirected, click on "**Install to Workspace**"

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.36.29.png>)

* Click on the left menu into the "**Features > Oauth & Permissions**" menu item, and from this page, copy the "**Bot User OAuth Token**" string. This is the token that you'll need to configure on Whaly side 🎉

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 11.37.51.png>)

## Giving access to the proper channels

Now, you have to invite "Whaly Push" user into the Slack channels you which it has access to by posting its name into the proper channels.

![](<../../.gitbook/assets/Screenshot 2022-06-08 at 12.07.26.png>)

In the popup that appear, accept to invite the user into the Channel 🤗
