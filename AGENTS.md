# Repository Guidelines

## Project Structure & Module Organization
- `_config.yml` holds global site settings; `index.md` is the main page entry.
- `_data/*.yml` stores resume content (for example: `experience.yml`, `projects.yml`, `education.yml`).
- `_includes/` contains reusable Liquid partials; `_layouts/default.html` defines the base page shell.
- `_sass/` stores style partials; `assets/main.scss` is the compiled stylesheet entrypoint.
- `images/` and `cv/` contain static assets.
- `_test/` contains a fixture config and sample data used by CI build checks.
- `lib/` and `modern-resume-theme.gemspec` are for gem packaging; `scripts/` contains release helpers.

## Build, Test, and Development Commands
- `bundle install`: install Ruby dependencies from `Gemfile`.
- `bundle exec jekyll serve`: run a local dev server at `http://localhost:4000`.
- `bundle exec jekyll build --config _test/_config.yml`: build the CI fixture site into `_site`.
- `bundle exec htmlproofer ./_site --disable-external`: validate generated HTML and internal links.
- `./scripts/bump-version.sh` and `./scripts/merge-downstream.sh`: maintainer-oriented release/merge automation.

## Coding Style & Naming Conventions
- Use 2-space indentation and avoid tabs.
- Keep includes focused and reusable; prefer editing `_includes/*.html` over duplicating markup.
- Use lowercase, descriptive file names and preserve existing directory conventions.
- Keep YAML keys consistent with template expectations (for example: `job_title`, `dates`, `description`).
- Prefer concise Markdown in `index.md`; keep structured content in `_data/*`.

## Testing Guidelines
- Before opening a PR, run the build and link checks locally (`jekyll build` + `htmlproofer`).
- If you change rendering logic or data shape, update `_test/_data` and `_test/_config.yml` to match.
- There is no strict coverage percentage; a clean local build and proofer run is the minimum bar.

## Commit & Pull Request Guidelines
- Existing history often uses short lowercase subjects (for example `update`), but prefer specific imperative commits (for example `update projects section links`).
- Keep each commit scoped to one change.
- PRs should include: summary, reason, linked issue (if applicable), validation commands run, and screenshots for visible UI changes.
- Follow `CONTRIBUTING.md` branch guidance: bug fixes from `master`, new features from `develop`.
