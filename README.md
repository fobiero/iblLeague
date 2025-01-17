# Interbase League (IBL)
Interbase league is a popular football festival based in Nairobi Kibera to be specific. The software acts as a catalyst to ensure the league runs smoothly and thus captures every tiny details.

[Django](https://www.djangoproject.com/) project template that we use at [KICINCO](https://kicinco.com).

Best suited for medium-sized and bigger apps that use JavaScript and React for frontend or single page web applications.
## Features

- Django-based backend

  - [Django](https://www.djangoproject.com/)
  - Separate settings for different environments (local/staging/production)
  - Python 3.6 or later
  - [SPA] Accessible from port `:8000` for local development
  - [PostgreSQL](https://docs.djangoproject.com/en/5.1/ref/databases/#postgresql-notes) - Structured database design for clean data fetch

- Frontend app with JavaScript (ES2015), React and SaaS

  - Latest JavaScript features from [ES2015](https://babeljs.io/docs/learn-es2015/) and beyond, transpiled with
    [Babel](https://babeljs.io/)
  - [React](https://facebook.github.io/react/) for fast modular user interfaces
  - [Sass](http://sass-lang.com/), [PostCSS](http://postcss.org/) and
  - [Webpack](https://webpack.github.io/) is used to bundle and minify JavaScript and styles

- Configs & Run

  - Docker / Docker Compose integration
  - Linting of Python, JavaScript and Sass code with [Prospector](http://prospector.landscape.io/),
    [ESLint](http://eslint.org/) and [stylelint](https://stylelint.io/)
  - Automated code-formatting using [black](https://black.readthedocs.io) and [prettier](https://prettier.io)
  - [py.test](http://pytest.org/) and [coverage](https://coverage.readthedocs.io/) integration
  - Deploy helpers, using [Ansible](https://www.ansible.com/)
  - Media files are stored in a CDN like S3 or Google Cloud Storage
  - Out-of-the-box configuration for nginx, gunicorn and logrotate
  - Includes [PyCharm](https://www.jetbrains.com/pycharm/) | [VSCode](https://code.visualstudio.com/) project config and cod formatter

## Usage

To use this template, first ensure that you have
[Django](https://docs.djangoproject.com/en/5.1/) available and installed.

After that, you should:

1. Install the requirements of the project template by running
   ```
   pip3 -m venv env
   ```
2. Activate the virtualenv 
   ```
   source ./env/bin/activate
   ```
3. Navigate to the directory where you'd like to create your project:
   ```
   cd /home/project_directory/
   ```
4. Run the following command to install all project packages and dependencies
   ```
    pip install -r requirements.txt
   ```
5. Once the virtual directory is activates, run
    ```
    python manage.py runserver (localhost:8000)
    ```

See README.md in the generated project for instructions on how to set up your development environment.

## Different frontend styles

### SPA

Isomorphic Javascript single-page application rendered with node and backed by Django Rest Framework. Enabled with `frontend_style == spa`.
During development and production separate node container is used to run and serve assets if needed.
Translations are done with [i18next](https://www.i18next.com/) and its companion library for React.

### Webapp

React powered application rendered with Django templates. This is the default option. Enabled with `frontend_style == webapp`.
During development separate container is used to build assets. In production, node built with multi-stage image.
Translations are done with Django JavaScriptCatalog.

## Project dependencies upgrade

First ensure you have a python3 interpreter with `django` installed.

To upgrade an existing project, change the current working directory to the root of the project you want to upgrade. i.e. `cd project-to-upgrade`. Ensure your have not checked out the `template` branch.

Then run `python ~/path/to/django-project-template/upgrade-template.py`

This will make a commit to the branch `template` in your project with the updates to the project template. Then merge the `template` branch.

## Applying codemods

First activate Python 3 interpreter with required dependencies and ensure `docker` is installed and working.

Change the current working directory to the root of the project you want to apply codemods for. i.e. `cd project-to-upgrade`.

Then run `python ~/path/to/django-project-template/upgrade-template.py --apply-frontend-codemods`

This will build custom docker image to update old frontend versions.

## Docker images

The template uses our own images for CI runs. One for the template itself and a second one
for generated projects. Both images are alpine based and contain python3, pip and some support
packages. The images are published to [repository container registry](https://gitlab.com/thorgate-public/django-project-template/container_registry) and also to [docker hub](https://hub.docker.com/u/thorgate).

The images are built in CI (from default branches only) and also updated every day via schedules.

**Project CI Image**

- [Dockerfile-ci](./utils/Dockerfile-ci)
- Image in repository registry: `registry.gitlab.com/thorgate-public/django-project-template/ci`
- Image in docker hub: `thorgate/django-template-ci`
  - [see online](https://hub.docker.com/r/thorgate/django-template-ci)

**Template CI Image:**

- [Dockerfile-base-ci](./utils/Dockerfile-base-ci)
- Image in repository registry: `registry.gitlab.com/thorgate-public/django-project-template/base-ci`
- Image in docker hub: `thorgate/django-template-base-ci`
  - [see online](https://hub.docker.com/r/thorgate/django-template-base-ci)
