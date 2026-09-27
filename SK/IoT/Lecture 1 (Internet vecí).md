# Prednáška 1: Internet vecí

> **IoT | Inter(net) of Thing(s)**  
> Zdroj: [prednáška IoT 01](https://kurzy.kpi.fei.tuke.sk/iot1/lectures/01/)

## 1. Čo je IoT?

**Internet vecí (IoT)** je paradigma, v ktorej sa bežné predmety a zariadenia stávajú pripojenými účastníkmi siete. Dokážu snímať svoje okolie, vymieňať si údaje, poskytovať svoj stav a ovládať iné zariadenia.

> Chytré zariadenie samo osebe ešte nie je IoT riešenie.

IoT vzniká vtedy, keď pripojené veci spolupracujú, vymieňajú si informácie a prinášajú **pridanú hodnotu**: automatizáciu, monitorovanie, optimalizáciu alebo lepšie rozhodovanie.

## 2. Od veci k IoT

| Fáza | Význam | Príklad |
| --- | --- | --- |
| **1. Vec** | Zariadenie funguje lokálne bez sieťovej pridanej funkcionality. | Žiarovka ovládaná vypínačom. |
| **2. Chytré zariadenie** | Zariadenie komunikuje s používateľom alebo iným zariadením. | Žiarovka ovládaná a stmievaná mobilnou aplikáciou. |
| **3. Sieť chytrých zariadení** | Viaceré zariadenia spolupracujú cez lokálnu sieť alebo platformu. | Meteostanica, senzor bránky a žiarovka vytvoria automatizáciu. |
| **4. Internet vecí** | Zariadenia sú súčasťou širšej siete a zdieľajú údaje aj mimo jednej lokality. | Elektromery, domácnosti, batérie a elektromobily koordinujú svoje správanie. |

Dôležité preto nie sú iba zariadenia a internet, ale aj komunikácia, údaje, spracovanie, používatelia a výsledná služba.

## 3. Štvorvrstvová IoT architektúra

### 1. vrstva: Veci, senzory a akčné členy

Fyzické zariadenia sledujú prostredie alebo v ňom vykonávajú akcie.

- **Senzory** merajú napríklad pohyb, svetlo, teplotu, naplnenie alebo spotrebu energie.
- **Akčné členy** vykonávajú činnosti, napríklad zapnú svetlo, otvoria ventil alebo spustia alarm.
- Zariadenia môžu komunikovať s bránou aj priamo medzi sebou.

Pri rýchlych reakciách je výhodná lokálna komunikácia. Senzor pohybu môže napríklad rozsvietiť svetlo bez čakania na vzdialený cloud.

### 2. vrstva: IoT brány a zber údajov

Brána sa nachádza blízko zariadení. Zbiera, spája, filtruje a prevádza nespracované údaje pred ich odoslaním do vyšších vrstiev.

Bránou môže byť smart-home hub, priemyselná brána, Wi-Fi router s IoT funkciami alebo USB koordinátor. Brány znižujú množstvo prenášaných údajov, prekladajú protokoly, vykonávajú prvotné spracovanie a zvyšujú bezpečnosť.

### 3. vrstva: Edge analytika

**Edge computing** presúva výpočty a úložisko bližšie k zariadeniam, ktoré údaje vytvárajú alebo používajú. Tým znižuje odozvu a objem prenášaných dát.

Edge systémy dokážu údaje analyzovať, rýchlo reagovať lokálne a synchronizovať vybrané výsledky s centrálnymi systémami. Táto vrstva je užitočná najmä v priemysle, ale nemusí byť súčasťou každého IoT riešenia.

### 4. vrstva: Dátové centrá a cloudové platformy

Cloud alebo lokálne dátové centrum poskytuje rozsiahle úložisko, spracovanie, analytiku, strojové učenie, dashboardy a používateľské aplikácie.

Táto vrstva zvládne viac údajov a výpočtov než väčšina zariadení na okraji siete. Podporuje dlhodobú analýzu a rozhodovanie, hoci môže byť geograficky vzdialená od zariadení.

## 4. Príklad: chytrý vývoz odpadu

Kontajnery vybavené senzormi môžu fungovať takto:

1. Senzor meria naplnenie kontajnera.
2. Brána zbiera údaje z mnohých kontajnerov a filtruje nepotrebné správy.
3. Edge infraštruktúra analyzuje lokálne údaje a pripravuje upozornenia alebo trasy.
4. Cloud ukladá históriu, vytvára dashboardy a optimalizuje harmonogram vývozu.

Základná služba zostáva rovnaká: vývoz odpadu. IoT však pridáva lepšie trasy, menej zbytočných jázd, nižšie náklady a spravodlivejšie účtovanie podľa skutočne poskytnutej služby.

## 5. Čo treba pri návrhu riešiť?

- Aké údaje zbierame a prečo?
- Ktorá vrstva ich má spracovať?
- Ako zariadenia komunikujú a overujú svoju identitu?
- Čo sa stane pri výpadku spojenia?
- Ako zariadenia aktualizujeme a chránime?
- Akú užitočnú automatizáciu alebo rozhodnutie údaje umožnia?

Nie každé riešenie potrebuje všetky štyri vrstvy. Malý lokálny systém si môže vystačiť so zariadeniami a bránou.

## Kontrolný zoznam na skúšku

- vysvetliť, prečo chytré zariadenie samo osebe nie je IoT riešenie;
- opísať postup od veci k Internetu vecí;
- vymenovať a vysvetliť štyri vrstvy IoT architektúry;
- rozlíšiť senzory, akčné členy, brány, edge systémy a cloud;
- vysvetliť, prečo brány filtrujú a spájajú údaje;
- vysvetliť účel edge computingu;
- určiť pridanú hodnotu v príklade chytrého vývozu odpadu.

### Hlavná myšlienka

IoT nie je iba pripojený hardvér. Je to systém vecí, komunikácie, spracovania údajov a služieb, ktorý premieňa spoluprácu zariadení na užitočnú pridanú hodnotu.