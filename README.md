JUNTOS:

The Juntos fork maintains the master branch to only take updates from the origin repo. For instructions on updating master from collectiveidea, see [How do I update a GitHub forked repository?](https://stackoverflow.com/questions/7244321/how-do-i-update-a-github-forked-repository)

The branch juntos_master is used as our production branch. To make Juntos changes, branch from juntos_master and do a pull request with a hacked URL like:  https://github.com/JuntosFinanzas/delayed_job_active_record/compare/juntos_master...<dev_branch>?expand=1

Mercury Gemfile is set up to use the juntos_master branch. We should never merge from juntos_master to master. Master sould always match collectiveidea and when we take updates from them, we need to then manually merge from our master to juntos_master.

**If you're viewing this at https://github.com/collectiveidea/delayed_job_active_record,
you're reading the documentation for the master branch.
[View documentation for the latest release
(4.1.7).](https://github.com/collectiveidea/delayed_job_active_record/tree/v4.1.7)**

# DelayedJob ActiveRecord Backend

[![Gem Version](https://img.shields.io/gem/v/delayed_job_active_record.svg)](https://rubygems.org/gems/delayed_job_active_record)
![CI](https://github.com/collectiveidea/delayed_job_active_record/workflows/CI/badge.svg)
[![Coverage Status](https://img.shields.io/coveralls/collectiveidea/delayed_job_active_record.svg)](https://coveralls.io/r/collectiveidea/delayed_job_active_record)

## Installation

Add the gem to your Gemfile:

    gem 'delayed_job_active_record'

Run `bundle install`.

If you're using Rails, run the generator to create the migration for the
delayed_job table.

    rails g delayed_job:active_record
    rake db:migrate

## Problems locking jobs

You can try using the legacy locking code. It is usually slower but works better for certain people.

    Delayed::Backend::ActiveRecord.configuration.reserve_sql_strategy = :default_sql

## Upgrading from 2.x to 3.0.0

If you're upgrading from Delayed Job 2.x, run the upgrade generator to create a
migration to add a column to your delayed_jobs table.

    rails g delayed_job:upgrade
    rake db:migrate

That's it. Use [delayed_job as normal](http://github.com/collectiveidea/delayed_job).
