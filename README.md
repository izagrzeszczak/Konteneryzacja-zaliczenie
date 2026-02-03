# Zaliczenie – „Konteneryzacja i orkiestracja usług IT” 

Ten projekt uruchamia **4 niezależne usługi w kontenerach** z użyciem `docker compose`:
1. **PostgreSQL** – baza danych (kontener `db`)
2. **Adminer** – panel WWW do zarządzania bazą (kontener `adminer`) – dostępny z przeglądarki
3. **Nginx** – prosty serwer WWW z przykładową stroną (kontener `web`) – dostępny z przeglądarki
4. **Portainer CE** – panel WWW do zarządzania środowiskiem Docker (kontener `portainer`) – dostępny z przeglądarki

Spełnione wymagania:
- ✅ min. 4 kontenery
- ✅ min. 1 kontener z bazą danych (PostgreSQL)
- ✅ min. 1 kontener dostępny z zewnątrz (3: Nginx, Adminer, Portainer)
- ✅ konfiguracja w `docker-compose.yml`
- ✅ dokumentacja (ten plik)


---

## Wymagania wstępne

- Docker Desktop / Docker Engine + plugin `docker compose`
- System: Windows / Linux / macOS

Sprawdzenie:
```bash
docker --version
docker compose version
```

---

## Uruchomienie

W katalogu projektu:

```bash
docker compose up -d
docker compose ps
```

Zatrzymanie i usunięcie kontenerów:
```bash
docker compose down
```

Usunięcie danych (volumes) – **uwaga: skasuje dane bazy**:
```bash
docker compose down -v
```

---

## Dostęp do usług (lokalnie)

Po uruchomieniu:

- **Strona WWW (Nginx)**: http://localhost:8080  
- **Adminer**: http://localhost:8081  
- **Portainer**: http://localhost:9000  

### Adminer – dane logowania do bazy

Na ekranie logowania w Adminer ustaw:

- System: **PostgreSQL**
- Serwer: **db**
- Użytkownik: **student**
- Hasło: **student123**
- Baza: **demo**

---

## Szybki test działania (przykładowe polecenia)

### 1) Status kontenerów
```bash
docker compose ps
```

Przykładowy oczekiwany rezultat (nazwy mogą się różnić):
- `zaliczenie-db` – Up
- `zaliczenie-adminer` – Up
- `zaliczenie-web` – Up
- `zaliczenie-portainer` – Up

### 2) Logi PostgreSQL
```bash
docker logs zaliczenie-db --tail=30
```

W logach powinny pojawić się linie w stylu:
- `database system is ready to accept connections`

### 3) Sprawdzenie strony WWW
Wejdź w przeglądarce na **http://localhost:8080** – powinna pojawić się strona „Zaliczenie – działa!”.

---

## Struktura projektu

```
.
├─ docker-compose.yml
└─ nginx/
   └─ html/
      └─ index.html
```

