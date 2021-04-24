FROM python:3.7.10-slim-buster AS build

WORKDIR /build
RUN pip install --no-cache-dir pybind11
RUN apt update && apt install -y build-essential
COPY ./xo_app .
RUN python3 setup.py bdist_wheel

FROM python:3.7.10-slim-buster
WORKDIR /app
COPY --from=build /build/dist /tmp
RUN pip install /tmp/xo_app-0.1.0-cp37-cp37m-linux_x86_64.whl
COPY ./xo_server .
RUN pip install --no-cache-dir -r requirements.txt
EXPOSE 8080
CMD ["server.py"]
ENTRYPOINT ["python3"]
