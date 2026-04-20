---
name: artisan-vitrine
description: >
  Créer des sites vitrine production-ready pour les artisans du bâtiment et des
  métiers techniques (électricien, plombier, menuisier, peintre, chauffagiste,
  maçon, carreleur, etc.). Structure reproductible, responsive mobile-first,
  accessibilité WCAG AA, SEO local et géo-ciblage intégrés, patterns UX
  orientés conversion (social proof, CTA clairs, trust signals). Aucun emoji,
  aucune esthétique IA générique. Résultat organique, artisanal, humain.
---

# Skill — Sites vitrine pour artisans

Ce skill produit du code HTML/CSS/JS (ou React) complet, propre et directement
utilisable pour tout corps de métier artisanal. Chaque génération doit sembler
faite à la main par un designer qui connaît le secteur, pas par une IA.

---

## 1. Avant de coder — Cadrage obligatoire

Avant d'écrire une seule ligne, répondre mentalement à ces questions :

- **Métier** : quel corps de métier précis ? (électricien, plombier, couvreur…)
- **Zone géographique** : ville(s) et département(s) couverts
- **Persona client** : particulier, copropriété, promoteur, entreprise ?
- **Différenciateur** : urgences 24h/24, certifications RGE, spécialité domotique, etc.
- **Ton** : sérieux et rassurant, local et chaleureux, expert et technique ?
- **Palette** : choisir une couleur dominante liée au métier (voir section 4), jamais imposée au hasard

---

## 2. Structure de page — Ordre fixe et reproductible

Chaque site suit EXACTEMENT cet ordre de sections. Ne pas réorganiser.
Chaque section a un `id` sémantique pour l'ancrage et le SEO.

```
1. <header>        Navigation fixe + logo + CTA téléphone visible
2. #hero           Accroche + sous-titre + CTA principal + photo réelle ou fond métier
3. #services       Grille des prestations (3 à 6 max)
4. #zones          Zone d'intervention géographique
5. #realisations   Galerie avant/après ou projets récents (3 minimum)
6. #temoignages    Avis clients (social proof)
7. #a-propos       Présentation humaine de l'artisan
8. #certifications Labels, assurances, certifications (Qualibat, RGE, etc.)
9. #contact        Formulaire + téléphone + adresse + carte (Google Maps embed)
10. <footer>       Mentions légales, SIRET, liens, zone de service résumée
```

---

## 3. SEO local et géo-ciblage — Règles techniques

### Balises HTML obligatoires

```html
<!-- Dans <head> -->
<title>[Métier] [Ville] — [Nom Artisan] | [Spécialité courte]</title>
<meta name="description" content="[Prénom Nom], [métier] à [Ville] ([Département]).
  [Spécialité 1], [Spécialité 2]. Devis gratuit — [Téléphone].">
<link rel="canonical" href="https://[domaine].fr/">

<!-- Open Graph -->
<meta property="og:title" content="[Métier] à [Ville] — [Nom]">
<meta property="og:description" content="[Même description courte]">
<meta property="og:type" content="website">
<meta property="og:locale" content="fr_FR">

<!-- Géolocalisation -->
<meta name="geo.region" content="FR-[code département]">
<meta name="geo.placename" content="[Ville]">
<meta name="geo.position" content="[latitude];[longitude]">
<meta name="ICBM" content="[latitude], [longitude]">
```

### Schema.org LocalBusiness (JSON-LD obligatoire dans <head>)

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "[Nom de l'entreprise]",
  "description": "[Description courte du métier et de la zone]",
  "url": "https://[domaine].fr",
  "telephone": "+33[numéro]",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "[Adresse]",
    "addressLocality": "[Ville]",
    "postalCode": "[Code postal]",
    "addressCountry": "FR"
  },
  "geo": {
    "@type": "GeoCoordinates",
    "latitude": [lat],
    "longitude": [lng]
  },
  "areaServed": [
    { "@type": "City", "name": "[Ville 1]" },
    { "@type": "City", "name": "[Ville 2]" }
  ],
  "openingHoursSpecification": [
    {
      "@type": "OpeningHoursSpecification",
      "dayOfWeek": ["Monday","Tuesday","Wednesday","Thursday","Friday"],
      "opens": "08:00",
      "closes": "18:00"
    }
  ],
  "hasCredential": "[RGE, Qualibat, etc.]",
  "priceRange": "€€"
}
</script>
```

### Contenu géo-ciblé dans la page

- Le `<h1>` doit contenir le métier ET la ville : "Électricien à Lyon"
- La section `#zones` liste les communes couvertes avec liens internes si multipage
- Le footer répète la zone de service en texte simple (utile pour le crawl)
- Chaque `<img>` a un `alt` descriptif incluant le métier et la ville si pertinent

