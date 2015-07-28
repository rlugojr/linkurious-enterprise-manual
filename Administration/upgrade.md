## Upgrade

<div class="alert alert-danger">
    Please backup Linkurious before proceeding to any upgrade.
</div>

### Automatic upgrades

If you have Linkurious v0.10.0 or later installed, you can upgrade using the automatic update script:

1. Download the latest version of Linkurious from our Website (e.g. `linkurious-linux-v1.0.0.zip`) and save it to the Linkurious folder.
2. Stop Linkurious using the `stop` script.
3. Backup the `data` folder. If you are using an external database for persistence (e.g. MySQL or PostgreSQL), backup the `linkurious` schema of that database.
4. Launch the update script (Linux

### Manual upgrades

Before Linkurious v0.10, no update procedure is available. To upgrade Linkurious, you need to install a new version and delete the previous one. All visualizations, users, groups and access-rights will be lost.

In some cases, copying the `database.db` file from the old Linkurious to new Linkurious folder can work, but it is not guaranteed and depends on versions.