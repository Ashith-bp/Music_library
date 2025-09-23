# Music Library (Python + MySQL)

**What**: A simple intermediate-level Music Library REST API using Flask and MySQL.

**Features**
- CRUD for Artists, Albums, Tracks, and Playlists
- Search tracks by title/artist/album
- Add tracks to playlists
- Pagination for list endpoints
- Sample SQL + sample data

**Requirements**
- Python 3.9+
- MySQL server (or MariaDB)
- `mysql-connector-python`

**Quick start (local)**
1. Create a Python virtualenv:
   ```bash
   python -m venv venv
   source venv/bin/activate     # on Windows: venv\Scripts\activate
   pip install -r requirements.txt
   ```
2. Create a MySQL database and user. Example SQL:
   ```sql
   CREATE DATABASE music_library;
   CREATE USER 'ml_user'@'localhost' IDENTIFIED BY 'ml_pass';
   GRANT ALL PRIVILEGES ON music_library.* TO 'ml_user'@'localhost';
   FLUSH PRIVILEGES;
   ```
3. Initialize schema and sample data:
   ```bash
   mysql -u ml_user -p music_library < db_init.sql
   ```
4. Copy `.env.example` -> `.env` and set DB credentials.
5. Run the app:
   ```bash
   export FLASK_APP=app.py
   flask run
   ```
   Or: `python app.py`

**API overview**
- `GET /artists` - list artists (supports `?page=&per_page=`)
- `POST /artists` - create artist `{"name": "..."}`
- `GET /albums`, `POST /albums`
- `GET /tracks`, `POST /tracks`, `GET /tracks/<id>`
- `GET /playlists`, `POST /playlists`, `POST /playlists/<id>/tracks`

**Docker**
- `docker-compose.yml` included for easier local testing.

**Notes**
- This project uses simple, explicit SQL through `mysql-connector-python` (no ORM) to keep dependencies minimal and illustrate SQL patterns.
