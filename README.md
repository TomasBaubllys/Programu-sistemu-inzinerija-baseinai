# Programų sistemų inžinerija: individualių ir grupinių užsiėmimų valdymo sistema

VU MIF Programų sistemų inžinerijos komandinio darbo saugykla. Komanda: Tomas Baublys, Tadas Plančiūnas, Goda Gutparakytė, Marijus Plančiūnas, Ugnė Skučaitė.

## Dokumentai

Kiekvienas dokumentas turi vieną pagrindinį `.tex` failą. Kompiliuojamas tik jis, o skyriai ir paveikslai įterpiami automatiškai.

| Nr. | Dokumentas | LD | Pagrindinis failas |
|---|---|---|---|
| 1 | Užsakovo poreikių aprašas | 1 | `1. business-need-statement/business-need-statement_LT.tex` |
| 2 | Sistemos vizija | 1 | `2. system-vision-doc/system_vision_LT.tex` |
| 3 | Projekto planas | 1 | `project-plan/src/main.tex` |
| 4 | Reikalavimų specifikacija | 2 | `Reikalavimų specifikacija/src/main.tex` |
| 5 | Analizės modelis | 2 | `analizes_modelis.tex` |

- **Projekto planas** pats įterpia visus `project-plan/src/` skyrius, WBS paveikslą `wbs.drawio.png` ir A priedą (funkcinių taškų skaičiavimą). `wbs.tex` yra tas pats WBS skyrius atskirame dokumente, plane jo nereikia.
- **Analizės modelis** įterpia dalis iš `Struktūrinė analizė/`, `OOA analizė/` ir `Atsekamumas/`. Kiekvienos dalies kelias nurodytas `analizes_modelis.tex` eilutėse `\dalis{...}`. Kol dalies failo nėra, jos vietoje rodomas tuščias poskyris su atsakingo žmogaus vardu, todėl nebaigtas dokumentas irgi kompiliuojasi.
- Naujas skyrius įtraukiamas `\input{...}` eilute į to dokumento pagrindinį failą.

## Kaip sukompiliuoti

Visi keliai `.tex` failuose rašomi nuo saugyklos šaknies, todėl kompiliuojama iš šaknies, o failų perkelti nereikia. Kompiliatorius – pdfLaTeX.

**Overleaf.** Meniu (Menu) nustatyme *Main document* pasirinkite dokumento pagrindinį failą iš lentelės, spauskite *Recompile*, tada atsisiųskite PDF. Kitam dokumentui pakeiskite *Main document*.

**Savo kompiuteryje** (TeX Live arba MacTeX) iš saugyklos šaknies paleiskite komandas žemiau. Visi PDF atsiras kataloge `pdf/`, kurio git nesaugo. Kiekvienas dokumentas kompiliuojamas du kartus, kad susidarytų turinys ir nuorodos.

```sh
mkdir -p pdf
for k in 1 2; do
  pdflatex -interaction=nonstopmode -output-directory=pdf -jobname="1. Užsakovo poreikių aprašas" "1. business-need-statement/business-need-statement_LT.tex"
  pdflatex -interaction=nonstopmode -output-directory=pdf -jobname="2. Sistemos vizija" "2. system-vision-doc/system_vision_LT.tex"
  pdflatex -interaction=nonstopmode -output-directory=pdf -jobname="3. Projekto planas" "project-plan/src/main.tex"
  pdflatex -interaction=nonstopmode -output-directory=pdf -jobname="4. Reikalavimų specifikacija" "Reikalavimų specifikacija/src/main.tex"
  pdflatex -interaction=nonstopmode -output-directory=pdf -jobname="5. Analizės modelis" "analizes_modelis.tex"
done
```

## Visas projekto paketas

Jei reikia supakuoti visą projektą, imkite penkis PDF ir šiuos failus:

| Failas | Kam |
|---|---|
| `wbs.drawio.png` | WBS paveikslas (yra ir Projekto plano PDF) |
| `project-plan/resources/schedule.csv` | tvarkaraščio duomenys, kuriais remiasi Projekto plano 3 skyrius |
| `Struktūrinė analizė/ER diagrama/er_diagrama.png` | ER diagrama (yra ir Analizės modelio PDF) |
| `OOA analizė/Panaudojimo atvejų analizė/panaudojimo_atvejai.drawio.png` | panaudojimo atvejų diagrama (yra ir Analizės modelio PDF) |

Sukompiliavus PDF, šiuos failus į tą patį `pdf/` katalogą galima nukopijuoti taip:

```sh
cp wbs.drawio.png project-plan/resources/schedule.csv "Struktūrinė analizė/ER diagrama/er_diagrama.png" "OOA analizė/Panaudojimo atvejų analizė/panaudojimo_atvejai.drawio.png" pdf/
```

Duomenų srautų ir esybių gyvavimo ciklų diagramos nubraižytos TikZ tiesiai `.tex` failuose, todėl atskirų paveikslų jos neturi ir yra tik Analizės modelio PDF.

ER diagramą imkite iš `Struktūrinė analizė/ER diagrama/`. `project-plan/src/er_diagrama.png` yra senesnė kopija, kurios joks dokumentas nenaudoja.

## Diagramų šaltiniai

| Paveikslas | Šaltinis | Kaip atnaujinti |
|---|---|---|
| `er_diagrama.png` | `er_diagrama.puml` | `plantuml -tpng -charset UTF-8 er_diagrama.puml` |
| `panaudojimo_atvejai.drawio.png` | `panaudojimo_atvejai.drawio` | draw.io: *File → Export as → PNG* |
| `wbs.drawio.png` | saugykloje nėra | – |

## Kiti failai

- `Pradinis užsakovo poreikių dokumentas.docx` – pradinis užsakovo dokumentas. Jo punktai F1–F19 ir išplėtimai X1–X15 susieti su mūsų poreikių aprašu Projekto plano atsekamumo skyriuje.
- `SE-Teamwork_assignments_DUK-1.tex` – laboratorinių darbų užduotys ir DUK.
- `OOA analizė/Panaudojimo atvejų analizė/tadas_2_2_perziura.tex` – atskira 2.2 poskyrio peržiūra (XeLaTeX, kompiliuojama iš to katalogo). Bendram dokumentui jos nereikia.