---

## 4. Esthétique — Identité visuelle par métier

### Palettes recommandées par corps de métier

| Métier | Couleur dominante | Accent | Fond |
|---|---|---|---|
| Electricien | #1a2b4a (bleu nuit) | #f5a623 (ambre électrique) | #f8f6f1 (blanc cassé chaud) |
| Plombier | #1e3a5f (bleu marine) | #e8d5b0 (sable) | #fafaf8 |
| Menuisier | #3d2b1f (brun bois) | #c8a96e (chêne clair) | #fdf8f2 |
| Peintre | #2c3e50 (ardoise) | palette variable selon charte client | #ffffff |
| Maçon | #4a3728 (terre cuite) | #b8956a (pierre) | #f7f4ef |
| Couvreur | #2d3a2e (vert ardoise) | #8b7355 (tuile) | #f5f3ef |
| Chauffagiste | #8b1a1a (rouge brique) | #c4a35a (cuivre) | #f9f6f1 |
| Carreleur | #2a2a2a (anthracite) | #b5a69a (grès) | #f8f7f5 |

Ces palettes sont des points de départ. Les adapter au client mais conserver la
logique : une couleur de métier profonde, un accent chaud, un fond neutre jamais
blanc pur.

### Typographie — Règles strictes

- **Titre principal (h1, hero)** : serif à empattements marqués ou sans-serif
  industriel avec caractère. Exemples : Playfair Display, Libre Baskerville,
  Barlow Condensed, Familjen Grotesk, DM Serif Display, Fraunces.
- **Corps de texte** : lisible, chaleureux, jamais froid. Exemples : Source Serif 4,
  Lora, Nunito, Outfit, IBM Plex Sans.
- **Ne jamais utiliser** : Inter, Roboto, Arial, Helvetica, Open Sans, Poppins,
  Space Grotesk, Montserrat seul sans personnalisation poussée.
- **Taille minimale** corps : 16px. Line-height : 1.6 minimum.
- Charger les fonts via Google Fonts avec `display=swap`.

### Ce qui rend le design organique (pas IA)

- Utiliser des angles très légèrement impurs sur les séparateurs de section
  (clip-path avec des valeurs irrégulières, pas 45deg exact)
- Varier les espacements entre sections (pas de padding uniforme partout)
- Une photo de vraie chantier ou de l'artisan au travail vaut mieux qu'une
  illustration vectorielle parfaite
- Les cartes de service ont des hauteurs légèrement différentes si le contenu
  le justifie — pas de grilles rigides au pixel
- Les couleurs de fond alternent entre sections : blanc cassé, teinte légère,
  blanc cassé — jamais deux fonds identiques consécutifs
- Les ombres sont douces et décalées (box-shadow avec valeurs légèrement
  asymétriques), jamais des drop-shadow identiques et parfaits partout

### Ce qu'il faut absolument éviter

- Aucun emoji dans le contenu (ni dans les titres, ni dans les listes)
- Pas d'icones Font Awesome génériques utilisées sans cohérence
- Pas de dégradé violet ou bleu néon
- Pas de fond entièrement noir avec texte blanc fluo
- Pas de cartes identiques et parfaitement alignées sans respiration
- Pas de boutons CTA avec `border-radius: 50px` pill générique
- Pas d'animations loop infinie (tourne, pulse, bounce) sauf usage précis
- Pas de hero avec overlay texte sur image floue en plein écran sans texture

---

## 5. Responsive — Mobile-first obligatoire

L'artisan est souvent cherché sur mobile en urgence. Le mobile est prioritaire.

