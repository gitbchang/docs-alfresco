# Troubleshooting Desktop Sync

Sorry you're having trouble syncing Desktop Sync.

To resolve data synchronizing issues between the desktop and Alfresco repository, we recommend you first try to isolate where the issue is occurring.

Your problem may be related to any one of the following issues:

-   [Desktop gets no response from the server](desktop-sync-troubleshooting.md#1)
-   [Topic messages or events are not being dispatched](desktop-sync-troubleshooting.md#2)
-   [Rollback transaction exceptions in client, such as desktop or Share](desktop-sync-troubleshooting.md#3)
-   [Changes made from Share are not committed to the database](desktop-sync-troubleshooting.md#4)
-   [Desktop Sync cannot register, subscribe or synchronize with Share](desktop-sync-troubleshooting.md#5)
-   [ActiveMQ is down](desktop-sync-troubleshooting.md#7)
-   [Synchronization service is down](desktop-sync-troubleshooting.md#8)
-   [Repository is down](desktop-sync-troubleshooting.md#9)
-   [Sync PostgreSQL database down](desktop-sync-troubleshooting.md#10)
-   [Optimal memory setting](desktop-sync-troubleshooting.md#11)

## Desktop gets no response from the server

If you see a client error message when you try to synchronize data from the desktop to the repository, it could mean that either the repository or synchronization service is down.

Check that the repository, ActiveMQ and synchronization service are all up. Check the repository and synchronization service log files.

![](../images/hr.png)

[back to top](desktop-sync-troubleshooting.md#)

## Topic messages or events are not being dispatched

If you see that the ActiveMQ queue is growing, it could mean that the synchronization service is down. In such an event, the updates will not be pulled off ActiveMQ and the synchronization service will not get any updates or changes.

Check that the synchronization service is up. Check the synchronization service log for exceptions.

![](../images/hr.png)

[back to top](desktop-sync-troubleshooting.md#)

## Rollback transaction exceptions occur in clients, such as Sync client or Share, and in the repository log file

ActiveMQ down or repository connection to ActiveMQ down.

Note that if the repository can't contact ActiveMQ, all transactions will fail.

![](../images/hr.png)

[back to top](desktop-sync-troubleshooting.md#)

## Changes made from Share are not committed to the database

If you see that the changes made from Share are not getting queued in ActiveMQ or the synchronization service cannot request changes from subscription service, it means that ActiveMQ is down. In such an event, changes from Share cannot be synced to ActiveMQ, as a result both the synchronization and subscription services will be out of sync with Share. Also, the synchronization service will terminate.

Check the ActiveMQ, repository, and services logs. Restart ActiveMQ, the synchronization service, and the desktop to check if that resolves the issue.

![](../images/hr.png)

[back to top](desktop-sync-troubleshooting.md#)

## Desktop Sync cannot register, subscribe or synchronize with the repository

Try the following:

-   Check that the repository is up.
-   Check the repository log for exceptions.
-   Make sure that the Desktop Sync amp has been applied to the repository.
-   Check that the synchronization service is up.
-   Check the synchronization service logs for exceptions.

[back to top](desktop-sync-troubleshooting.md#)

![](../images/hr.png)

## ActiveMQ is down

If you are using an ActiveMQ cluster, you benefit from reliable high performance and load balancing of messages. If ActiveMQ is down, the transaction will fail and any file\(s\) added to the Alfresco folder on your desktop will be deferred. In File Explorer, the file will shows a blue icon and a notification is displayed on the system tray. When ActiveMQ is up and running again, the file is synced and shows a green icon in the File Explorer.

[back to top](desktop-sync-troubleshooting.md#)

![](../images/hr.png)

## Synchronization service is down

If the synchronization service goes down, the size of the `Consumer.*.VirtualTopic.alfresco.repo.events.nodes` queue in ActiveMQ grows. The dispatched number does not increase and the events will be retained until the synchronization service comes back again.

While the synchronization service is down, any file to the Alfresco folder on your desktop will be deferred until the synchronization service is back up. In File Explorer, the file will shows a blue icon and a notification is displayed on the system tray.

[back to top](desktop-sync-troubleshooting.md#)

![](../images/hr.png)

## Repository is down

If the Alfresco repository is down, any file\(s\) added to the Alfresco folder will be deferred until the repository is back again. In File Explorer, the file will shows a blue icon and a notification is displayed on the system tray.

[back to top](desktop-sync-troubleshooting.md#)

![](../images/hr.png)

## Sync PostgreSQL database down

If you are using a PostgreSQL database cluster, the chances of your database being down are rare in a production environment. If it does occur, the files added to the Alfresco folder on the desktop will be deferred.

In File Explorer, the file will shows a blue icon and a notification is displayed on the system tray.

[back to top](desktop-sync-troubleshooting.md#)

![](../images/hr.png)

## Optimal memory setting

It is recommended that you use at least 2GB heap size for your installation. The optimal memory setting for your installation will largely depend on:

-   The amount of sync activity; more syncs will require more memory.
-   The number of sync changes per sync. Syncing files and folders consume memory until the sync is complete. After syncing is complete, the memory is reclaimed. By default, the client syncs every 5 minutes, but this needs to account for users going offline for long periods of time. So, the calculation must account for this time.
-   The setting of the `sync.cache.expiryTime` property in the config.yml file. The default value is 30s. This will reclaim the memory used by a sync after 30s if it hasn't already been reclaimed.

[back to top](desktop-sync-troubleshooting.md#)

**Parent topic:**[Administering Desktop Sync](../concepts/desktop-sync.md)

