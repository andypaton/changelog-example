

Example repo that enforces a changelog

----
commit formats:

# Patch release
fix: correct API error handling

# Minor release
feat: add user profile endpoint

# Major release (breaking)
BREAKING CHANGE: auth flow changed completely

----
When someone opens a PR, GitHub provides:
github.event.pull_request.title

The pr-title.yml checks that the PR title matches Conventional Commit format, e.g.:

* ✅ feat: add login endpoint
* ✅ fix(api): handle timeout correctly
* ❌ updated stuff
* ❌ bug fix

----
# Example commit messages

## 🟢 PATCH release (x.x.+1). Triggered by bug fixes and small changes
fix: handle null response from API
fix(auth): prevent crash on expired token
perf: improve query performance for user lookup

## 🔵 MINOR release (x.+1.0). Triggered by new features (non-breaking)
feat: add user profile endpoint
feat(ui): add dark mode toggle

## 🔴 MAJOR release (+1.0.0). Triggered by breaking changes
feat!: remove legacy authentication flow

or

feat(auth): redesign login system
BREAKING CHANGE: login API no longer accepts username, only email

## ⚪ NO release
docs: update README examples
chore: update dependencies
test: add integration tests for API

----

# test it:

1. clone this repo
2. modify update.me.txt
3. git commit -a "any git commit message"
4. git push -u origin
5. on github create a PR
6. merge the PR
7. check the version has been updated