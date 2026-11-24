# Osječka Biblija

Hrvatski prijevod cijele Biblije, stih po stih, s hebrejskim i grčkim izvornikom i transliteracijom. Isti tekst čita se na [biblija.hr](https://biblija.hr).

- **Verzija:** 2.0
- **Datum:** 24. 11. 2026.
- **Datoteka:** `osjecka_biblija_v2.0.json` (UTF-8)
- **Opseg:** 66 knjiga, 31.304 zapisa
- **Licenca:** [CC BY-SA 4.0](LICENSE)

## Sadržaj datoteke

Datoteka je jedan JSON niz, a svaki zapis u nizu je jedan stih. Zapisi su poredani po knjizi, poglavlju i stihu.

```json
{
  "id_stiha": 1,
  "id_knjige": 1,
  "knjiga": "Postanak",
  "poglavlje": 1,
  "stih": 1,
  "tekst": "U početku stvori Bog Nebesa i Zemlju.",
  "jezik": "heb",
  "izvornik": "בראשית ברא אלהים את השמים ואת הארץ׃",
  "transliteracija": "be.re.Shit ba.Ra' 'E.lo.Him 'et ha.sha.Ma.yim ve.'Et ha.'A.retz",
  "verzija": "2.0",
  "datum": "2026-11-24"
}
```

| Polje | Značenje |
| --- | --- |
| `id_stiha` | stalni ID stiha; isti stih ima isti ID u svim budućim verzijama, pa se po njemu spajaju izmjene |
| `id_knjige` | redni broj knjige (1 = Postanak … 66 = Otkrivenje) |
| `knjiga` | naziv knjige na hrvatskom |
| `poglavlje`, `stih` | mjesto stiha u hrvatskoj numeraciji |
| `tekst` | tekst Osječke Biblije |
| `jezik` | jezik izvornika: `heb` (hebrejski, Stari zavjet) ili `grk` (grčki, Novi zavjet) |
| `izvornik` | tekst stiha na izvornom jeziku, riječi odvojene razmakom |
| `transliteracija` | izgovor izvornika latinicom, riječ po riječ |
| `verzija`, `datum` | verzija i datum izvoza |

## Napomene

**Numeracija je hrvatska.** Gdje se hrvatska numeracija razlikuje od hebrejske ili od numeracije drugih prijevoda (npr. Joel 3–4, Malahija 3–4, naslovi psalama, Brojevi 16–17), postoje zapisi s tekstom `#`. Takvih je 220. Oni nemaju svoj sadržaj, a postoje da bi se Osječka Biblija mogla stih po stih poravnati s drugim prijevodima. Sadržaj tih stihova nalazi se u susjednom poglavlju.

**Stihovi bez izvornika.** Polje `izvornik` je prazno za 42 stiha, jer tih stihova nema u izdanjima izvornika koja koristimo:

- Novi zavjet (40): npr. Mt 17,21; Mt 18,11; Mt 23,14; Mk 7,16; Mk 16,9–20; Lk 17,36; Iv 5,4; Iv 7,53–8,11; Dj 8,37; Rim 16,24.
- Stari zavjet (2): Jš 21,36–37, kojih nema u Lenjingradskom kodeksu.

**Hebrejski izvornik** je suglasnički tekst bez samoglasničkih znakova (niqqud), sa znakom kraja stiha `׃`.

**Transliteracija** slijedi zapis STEPBible: točka dijeli slogove, a veliko slovo označava naglašeni slog (`be.re.Shit` = be-re-šit, naglasak na zadnjem slogu).

**Grčki izvornik** sadrži riječi koje su u podacima STEPBible označene kao dio izdanja Nestle-Aland. Riječi koje postoje samo u drugim izdanjima, npr. u Textus Receptusu, nisu uključene.

**Tekst** je čist, bez podnaslova, kurziva, oznaka poezije i fusnota.

## Primjer korištenja

Python:

```python
import json

with open("osjecka_biblija_v2.0.json", encoding="utf-8") as f:
    biblija = json.load(f)

stih = next(s for s in biblija if s["knjiga"] == "Ivan" and s["poglavlje"] == 3 and s["stih"] == 16)
print(stih["tekst"])
print(stih["izvornik"])
```

## Izvori i atribucija

| Dio | Izvor | Licenca |
| --- | --- | --- |
| Hrvatski tekst | Osječka Biblija, izmijenjena inačica ekumenskog prijevoda T. Dretara, [biblija.hr](https://biblija.hr) | CC BY-SA 4.0 |
| Hebrejski tekst | Westminster Leningrad Codex (WLC) | javno vlasništvo |
| Hebrejski i grčki tekst po riječima, transliteracija | [STEPBible Data](https://github.com/STEPBible/STEPBible-Data), Tyndale House, Cambridge | CC BY 4.0 |
| Hebrejska morfologija | [Open Scriptures Hebrew Bible (OSHB)](https://github.com/openscriptures/morphhb) | CC BY 4.0 |

Tko koristi ove podatke, navodi: „Osječka Biblija, biblija.hr, CC BY-SA 4.0” i izvore iz tablice. Izmijenjena djela dijele se pod istom licencom (CC BY-SA 4.0).

Cjelovite licence i uvjeti: [biblija.hr/licenca-i-izvori](https://biblija.hr/licenca-i-izvori).

## Kontakt

Laus Deo d.o.o., Osijek · [biblija.hr](https://biblija.hr) · info@biblija.hr

---

## English summary

The Osječka Biblija is a complete Croatian translation of the Bible. This repository holds it as one UTF-8 JSON file, one record per verse, with the Hebrew or Greek source text and a transliteration. Numbering follows the Croatian tradition; records whose text is `#` exist only to align with other versifications. `id_stiha` is a stable verse ID across versions. The Croatian text is licensed under CC BY-SA 4.0; source-text attributions are listed above.
