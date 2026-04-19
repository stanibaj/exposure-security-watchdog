# Znalostní báze pro hodnocení kybernetického perimetru (v1.1)

Tato znalostní báze definuje metodiku pro identifikaci, kategorizaci a vyhodnocování bezpečnostních rizik zjištěných z externích zdrojů: DNS, Shodan, VirusTotal a Certificate Transparency (CT) logy. Slouží jako referenční rámec pro automatizované reporty i manuální expertní posouzení.

## 1. Definice úrovní závažnosti (Severity Levels) pro bezpečnostní nálezy

Každý nález v rámci perimetru musí být klasifikován podle jedné ze čtyř úrovní závažnosti. Tato klasifikace určuje prioritu nápravy a ovlivňuje výsledné bezpečnostní skóre organizace.

| Úroveň (Severity) | Barevný kód | Technický popis rizika | Požadovaná akce (SLA) |
| :--- | :--- | :--- | :--- |
| **CRITICAL** | Červená | Přímá cesta ke kompromitaci (RCE, nechráněná DB, aktivní malware). | Okamžitá náprava (v řádu hodin). |
| **HIGH** | Oranžová | Vysoké riziko zneužití, chybějící kritické bezpečnostní prvky. | Prioritní řešení (v řádu dnů). |
| **MEDIUM** | Žlutá | Konfigurační nedostatky, které vyžadují další řetězení útoků. | Standardní údržba. |
| **LOW** | Modrá | Odchylky od "best practices", informační nálezy bez přímého průniku. | Dle uvážení / dlouhodobý plán. |

---

## 2. Kategorizace a logika hodnocení nálezů dle datových zdrojů

V této sekci je definována logika hodnocení pro jednotlivé typy technických dat. Každý nález je interpretován v kontextu jeho původu.

### 2.1 Hodnocení rizik u DNS záznamů (Domain Name System)
DNS konfigurace odhaluje integritu doménové struktury a úroveň ochrany proti podvrhům (spoofingu).

| Nález (DNS Finding) | Popis a dopad | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Zone Transfer (AXFR)** | DNS server umožňuje stažení celé zóny. | **HIGH** | Útočník získá kompletní mapu interní a externí struktury. |
| **Chybějící SPF/DMARC** | Absence ochrany proti e-mailovému spoofingu. | **MEDIUM** | Vysoké riziko zneužití domény pro phishing jménem firmy. |
| **Subdomain Hijacking** | CNAME míří na neexistující cloudovou službu. | **HIGH** | Útočník může převzít kontrolu nad obsahem subdomény. |
| **Open Resolver** | Server odpovídá na rekurzivní dotazy komukoliv. | **MEDIUM** | Riziko zneužití pro DNS Amplification DDoS útoky. |
| **Slabá SPF politika** | SPF obsahuje ~all místo hard fail -all | **INFO** | Spam je přes chybu v autentizaci přesto doručen do mailové schránky. Tohle by mělo být pouze přechodné řešení. |

### 2.2 Hodnocení rizik v infrastruktuře dle dat ze Shodanu
Skenování Shodan identifikuje vystavené porty, zranitelnosti (CVE) a chyby v konfiguraci služeb běžících na IP adresách organizace.

| Nález (Shodan Finding) | Popis a dopad | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Exponovaný RDP/SMB** | Porty 3389 nebo 445 otevřené do internetu. | **CRITICAL** | Hlavní vstupní bod pro ransomware a brute-force útoky. |
| **Nezabezpečená DB** | MongoDB, Elasticsearch, Redis bez autentizace. | **CRITICAL** | Přímý únik dat bez nutnosti aktivního hackování. |
| **Zastaralý SW (CVE)** | Verze softwaru s veřejně dostupným exploitem. | **HIGH** | Závisí na kritičnosti CVSS skóre dané zranitelnosti. |
| **Self-signed Certifikát** | Služba používá nedůvěryhodný TLS/SSL certifikát. | **LOW** | Riziko MITM, indikuje nedostatečnou správu certifikátů. |
| **Telnet / FTP** | Použití nešifrovaných protokolů pro přenos dat. | **HIGH** | Možnost odposlechu přihlašovacích údajů v síti. |

### 2.3 Reputace a detekce malware v datech VirusTotal
Analýza využívá historická data a výsledky desítek antivirových enginů k posouzení reputace aktiv organizace.

