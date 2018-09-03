{% include 'misc/header.py' %}

LABEL maintainer="{{ cookiecutter.author_email }}"

LABEL description="{{ cookiecutter.description }}"

FROM {{ cookiecutter.project_shortname }}-base:latest

USER 0

COPY ./ ${WORKING_DIR}/src
WORKDIR ${WORKING_DIR}/src
COPY ./docker/uwsgi/ ${INVENIO_INSTANCE_PATH}

RUN chown -R invenio:invenio ${WORKING_DIR}

USER 1000

# workaround
RUN npm uninstall --prefix `pipenv --venv` --silent -g node-sass clean-css uglify-js requirejs

RUN ./scripts/bootstrap --deploy

