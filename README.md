# AutoPoint – Online rezervační systém pro autoservis

* **Předmět:** Úvod do softwarového inženýrství
* **Autor:** Ruslan Naumov
* **Repozitář:** Https://github.com/RuslanNum/CUSI26.git

---

## 1. Stručný popis projektu
AutoPoint je jednoduchá webová aplikace pro motoristy a menší autoservisy. Cílem je zbavit se zdlouhavého domlouvání termínů po telefonu. Zákazník si přes web vybere požadovaný úkon (přezutí pneumatik, výměna oleje, kontrola brzd), zvolí volný termín a po přistavení auta může online sledovat aktuální stav opravy. Servis má k dispozici přehlednou nástěnku s kalendářem a seznamem zakázek.

---

## 2. Business požadavky
* **Online rezervace 24/7:** Možnost objednat se kdykoliv bez nutnosti telefonovat do servisu během pracovní doby.
* **Přehlednost pro zákazníka:** Řidič v aplikaci vidí odhadovanou cenu a aktuální stav zakázky (nemusí zjišťovat, zda je auto už hotové).
* **Efektivní plánování v servisu:** Omezení překrývání termínů a rovnoměrné rozvržení práce na dílně.
* **Historie oprav:** Každé auto má přehled dříve provedených úkonů (elektronická servisní historie).

---

## 3. Systémové požadavky

### Uživatelské role
* **Zákazník:** Prohlíží služby, spravuje svá auta, vytváří rezervace a sleduje stav zakázky.
* **Mechanik / Technik:** Vidí denní rozpis, mění stavy zakázek a zapisuje hotové úkony.
* **Admin:** Spravuje otevírací dobu servisu, ceník služeb a uživatelské účty.

### Funkční požadavky
1. **Správa profilu a vozidel:** Uživatel si do profilu může uložit svá auta (SPZ, značka, model, rok výroby).
2. **Rezervační formulář:** Výběr konkrétní služby ze seznamu a volba volného data a času.
3. **Sledování stavu opravy:** Stav zakázky v reálném čase:
   * *Nová rezervace* $\rightarrow$ *Potvrzeno servisem* $\rightarrow$ *V servisu (probíhá oprava)* $\rightarrow$ *Hotovo k vyzvednutí*.
4. **Správa zakázek pro servis:** Jednoduchá tabulka / kalendář pro mechaniky s možností změny stavu zakázky jedním kliknutím.

### Nefunkční požadavky
* **Responzivita:** Aplikace musí fungovat pohodlně na počítači i na mobilním telefonu.
* **Rychlost:** Běžné načtení stránek a odeslání rezervace do 1 sekundy.
* **Bezpečnost:** Hesla uživatelů budou bezpečně zahashována v databázi.

---

## 4. Zvolený TechStack
* **Programovací jazyk & Backend:** Python (FastAPI) – moderní, přehledný a rychlý framework s automatickou dokumentací API.
* **Frontend:** HTML5, CSS (Tailwind CSS) a JavaScript – jednoduché a čisté rozhraní bez zbytečné složitosti.
* **Databáze:** SQLite pro vývoj (v případě potřeby PostgreSQL pro produkci).
* **Verzovací systém:** Git a GitHub (práce ve větvích, přehledná historie commitů).
* **Dokumentace:** Markdown přímo v repozitáři (`README.md`, složka `/docs` pro budoucí UML diagramy).

---

## 5. Scrum přístup a organizace práce
* **Iterace / Sprinty:** Vývoj bude rozdělen do dvoutýdenních sprintů.
* **Správa úkolů:** GitHub Projects (jednoduchá Kanban nástěnka se sloupci *To Do*, *In Progress*, *Done*).
* **Plán:**
  * **Iterace 0:** Zadání, specifikace požadavků a architektury (tento dokument).
  * **Iterace 1:** Návrh databáze, UML diagramy (Use Case, Class diagram).
  * **Další iterace:** Implementace REST API, frontend formulářů a propojení systému.