| Nález (VT Finding) | Popis a dopad | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Malicious URL/IP** | Více než 5 enginů označuje asset za škodlivý. | **CRITICAL** | Doména je aktivně využívána pro C2 nebo phishing. |
| **Suspicious Activity** | 1-3 detekce u historických záznamů. | **MEDIUM** | Potenciální false positive nebo stará, neaktivní infekce. |
| **Asociace s malwarem** | Komunikace se známými vzorky škodlivého kódu. | **HIGH** | Indikace probíhající infiltrace nebo útoku. |

### 2.4 Asset Discovery a Shadow IT pomocí Certificate Transparency (CT)
Monitoring CT logů slouží k odhalení zapomenutých assetů a neschválených změn v certifikační autoritě.

| Nález (CT Finding) | Popis a dopad | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Dev/Stage subdomény** | Nalezeny záznamy jako `dev.*` nebo `test.*`. | **MEDIUM** | Tyto servery mívají často nižší úroveň zabezpečení. |
| **Expirovaný certifikát** | Certifikát v CT již není platný, ale DNS stále míří na IP. | **LOW** | Indikace opuštěného (zombie) assetu, který není spravován. |
| **Neočekávaná CA** | Certifikát vydala jiná než schválená autorita. | **MEDIUM** | Příznak Shadow IT nebo přípravy na phishingový útok. |

---

## 3. Metodika výpočtu finálního Security Health Score

Výsledné hodnocení (známka) odráží celkový stav bezpečnosti perimetru. Výpočet je založen na bodové penalizaci z výchozího stavu 100 bodů.

### Algoritmus výpočtu skóre
Finální skóre se vypočítá podle následujícího vzorce:

$$Score_{final} = \max(0, 100 - \sum (P_{crit}) - \sum (P_{high}) - \sum (P_{med}) - \sum (P_{low}))$$

**Váhy penalizací (P):**
- **CRITICAL**: -50 bodů
- **HIGH**: -20 bodů
- **MEDIUM**: -5 bodů
- **LOW**: -1 bod

*Kritická podmínka: Pokud existuje alespoň jeden nález úrovně **CRITICAL**, výsledná známka nesmí být lepší než **D**, bez ohledu na celkový počet bodů.*

### Klasifikace zdraví perimetru

| Body (Score) | Známka | Status | Interpretace pro management |
| :--- | :--- | :--- | :--- |
| **90 - 100** | **A** | Excelentní | Minimální nálezy, pouze informativní charakter. |
| **75 - 89** | **B** | Dobrý | Drobné konfigurační chyby (např. chybějící DMARC). |
| **50 - 74** | **C** | Varovný | Existují High nálezy, perimetr vyžaduje pozornost. |
| **25 - 49** | **D** | Špatný | Jeden nebo více Critical nálezů. Vysoké riziko průniku. |
| **0 - 24** | **F** | Kritický | Perimetr je pravděpodobně kompromitován. |

---

## 4. Pokyny pro expertní vyhodnocování a kontextualizaci

Při automatizovaném zpracování nebo manuálním review se držte těchto pravidel pro eliminaci šumu:

1. **Sémantická kontextualizace:** Port 443 (HTTPS) u webového serveru je **LOW** (info), ale u tiskárny nebo průmyslového kontroléru (PLC) je to **HIGH**.
2. **Agregace duplicit:** Více zranitelností na jedné IP adrese/službě se počítá jako **jeden incident** s nejvyšší zjištěnou prioritou, aby nedocházelo k umělé devalvaci skóre.
3. **Validace VirusTotal:** Důvěřujte primárně velkým vendorům (Microsoft, CrowdStrike, Kaspersky). Detekce od jediného, neznámého engine (např. Zillya) by měla být snížena na **LOW** nebo ignorována.
4. **Priorita DNS záznamů:** Chybějící DNSSEC je hodnoceno jako **LOW**, ale chybějící SPF u domény s aktivním MX záznamem je minimálně **MEDIUM/HIGH**.

## 5. Pokyny pro nápravu a dlouhodobý plán (Remediation Plan)

- **Implementace DMARC:** Vždy začínat s politikou `p=none`. Přechod na `p=quarantine` nebo `p=reject` je možný až po analýze reportů, aby nedošlo k zablokování legitimní komunikace.
- **Sanace Shadow IT:** Assety identifikované v CT logách nebo Shodanu, které nejsou v asset inventory, musí být buď zabezpečeny podle standardu, nebo vyřazeny z provozu (včetně smazání DNS záznamů).
