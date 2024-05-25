1. Clone the Repository

2. Install the Required Libraries:

    pip install -r requirements.txt

3. Create and configure the PostgreSQL Database Connection in the main directory of project:

    {
    "user": "your_postgres_username",
    "password": "your_postgres_password",
    "database": "your_postgres_database"
    }

4. Run Docker Compose and access to the kafka container:

    1. docker-compose up
    2. docker exec -it kafka bash 

5. Create Kafka Topic inside of the container:

    kafka-topics --bootstrap-server kafka --create --topic kafka-workshop

6. Finally open two new terminals and run the following command:

    1. python consumer.py
    2. python producer.py
