# Kodutöö – programmeerimisprojekti plaan

## 1. Projekti nimi

**Kuukülv** on eestikeelne külvikalender Androidi ja iOS-i telefonidele.

## 2. Eesmärk

Kuukülv aitab koduaednikul leida, millal valitud taime külvata. Ühes vaates saab näha Eesti kasvutingimustele sobivat külviperioodi ning selle sees kuufaasi järgi soovitatud päevi. Kuusoovitused on märgitud pärimuslikuna. Kasutaja näeb ka külviperioodi ennast ja soovituse põhjendust.

## 3. Sihtgrupp

Rakendus on mõeldud Eesti koduaednikele, kes kasvatavad köögivilju aias, rõdul või kasvuhoones. See aitab nii algajal, kes otsib sobivat külviaega, kui ka kogenud aednikul, kes soovib külve kuufaaside järgi ajastada.

## 4. Funktsionaalsus

1. **Vali kultuur.** Esimesse versiooni plaanin lisada redise, porgandi, herne ja aedsalati.
2. **Vali külviviis.** Vaata avamaale külvi või ettekasvatuse aega, kui valitud taime kasvatamisjuhis seda viisi toetab.
3. **Vaata külviperioodi.** Kalender kuvab algus- ja lõpukuupäeva ning vajaduse korral märkuse mulla temperatuuri või öökülmaohu kohta.
4. **Vaata kuufaase.** Kalender märgib noorkuu, esimese veerandi, täiskuu ja viimase veerandi kuupäeva Eesti aja järgi.
5. **Leia järgmine kuufaasi järgi soovitatud külvipäev.** Rakendus tõstab sobivad päevad külviperioodis esile. Päeva avamisel näeb kasutaja kuufaasi ja soovituse põhjendust.
6. **Kasuta külvikalendrit võrguühenduseta.** Rakendusega kaasas olevad andmed võimaldavad vaadata külviperioode ja leida kuusoovitusi andmetega kaetud päevadel.

## 5. Tehnoloogiad

