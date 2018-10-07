restore-bareos-backup
=========

(CURRENTLY IN PROGRESS)

Ansible role that restores a Bareos Backup that exists on your server and restores it to a given server and file path.  

These links may help finish out adding the proper tasks to this role:
 - [bacula-test-restore-before-job-script](http://bacula.us/bacula-test-restore-before-job-script/)
 - [running-bacula-bconsole-commands-from-bash-cli](http://gosysop.com/running-bacula-bconsole-commands-from-bash-cli/)


Requirements
------------

Bareos Backup Server that holds the backups you want to restore.

Role Variables
--------------

(Required) The name of the client listed inside Bareos Server that you want to restore
```
	restore_bareos_bareos_client_to_restore: "name of Bareos client"
```
(Required) The Bareos client name of the server where you want to restore this backup to. 
```
	restore_bareos_destination_client: "name of Bareos destination client"
```
(Required) The name of the Bareos Fileset to restore
```
	restore_bareos_fileset: "{{ restore_bareos_bareos_client_to_restore }}-FileSet"
```
(Optional) Bareos Server Job ID to restore. If filled in this will only restore files from that Job ID.
```
	restore_bareos_jobid: 3
```
(Optional) Restores all backed up files from before a certain date.
```
	restore_bareos_date_before: "2018-10-02 00:00:00"
```
(Default) The absolute file path where the backup files should be restored to. This is the default.
```
	restore_bareos_backup_restore_file_path_on_client: "/tmp/bareos-restores"
```
(Default) Bareos Server option to replace the existing files when restoring. This is the default.
```
	restore_bareos_backup_replace_files_on_client: "never"
```

Dependencies
------------

None

Example Playbook
----------------

	- hosts: your_bareos_server
	  vars_files:
	    - vars/main.yml
	  roles:
	    - stancel.restore-bareos-backup


or 


	- hosts: your_bareos_server
	  vars:
		restore_bareos_bareos_client_to_restore: "bareos-name-of-server-where-backed-up"
		restore_bareos_destination_client: "bareos-name-of-my-new-server"
		restore_bareos_fileset: "{{ restore_bareos_bareos_client_to_restore }}-FileSet"
	  roles:
	    - stancel.restore-bareos-backup

License
-------

Proprietary for now

Author Information
------------------

Brad Stancel
