## 0.4.11 - 2019-03-07

* [maintenance] Fix to use `response.status.error_result` instead of `response.status.errors` to check job failure status (thanks to @nownabe)

## 0.4.10 - 2018-11-08
* [enhancement] Support column-based partition (thanks to Chi-Ruei Li)

## 0.4.9 - 2018-09-08
* [enhancement] Enable object lifecycle management when creating buckets with `auto_create_gcs_bucket` (thanks to @potato2003)

## 0.4.8 - 2017-05-23
* [enhancement] Support location option for `auto_create_gcs_bucket` option (thanks to @potato2003)

## 0.4.7 - 2017-05-02
* [enhancement] Support location option to allow to use 'asia-northeast1' region

## 0.4.6 - 2017-04-17
* [enhancement] Support auth_method 'application_default'

## 0.4.5 - 2017-04-04

* [maintenance] Fix deprecated warning log condition for `timeout_sec`

## 0.4.4 - 2017-04-04

* [maintenance] Support google-api-ruby-client >= v0.11.0
* [maintenance] Add `send_timeout_sec` and `read_timeout_sec` option for google-api-ruby-client >= v0.11.0

## 0.4.3 - 2017-02-11

* [maintenance] Fix `schma_update_options` was not set with load_from_gcs (thanks to h10a-bf)

## 0.4.2 - 2016-10-12

* [maintenance] Fix `schema_update_options` was not working (nil error)

## 0.4.1 - 2016-10-03

* [enhancement] Support `schema_update_options` option

## 0.4.0 - 2016-10-01

* [enhancement] Support partitioned table
* [maintenance] Add `progress_log_interval` option to control the interval of showing progress log, and now showing progress log is off by default

## 0.3.7 - 2016-08-03

* [maintenance] Fix Thread.new to use thread local variables to avoid nil idx error (thanks to @shyouhei and @umisora)

## 0.3.6 - 2016-06-15

* [maintenance] if `is_skip_job_result_check` is true, skip output_rows checking (thanks to @joker1007)

## 0.3.5 - 2016-06-13

* [enhancement] retry backendError and internalError in waiting load job
* [enhancement] retry Broken pipe and Connection reset in inserting object to GCS

## 0.3.4 - 2016-06-01

* [new feature] Add `gcs_bucket` option to load multiple files from a GCS bucket with one load job

## 0.3.3 - 2016-05-24

* [maintenance] Fix `private_key` auth is not working

## 0.3.2 - 2016-05-03

* [new feature] Add `abort_on_error` option
* [maintenance] Use uuid instead of current time for temp_table name

## 0.3.1 - 2016-04-15

