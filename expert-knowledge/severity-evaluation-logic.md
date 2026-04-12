# Znalostní báze pro hodnocení kybernetického perimetru (v1.0)

Tato znalostní báze definuje standardy pro vyhodnocování nálezů z DNS, Shodanu, VirusTotalu a Certificate Transparency (CT) logů.

## 1. Definice úrovní závažnosti (Severity Levels)

| Úroveň | Barevný kód | Popis | Akce |
| :--- | :--- | :--- | :--- |
| **CRITICAL** | Červená | Přímá cesta ke kompromitaci (RCE, nechráněná DB, aktivní malware). | Okamžitá náprava (v řádu hodin). |
| **HIGH** | Oranžová | Vysoké riziko zneužití, chybějící kritické bezpečnostní prvky. | Prioritní řešení (v řádu dnů). |
| **MEDIUM** | Žlutá | Konfigurační nedostatky, které vyžadují další řetězení útoků. | Standardní údržba. |
| **LOW** | Modrá | Odchylky od "best practices", informační nálezy. | Dle uvážení / dlouhodobý plán. |

---

## 2. Kategorizace nálezů dle datových zdrojů

### 2.1 DNS Záznamy (Domain Name System)
DNS odhaluje konfigurační integritu a ochranu proti podvrhům.

| Nález | Popis | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Zone Transfer (AXFR)** | DNS server umožňuje stažení celé zóny. | **HIGH** | Útočník získá mapu celé interní struktury. |
| **Chybějící SPF/DMARC** | Doména nemá nastavenou ochranu proti spoofingu. | **MEDIUM** | Vysoké riziko zneužití pro phishing jménem firmy. |
| **Subdomain Hijacking** | CNAME záznam míří na neexistující službu (např. Azure, GitHub). | **HIGH** | Útočník může převzít kontrolu nad subdoménou. |
| **Open Resolver** | DNS server odpovídá na rekurzivní dotazy komukoliv. | **MEDIUM** | Riziko zneužití pro DNS Amplification DDoS útoky. |

### 2.2 Shodan (Služby a infrastruktura)
Shodan identifikuje vystavené porty, zranitelnosti a verze software.

| Nález | Popis | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Exponovaný RDP/SMB** | Porty 3389 nebo 445 otevřené do internetu. | **CRITICAL** | Hlavní vstupní bod pro ransomware (Brute force/Exploit). |
| **Nezabezpečená DB** | MongoDB, Elasticsearch, Redis bez autentizace. | **CRITICAL** | Přímý únik dat bez nutnosti hackování. |
| **Zastaralý SW (CVE)** | Detekovaná verze s veřejným exploitem (např. starý Apache). | **HIGH** | Závisí na CVSS skóre dané zranitelnosti. |
| **Self-signed Certifikát** | Služba používá nedůvěryhodný certifikát. | **LOW** | Riziko MITM, ale často jde o administrativní rozhraní. |
| **Telnet / FTP** | Nešifrované protokoly pro přenos hesel. | **HIGH** | Odposlech přihlašovacích údajů v síti. |

### 2.3 VirusTotal (Reputace a malware)
Analýza historických dat a detekce antivirovými engine.

| Nález | Popis | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Malicious URL/IP** | Více než 5 enginů označuje doménu jako škodlivou. | **CRITICAL** | Doména je aktivně využívána pro C2 server nebo phishing. |
| **Suspicious Activity** | 1-3 detekce u historických záznamů. | **MEDIUM** | Může jít o false positive nebo starou infekci. |
| **Asociace s malwarem** | Doména komunikuje se známými vzorky malwaru. | **HIGH** | Indikace probíhajícího útoku nebo infiltrace. |

### 2.4 Certificate Transparency (Asset Discovery)
CT logy slouží k odhalení "zapomenutých" subdomén.

| Nález | Popis | Severita | Logika hodnocení |
| :--- | :--- | :--- | :--- |
| **Dev/Stage subdomény** | Nalezeny domény jako `dev.firma.cz`, `test.firma.cz`. | **MEDIUM** | Tyto servery mívají slabší zabezpečení než produkce. |
| **Expirovaný certifikát** | Certifikát nalezený v CT již není platný, ale DNS míří na IP. | **LOW** | Indikace opuštěného (zombie) assetu. |
| **Neočekávaná CA** | Certifikát vydala jiná autorita než obvykle (např. Let's Encrypt místo Digicert). | **MEDIUM** | Může jít o Shadow IT nebo přípravu útočníka na phishing. |

---

## 3. Výpočet finálního Security Health Score

Finální zdraví domény není prostým průměrem, ale odvíjí se od **nejzávažnějšího nálezu**.

### Metodika výpočtu (Algoritmus):
1. **Základní skóre:** 100 bodů.
2. **Srážky za nálezy:**
   - Každý **CRITICAL**: -50 bodů (limitováno na min. 0).
   - Každý **HIGH**: -20 bodů.
   - Každý **MEDIUM**: -5 bodů.
   - Každý **LOW**: -1 bod.
3. **Váhová korekce:** Pokud existuje alespoň jeden CRITICAL nález, výsledná známka nemůže být lepší než **D (Nedostatečná)**, bez ohledu na počet bodů.

### Klasifikace zdraví:

| Body | Známka | Status | Interpretace |
| :--- | :--- | :--- | :--- |
| **90 - 100** | **A** | Excelentní | Minimum nálezů, pouze informativní low priority věci. |
| **75 - 89** | **B** | Dobrý | Drobné konfigurační chyby (např. chybějící DMARC). |
| **50 - 74** | **C** | Varovný | Existují High nálezy, perimetr vyžaduje pozornost. |
| **25 - 49** | **D** | Špatný | Jeden nebo více Critical nálezů. Vysoké riziko průniku. |
| **0 - 24** | **F** | Kritický | Perimetr je pravděpodobně již kompromitován nebo zcela otevřen. |

---

## 4. Pokyny vyhodnocování

Při generování reportu se drž těchto pravidel, aby nedocházelo k nadhodnocování/podhodnocování:

1.  **Kontextualizace:** Ne každý otevřený port je chyba. Port 80/443 u webového serveru je **LOW** (informační), port 443 u tiskárny je **HIGH**.
2.  **Agregace:** Pokud Shodan najde 10 otevřených portů s podobnou zranitelností na jedné IP, nepočítej to jako 10 kritických chyb, ale jako jeden **High/Critical incident** s deseti vektory.
3.  **Falešná pozitiva (VirusTotal):** Pokud doménu označuje pouze jeden neznámý antivirus (např. "Zillya" nebo "CMC"), ignoruj to nebo sniž severitu na **LOW**. Důvěřuj velkým hráčům (Kaspersky, Microsoft, CrowdStrike).
4.  **Priorita DNS:** Chybějící DNSSEC je **LOW**, ale chybějící SPF u domény, která posílá maily, je **MEDIUM/HIGH**.

## 5. Pokyny pro plán na odstranění nedostatků
- Pokud chybí DMARC, je lepší začít s P=none a monitorovat. Bez tohoto reportingu nebudeme moci vědět, jestli bude přechod na P=quarantine nezpůsobí problémy s doručováním emailů.
