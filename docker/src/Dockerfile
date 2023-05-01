FROM jupyter/minimal-notebook

RUN mkdir -p src
WORKDIR /src

COPY main.py /src/main.py
COPY notebooks /src/notebooks

RUN pip install --upgrade pip
RUN pip install poetry poetry-core

COPY poetry.lock poetry.lock
COPY pyproject.toml pyproject.toml
COPY README.md README.md

RUN poetry config virtualenvs.create false
RUN poetry install -vvv

ENV PYTHONPATH .
RUN ipython profile create
COPY ipython_config.py /root/.ipython/profile_default/ipython_config.py

CMD ["jupyter", "notebook"]