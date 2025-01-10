FROM python:3.8-slim AS build

WORKDIR /app
COPY requirements.txt ./
RUN echo "Installing packages" &&pip install --no-cache-dir -r requirements.txt && pip list

COPY . . 

RUN echo "Verifying installation and app files" && ls -l /app && pip list

FROM python:3.8-slim AS runtime
WORKDIR /app
COPY --from=build /usr/local/lib/python3.8/site-packages /usr/local/lib/python3.8/site-packages
COPY --from=build /usr/local/bin /usr/local/bin

COPY . .
RUN ls -l && cd app && ls -l

EXPOSE 5000
ENTRYPOINT ["python", "app/main.py"]



