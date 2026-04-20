# liquibase-hello-db
## Install liquibase
### MacOs
````bash
brew install --cask liquibase-community
````
## 1. Create your DB objects in changelogs/*.yaml


## 2. Credentials config
Never commit your credentials to github!

### Option 1 : .env file
Create a new .env file in your root folder and add variables to it : 
````bash 
touch .env
# Add variables to .env
DB_URL=jdbc:postgresql://localhost:5432/your_db_name
DB_USERNAME=postgres
DB_PASSWORD=your_password_here
  ````
### Option 2 : terminal
Run the following in your terminal :
````bash 
export DB_URL="jdbc:postgresql://localhost:5432/postgres"
export DB_USERNAME="postgres"
export DB_PASSWORD="postgres"
  ````
## Download the correct jdbc drivers 
(Go AI it if you don't know what that means :D )
For Postgres that can be found here 
 <a>https://jdbc.postgresql.org/</a>

## 3. Local Execution
Ensure the db executes correctly before deploying to other environments
To run locally  :
````bash 
liquibase \
  --changelog-file=changelog-master.yaml \
  --url="$DB_URL" \
  --username="$DB_USERNAME" \
  --password="$DB_PASSWORD" \
  --driver=org.postgresql.Driver \
  --classpath=./lib/postgresql-42.7.10.jar\
  update

  # If you made a mistake (locally only) run :
  liquibase clear-checksums

  ````

