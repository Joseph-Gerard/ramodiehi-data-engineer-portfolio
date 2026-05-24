
ramodiehi-data-engineer-portfolio/
│
├── README.md
├── requirements.txt
├── .gitignore
├── docker-compose.yml
│
├── assets/
│   ├── architecture-diagrams/
│   ├── screenshots/
│   └── profile-banner.png
│
├── projects/
│   │
│   ├── rewards-loyalty-platform/
│   │   ├── airflow/
│   │   ├── etl/
│   │   ├── sql/
│   │   ├── dashboards/
│   │   └── README.md
│   │
│   ├── warehouse-delivery-streaming/
│   │   ├── kafka-producers/
│   │   ├── kafka-consumers/
│   │   ├── monitoring/
│   │   └── README.md
│   │
│   └── upholstery-customization-platform/
│       ├── apis/
│       ├── automation/
│       ├── database/
│       └── README.md
│
├── architecture/
│   ├── kafka-streaming-architecture.md
│   ├── etl-pipeline-architecture.md
│   └── cloud-data-platform.md
│
├── scripts/
│   ├── api_ingestion.py
│   ├── kafka_producer.py
│   ├── kafka_consumer.py
│   └── data_cleaning.py
│
└── docs/
    ├── certifications.md
    ├── technical-skills.md
    └── career-objective.md
    pandas
requests
apache-airflow
kafka-python
psycopg2-binary
sqlalchemy
pyspark
boto3
flask
fastapi
docker

version: '3'

services:

  zookeeper:
    image: confluentinc/cp-zookeeper:latest
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181

  kafka:
    image: confluentinc/cp-kafka:latest
    ports:
      - "9092:9092"
    environment:
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092
    depends_on:
      - zookeeper

  postgres:
    image: postgres:15
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: admin
      POSTGRES_DB: datawarehouse
    ports:
      - "5432:5432"
