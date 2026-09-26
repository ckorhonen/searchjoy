# Repository guide

## Map and setup

Searchjoy is a Rails search-analytics engine. `lib/searchjoy/` owns tracking/model behavior; `lib/generators/searchjoy/` installs the host-app migration; `app/controllers/` and `app/views/` implement the dashboard; `config/routes.rb` defines engine routes.

Install gem development dependencies with `bundle install`. `searchjoy.gemspec` requires legacy Bundler ~> 1.3; no Ruby version or lockfile is pinned. The README describes Rails 3.1+ host integration, not a standalone app. `Rakefile` loads only Bundler gem tasks: `bundle exec rake build` packages the gem, but there is no test, lint, or dev-server task and no tracked test suite/CI.

For Ruby edits, syntax-check the changed file with `ruby -c path/to/file.rb` and add focused regression coverage where practical. Dashboard/generator behavior needs a disposable compatible Rails host with a test database; `rails generate searchjoy:install` and `rake db:migrate` modify that host. Preserve dashboard authentication and use synthetic searches/user IDs; do not migrate a real app or expose search history as a smoke test.

## Completion

Begin with `git status --short` and preserve unrelated edits. Carry authorized local work through relevant verification and repair without asking about routine reversible details. Report exact legacy dependency or host-app blockers, and continue independent work. For prose-only changes, inspect links/commands and run `git diff --check`. Close with changed paths, executed checks, and unverified host integration. Live database actions and gem publication require explicit task authorization.
