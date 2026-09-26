# Prednáška 1: Analýza funkčných bodov a COCOMO

> **MSP | Odhadovanie softvérových projektov**

## 1. Prečo odhadovať softvérové projekty?

Funkcionalita softvéru sa meria ťažko. Kým stavebný projekt možno odhadovať v metroch štvorcových, pri softvéri treba z požiadaviek odhadnúť úsilie, čas a náklady.

Odhady založené na odbornom názore sa používajú najmä preto, že na začiatku projektu chýbajú informácie a jednotlivé domény sa líšia. Ich presnosť však nie je stabilná, čo môže spôsobiť prekročenie rozpočtu a harmonogramu.

## 2. Metriky funkčných bodov

Funkčné body (FP) merajú **funkčnú veľkosť** softvéru z pohľadu používateľa. Vyvinul ich Allan Albrecht v IBM.

> **Dôležité:** funkčná veľkosť a úsilie na vývoj sú rozdielne veličiny. Súvisia spolu, ale nie sú totožné.

FP pomáhajú obmedziť závislosť od počtu riadkov kódu (LOC), ktorý závisí od programovacieho jazyka a na začiatku projektu sa odhaduje ťažko.

### Použitie FPA

- určenie a vyjednávanie rozsahu projektu;
- vyhodnotenie požiadaviek, vplyvu a nákladov náhrady systému;
- odhad potrebných zdrojov a testovania;
- plánovanie rizík a etáp vývoja;
- sledovanie funkčného rozrastania a priebehu práce;
- prioritizácia práce, benchmarking a identifikácia dobrej praxe;
- plánovanie podpory, rozpočtu a nových verzií;
- vyhodnotenie softvérových aktív.

## 3. Postup odhadu

1. Spočítať funkcie systému a určiť **neupravené funkčné body (UFP)**.
2. Vyhodnotiť faktory zložitosti a vypočítať **VAF** a **upravené funkčné body (AFP)**.
3. Prepočítať FP na LOC podľa zvoleného programovacieho jazyka.
4. Zvoliť typ projektu a koeficienty z tabuľky COCOMO.
5. Vypočítať úsilie, trvanie a počet pracovníkov.

### Základné vzorce

$$
VAF = 0{,}65 + \frac{\sum_i SM_i}{100}
$$

$$
AFP = UFP \times VAF
$$

$$
E = a_b(KLOC)^{b_b},\quad D = c_b(E)^{d_b},\quad P = \frac{E}{D}
$$

### Ako čítať vzorce

| Symbol | Význam |
| --- | --- |
| **UFP** | Neupravený počet funkčných bodov pred zohľadnením zložitosti. |
| **SMᵢ** | Skóre *i*-tej vlastnosti systému, napríklad výkonu alebo bezpečnosti. |
| **ΣSMᵢ** | Súčet všetkých skóre vlastností. |
| **VAF** | Faktor úpravy hodnoty; násobiteľ vyjadrujúci zložitosť systému. |
| **AFP** | Upravené funkčné body: **UFP × VAF**. |
| **KLOC** | Tisíce riadkov kódu. **20 KLOC** znamená 20 000 riadkov. |
| **E** | Úsilie v človekomesiacoch, teda celkové množstvo práce. |
| **D** | Trvanie v kalendárnych mesiacoch. |
| **P** | Priemerný počet pracovníkov: **E ÷ D**. |
| **aᵦ, bᵦ** | Koeficienty určujúce odhad úsilia. |
| **cᵦ, dᵦ** | Koeficienty prevádzajúce úsilie na trvanie. |

Index **b** označuje súbor koeficientov pre zvolený režim COCOMO. Koeficienty sa vyberajú z tabuľky COCOMO, nie odhadujú náhodne.

### Krátky príklad

Pre projekt s veľkosťou 20 KLOC použijeme iba ilustračné koeficienty **aᵦ = 2,4**, **bᵦ = 1,05**, **cᵦ = 2,5** a **dᵦ = 0,38**:

1. Úsilie: **E = 2,4 × 20^1,05 ≈ 55,8 človekomesiaca**.
2. Trvanie: **D = 2,5 × 55,8^0,38 ≈ 11,5 mesiaca**.
3. Priemerný tím: **P = 55,8 ÷ 11,5 ≈ 4,8 pracovníka**.

Výsledok teda znamená približne **56 človekomesiacov práce**, **11,5 mesiaca** kalendárneho času a priemerný tím **5 ľudí**.

## 4. Experimentálne pravidlá

- **1 FP približne 100 LOC**;
- počet strán dokumentácie **približne FP^1.15**;
- počet testov **približne FP^1.12**;
- kontrola odhalí približne 30 % chýb;
- čas vývoja **približne FP^0.4**;
- počet pracovníkov na vývoj **približne FP / 150**;
- počet pracovníkov na údržbu **približne FP / 500**;
- pri organickom projekte je úsilie približne **2,4 × KLOC^1.05**.

Pravidlá treba overiť a kalibrovať podľa historických údajov organizácie.

## 5. Model COCOMO

COCOMO je **Constructive Cost Model**, algoritmický model odhadu nákladov, ktorý vytvoril Barry W. Boehm.

### COCOMO 81

- **Basic:** rýchly počiatočný odhad založený najmä na veľkosti programu;
- **Intermediate:** pridáva nákladové faktory a násobitele úsilia;
- **Detailed:** zohľadňuje aj vplyv jednotlivých etáp vývoja.

Režimy vývoja:

- **Organic:** malý skúsený tím a pružné požiadavky;
- **Semi-detached:** stredne veľký tím s rôznou úrovňou skúseností;
- **Embedded:** systém vzniká v rámci prísnych obmedzení.

### Nákladové faktory

15 atribútov sa hodnotí od *veľmi nízkej* po *mimoriadne vysokú* úroveň. Súčin ich násobiteľov dáva **EAF**, typicky približne **0,9-1,4**.

- **Produkt:** spoľahlivosť, veľkosť databázy, zložitosť;
- **Hardvér:** výkon, pamäť, volatilita virtuálneho stroja, čas odozvy;
- **Personál:** schopnosti analytika a vývojára a ich skúsenosti;
- **Projekt:** nástroje, metódy a požadovaný harmonogram.

### COCOMO II

COCOMO II je určený pre moderné procesy vývoja. Jeho fázy sú **Application Composition**, **Early Design** a **Post-Architecture**. Medzi škálové faktory patria **PREC**, **FLEX**, **RESL**, **TEAM** a **PMAT**.

## Kontrolný zoznam na skúšku

- vysvetliť, prečo FP nie sú to isté ako úsilie;
- rozlišovať UFP, VAF a AFP;
- poznať prevod FP na LOC a postup odhadu;
- uviesť tri úrovne COCOMO 81 a režimy projektov;
- vysvetliť rozdiel medzi Basic, Intermediate a Detailed COCOMO;
- vymenovať fázy a škálové faktory COCOMO II.

## Zapamätať si

FPA odhaduje **čo softvér poskytuje** (funkčnú veľkosť). COCOMO potom odhaduje **čo je potrebné na jeho vytvorenie** (úsilie, čas a ľudia). Empirické vzorce vyžadujú lokálnu kalibráciu.