### Breakpoints

```css
/* Mobile first — base styles pour 320px+ */
/* Tablette */
@media (min-width: 768px) { }
/* Desktop */
@media (min-width: 1024px) { }
/* Large */
@media (min-width: 1280px) { }
```

### Règles mobiles critiques

- Le numéro de téléphone est un `<a href="tel:+33...">` cliquable, toujours
  visible dans le header sur mobile (pas caché dans un menu)
- Le CTA principal du hero est pleine largeur sur mobile
- La navigation mobile est un menu hamburger simple, sans animation complexe
- Les grilles de services passent en colonne unique sous 768px
- Les images utilisent `srcset` et `sizes` pour le responsive images
- `font-size` des titres réduit via `clamp()` : `clamp(1.8rem, 5vw, 3.5rem)`
- Aucun texte ne dépasse la largeur de l'écran (overflow-x: hidden sur body)
- Touch targets minimum 44x44px (boutons, liens de nav)

---

## 6. Accessibilité — WCAG AA minimum

```html
<!-- Structure sémantique obligatoire -->
<header role="banner">
<nav aria-label="Navigation principale">
<main id="contenu-principal">
<section aria-labelledby="id-du-titre-de-section">
<footer role="contentinfo">

<!-- Skip link (premier élément du body) -->
<a href="#contenu-principal" class="skip-link">Aller au contenu</a>
```

### Checklist accessibilité

- Ratio de contraste texte/fond minimum 4.5:1 (vérifier avec les palettes choisies)
- Tous les `<img>` ont un attribut `alt` descriptif (ou `alt=""` si décoratif)
- Les formulaires ont des `<label>` associés à chaque `<input>`
- Les boutons ont un texte visible ou `aria-label` explicite
- Focus visible sur tous les éléments interactifs (ne pas supprimer l'outline)
- Le plan de page est logique sans CSS (order HTML = order visuel)
- Les couleurs ne sont pas le seul moyen de transmettre une information

```css
/* Skip link */
.skip-link {
  position: absolute;
  top: -100%;
  left: 1rem;
  background: var(--couleur-accent);
  color: #fff;
  padding: 0.5rem 1rem;
  z-index: 9999;
}
.skip-link:focus {
  top: 1rem;
}

/* Focus visible */
:focus-visible {
  outline: 3px solid var(--couleur-accent);
  outline-offset: 3px;
}
```

---

## 7. Patterns UX — Conversion et confiance

### Hero section

```
Structure obligatoire :
H1 : [Métier] à [Ville] — [Promesse principale]
Sous-titre : [Spécialité] + [Argument de confiance court] + [Zone]
CTA principal : "Demander un devis gratuit" → ancre #contact
CTA secondaire : "Appeler maintenant" → tel:
Badge de confiance : "X ans d'expérience" ou logo certification
```

Le CTA principal est un `<a>` stylisé en bouton, jamais un `<button>` générique
sans contexte. La couleur du CTA est l'accent de la palette, pas une couleur
aléatoire.

### Section services

- Maximum 6 prestations
- Chaque carte : titre court, description 2-3 phrases, lien "En savoir plus" ou
  ancre vers une section détaillée
- Pas d'icone seule sans texte
- L'ordre des services reflète la fréquence de recherche (le service le plus
  demandé en premier)

### Social proof — Témoignages

```html
<!-- Structure d'un témoignage -->
<blockquote>
  <p>[Texte du témoignage, entre 30 et 80 mots, réel et spécifique]</p>
  <footer>
    <cite>[Prénom Nom]</cite>
    <span>, [Ville], [Année]</span>
    <!-- Étoiles en SVG ou caractères Unicode, pas en emoji -->
    <div class="etoiles" aria-label="5 étoiles sur 5">
      <span aria-hidden="true">★★★★★</span>
    </div>
  </footer>
</blockquote>
```

- Minimum 3 témoignages
- Inclure la ville du client (preuve géographique)
- Mentionner le type de travaux dans le témoignage si possible
- Ajouter un lien vers la source (Google, Pages Jaunes) si disponible

### Trust signals — Section certifications

