FROM jupyter/minimal-notebook

RUN mkdir -p src
WORKDIR /src

RUN pip install --upgrade pip==23.1.2
RUN pip install poetry==1.4.2 poetry-core==1.5.2

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