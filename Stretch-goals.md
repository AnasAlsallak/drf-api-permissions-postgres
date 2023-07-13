# how to directly access postgres running inside container

To directly access PostgreSQL running inside a Docker container based on Ubuntu 20.04, and assuming that the PostgreSQL client tools are not already installed in the container, we follow these steps:

1. Find the container name or ID: Run the command `docker ps` to list all running containers. Identify the container running PostgreSQL and note its name or ID. in my case it's : 677911fd531f

2. Access the container's shell: Use the `docker exec` command to access the container's shell. Replace `CONTAINER_NAME` with the actual name or ID of the PostgreSQL container:

   ```bash
   docker exec -it 677911fd531f bash
   ```

3. Install PostgreSQL client tools: Inside the container's shell, use the following command to install the PostgreSQL client tools:

   ```bash
   apt-get update
   apt-get install postgresql-client
   ```

4. Connect to PostgreSQL: Once the client tools are installed, you can connect to PostgreSQL using the container's hostname or IP address. Use the following command: (in my case db)

   ```bash
   psql -h db -U postgres
   ```

   The `-U postgres` option specifies the username to connect as (assuming the default PostgreSQL username).

   I provided the password bc the authentication is enabled. (you can find it in the .yml file in the environment property)

   After successful authentication, you are now connected to the PostgreSQL database prompt where you can run SQL commands.
