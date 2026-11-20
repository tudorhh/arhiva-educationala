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

### Ce inseamna baleierea (Sweep-line)

[Baleierea](https://ro.wikipedia.org/wiki/Algoritm_de_baleiere) reprezinta metoda de parcurgere a informatiei dupa directia unei drepte.
Ea ajuta la parcurgerea informatiei dintr-un plan intr-o ordine logica si usor de utilizat.
In problemele de informatica, baleierea poate fi folosita in doua moduri:
- Baleiere geometrica: Pentru probleme ce contin puncte in plan ce trebuie procesate.
- Baleiere algebrica: Pentru probleme ce impun mai multe conditii de inegalitate.


### Sweep-line geometric

Baleierea geometrica ajuta la rezolvarea problemelor ce utilizeaza forme geometrice, precum drepte/segmente, dreptunghiuri sau triunghiuri.

### Problema [Restaurant Customers](https://cses.fi/problemset/task/1619) (usoara)

Problema introductiva Restaurant Customers ne cere sa vedem numarul maxim de clienti dintr-un moment.
Situatia din restaurant poate fi vazuta ca o dreapta de timp cu mai multe segmente, iar cerinta se poate traduce in: "dandu-se $n$ segmente, sa se gaseasca cardinalul intersectiei nevide maxime.".

O prima metoda de rezolvare este sa folosim Smenul lui Mars pentru a adauga $+1$ pe intervalul de timp al fiecarui client.
Problema este ca timpii de venire si de plecare ale clientilor pot fi foarte mari, ceea ce nu ne permite sa folosim un vector.

O observatie este ca nu toti timpii sunt importanti. Daca un client este in restaurant pe intervalul de timp $[1,10]$, iar un alt client, pe $[6,15]$, timpi precum cei din intervalul $[1,5]$ au aceeasi valoare: $1$.
Astfel, putem vedea ca ne interseaza doar momentele in care vin sau pleaca clienti.
Aceste momente le vom incapsula intr-o structura $Event$ si le vom parcurge in ordine crescatoare dupa momentul in care au loc. (de observat ca plecarea are loc la momentul $r + 1$)

De ce este nevoie de compararea dupa $delta$?
Deoarece exista mai multe evenimente ce se intampla in acelasi moment.
Astfel, daca la momentul $t$ vine un client si pleaca un altul, iar noi procesam prima data sosirea, atunci vom obtine un rezultat mai mare decat cel dorit.
Pentru rezolvarea acetui caz, sortarea se face si crescator dupa delta.
O alta varianta ar fi fost procesarea impreuna a evenimentelor simultane:

```cpp
for (int i = 1; i <= 2 * n; i++) {
        cnt += events[i].delta;
        if (i==n*2 || events[i].t!=events[i+1].t)
            answer = max(answer, cnt);
    }
```

Sursa completa cu sortare si dupa delta

```cpp
#include <bits/stdc++.h>
 
using namespace std;
 
const int nmax = 2e5;
 
struct Event {
    int t, delta;
    bool operator <(const Event &other) const {
        if (t != other.t)
            return t < other.t;
        return delta < other.delta;
    }
} events[2 * nmax + 1];
 
int n, answer;
 
void read() {
    cin >> n;
    for (int i = 1; i <= n; i++) {
        int l, r;
        cin >> l >> r;
        events[i] = {l, 1};
        events[i + n] = {r + 1, -1};
    }
}
 
void sweep() {
    int cnt = 0;
    for (int i = 1; i <= 2 * n; i++) {
        cnt += events[i].delta;
        answer = max(answer, cnt);
    }
}
 
void print() {
    cout << answer;
}
 
int main() {
    ios_base::sync_with_stdio(false);
    cin.tie(NULL);
    read();
    sort(events + 1, events + n * 2 + 1);
    sweep();
    print();
    return 0;
}
```

Practic, noi am mers cu o dreapta, de la stanga la dreapta, prin mai multe intervale, tinand mereu minte cate intervale deschise avem.

!!! note "Observații"
    Trebuie acordata atentie cazului de egalitate dintre evenimente. (ce se intampla cand dreapta cu care baleiem atinge doua evenimente in acelasi timp?)






Algoritmul de baielere (sweep line) consta in parcurgerea punctelor dintr-un plan folosind o dreapta (verticala, orizontala sau oblica).
Acesta este folosit pentru a rezolva probleme ce utilizeaza forme geometrice precum dreptunghiuri sau triunghiuri pentru a impune restrictii sau pentru a efectua actualizari.
In functie de problema, la un moment dat ne pot interesa doar punctele de pe dreapta, sau doar punctele parcurse anterior.
Adesea, pentru a mentine punctele de interes, este nevoie de o structura de date precum arborele de intervale sau setul.

Parcurgerea punctelor dupa o dreapta presupune sortarea lor. (de exemplu: pentru o baleiere de la stanga la dreapta, punctele vor fi sortate crescator dupa x).


!!! note "Observații"
    De obicei, problemele ce se rezolva cu algoritmul de baleiere presupun interogari despre puncte in plan. Sortarea evenimentelor (punctelor si implicit a interogarilor) presupune ca problema poate fi rezolvata offline (toate interogarile sunt primite la inceputul programului si nu apar sau dispar puncte intre interogari).
    De asemenea, trebuie acordata atentie cazului de egalitate dintre evenimente. (ce se intampla cand dreapta cu care baleiem atinge doua evenimente in acelasi timp?)

Problema clasica 
Restaurant Customers https://cses.fi/problemset/task/1619 OKKKKKKKKKKKKK




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