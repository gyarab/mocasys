# Ročníkový projekt -- Informační systém pro školní jídelny

Cílem práce bylo vytvořit počítačový systém pro správu zařízení hro- madného
stravování určený pro zaměstnance i strávníky. Systém řeší tvorbu jídel- níčku,
správu seznamu strávníků a jejich kont a volbu jídel ze strany strávníků.  Pro
tvorbu systému byly využity unikátní techniky a vlastní knihovny, které lze
dále využít pro další projekty.

## Instalace

Mocasys je komplexní projekt složený z několika částí, tudíž je instalace kom-
plikovaný proces zahrnující vícero programovacích jazyků a prostředí. Momen-
tálně je jediným podporovaným operačním systémem pro vývoj Mocasysu a spuš-
tění serverových částí GNU/Linux.

Tyto instrukce byly ověřeny na Arch Linuxu a balíčcích z května 2019. Návod
předpokládá, že máte stažené všechny repozitáře projektu ve struktuře složek
určené submoduly.

### Instalace Backendu

* Nejprve nainstalujte PostgreSQL verze 11 a vytvořte prázdné databázové
  schéma.
* Stáhněte, zkompilujte a nainstalujte rozšíření PostgreSQL temporal\_tables.
* Ve složce `mocasys-backend` spusťte skript `setup_db.sh`. Skriptu můžete dát
  další parametry, které budou předány použitému příkazu `psql`.

### Instalance Middleendu
* Nainstalujte Node.js a NPM.
* Upravte soubor `mocasys-middleend/config/default.json` tak, aby ob- sahoval
  správné nastavení pro připojení k databázi. Middleend využívá dvě databázová
  spojení, „middleend“ a „qdb“. „Middleend“ by měl být připo- jen pomocí
  uživatele, který má přístup k tabulkám `user_passwords_data` a
  `user_mifare_cards_current`. „Qdb“ používá uživatele uptest, který byl vytvořen
  skriptem `setup_db.sh`.
* Ve složce `mocasys-middleend` spusťte příkaz `npm install`, což nainstaluje NPM
  balíčky, a `npm run start`, což spustí server middleendu.

### Instalace Frontendu

* Nainstalujte SBT.
* Ve složce `mocasys-frontend` spusťte příkaz `sbt devel`, poté `devserver.py`,
  což spustí webserver hostující aplikaci.
* Navštivte ve webovém prohlížeči stránku `http://127.0.0.1:8080`.

## Autorská práva a licence

Momenálně nemají části projektu stanovenou licenci. Toto chápejte jako
implicitní zákaz všech využití těch částí, pokud není využití explicitně
povoleno (viz stranu `i` dokumentace). V blízké budoucnosti bude kód uveřejněn
pod FLOSS licencí.
