# Labbdokumentation

## Introduktion

Namn: Balac  
Kurs: Introduktion till yrkesrollen och grunderna i IT-infrastruktur  
Datum: 2026-09-22
Den här dokumentationen beskriver min virtuella labbmiljö med två virtuella Linux-maskiner. Jag kommer att dokumentera nätverkskonfiguration, kommandoradsarbete, Git och min användning av AI.

## Labbmiljö

Jag har skapat en virtuell labbmiljö i Oracle VirtualBox med två virtuella Linux-maskiner. Maskinerna är anslutna till samma interna nätverk som heter `LabNetwork`.
| Maskin | Hostname | IP-adress | Nätmask | Nätverkskort |
| --- | --- | --- | --- | --- |
| Desktop (lubu) | puppypc4393 | 192.168.1.51 | /24 (255.255.255.0) | eth0 |
| Server | Ubuntu-Server-Lab | 192.168.1.50 | /24 (255.255.255.0) | enp0s3 |

Jag testade kommunikationen från desktop till server med:

`ping -c 4 192.168.1.50`

Resultatet blev 4 skickade paket, 4 mottagna paket och 0 % packet loss. Det visar att maskinerna kan kommunicera med varandra på `LabNetwork`.

## CLI-arbete

Jag har arbetat med kommandoraden i Linux på mina virtuella maskiner.

### Linux

Jag använde Linux-terminalen för att skapa kataloger, filer, grupper och konfigurera rättigheter.

Jag skapade katalogen:

`mkdir -p /var/systementor/konsultdata`

Jag skapade filen:

`touch /var/systementor/konsultdata/anteckningar.txt`

Jag skapade gruppen:

`groupadd konsulter`

Jag kopplade gruppen till katalogen och filen:

`chgrp -R konsulter /var/systementor/konsultdata`

Jag satte rättigheten 750 på katalogen:

`chmod 750 /var/systementor/konsultdata`

Jag satte rättigheten 640 på filen:

`chmod 640 /var/systementor/konsultdata/anteckningar.txt`

Jag kontrollerade resultatet med:

`ls -la /var/systementor/konsultdata`

Resultatet visade att katalogen hade rättigheten `drwxr-x---` (750) och att `anteckningar.txt` hade rättigheten `-rw-r-----` (640). Gruppen var `konsulter`.

Jag använde även `ip addr show` för att kontrollera IP-adresser och `ping` för att testa kommunikationen mellan de virtuella maskinerna.

## AI-användning

Jag använde generativ AI för att få hjälp med Linux-kommandon och nätverkskonfiguration.

### Prompt

Jag frågade AI:

"Vad betyder Linux-rättigheterna 750 för en katalog och 640 för en fil?"

### AI:s svar

AI förklarade att:

- 750 betyder att ägaren får läsa, skriva och köra. Gruppen får läsa och köra. Andra användare har inga rättigheter.
- 640 betyder att ägaren får läsa och skriva. Gruppen får läsa. Andra användare har inga rättigheter.

### Min kontroll

Jag kontrollerade AI:s svar själv i Linux-terminalen med kommandot:

`ls -la /var/systementor/konsultdata`

Resultatet visade att katalogen hade `drwxr-x---`, vilket motsvarar 750, och att filen `anteckningar.txt` hade `-rw-r-----`, vilket motsvarar 640.

AI:s förklaring stämde alltså med resultatet i min labbmiljö. Jag är samtidigt medveten om att AI kan ge felaktiga eller gamla svar, därför kontrollerade jag informationen praktiskt innan jag använde den.

## Git och versionshantering

Jag använde Git för versionshantering av mitt projekt. Jag skapade ett lokalt Git-repository och gjorde flera commits under arbetets gång.

Mitt GitHub-repository:
https://github.com/balachmohammed/labbm-jli

Jag använde bland annat följande Git-kommandon:

- `git init` – skapade Git-repositoryt.
- `git add` – lade till ändringar.
- `git commit` – sparade olika versioner av arbetet.
- `git status` – kontrollerade projektets status.
- `git push` – skickade projektet till GitHub.
### Commit-historik

Mitt GitHub-repository innehåller flera commits som visar hur dokumentationen har utvecklats:

- `1871707` – Add files via upload
- `7252bb1` – Update Labbdokumentation.md
- `af5b83f` – Dokumentera nätverk och Linux CLI
- `f63119c` – Rätta labbdokumentationen

Jag kontrollerade versionshistoriken i GitHub. Historiken motsvarar resultatet som visas med kommandot `git log --oneline`, där varje rad visar commit-ID och commit-meddelande.
