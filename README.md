# Palworld Dedicated Server (Docker)

This repo contains everything you need to run a Palworld dedicated server using Docker Compose, with support for migrating existing config and save files.

## Structure

- `docker-compose.yml`: Docker Compose setup for the server.
- `config/`: Place your `PalWorldSettings.ini` here to migrate settings.
- `savegames/`: Place your Palworld save files here for migration.
- `scripts/`: Helper scripts for migration and management.

## Migration Instructions

1. **Initialize the Docker volume on your server:**
   - SSH into your server and run:
     ```sh
     docker compose up -d
     ```
2. **Copy your config and save files to the server:**
   - Use `scp` or `rsync` to upload your files to `config/` and `savegames/`.
3. **Run the migration script:**
   - On your server, run:
     ```sh
     ./scripts/migrate_saves.sh
     ```
   - This will copy your `.ini` and save files into the Docker volume.
4. **Restart the server container:**
   - ```sh
     docker compose restart
     ```

See `scripts/migrate_saves.sh` for details.
