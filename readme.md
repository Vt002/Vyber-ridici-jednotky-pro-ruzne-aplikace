[Co dodělat ]: #
[pojmy ]: #

# Výběr řídící jednotky pro různé aplikace

$${\color{#FFA500}E9 \space \color{#4682B4}A6 }$$

## Cíl

-   Studenti budou mít základní přehled o nejčastěji používaných řídících jednotkách,
-   a jejich vlastnostech (parametrech). Především z pohledu výpočetního výkonu a paměťového prostoru.
-   Dále pak z pohledu odolnosti a robustnosti hardwaru i softwaru.
-   A ke každému druhu řídících jednotek uvedou příklady z praxe.


## Ověření cílů

Výběr řídící jednotky pro různé aplikace

1. Příklady řídících jednotek 
2. Jejich základní vlastnosti z hlediska výpočetního výkonu a velikosti paměťového prostoru
3. A z hlediska odolnosti
4. Příklady použití v praxi (kde se používají MCU, a kde ř. j. s MPU)

## Úlohy

### 1. Typy řídících jednotek a jejich základní vlastnosti (parametry)

1. Zjistěte, jaké řídící jednotky se skrývají pod následujícími zkratkami a k čemu se používají (v jakých aplikacích se s nimi lze setkat):
-   MCU
-   MPU
-   embedded
-   PLC
-   iPC
-   NC (Numerical Control)
-   programovatelná relé

Pro zajímavost se ještě podívejte na zkratky:
-   SoC - System on a chip
-   DSP - Digital signal processor
-   FPGA - Field-programmable gate array 

2. Co je za parametr (vlastnost) výpočetní výkon? Jaké jiné parametry mají na něj vliv? A jak se dá měřit?

<details>
    <summary> :bulb: Tip: </summary>
        <p>Podívejte se, co to jsou benchmarky a k čemu se používají?</p>
        <p>A co je ekvivalent benchmarků pro mikrořadiče?</p>
</details>

3. Porovnejte dle výpočetního výkonu MPU a MCU. Podívejte se i na vybavenost integrovanými periferiemi. A vymyslete, proč se stále MCU vyrábí a používají.

4. Podobně porovnejte PLC, iPC a NC. Proč se vyrabí různě výkonná PLC (často se pak rozdělují na malá, střední a velká)? A jaký vliv má výpočetní výkon na použití těchto řídících jednotek?

<details>
    <summary> :bulb: Tip: </summary>
        <p>PLC se často navíc rozdělují podle výpočetního výkonu na malá/mini, též někdy jako programovatelná relé. Středně výkonná a velmi výkonná. Další hledisko je pak rozdělení na modulární a kompaktní. To do značné míry předurčuje, kde se dané PLC používá. Rozdělení a určení však není striktní, jde tedy spíše o získání představy, k čemu použít jakou řídící jednotku.</p>
</details>

5. Podívejte se, jaké typy pamětí se používají ve výše uvedených řídících jednotkách. Na jakém principu jsou založeny a k čemu se používají?


### 2. Rozdělení řídících jednotek z hlediska odolnosti a robustnosti

1. Odolnost řídících jednotek můžeme hodnotit jednak z hlediska mechanických vlastností a jednak z hlediska funkčnosti a stability vykonávání zadaných úloh (zpracování programu). S tím souvisí i pojem robustnost řízení. Zjistěte, co tento pojem znamená.

2. 


5. Jak se ve výše diskutovaných požadavcích liší od sebe výpočetní technika pro běžné uživatele, řídící jednotky pro průmysl, zdravotnictví a armádu?








***************************************************************************************



# Regulace

$${\color{#FFA500}E13 \space \color{Gold}S24 }$$

## Cíl
-   Studenti na příkladech vysvětlí, co je to regulátor a kde se používá
-   Budou umět rozlišit mezi řízením bez zpětné vazby (ovládáním) a se zpětnou vazbou (regulací)
-   Budou umět navrhnout a realizovat dvoustavový regulátor bez hystereze i s hysterezí
-   Dále se budou orientovat v základních pojmech z oblasti řízení a regulace

## Ověření cílů

Regulace

1. Vysvětlete, co je to regulace, nakreslete regulační schéma a vysvětlete jednotlivé části
2. Na příkladu vysvětlete princip dvoustavového regulátoru s a bez hystereze
3. Na příkladu vysvětlete význam senzorů v regulátorech
4. Ve zvoleném programovacím jazyce napište hlavní část algoritmu dvoustavového regulátoru s a bez hystereze

## Úlohy

### 1. Jaký je rozdíl mezi ovládáním a regulací

1. Vyhledejte pojmy ovládání a regulace a na základě toho vyhledejte tři praktické příklady ovládání a tři praktické příklady regulace. 
2. Zkuste zjistit, zda následující příklady řízení patří do ovládání, nebo regulace:
    - Pás na pokladně v supermarketu, který se automaticky zastaví, pokud zboží přeruší optozávoru.
    - Automatická závlaha zahrady, která se standardně spouští každou noc mezi 2 a 3 hodinou ranní. A pouze v případě, že celkové množství srážek od poslední závlahy přesáhne nastavenou hodnotu, závlaha se nespustí.
    - Halový portálový jeřáb s koncovými spínači (lidově koncáky), které zajišťují, že se v daném směru pohon zastaví. Tyto spínače slouží jako elektronické dorazy.
3. Vyhledejte alespoň pět příkladů regulátorů.

### 2. Navrhněte a realizujte dvoustavový regulátor

1. Navrhněte dvoustavový regulátor teploty (termostat) bez hystereze a s hysterezí.
2. Program nejprve odzkoušejte v simulátoru. Měřenou teplotu z čidla/senzoru teploty simulujte proměnnou, kterou budete ručně měnit.
3. Vyberte vhodný senzor/čidlo teploty a zprovozněte dvoustavový regulátor v řídící jednotce.
4. Hodnoty z termostatu podle možností řídící jednotky zakomponujte do vizualizace, nebo alespoň zobrazujte na displeji.

> :key: **Termostat**
>
> Dvoustavový regulátor teploty, často s nastavitelnou hysterezí.

> :key: **Hystereze**
>
> V regulaci se s ní setkáme buď v podobě přirozené setrvačnosti soustavy, např. litinový radiátor se pomalu nahřeje a dlouho vydrží hřát i po uzavření ventilu. Nebo ji vnášíme úmyslně v podobě tzv. regulátoru s hysterezí. Je důležitá u akčních členů, kterým nesvědčí časté zapínání/vypínání, např. kvůli menší účinnosti (spalovací kotle na uhlí, dřevo, štěpku, apod.), větší poruchovosti, apod. Hysterezi do otopné soustavy můžeme také vnést např. použitím velkých akumulačních nádrží.

> :key: **Dopravní zpoždění**
>
> Doba než se projeví vliv regulátoru na soustavě.

### 3. Navrhněte a realizujte PID regulátor

1. Navrhněte PID regulátor teploty (termostat) bez hystereze a s hysterezí.
2. Program nejprve odzkoušejte v simulátoru. Měřenou teplotu z čidla/senzoru teploty simulujte proměnnou, kterou budete ručně měnit.
3. Vyberte vhodný senzor/čidlo teploty a zprovozněte dvoustavový regulátor v řídící jednotce.




