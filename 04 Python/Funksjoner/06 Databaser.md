---
title: 06 Databaser
aliases: [Databaser, SQLite]
lang: nb-NO
authors:
  - Sondre Grønås
tags:
  - Definisjon
created: 2022-07-27 02:00:00
updated: 2022-08-13 20:26:04
---
# 06 Databaser

Forklaring kommer.

Eksempelkode:
```python
import sqlite3

DB = 'example.db'


def get_users():
    """Koble til DB og returner all data i en liste fra users i JSON/dictionary format"""
    conn = sqlite3.connect(DB)
    # row_factory = henter ut nøklene (username, password)
    conn.row_factory = sqlite3.Row
    data = conn.cursor().execute('SELECT * FROM users').fetchall()
    conn.close()
    # Konverter til en liste med data i JSON format
    # [
    #   {key1: value, key2: value},
    #   {key1: value, key2: value}
    # ]
    return [dict(ix) for ix in data]


if __name__ == '__main__':
    """Koble til, eller opprett database DB"""
    conn = sqlite3.connect(DB)

    # Lag peker (cursor)
    # cursor er definisjonen på der man skriver tekst
    cur = conn.cursor()

    # Lag en databasetabell, hvis den ikke eksisterer (Skriv følgende tekst på cursor)
    cur.execute("CREATE TABLE IF NOT EXISTS users"
                "(username text,"
                "password text,"
                "UNIQUE(username))"  # Definer verdier som ikke kan være like
                )

    try:
        # Forsøk å legg til bruker
        cur.execute("INSERT INTO users VALUES ('Test', 'abc123')")
    except sqlite3.IntegrityError as e:
        print(e)  # Hvis bruker allerede eksisterer: UNIQUE constraint failed: users.username

    # Alternativt kan "OR IGNORE" benyttes:
    cur.execute("INSERT OR IGNORE INTO users VALUES ('Test', 'abc123')")

    # Fullfør endringer
    conn.commit()

    # Lukk database
    conn.close()

    # Hent ut JSON format fra tabell 'users'
    users = get_users()

    # Print resultatet
    print(users)  # {'username': 'Test', 'password': 'abc123'}

    # Itererer individuelle brukere (hvis tabell har flere brukere)
    for user in users:
        print(user['username'])  # Test

```