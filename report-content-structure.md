# Instrukce pro generování reportu kybernetické bezpečnosti

Tento dokument definuje strukturu a obsah závěrečného reportu.

## 1. Jazyk reportu
* Celý report musí být vypracován výhradně v **českém jazyce**.

## 2. Struktura reportu

### Snímek 1: Úvodní strana
* **Název:** Report bezpečnostního perimetru
* **Analyzovaná doména:** {{domain_name}}
* **Datum vypracování:** {{current_date}}

### Snímek 2: Manažerské shrnutí (Executive Summary)
* Stručný odstavec shrnující celkový stav perimetru na základě analýzy DNS, Shodan a VirusTotal.
* **Skóre zdraví domény:** Jasné vizuální hodnocení pomocí jediné hodnoty.

### Snímek 3: Přehled útočné plochy (Attack Surface Overview)
* **Nalezené subdomény:** Seznam unikátních subdomén z CT listů a DNS.
* **Zapojené technologie a poskytovatelé:** Identifikace infrastruktury (např. "E-mail: Microsoft 365", "Hosting: AWS", "CDN: Cloudflare").
* **Nelezené služby dostupné z veřejného internetu**

### Snímek 4 [+ volitelně další]: Detailní přehled nálezů
Podle počtu nálezů je možné využít 1 až 3 strany pro přehled. 
Pro každý identifikovaný problém (otevřené nebezpečné porty, expirující certifikáty, malware záznamy ve VirusTotal, chybějící DNS zabezpečení jako SPF/DMARC) uveďte:
1.  **Název nálezu**
2.  **Závažnost (Severity Score):** (Informativní / Nízká / Střední / Vysoká / Kritická)
3.  **Popis:** Co bylo nalezeno a proč je to riziko.
4.  **Navržená náprava:** Konkrétní technický krok k odstranění rizika.

### Snímek N-2: Plán nápravy (Remediation Plan)
* Prioritizovaný seznam kroků "Krok za krokem".
* Zaměřte se na opravu nejzávažnějších nálezů jako první.

### Snímek N-1: Závěrečná strana (Kontakt)
* **Poskytovatel reportu:** {{company_name}}
* **Kontaktní osoba:** {{contact_person}}
* **E-mail:** {{contact_email}}
* **Webové stránky:** {{website_domain_name}}


### Snímek N: Příloha (Technical Appendix)
**Nadpis: Podrobný technický výpis dat které jsou příliš dlouhé pro hlavní část reportu.**
