---
id: sweep-line
authors: [stefdasca]
prerequisites:
    - sorting
    - basic-geometry
tags:
    - geometrie
    - sortare
    - structuri de date
---

Sweep line (geometric/algebric)

Sweep line geometric


Algoritmul de baielere (sweep line) consta in parcurgerea punctelor dintr-un plan folosind o dreapta (verticala, orizontala sau oblica).
Acesta este folosit pentru a rezolva probleme ce utilizeaza forme geometrice precum dreptunghiuri sau triunghiuri pentru a impune restrictii sau pentru a efectua actualizari.
In functie de problema, la un moment dat ne pot interesa doar punctele de pe dreapta, sau doar punctele parcurse anterior.
Adesea, pentru a mentine punctele de interes, este nevoie de o structura de date precum arborele de intervale sau setul.

Parcurgerea punctelor dupa o dreapta presupune sortarea lor. (de exemplu: pentru o baleiere de la stanga la dreapta, punctele vor fi sortate crescator dupa x).


!!! note "Observații"
    De obicei, problemele ce se rezolva cu algoritmul de baleiere presupun interogari despre puncte in plan. Sortarea evenimentelor (punctelor si implicit a interogarilor) presupune ca problema poate fi rezolvata offline (toate interogarile sunt primite la inceputul programului si nu apar sau dispar puncte intre interogari).
    De asemenea, trebuie acordata atentie cazului de egalitate dintre evenimente. (ce se intampla cand dreapta cu care baleiem atinge doua evenimente in acelasi timp?)

Problema clasica 
Restaurant Customers https://cses.fi/problemset/task/1619




Intersection Points https://cses.fi/problemset/task/1740

Rectangle Union https://codeforces.com/problemset/problem/610/D


Skyline?


Probleme: (check title!)
Triangle queries https://www.codechef.com/problems/TRIQUERY

Nuke https://kilonova.ro/problems/2260
rectpoints https://kilonova.ro/problems/658
inspiratie https://kilonova.ro/problems/4285
skittlez https://kilonova.ro/problems/3327



Sweep line algebric

Tot offline, query-uri sortate

kquery https://www.spoj.com/problems/KQUERY/

Ușoare (evenimente +1/−1, câte intervale sunt active)

Meeting Rooms II și Car Pooling (LeetCode) sunt exemple ușoare de sweep. 
techinterview
USACO Bronze 2018 December, The Bucket List, are o soluție de tip sweep. 
usaco
CSES Restaurant Customers (din memorie): câți clienți sunt simultan în restaurant. Cred că e și cea mai simplă introducere.

Medii

CSES Intersection Points și CSES Area of Rectangles sunt probleme de practică pentru sweep line. Prima e cea mai apropiată de ce căutai: numărarea intersecțiilor dintre segmente. 
github
USACO Load Balancing se rezolvă cel mai bine cu sweep line. 
usaco
My Calendar III (LeetCode) e o problemă de dificultate medie. 
techinterview
USACO FEB12 planting cere aria totală acoperită de dreptunghiuri, în O(N log N). 
tjhsst

Grele

Skyline Problem și Rectangle Area II (LeetCode) sunt probleme grele, care combină sweep-ul cu structuri de date. 
techinterview
CSES Minimum Euclidean Distance (cea mai apropiată pereche de puncte) e un clasic pentru sweep line, iar Line Segments Trace I și II sunt alte probleme CSES cu segmente. 
github
Manhattan MST apare și el în lista USACO Guide pentru sweep line. 
vercel
Sweep radial (o rază care se rotește în jurul unui punct): USACO Guide listează probleme de la CEOI, POI, APIO și JOI

Daca vreti sa ne ajutati cu acest articol, ne puteti gasi pe
[github](https://github.com/roalgo-discord/arhiva-educationala) sau pe [serverul
nostru de discord](https://discord.gg/vdDRSmg3fC)

Mai jos găsiți resurse pe care le puteți citi până atunci.

## Introducere

## Problema exemplu

## Concluzii

## Probleme suplimentare

## Resurse suplimentare

- [Sweep Line - USACO Guide](https://usaco.guide/plat/sweep-line?lang=cpp)
- [Sweep line algorithm - Wikipedia](https://en.wikipedia.org/wiki/Sweep_line_algorithm)
- [Line sweep algorithms - Leetcode](https://leetcode.com/discuss/study-guide/2166045/line-sweep-algorithms)
- [Algoritmi de baleiere - Infoarena](https://www.infoarena.ro/algoritmi-de-baleiere)
- [Arbori de intervale și aplicaţii în Geometria Computaţională - Infobits](https://www.infobits.ro/docs/arbori_de_intervale_prof_dana_lica.pdf)
- [Arbori de intervale, pagina 10 - CPPI Sync](https://cppi.sync.ro/materia/lectii/arbori%20de%20intervale.pdf)
- [Sweep Line and Segment Trees - robert1003](https://robert1003.github.io/2020/02/10/sweep-line-and-segment-tree.html)