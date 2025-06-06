# Changelog

## Version 2.5

* fix runtime environment by creating backup directories separately (Closes: [#43](https://github.com/k0lter/autopostgresqlbackup/issues/43)

## Version 2.4

* Fix runtime environment (backup directories created too early) (Closes: [#43](https://github.com/k0lter/autopostgresqlbackup/issues/43)

## Version 2.3

* Add `REPORT_ERRORS_ONLY` (default: `yes`) configuration variable. Set it to `no` permits to receive a backup report even if there are no errors. (Closes: [#35](https://github.com/k0lter/autopostgresqlbackup/issues/35))
* Add cron and systemd examples
* Manpage is by now built from Documentation.md using pandoc

## Version 2.2

* Fix manpage issue

## Version 2.1

* Default configuration file /etc/default/autopostgresqlbackup is now deprecated in favor of /etc/autodbbackup.d
* Add support for MySQL/MariaDB (using the `DBENGINE` configuration parameter).
* Add a command line option `-c` to specify an alternate config file or directory (see [Documentation](/Documentation.md)).
* Add manpage
* Fix hypothetical shell injection by crafting special database names
* Variable `OPT` (used with pg_dump) is renamed to `PGDUMP_OPTS` and a new variable `PGDUMPALL_OPTS` is available (used for dump globals with pg_dumpall) (Closes: [#12](https://github.com/k0lter/autopostgresqlbackup/issues/12))
* Fix stderr capture and check return code while running pg_dump/pg_dumpall commands
* Add `MIN_DUMP_SIZE` configuration variable to raise a warning when a backup file size is below this limit (Closes: [#15](https://github.com/k0lter/autopostgresqlbackup/issues/15))
* Various bug fixes

## Version 2.0

* Huge code cleanup and refactoring (Closes: [#2](https://github.com/k0lter/autopostgresqlbackup/issues/2))

### Added features

* Compressing and/or encrypting dumps on the fly (Closes: [#1](https://github.com/k0lter/autopostgresqlbackup/issues/1))
* The day of the week for the weekly backups is now configurable (1 for Monday, 0 disable weekly backups) (Closes: [#1](https://github.com/k0lter/autopostgresqlbackup/issues/1), [#9](https://github.com/k0lter/autopostgresqlbackup/issues/9))
* The day of the month for the monthly backups is now configurable (instead of 1 by default, 0 disable the monthly backups) (Closes: [#1](https://github.com/k0lter/autopostgresqlbackup/issues/1), [#8](https://github.com/k0lter/autopostgresqlbackup/issues/8))
* Support for any compression tool that supports to read data to be compressed from stdin and outputs it to stdout (Closes: [#3](https://github.com/k0lter/autopostgresqlbackup/issues/3), [#6](https://github.com/k0lter/autopostgresqlbackup/issues/6))
* Daily, weekly and monthly dumps keeped are now configurable (by default, 14 daily, 5 weekly and 6 monthly backups)
* Switch encryption from OpenSSL to GnuPG, see [details](https://github.com/k0lter/autopostgresqlbackup#openssl-encryption) (Closes: [#10](https://github.com/k0lter/autopostgresqlbackup/issues/10))

### Removed features

* It's no longer possible to dump all databases in a single file
* Copying the latest dump in the latest/ directory is no longer supported
* Specifying the databases names to dump during the monthly backup is no longer supported
* It is no longer supported to send backup files by email (MAILCONTENT=files). It was anyway probably not a good idea to send backup files by email (for various reasons: file size, privacy, data leaks, etc.) but I guess that it could easily be implemented in a POSTBACKUP script if needed.
