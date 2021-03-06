## Select a Restore Point

On this wizard page, you can select whether you need to restore specific file versions, or restore to a specific point in time.

![](/assets/restore-sql-point-in-time.png)

The following options are available in the wizard:

* **Latest version                
  **Enables you to restore the latest versions of your images available in a backup.

  > CloudBerry backups include only images that was modified since the previous backup date. As a result, selecting this option will restore only those image versions that were modified before the most recent backup.

* **Point in time                
  **Enables you to restore image versions available in your backup storage at the specified date and time.

  > CloudBerry backups include only images that were modified since the previous backup date. As a result, selecting this option will restore only those image versions that were modified before the most recent backup and are not yet available in the destination folder.
  >
  > If earlier versions of the corresponding images already exist in the destination folder, they will not be restored unless you explicitly enable their overwriting further in this wizard.



