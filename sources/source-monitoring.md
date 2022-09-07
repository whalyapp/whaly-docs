# 🧙 Source monitoring

Whaly allow you to monitor your sources. This starts on your workspace where you can switch from your content to the source monitoring by clicking on the **Source** menu.

<figure><img src="../.gitbook/assets/Screen Cast 2022-09-07 at 6.15.33 PM.gif" alt=""><figcaption></figcaption></figure>

## Source Execution

### Triggering a sync

Although you can manage the frequency at which you want your sync to happen, you can trigger a sync whenever you need it. To change you schedule you can click on **Settings** and change the **Sync Frequency.**

<figure><img src="../.gitbook/assets/image (5).png" alt=""><figcaption><p><strong>Changing sync frequency</strong></p></figcaption></figure>

In order to trigger a sync, go to the **Overview** menu and click on **Sync Now**. You can't trigger a sync if your source is already syncing. From the **Overview** menu you can also view when the next sync is scheduled for.

&#x20;

<figure><img src="../.gitbook/assets/image.png" alt=""><figcaption><p>Trigger a new sync</p></figcaption></figure>

### Error and Alerting

A source can be in error when we deal with issues of connectivity of if something goes wrong during the replication process, we flag the source in ERROR. By doing so we alert all [Admin Builders](../organization/manage-access-control.md#admin-builder) in your organisation in real time with the cause of the error so they can troubleshoot the integration. When your source is in error you can find an error warning on the main screen as well as next to the source and you can view your error in the user interface.

&#x20;

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption><p>Source alerts</p></figcaption></figure>

### Execution log

In order for you to troubleshoot your execution, we provide you with the full log of what happened during the sync. Those logs are available for 30 days after the creation date of the execution. In order to check the logs you can click on the log button next to the execution to view the full logs.



<figure><img src="../.gitbook/assets/image (9).png" alt=""><figcaption><p>Source logs</p></figcaption></figure>

## &#x20;Selective sync

In order to speed up your syncs you can select which tables you want to sync and how. In order to do so you can click on the **Selective sync** tab and when you are done editing you can click on **Save.**

<figure><img src="../.gitbook/assets/image (7).png" alt=""><figcaption><p>Selective sync</p></figcaption></figure>

In order to better understand which table is taking the most time you can browser the **Usage** tab that will give you the amount of time it takes to replicate each tables.

<figure><img src="../.gitbook/assets/image (1).png" alt=""><figcaption><p>Usage tab</p></figcaption></figure>

## Modifying your source settings&#x20;

You can modify at any time how your source is configured. Please note that only [Admin Builder](../organization/manage-access-control.md#admin-builder) have the right to do so. In order to do it, you can open the **Settings** tab and modify one by one your source connection properties.

<figure><img src="../.gitbook/assets/image (3).png" alt=""><figcaption><p>Settings update</p></figcaption></figure>