* [new feature] Add `sdk_log_level` option to show log of google-api-client
* [maintenance] Fix `prevent_duplicate_insert` was not working correctly
* [maintenance] Change to get `num_output_rows` of `transaction_report` from `get_table` API
* [maintenance] Log response.statistics of load jobs
* [maintenance] Always create job_id on client side as [google recommends](https://cloud.google.com/bigquery/docs/managing_jobs_datasets_projects#managingjobs) so that duplication not to be occurred
* [maintenance] Fix a possibility which rehearsal would load 0 rows file

## 0.3.0 - 2016-04-08

Big change is introduced. Now, embulk-output-bigquery is written in JRuby.

* [new feature] Support parallel loads. Fix [#28](https://github.com/embulk/embulk-output-bigquery/issues/28).
* [new feature] Create table first. Fix [#29](https://github.com/embulk/embulk-output-bigquery/issues/29).
* [new feature] Introduce rehearsal mode. Fix [#30](https://github.com/embulk/embulk-output-bigquery/issues/30).
* [new feature] Support `dataset_old` option for `replace_backup`. Fix [#31](https://github.com/embulk/embulk-output-bigquery/issues/31).
* [maintenance] Fix default timestamp format to `%Y-%m-%d %H:%M:%S.%6`. Fix [#32](https://github.com/embulk/embulk-output-bigquery/issues/32).
* [new feature] Support request options such as `timeout_sec`, `open_timeout_sec`, `retries`. Fix [#33](https://github.com/embulk/embulk-output-bigquery/issues/33).
* [new feature] Support continuing from file generation with `skip_file_generation` option.
* [new feature] Guess BigQuery schema from Embulk schema. Fix [#1](https://github.com/embulk/embulk-output-bigquery/issues/1).
* [new feature] Support automatically create dataset.
* [new feature] Support transactional append mode.
* [incompatibility change] Formatter plugin support is dropped. Formatter is done in this plugin for specified `source_format`.
* [incompatibility change] Encoder plugin support is dropped. Encoding is done in this plugin for specified `compression`.
* [incompatibility change] `append` mode now expresses a transactional append, and `append_direct` is one which is not transactional (this was `append` mode before)

## 0.2.3 - 2016-02-19

* [maintenance] Fix detect logic of delete_in_advance mode. [#26](https://github.com/embulk/embulk-output-bigquery/issues/26). @sonots thanks!

## 0.2.2 - 2016-02-15

* [new feature] Added template_table option. [#25](https://github.com/embulk/embulk-output-bigquery/pull/25). @joker1007 thanks!

## 0.2.1 - 2016-01-28

* [maintenance] Upgraded Embulk version to 0.8.1 [#22](https://github.com/embulk/embulk-output-bigquery/pull/22). @joker1007 thanks!
* [maintenance] Formatted code style by checkstyle [#23](https://github.com/embulk/embulk-output-bigquery/pull/23)

## 0.2.0 - 2016-01-26

* [new feature] Added mode parameters and support 4 modes(append, replace, replace_backup, delete_in_advance). [#20](https://github.com/embulk/embulk-output-bigquery/pull/20) [#21](https://github.com/embulk/embulk-output-bigquery/pull/21) @joker1007 thanks!

## 0.1.11 - 2015-11-16

* [maintenance] Change error result display for easy investigation. [#18](https://github.com/embulk/embulk-output-bigquery/pull/18)

## 0.1.10 - 2015-10-06

* [new feature] Added new auth method - json_keyfile of GCP(Google Cloud Platform)'s service account [#17](https://github.com/embulk/embulk-output-bigquery/pull/17)

## 0.1.9 - 2015-08-19

* [maintenance] Upgraded Embulk version to 0.7.1

## 0.1.8 - 2015-08-19

* [new feature] Supported mapreduce-executor. @frsyuki thanks! [#13](https://github.com/embulk/embulk-output-bigquery/pull/13)
* [maintenance] Fixed job_id generation logic [#15](https://github.com/embulk/embulk-output-bigquery/pull/15)
* [maintenance] Refactored [#11](https://github.com/embulk/embulk-output-bigquery/pull/11)

## 0.1.7 - 2015-05-20

* [new feature] Added allow_quoted_newlines option [#10](https://github.com/embulk/embulk-output-bigquery/pull/10)
* [maintenance] Upgraded embulk version to 0.6.8

## 0.1.6 - 2015-04-23

* [new feature] Added ignore_unknown_values option to job_id generation logic. [#9](https://github.com/embulk/embulk-output-bigquery/pull/9)

## 0.1.5 - 2015-04-23

* [new feature] Added ignore_unknown_values option.  [#8](https://github.com/embulk/embulk-output-bigquery/pull/8) @takus thanks!

## 0.1.4 - 2015-04-21

* [new feature] Added prevent_duplicate_insert option

## 0.1.3 - 2015-04-06

* [new feature] Added new auth method - pre-defined access token of GCE(Google Compute Engine)
* [maintenance] Updated Google provided libraries
  * http-client:google-http-client-jackson2 from 1.19.0 to 1.20.0
  * apis:google-api-services-bigquery from v2-rev193-1.19.1 to v2-rev205-1.20.0

## 0.1.2 - 2015-04-01

* [new feature] Changed bulk-load method from "via GCS" to direct-insert
* [new feature] added dynamic table creationg option
