FROM python:3.7-slim

WORKDIR /app

RUN groupadd -r webservice && useradd --no-log-init -r -g webservice webservice

RUN pip install networkx dash plotly

COPY . .

USER webservice:webservice

# indicates the ports on which a container listens for connections
EXPOSE 8050

ENTRYPOINT ["python", "GraphAnalysis.py"]
CMD ["obj_dependency_data.csv"]
