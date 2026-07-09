# Faits historiques

Référentiel de contexte historique (événements mondiaux, nationaux, régionaux, communaux).

## Structure

- `monde.json` — faits mondiaux (`type: MONDE`, ex. guerres mondiales, pandémies)
- `national/<pays>.json` — faits nationaux (`type: NATIONAL`, ex. règnes avec `categorie: REGNE`)
  - `national/france.json` pour la France (pays dominant du GEDCOM)
- `regional/<slug>.json` — faits régionaux (`type: REGIONAL`)
- `departement/<slug>.json` — faits départementaux
- `communal/<slug>.json` — faits communaux (`type: COMMUNAL`)

Chaque fichier est un **tableau JSON trié par `debut`** (à respecter à la saisie).

## Slugs de fichiers

Les noms de fichiers reprennent les lieux du GEDCOM (`fminier.ged`) :
ASCII, sans accents, espaces/tirets → `_` (ex. `saint_guyomard.json`, `morbihan.json`, `france.json`).

## Exemples d'entrées

Monde :

```json
{
  "type": "MONDE",
  "categorie": "GUERRE",
  "debut": "1939",
  "fin": "1945",
  "libelle": "Seconde Guerre mondiale"
}
```

France (règne) :

```json
{
  "type": "NATIONAL",
  "categorie": "REGNE",
  "debut": "1830",
  "fin": "1848",
  "libelle": "Monarchie de Juillet",
  "description": "Louis-Philippe Ier, roi des Français",
  "pays": "FR"
}
```

## Régénérer la structure vide

Depuis le monorepo `gwriziou` :

```powershell
python scripts/init_faits_historiques.py
```

Ajoute les fichiers manquants pour de nouvelles communes du GEDCOM, sans écraser le contenu existant.
