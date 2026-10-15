# sshiutb

TP **R202 : SSH --- TIPS & TRICKS** (clés, agent, bastion, tunnels, multiplexage).
Support de cours du module R202 / M2102, IUT Béziers.

Le document est un fichier LaTeX **autonome** : `ssh-indep.tex` contient son propre
préambule, il n'inclut aucun fichier externe et se compile n'importe où.

## Compilation

```bash
latexmk -pdf -shell-escape ssh-indep.tex
```

ou simplement :

```bash
make
```

Le `-shell-escape` est indispensable : le document utilise `minted` (coloration de code
via Pygments), qui appelle `pygmentize` depuis LaTeX.

Dépendances : TeXLive (classe `exam`, `minted2`, `babel` français, `hyperref`,
`microtype`, `xcolor`, `listings`, `enumitem`, `parskip`) et `pygments`.

`minted2.sty` (version Debian, licence LPPL) est **embarqué dans le dépôt** : il n'existe
que dans TeXLive Debian, pas dans TeXLive amont ni Ubuntu. LaTeX le trouve dans le
dossier courant, ce qui rend la compilation identique partout.

Sous Debian :

```bash
sudo apt install latexmk texlive-latex-base texlive-latex-recommended \
                 texlive-latex-extra texlive-fonts-recommended \
                 texlive-lang-french python3-pygments
```

## Contribuer

Ce TP est amélioré par ceux qui le font. Le principe :
**une idée se signale par une issue, une issue se règle par une petite pull request.**

1. Ouvrir une issue (trois modèles : signaler une commande erronée, proposer une
   question, demander une clarification).
2. Attendre un feu vert en commentaire.
3. Ouvrir une PR petite : une intention, une section.
4. Relire le PDF produit par la CI (artifact `ssh-indep-pdf`), pas seulement le diff.

Pour commencer : [issues label `bonne-premiere-PR`](https://github.com/pushou/sshiutb/labels/bonne-premiere-PR).
Le détail complet est dans [CONTRIBUTING.md](CONTRIBUTING.md).

**Une PR ne peut être fusionnée que si la compilation LaTeX réussit** : le check
`compile (LaTeX)` de la CI GitHub Actions est obligatoire sur la branche `main`. S'il est
rouge (erreur LaTeX, PDF absent ou vide, dépendance externe introduite), le bouton de
merge est bloqué.

## Contenu

| Fichier | Rôle |
|---|---|
| `ssh-indep.tex` | le TP, autonome (préambule inline) |
| `minted2.sty` | variante Debian de `minted`, embarquée (licence LPPL) |
| `LICENSE` | texte canonique CC BY-SA 4.0 |
| `NOTICE` | application de la licence : ce qui est couvert, citation attendue |
| `Makefile` | compilation locale (`make`, `make check`, `make test-autonomie`) |
| `tools/check-fls.sh` | preuve d'autonomie : aucun fichier lu hors du dépôt |
| `tools/test-autonomie.sh` | test du garde-fou d'autonomie |
| `.github/workflows/build.yml` | vérification de compilation sur chaque PR |
| `.github/ISSUE_TEMPLATE/` | modèles d'issues pour les contributions |
| `.github/pull_request_template.md` | cadre d'une pull request |

## Licence

**CC BY-SA 4.0** (Creative Commons Attribution - Partage dans les Mêmes Conditions 4.0
International), décidée par l'auteur.

`LICENSE` contient le texte canonique CC BY-SA 4.0, repris sans modification pour être
reconnu automatiquement par GitHub. `NOTICE` précise ce qui est couvert, ce qui ne
l'est pas, et la citation attendue.

Vous pouvez copier, redistribuer, adapter ce support de cours, y compris commercialement,
à condition de créditer l'auteur et de diffuser vos adaptations sous la même licence.

Le fichier `minted2.sty` n'est pas concerné : il garde sa propre licence LPPL
(Geoffrey M. Poore, Konrad Rudolph).
