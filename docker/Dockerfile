FROM python:3.7.10-slim-buster AS build

WORKDIR /build
RUN pip install --no-cache-dir pybind11
RUN apt update && apt install -y build-essential
COPY ./xo_app .
RUN python3 setup.py bdist_wheel

FROM python:3.7.10-slim-buster
WORKDIR /app
COPY --from=build /build/dist /tmp
CMD "/bin/bash"