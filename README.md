restore-bareos-backup
=========

(CURRENTLY UNFINISHED)

Ansible role that restores a Bareos Backup that exists on your server and restores it to a given server and file path.  

These links may help finish out adding the proper tasks to this role:
 - [bacula-test-restore-before-job-script](http://bacula.us/bacula-test-restore-before-job-script/)
 - [running-bacula-bconsole-commands-from-bash-cli](http://gosysop.com/running-bacula-bconsole-commands-from-bash-cli/)


Requirements
------------

Bareos Backup Server that holds the backups you want to restore.

Role Variables
--------------

The Bareos Server that stores the backups

```
	restore_bareos_backup_bareos_server: "hostname-of-bareos-server"
```
Bareos Server option to replace the existing files when restoring

```
	restore_bareos_backup_replace_files_on_client: "never"
```
Bareos Server option to merge all filesets when doing a restore 

```
	restore_bareos_backup_merge_all_client_filesets: "yes"
```
Bareos Server option to merge all related jobs to last full backup of selected backup job

```
	restore_bareos_backup_merge_jobs_to_last_full_backup: "yes"
```
Bareos Server Restore Job Name

```
	restore_bareos_backup_restore_job_name: "RestoreFiles"
```
The absolute file path where the backup files should be restored to

```
	restore_bareos_backup_restore_file_path_on_client: "/tmp/bareos-restores/"
```


Dependencies
------------

None

Example Playbook
----------------

	- hosts: your_restore_destination
	  vars_files:
	    - vars/main.yml
	  roles:
	    - { role: stancel.restore-bareos-backup }


or 


	- hosts: your_restore_destination
	  vars:
		restore_bareos_backup_bareos_server: "hostname-of-bareos-server"
		restore_bareos_backup_restore_file_path_on_client: "/some/path/here"
	  roles:
	    - stancel.restore-bareos-backup

License
-------

Proprietary for now

Author Information
------------------

Brad Stancel
