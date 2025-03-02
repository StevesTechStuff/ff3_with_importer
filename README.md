### README for Firefly III and Importer Docker Setup (Portainer)

#### Prerequisites
1. Ensure **Portainer** is installed and running on your Docker host.
2. Have the `docker-compose.yml` and `.env` files ready.
3. Use [random.org/strings](https://www.random.org/strings/) to generate secure, 32-character random strings.

---

#### Steps to Deploy with Portainer

1. **Access Portainer**
   - Log in to your Portainer dashboard.

2. **Create a New Stack**
   - Navigate to the **Stacks** section and click **Add Stack**.
   - Name the stack (e.g., `firefly`).

3. **Upload the Compose File**
   - Select the **Upload** option and upload the `docker-compose.yml` file.

4. **Load Environment Variables**
   - Check the box for **Load environment variables from .env file**.
   - Upload the `.env` file.

5. **Generate Secure Strings**
   - Go to [random.org/strings](https://www.random.org/strings/) and generate three secure, 32-character strings.
   - Replace the following in Portainer:
     - `ROOT_PASSWORD=String1` with a generated string.
     - `APP_KEY=String2` with another generated string.
     - `STATIC_CRON_TOKEN=String3` with a third generated string.
     - 'DB_PASSWORD' with the forth generated string.

6. **Update Additional Variables**
   - Set `TZ` to your desired timezone (e.g., `America/New_York`).
   - Set 'FIREFLY_III_URL' to your servers address.


7. **Launch the Stack**
   - Click **Deploy the Stack** to start the services.

---

#### Post-Launch Configuration

1. **Spin Up the Containers**
   - Ensure all services (database, Firefly III, importer, etc.) are running.

2. **Configure the Importer**
   - Browse to the importer interface (e.g., `http://<your-docker-host>:8181`).
   - Copy the **Callback URL** provided by the importer.

3. **Set Up Firefly III OAuth**
   - Browse to Firefly III (e.g., `http://<your-docker-host>:8080`).
   - Register an account if not already done.
   - Navigate to **Options > Profile**.
   - Open the **OAuth** tab.
   - Create a new client:
     - Give it a **Name**.
     - Paste the **Callback URL** from the importer.
     - Uncheck the **Confidential** option.

4. **Generate and Configure the Client ID**
   - Firefly III will generate a **Client ID**.
   - Copy the **Client ID** and paste it into the importer interface.

5. **Authorize the Client ID**
   - Authorize the client in the importer to establish the connection.

6. **Ready for File Import**
   - Once authorization is complete, the importer is ready to process files.

---

#### Notes

- **Access Services**:
  - Firefly III: `http://<your-docker-host>:8080`
  - Importer: `http://<your-docker-host>:8181`

- **Persistent Volumes**:
  - Data is stored in `firefly_data` and `firefly_db` volumes.

- **Security**:
  - Always use strong, unique passwords and keys for environment variables.




