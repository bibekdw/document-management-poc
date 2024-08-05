# POC with Liquibase and jOOQ Integration

This proof of concept project demonstrates the integration of Liquibase and jOOQ to manage database schema migrations and to facilitate query building in a Java application. Liquibase handles the database schema changes, while jOOQ is used to generate Java code from the database schema, enabling type-safe SQL query construction in the application.

## Prerequisites

Before you start, ensure you have the following installed:
- Java JDK 11 or newer
- Maven 3.6 or newer
- PostgreSQL Server (You can adjust the database configuration in `src/main/resources/liquibase.properties` as needed)

## Setting Up

To get started, clone the repository:

```bash
git clone https://github.com/bibekdw/document-management-poc.git
cd document-management-poc

## Database Configuration

Modify the `src/main/resources/application.properties` file with your database connection details:

```properties
changeLogFile=src/main/resources/db/changelog/db.changelog.yml
url=jdbc:postgresql://localhost:5432/doc_mgmt_poc
username=postgres
password=postgres
driver=org.postgresql.Driver

## Running Liquibase Migrations

Liquibase migrations are configured in src/main/resources/db/changelog/db.changelog.yml
. To apply migrations to your database, execute:

```bash
mvn liquibase:update

## Generating jOOQ Classes
Generate jOOQ classes from your database schema using the following Maven command:

```bash
mvn generate-sources

This will generate classes in the target/generated-sources directory.
