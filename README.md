Ruby GitLab CI
===

This is GitLab CI templates for Ruby and Rails project.

## Requirements

GitLab 14.3+

## Usage

Include YAML in your `.gitlab-ci.yml` and apply `variables` and `rules` to control it.

```yaml
include:
  remote: https://github.com/elct9620/ruby-gitlab-ci/raw/main/rails.yml

variables:
  RUBY_VERSION: 2.7.4
  ASSETS_PRECOMPILE: 'yes'

brakeman:
  rules:
    - if: $CI_MERGE_REQUEST_ID
```

### Options

The options are usually based on the `rules` keyword to enable the task. If you overwrite the `rules` the variables are not necessary to configure.

| Type   | Environment Name    | Default | Description                                                          |
|--------|---------------------|---------|----------------------------------------------------------------------|
| Rails  | `ASSETS_PRECOMPILE` | Unset   | Run Rails Assets Precompile and save into artifacts                  |
| Docker | `DOCKER_ENABLED`    | Unset   | Run `docker build .`                                                 |
| Docker | `TRIVY_ENABLED`     | Unset   | Use [trivy](https://github.com/aquasecurity/trivy) to scan container |

## Roadmap

* [x] Ruby support
  * [x] Rubocop
  * [x] RSpec
  * [x] Bundler Audit
  * [x] Bundler Leak
* [ ] Rails support
  * [x] Brakeman
  * [x] Assets Precompile
  * [ ] S3 Upload for CDN
  * [ ] Database
    * [x] PostgreSQL
    * [ ] MySQL
* [ ] JavaScript support
  * [ ] ESLint
  * [x] Yarn Audit
  * [ ] Jest
* [ ] Containerize support
  * [x] Docker
  * [ ] Dockle
  * [x] Trivy Scanner
  * [ ] Registry
    * [x] GitLab Registry
    * [ ] AWS ECR
