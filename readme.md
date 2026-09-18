[Co dodělat ]: #
[pojmy ]: #

# Výběr řídící jednotky pro různé aplikace

$${\color{#FFA500}E9 \space \color{#4682B4}A1 }$$

## Cíle

- **Kategorizovat a porovnat** architektury řídicích systémů (MCU, MPU, embedded systémy, PLC, iPC, programovatelná relé) podle výkonu, paměti, determinismu a spolehlivosti.
- **Analyzovat provozní prostředí a vnější vlivy** (krytí IP, teplotní rozsah, EMC rušení, vibrace) a stanovit požadavky na mechanickou a elektrickou odolnost hardware.
- **Sestavit I/O bilanci** a navrhnout optimální řídicí jednotku z reálných katalogů výrobců pro konkrétní průmyslovou či IoT aplikaci včetně projektové rezervy.
- **Vypracovat vícekriteriální rozhodovací matici** a obhájit zvolenou platformu z technického a ekonomického hlediska (pořizovací cena, náročnost vývoje, údržba a spolehlivost).
- **Provést kritický technický audit (troubleshooting)** nevhodného návrhu řízení, identifikovat bezpečnostní a provozní rizika a navrhnout certifikované řešení v souladu s průmyslovými standardy.

## Ověření cílů

Výběr řídící jednotky pro různé aplikace

1. Příklady řídících jednotek
2. Jejich základní vlastnosti z hlediska výpočetního výkonu a velikosti paměťového prostoru
3. A z hlediska odolnosti
4. Příklady použití v praxi (kde se používají MCU, a kde ř. j. s MPU)

%%

1. Správné vysvětlení pojmů, architektur a zkratek z oblasti řídicích systémů.
2. Schopnost posoudit vliv prostředí na výběr hardwaru a dešifrovat IP kód.
3. Vypracování rozhodovací matice pro volbu vhodné platformy (MCU vs. PLC vs. iPC).
4. Návrh konkrétní konfigurace řídicí jednotky na základě zadané I/O bilance a provozních podmínek.
5. Kritická technická oponentura (audit) nevhodně navrženého řešení. %%

---

## Úlohy


### 1. Základní pojmy a architektury řídicích jednotek

*Časová dotace: 10–15 minut | Úvodní orientační úloha*

Doplňte do níže uvedené tabulky význam zkratek, základní princip a typický příklad reálného nasazení nebo zástupce:

| Zkratka / Pojem          | Co zkratka znamená (česky / anglicky) | Základní charakteristika (architektura, kde běží program)                                            | Typický zástupce (konkrétní rodina / model) | Příklad reálného nasazení                |
| :----------------------- | :------------------------------------ | :--------------------------------------------------------------------------------------------------- | :------------------------------------------ | :--------------------------------------- |
| **MCU**                  |                                       | Integrovaný čip (CPU + RAM + Flash na jednom substrátu), deterministický běh bez OS nebo RTOS        | např. ESP32, PIC16LF1xxx, RP2040            |                                          |
| **MPU**                  |                                       | Samostatný procesor vyžadující externí RAM a úložiště, zpravidla běží plnohodnotný OS (Linux)        |                                             |                                          |
| **Embedded**             |                                       |                                                                                                      | Embedded PLC, Embedded PC                   | Bílá technika, bankomaty, regulace kotlů |
| **PLC**                  |                                       | Průmyslový automat pro cyklické deterministické řízení procesů, vysoká odolnost, modulární/kompaktní |                                             |                                          |
| **iPC**                  |                                       |                                                                                                      |                                             |                                          |
| **Programovatelné relé** |                                       | Zjednodušené kompaktní PLC pro méně náročné úlohy, nahrazuje časovací relé a stykačové kombinace     |                                             |                                          |

> :key: **Vysvětlení pojmů a odborné zdroje:**
> - **SoC (System on Chip):** Integrovaný obvod sdružující všechny klíčové elektronické obvody a komponenty celého počítače či elektronického systému na jediném křemíkovém čipu. 
> 	 Systém na čipu. *Wikipedie: Otevřená encyklopedie* [online]. San Francisco (CA): Wikimedia Foundation, 2024, 2024-06-07 [cit. 2026-09-17]. Dostupné z: https://cs.wikipedia.org/wiki/Syst%C3%A9m_na_%C4%8Dipu
> - **DSP (Digital Signal Processor):** Specializovaný mikroprocesor architektury Harvard optimalizovaný pro matematické výpočty v reálném čase (rychlá Fourierova transformace FFT, filtrace šumu, digitální vektorové řízení střídavých motorů). 
> 	Digitální signálový procesor. In: _Wikipedia: otevřená encyklopedie_ [online]. St. Petersburg (Florida): Wikimedia Foundation, 2006, poslední editace 28. 2. 2026 [cit. 2026-09-14]. Dostupné z: [Digitální signálový procesor – Wikipedie](https://cs.wikipedia.org/wiki/Digit%C3%A1ln%C3%AD_sign%C3%A1lov%C3%BD_procesor)
> - **FPGA (Field-Programmable Gate Array):** Programovatelné logické hradlové pole, jehož vnitřní struktura logických bloků a propojení je konfigurovatelná až u zákazníka. Umožňuje masivní paralelní zpracování s hardwarovou latencí v řádu nanosekund. 
> 	Programovatelné hradlové pole. *Wikipedie: Otevřená encyklopedie* [online]. San Francisco (CA): Wikimedia Foundation, 2024, 2024-01-10 [cit. 2026-09-17]. Dostupné z: https://cs.wikipedia.org/wiki/Programovateln%C3%A9_hradlov%C3%A9_pole


<details>
<summary> :bulb: Tip k doplnění tabulky: </summary>
<p>Zaměřte se na čas náběhu a architekturu: U MCU je kód ve vnitřní paměti Flash procesoru a vykonává se okamžitě po přivedení napájení (řádově milisekundy). U systémů s MPU a iPC musí BIOS/bootloader nejprve zavést jádro operačního systému (OS Linux, Windows) z disku/eMMC/SD karty do operační paměti RAM, což trvá desítky sekund.</p>
</details>

:star2: **Bonusová otázka k úloze 1:**
Proč se u kritických aplikací v letectví (např. systém řízení letu Fly-by-Wire) nebo v jaderné energetice stále upřednostňují jednoduché deterministické mikrořadiče s několika desítkami kilobajtů paměti nebo obvody FPGA před moderními vícejádrovými gigahertzovými procesory s gigabajty RAM?

*Vaše odpověď:*
`...`

---

### 2. Parametry, paměti a provozní odolnost (IP krytí)

*Časová dotace: max. 15 minut | Mírně náročnější úloha propojující parametry a praxi*

1. **Typy pamětí v řídicích jednotkách:**
   - Doplňte porovnání pamětí z hlediska stálosti dat a rychlosti:
     - **RAM:** 
	     - Je volatilní (energeticky závislá)? `[Ano / Ne]`
	     - Rychlost zápisu: `...` 
	     - K čemu se využívá v PLC/MCU: `...`
     - **Flash (ROM):** 
	     - Je volatilní? `[Ano / Ne]`
	     - K čemu se využívá v PLC/MCU: `...`
     - **EEPROM / NVRAM:** 
	     - Je volatilní? `[Ano / Ne]`
	     - K čemu se využívá v PLC/MCU: `...`
   - *Otázka z praxe:* Kam se v průmyslovém PLC ukládají aktuální provozní proměnné (např. čítače vyrobených kusů nebo motohodiny), aby se při nečekaném výpadku napájení neztratily (tzv. remanentní / retain data)?
     - Odpověď: `...`

2. **Reálný čas a determinismus (Hard vs. Soft Real-Time):**
   - Proč pro reakci na nouzové zastavení lisu (požadavek reakce do 5 ms) použijeme PLC či mikrokontrolér s RTOS, a nikoliv běžné Raspberry Pi s operačním systémem Raspberry Pi OS (standardní Linux)?
     - Odpověď: `...`

3. **Odolnost vůči vlivům prostředí a dešifrování kódu IP:**
   - Dešifrujte kód **IP68**:
     - První číslice (6): `...`
     - Druhá číslice (8): `...`
   - Jaké minimální krytí IP musí mít rozváděč umístěný ve venkovním nekrytém prostředí, kde na něj přímo dopadá déšť a fouká polétavý prach?
     - Označte správnou volbu: `[ ] IP20` | `[ ] IP44` | `[ ] IP65` | `[ ] IP00`
     - Zdůvodnění: `...`

4. **Konstrukční rozdíly kancelářského PC vs. průmyslového iPC:**
   - Vyberte a doplňte hlavní odlišnosti:
     - *Chlazení:* 
	     - Kancelářské PC: `...` 
	     - vs. iPC: `...`
     - *Napájecí napětí a filtrace:* 
	     - Kancelářské PC: `...` 
	     - vs. iPC: `...`
     - *Odolnost proti otřesům a vibracím:* `...`
     - *Způsob montáže:* 
	     - Kancelářské PC: na stůl/pod stůl 
	     - vs. iPC: `...`

> :key: **Vysvětlení pojmů a odborné zdroje:**
> - **Determinismus (Real-Time):** Vlastnost systému, která zaručuje, že odezva na vstupní událost proběhne vždy v přesně definovaném a předvídatelném čase (deadline). V *Hard Real-Time* systémech znamená nedodržení časového limitu fatální havárii celého procesu. 
> 	Operační systém reálného času. *Wikipedie: Otevřená encyklopedie* [online]. San Francisco (CA): Wikimedia Foundation, 2024, 2024-05-12 [cit. 2026-09-17]. Dostupné z: https://cs.wikipedia.org/wiki/Opera%C4%8Dn%C3%AD_syst%C3%A9m_re%C3%A1ln%C3%A9ho_%C4%8Dasu
> - **Krytí IP (Ingress Protection):** Mezinárodní standard dle normy **ČSN EN 60529** určující stupeň ochrany krytem před vniknutím pevných cizích těles včetně prachu (1. číslice 0–6) a vniknutím vody (2. číslice 0–9K).
> 	ČESKÝ NORMALIZAČNÍ INSTITUT. *ČSN EN 60529 (33 0330) Stupně ochrany krytem (krytí - IP kód)*. Praha: Český normalizační institut, 1993. Třídící znak 330330.
> - **Remanentní paměť (Retain):** Paměťový prostor v PLC, jehož obsah zůstává zachován i po přerušení napájecího napětí (využívá zálohovací baterii, superkondenzátor nebo zápis do FRAM/MRAM/EEPROM).

<details>
<summary> :bulb: Tip k otázce determinismu: </summary>
<p>Běžný Linux je <b>preemptivní víceúlohový systém</b>, který se snaží spravedlivě rozdělit čas procesoru mezi stovky procesů. Může se stát, že kvůli obsluze disku, správě paměti nebo síťovému provozu se proces řízení pozdrží na desítky milisekund. PLC naproti tomu vykonává cyklus v pevném taktu bez zpoždění vyvolaného aplikacemi na pozadí.</p>
</details>

:star2: **Bonusová otázka k úloze 2:**
Co označuje doplňkové písmeno **K** v kódu krytí **IP69K** a v jakém průmyslovém odvětví je toto krytí bezpodmínečně vyžadováno?

*Vaše odpověď:*
`...`

---

