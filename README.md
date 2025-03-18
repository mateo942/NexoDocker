# Insert Nexo SDK - Docker Image

## 📌 O projekcie

Ten projekt zawiera obraz Dockera z SDK dla Insert Nexo, co umożliwia łatwe uruchomienie i integrację z systemem Insert bez potrzeby instalacji dodatkowego oprogramowania na lokalnej maszynie.

## ❓ Co to jest Insert Nexo?

Insert Nexo to zestaw aplikacji biznesowych, takich jak Subiekt Nexo (system ERP), Rachmistrz Nexo (księgowość) czy Gratyfikant Nexo (kadry i płace). SDK pozwala na automatyzację i integrację tych systemów z innymi aplikacjami, np. e-commerce czy CRM.

## 🚀 Jak uruchomić kontener?

### Wymagania

- Zainstalowany Docker z kontenerami Windows
- Opcjonalnie: Docker Compose dla ułatwionej konfiguracji

### Tesowane na

- Microsoft Windows Server 2025 Standard 

### Uruchomienie kontenera

1. Pobierz obraz Dockera

```bash
docker pull ghcr.io/mateo942/nexo-sdk:<wersja_nexo>
```

2. Uruchom kontener:

```bash
docker run -it --rm ghcr.io/mateo942/nexodocker:<wersja_nexo> powershell
```

## 📂 Zawartość SDK

Całe SDK znajduje się w folderze C://InsertNexoSDK.

## 🤝 Współtworzenie

1. Fork repozytorium
2. Stwórz nową gałąź (git checkout -b feature-nazwa)
3. Wprowadź zmiany i zatwierdź (git commit -m 'Opis zmiany')
4. Wypchnij zmiany (git push origin feature-nazwa)
5. Otwórz Pull Request