| Tehnoloogia | Kasutus projektis |
| --- | --- |
| TypeScript | Rakenduse loogika, andmetüübid ja külvisoovituste arvutus. |
| React Native ja Expo | Mobiilivaated ja arendus ühise koodibaasiga Androidile ja iOS-ile. |
| JSON | Rakendusega kaasas olevad kultuuride külviperioodid, allikaviited ja kuufaaside andmed. |
| Git ja GitHub | Versioonihaldus ning projekti plaani hoidmine failis `README.md`. |
| US Naval Observatory andmed | Nelja peamise kuufaasi ajahetkede allikas. [USNO kuufaaside andmed](https://aa.usno.navy.mil/data/MoonPhases). |

## 6. Teostusplaan

1. Visanda kultuuri valiku, kalendri ja päeva detailvaate ekraanid.
2. Kontrolli nelja kultuuri külviaegu Eesti kasvatusjuhenditest ning koosta allikaviidetega algandmestik. Lisa kuufaaside andmed ja määra nende kaetud periood.
3. Loo Expo projekt ning ehita kultuuri valik ja kalendrivaade.
4. Lisa külvisoovituste arvutus, päeva põhjendus ja teated puuduva kuufaasi või puuduva soovituse korral.
5. Testi külviakna piire, kuufaasi vahetumist ja Eesti ajavööndit. Proovi kogu kasutajateekonda Androidil ja iOS-il, sealhulgas lennurežiimis.
6. Paranda testimisel leitud vead ning lisa README-sse äpi käivitamise juhis.

## 7. Valmisoleku kriteeriumid

- Äpp käivitub Androidil ja iOS-il ning põhivaated on eestikeelsed.
- Kõigi nelja kultuuri jaoks saab valida vähemalt ühe külviviisi ja näha allikaviitega külviperioodi.
- Kalendri nelja peamise kuufaasi kuupäevad ühtivad kontrollnäidetes USNO aega Eesti ajavööndisse teisendades saadud kuupäevadega.
- Iga esile tõstetud päev jääb valitud külviperioodi ja vastab kuufaasi reeglile. Päeva detailvaade selgitab, miks päev sobib, ja märgib soovituse pärimuslikuna.
- Lennurežiimis saab valida kultuuri, vaadata kalendrit ja avada kaetud päeva põhjenduse. Kui kuufaasiandmed puuduvad, jääb külviperiood nähtavale ja äpp kuvab selle kohta selge teate.
- README-s on juhis, mille järgi saab teine inimene projekti käivitada.

## Arenduse märkmed

### Külvikalendri tööpõhimõte

1. Kuva allikaga põhjendatud külviaken valitud kultuuri ja külviviisi jaoks. Hoia avamaale külv ja ettekasvatus omaette valikutena seal, kus allikas neid toetab. Näita asjakohaseid mulla temperatuuri ja öökülma märkusi.
2. Tõsta külviaknas esile kuufaasiga sobivad kalendripäevad. Esimese versiooni pärimusreegel seob maapealse saagiga kultuurid kasvava kuuga ja maa-aluse saagiga kultuurid kahaneva kuuga. Üleminekupäeva määramiseks kasutab äpp oma kokkulepet ja kontrollib kuufaasi kell 12.00 Eesti ajas. Kasvav periood algab noorkuu täpsel hetkel ja lõpeb täiskuu hetkel. Kahanev periood algab täiskuu täpsel hetkel ja lõpeb järgmise noorkuu hetkel. Piirihetk kuulub algavasse perioodi. [Pärimusreegli allikas](https://www.almanac.com/planting-by-the-moon).
3. Näita põhjendust, näiteks „Kuu järgi soovitatud külvipäev. Päev jääb külviaknasse ja kuu on kasvav.“ Lisa lühike selgitus, et kuu järgi külvamine on pärimus. Teaduskirjanduse ülevaade ei leidnud usaldusväärset alust kuufaaside järgi külvamisele saagi parandamiseks. [Mayoral jt, 2020](https://doi.org/10.3390/agronomy10070955).
4. Hoia faasihetked UTC-s ja kuva need ajavööndis `Europe/Tallinn`. Kuva terve külviaken koos algus- ja lõpupäevaga ka siis, kui faasiandmed katavad ainult osa sellest. Anna kuusoovitusi kaetud päevadele ja märgi ülejäänud päevadel andmete puudumine. Päev on kaetud, kui selle kohalik keskpäev jääb teadaolevasse järjestikuste noor- ja täiskuu vahemikku. Kui kogu külviaken on kaetud ja ükski päev ei sobi, ütle, et sel perioodil kuu järgi soovitatud päevi ei ole. [USNO kuufaaside andmestik](https://aa.usno.navy.mil/data/MoonPhases).

### Agendid

| Agent | Tulemus |
| --- | --- |
| `toode_ja_kasutuskogemus` | Mobiilivaated, eestikeelsed tekstid ja vastuvõtukriteeriumid. |
| `kuukalender_ja_aiandus` | Allikatega kultuuriandmed, faasireeglid ja arvutuse kontrollnäited. |
| `mobiiliarendus` | Töötav mobiiliäpp ja kohapeal käivitatavad kontrollid. |
| `kvaliteedikontroll` | Sõltumatu ülevaatus koos kordamise sammude ja testitulemustega. |

Ava `aiandus` Codexis töökaustana ning nimeta vestluses roll, kellele soovid ülesande anda. Käsurealt saab töökausta valida näiteks käsuga `codex -C aiandus` kaustas `VIKK`. [Codexi juhend projekti agentidele](https://learn.chatgpt.com/docs/agent-configuration/subagents#custom-agents).

> Loo `aiandus` kausta esimene Androidi ja iOS-i prototüüp. Kaasa `toode_ja_kasutuskogemus` põhivaadete kavandamiseks, `kuukalender_ja_aiandus` külviakende ja faasireeglite kontrolliks ning `mobiiliarendus` rakenduse ehitamiseks. Lase `kvaliteedikontroll` agendil valmis külvikalender üle vaadata.
