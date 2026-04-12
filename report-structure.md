# Instrukce pro generování reportu kybernetické bezpečnosti

Tento dokument definuje strukturu, obsah a vizuální formátování závěrečného reportu.

## 1. Jazyk reportu
* Celý report musí být vypracován výhradně v **českém jazyce**.

## 2. Technické požadavky na formát (HTML/CSS)
* **Layout:** Vertikální slide-deck. Report je koncipován jako série na sebe navazujících snímků řazených pod sebou. Každý <section> musí mít nastaveno min-height: 100vh; a width: 100%;, aby vizuálně vyplnil celou plochu obrazovky.
* **Styling:** Moderní, responzivní design. Veškeré CSS musí být vloženo v tagu `<style>` uvnitř HTML hlavičky. **Nepoužívejte žádné externí knihovny** (jako Bootstrap nebo Tailwind), aby report fungoval offline.
* **Barvy a Branding:** * Musí vycházet z vizuální identity poskytovatele reportu. Žádné jiné visuální styly nejsou povoleny, pouze ty definované v pravidlech pro vizuální identitu poskytovatele reportu.
* **Overflow (Přetečení):** Pokud seznam subdomén nebo nálezů přesáhne kapacitu jednoho snímku, AI zobrazí pouze 5 nejdůležitějších položek a vytvoří na konci dokumentu sekci **Příloha (Appendix)**, kde budou vypsána všechna zbývající data.
* **Znaková sada reportu** musí být UTF-8: <meta charset="UTF-8">.

---

## 3. Struktura reportu

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

### Snímek 4 až 6: Detailní přehled nálezů
Podle počtu nálezů je možné využít 1 až 3 strany pro přehled. 
Pro každý identifikovaný problém (otevřené nebezpečné porty, expirující certifikáty, malware záznamy ve VirusTotal, chybějící DNS zabezpečení jako SPF/DMARC) uveďte:
1.  **Název nálezu**
2.  **Závažnost (Severity Score):** (Informativní / Nízká / Střední / Vysoká / Kritická)
3.  **Popis:** Co bylo nalezeno a proč je to riziko.
4.  **Navržená náprava:** Konkrétní technický krok k odstranění rizika.

### Snímek 5, 6 nebo 7 (dle Detailního přehled nálezů): Plán nápravy (Remediation Plan)
* Prioritizovaný seznam kroků "Krok za krokem".
* Zaměřte se na opravu nejzávažnějších nálezů jako první.

### Snímek 6, 7 nebo 8 (dle Detailního přehled nálezů): Závěrečná strana (Kontakt)
* **Poskytovatel reportu:** {{company_name}}
* **Kontaktní osoba:** {{contact_person}}
* **E-mail:** {{contact_email}}

---

### Příklad CSS pro horizontální layout (pro inspiraci agenta):
```css
body {
    font-family: sans-serif;
    margin: 0;
    overflow-x: auto;
    display: flex;
    scroll-snap-type: x mandatory;
    background: #f0f2f5;
}
section {
    flex: 0 0 100vw;
    height: 100vh;
    scroll-snap-align: start;
    padding: 40px;
    box-sizing: border-box;
    display: flex;
    flex-direction: column;
    justify-content: center;
}
.finding-card {
    background: white;
    border-left: 5px solid [PRIMARY_COLOR];
    padding: 15px;
    margin-bottom: 10px;
    border-radius: 4px;
}
```
