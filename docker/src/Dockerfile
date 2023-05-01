FROM jupyter/minimal-notebook

RUN mkdir -p src
WORKDIR /src

RUN pip install --upgrade pip
RUN pip install poetry poetry-core

COPY notebooks /src/notebooks
COPY poetry.lock poetry.lock
COPY pyproject.toml pyproject.toml
COPY README.md README.md

RUN poetry config virtualenvs.create false
RUN poetry install -vvv

ENV PYTHONPATH .

RUN ipython profile create
COPY ipython_config.py /root/.ipython/profile_default/ipython_config.py

CMD ["jupyter", "notebook"]