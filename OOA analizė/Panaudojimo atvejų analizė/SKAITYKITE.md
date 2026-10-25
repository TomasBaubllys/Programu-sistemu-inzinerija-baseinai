# Tado dalis: 2.2. Panaudojimo atvejų analizė

- `panaudojimo_atveju_analize_LT.tex` – į bendrą Analizės modelio dokumentą įterpiamas poskyris. Jis pats nedeklaruoja dokumento klasės ir nekeičia kitų dalių.
- `tadas_2_2_perziura.tex` – atskiras peržiūros dokumentas; kompiliuoti XeLaTeX du kartus iš šio katalogo.
- `tadas_2_2_perziura.pdf` – parengta peržiūra.
- `panaudojimo_atvejai.drawio` – keturi redaguojami UML diagramos lapai; jie atitinka PDF diagramas.

Integruojant reikia paketų longtable, array, booktabs, enumitem, tikz ir TikZ bibliotekos shapes.geometric. Bendrame dokumente prieš šį failą turi būti 2 skyrius ir 2.1 poskyris: `\input{panaudojimo_atveju_analize_LT}`.

Apimtis: 3 aktoriai, 18 panaudojimo atvejų su scenarijais, 4 diagramos. Ugnės veiklos diagramai skirtas PA-09: pagrindiniai 1–7 žingsniai ir alternatyvos 5a–5d bei 6a. Taisyklės suderintos su duomenų srautų diagramomis ir esybių gyvavimo ciklais.

Naudota 2026-10-16 nuskaityta pagrindinės GitHub šakos medžiaga (commit 2afb7e43e0e4c9036bd49645ca3c90b4fec30ec3). Ankstesni failai nepakeisti; į GitHub niekas neįkelta.