Afficher sous forme de liste horizontale avec logos SVG ou noms textuels :
- Assurance décennale (obligatoire bâtiment)
- Qualibat / RGE / QualiPAC selon le métier
- Numéro SIRET visible dans le footer
- Ancienneté de l'entreprise
- Nombre de chantiers réalisés si pertinent

### CTA de contact

- Le formulaire ne demande que l'essentiel : Prénom, Téléphone, Type de travaux,
  Message (optionnel)
- Un champ de plus = moins de conversions. Pas d'email obligatoire si le
  téléphone suffit pour le métier
- Après le formulaire : le numéro de téléphone en grand, les horaires, l'adresse
- Google Maps embed avec `loading="lazy"` et titre accessible

---

## 8. Performance et code propre

- CSS custom properties (variables) pour toutes les couleurs et espacements
- Pas de framework CSS externe sauf si demandé (pas de Bootstrap par défaut)
- Les images ont `width` et `height` déclarés pour éviter le layout shift
- `loading="lazy"` sur toutes les images hors hero
- Le CSS critique (above the fold) peut être inline dans `<style>` si mono-page
- Pas de JavaScript inutile : le site doit fonctionner sans JS pour les contenus
- Les fonts Google sont chargées avec `<link rel="preconnect">` en amont

```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
```

---

## 9. Variables CSS — Template de base

```css
:root {
  /* Couleurs — à adapter par métier */
  --c-primaire: #1a2b4a;
  --c-accent: #f5a623;
  --c-fond: #f8f6f1;
  --c-fond-alt: #eeeae3;
  --c-texte: #1e1e1e;
  --c-texte-clair: #5a5a5a;
  --c-blanc: #ffffff;

  /* Typographie */
  --t-titre: 'Playfair Display', Georgia, serif;
  --t-corps: 'Source Serif 4', Georgia, serif;
  --t-taille-base: 1rem;
  --t-ligne: 1.65;

  /* Espacements */
  --espace-xs: 0.5rem;
  --espace-s: 1rem;
  --espace-m: 2rem;
  --espace-l: 4rem;
  --espace-xl: 7rem;

  /* Conteneur */
  --largeur-max: 1200px;
  --padding-page: clamp(1rem, 5vw, 3rem);

  /* Ombres */
  --ombre-legere: 0 2px 12px rgba(0,0,0,0.07);
  --ombre-card: 0 4px 24px rgba(0,0,0,0.10);

  /* Rayons */
  --rayon-s: 4px;
  --rayon-m: 8px;
  --rayon-l: 16px;

  /* Transitions */
  --transition: 0.25s ease;
}
```

---

## 10. Checklist finale avant livraison

Avant de terminer la génération, vérifier mentalement chaque point :

**Structure**
- [ ] Les 10 sections sont présentes dans l'ordre défini
- [ ] Chaque section a son `id` sémantique
- [ ] Le skip link est en premier dans le body

**SEO / Géo**
- [ ] `<title>` contient métier + ville + nom
- [ ] `<meta description>` contient métier + ville + téléphone
- [ ] Schema.org LocalBusiness complet en JSON-LD
- [ ] Balises geo.region et geo.position présentes
- [ ] H1 contient métier + ville
- [ ] Section zones avec les communes listées

**Accessibilité**
- [ ] Tous les `alt` remplis
- [ ] Labels sur tous les champs de formulaire
- [ ] Contrastes vérifiés mentalement avec la palette choisie
- [ ] Focus visible non supprimé

**Mobile**
- [ ] Téléphone cliquable dans le header
- [ ] CTA hero pleine largeur mobile
- [ ] Grille services en colonne sur mobile
- [ ] Pas d'overflow horizontal

**UX / Conversion**
- [ ] CTA principal visible sans scroll sur desktop et mobile
- [ ] Minimum 3 témoignages avec ville et date
- [ ] Formulaire avec 4 champs maximum
- [ ] Certifications et assurance visibles

**Esthétique organique**
- [ ] Aucun emoji dans le code
- [ ] Police de titre distinctive (pas Inter, Roboto, etc.)
- [ ] Palette cohérente avec le métier
- [ ] Pas de dégradé générique violet/bleu
- [ ] Animations discrètes et utiles uniquement
