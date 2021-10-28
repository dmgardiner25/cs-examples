FROM python:3.8-slim-bullseye AS build-stage
RUN apt-get update && apt-get install -y --no-install-recommends gcc
RUN python -m venv /venv
ENV PATH=/venv/bin:$PATH
RUN pip install pyrsistent

FROM python:3.8-slim-bullseye AS runtime-stage
RUN apt-get update && apt-get -y upgrade
COPY --from=build-stage /venv /venv
ENV PATH=/venv/bin:$PATH
ENTRYPOINT ["python", "-c", "import pyrsistent; print(pyrsistent.__file__)"]