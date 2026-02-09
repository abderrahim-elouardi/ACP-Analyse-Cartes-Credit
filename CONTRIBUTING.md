# Guide de Contribution

Merci de votre intérêt pour contribuer à **ACP-Analyse-Cartes-Credit** !

---

## Comment Contribuer

### Étapes Rapides

1. **Forkez** le projet
2. **Créez** une branche : `git checkout -b feature/ma-contribution`
3. **Commitez** : `git commit -m "feat: ajout nouvelle fonctionnalité"`
4. **Poussez** : `git push origin feature/ma-contribution`
5. **Ouvrez** une Pull Request

---

## Types de Contributions Acceptées

- Corrections de bugs
- Nouvelles fonctionnalités
- Améliorations des analyses
- Documentation
- Tests

---

## Standards de Code

### Code R

- Utilisez **snake_case** pour les variables et fonctions
- Commentez les parties complexes
- Testez avant de soumettre

```r
# Bon exemple
data_clean <- data %>%
  filter(!is.na(BALANCE)) %>%
  mutate(log_balance = log1p(BALANCE))
```

---

## Signaler un Bug

Ouvrez une [Issue](https://github.com/votre-repo/ACP-Analyse-Cartes-Credit/issues) avec :
- Description du problème
- Étapes pour reproduire
- Environnement (OS, R version)

---

**Merci pour votre contribution !**
