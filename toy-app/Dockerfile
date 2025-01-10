FROM python:3.8-slim AS build

WORKDIR /app
COPY requirements.txt ./
RUN pip3 install --no-cache-dir -r requirements.txt && \
    pip3 list

COPY ./ ./
COPY . . 


FROM python:3.8-slim AS runtime
WORKDIR /app
COPY --from=build /usr/local/lib/python3.8/site-packages /usr/local/lib/python3.8/site-packages
COPY --from=build /usr/local/bin /usr/local/bin

COPY ./ ./
COPY . . 

RUN pip3 list

EXPOSE 5000
ENTRYPOINT ["python3", "app/main.py"]

RUN pip3 list
