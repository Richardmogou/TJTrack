# TJTrack
# 🧾 Cahier des charges — Marketplace de commerce local avec livraison rapide et système publicitaire intégré

## 🎯 Objectif principal
**Digitaliser le commerce de proximité** tout en offrant aux **commerçants, livreurs et clients** des **outils marketing performants et adaptés** à l’économie locale.

---

## 🧩 SPÉCIFICATIONS FONCTIONNELLES

### 🔹 Module publicitaire complet

#### 1. PRODUITS SPONSORISÉS (Priorité MVP)
- Mise en avant de produits sponsorisés en haut des résultats de recherche et dans les catégories associées.
- Système d’enchère simple ou de tarification journalière fixe.
- Statistiques pour le commerçant : impressions, clics, taux de conversion.
- Gestion du budget publicitaire (journalier ou total).
- Interface de suivi dans le tableau de bord commerçant.

#### 2. BANNIÈRES PROMOTIONNELLES (Phase 2)
- Emplacements visuels dans la page d’accueil, les pages de catégories ou panier.
- Formats standards (ex. : 1080x400, 600x200).
- Ciblage par zone géographique ou centre d’intérêt.
- Validation préalable par l’administrateur.
- Mesure des performances : vues, clics, CTR.

#### 3. NOTIFICATIONS PUSH COMMERCIALES (Phase 3)
- Envoi de notifications ciblées (géolocalisation, historique d’achat, préférences).
- Possibilité de personnaliser le message et le visuel.
- Outil de planification et segmentation d’audience.
- Suivi des taux d’ouverture et d’interaction.
- Garde-fous anti-spam : limites journalières, opt-in obligatoire du client.

---

### 👥 User Stories

#### Commerçant
- “En tant que commerçant, je veux **sponsoriser mes produits** pour apparaître en tête des résultats.”
- “En tant que commerçant, je veux **voir les statistiques** de mes campagnes (clics, vues, ventes générées).”
- “En tant que commerçant, je veux **payer directement via Mobile Money** mes campagnes publicitaires.”

#### Administrateur
- “En tant qu’administrateur, je veux **modérer et valider les campagnes publicitaires** avant leur diffusion.”
- “En tant qu’administrateur, je veux **gérer les tarifs et budgets publicitaires** selon les zones et les périodes.”
- “En tant qu’administrateur, je veux **voir les performances globales** du système publicitaire.”

#### Client
- “En tant que client, je veux **voir des produits sponsorisés pertinents** sans être spammé.”
- “En tant que client, je veux **désactiver les notifications commerciales** si je le souhaite.”
- “En tant que client, je veux **accéder rapidement aux promotions locales** autour de moi.”

---

## 💰 SYSTÈME DE MONÉTISATION

### Tarification des options publicitaires
| Type de publicité | Format | Tarification indicative |
|--------------------|---------|--------------------------|
| Produits sponsorisés | Par jour | **1 300 – 3 300 FCFA / jour** |
| Bannières boutique | Par semaine | **6 500 – 33 000 FCFA / semaine** |
| Push notifications | Par envoi ciblé | **65 – 325 FCFA / envoi** |

*(Conversion indicative basée sur 1 € ≈ 655 FCFA)*

### Moyens de paiement intégrés
- **Mobile Money** (MTN, Orange, Moov, etc.)
- **Cartes bancaires locales et internationales**
- **Portefeuille interne (Wallet)** pour micro-crédits publicitaires

### Facturation & reporting
- Génération automatique de factures PDF.
- Tableau de bord avec récapitulatif : budget dépensé, ROI, clics.
- Notifications automatiques de renouvellement ou fin de campagne.

---

## 🧠 TECHNIQUE & ARCHITECTURE

### Stack technique
| Couche | Technologie |
|--------|--------------|
| Frontend Mobile | React Native |
| Backend API | Node.js (NestJS/Express) |
| Base de données | PostgreSQL |
| Authentification | JWT + OAuth2 |
| Hébergement | AWS / GCP / Render |
| Notifications | Firebase Cloud Messaging (FCM) |

### Nouvelles entités BDD
- **Campagne** : id, type, statut, budget, dates, commerçant_id  
- **Emplacement** : zone, type (bannière, push, sponsorisé)  
- **Clic** : id, campagne_id, utilisateur_id, timestamp  
- **Facturation** : id, campagne_id, montant, statut, date

### API publicitaire (exemples)
- `POST /ads/campaigns` → créer une campagne  
- `GET /ads/campaigns/{id}` → consulter une campagne  
- `POST /ads/click` → enregistrer un clic  
- `GET /ads/statistics` → statistiques globales  
- `POST /ads/payment` → paiement via Mobile Money  

### Ciblage géolocalisé
- Basé sur la position GPS de l’utilisateur.
- Rayon de diffusion configurable (ex. 2 km, 5 km).
- Intégration possible avec **Google Maps API** pour calcul de distance.

---

## 🚀 PLAN DE DÉPLOIEMENT

### Phase 1 — **MVP : Produits sponsorisés**
- Objectif : tester la demande locale et valider le modèle économique.
- Modules : sponsorisation produit, paiement Mobile Money, tableau de bord commerçant.
- Indicateurs clés :
  - Taux de clic sur produits sponsorisés (CTR)
  - Revenu publicitaire moyen par commerçant

### Phase 2 — **Extension : Bannières promotionnelles**
- Intégration de visuels personnalisés sur pages clés.
- Outils de reporting avancés.
- Déploiement d’un mini “Ad Manager” pour commerçants.

### Phase 3 — **Notifications & Publicité programmatique**
- Segmentation intelligente (IA légère, comportement d’achat).
- Envoi de push commerciaux avec limitation anti-spam.
- Monétisation de l’espace publicitaire externe (bannières locales).

---

## 📊 MÉTRIQUES DE PERFORMANCE PUBLICITAIRE

| Indicateur | Description | Objectif |
|-------------|-------------|-----------|
| CTR (Click-Through Rate) | Clics / Impressions | ≥ 3% |
| CPC (Coût par clic) | Dépense / Clics | ≤ **200 FCFA** |
| ROI Publicitaire | (Ventes générées / Dépense) x 100 | ≥ 150% |
| Taux de conversion | Achats après clic | ≥ 5% |
| Taux d’opt-out push | % de clients désactivant les push | ≤ 10% |

---

## 🛡️ GARDE-FOUS ANTI-SPAM & QUALITÉ

- Validation manuelle de chaque campagne par l’équipe admin.
- Fréquence maximale de push : **2/jour par commerçant**.
- Système d’évaluation des publicités (pertinence, feedback client).
- Blocage automatique en cas d’abus ou taux de signalement élevé.
- Respect des réglementations locales (RGPD, consentement opt-in).

---

## 📅 SYNTHÈSE DU ROADMAP

| Phase | Fonctionnalités principales | Durée estimée |
|--------|------------------------------|----------------|
| 1️⃣ MVP | Produits sponsorisés + paiement | 3 mois |
| 2️⃣ Extension | Bannières + reporting avancé | 2 mois |
| 3️⃣ Finalisation | Notifications + ciblage IA | 3 mois |

---

## 🧭 Conclusion
Ce projet vise à **moderniser le commerce local** en créant un écosystème où :
- les **commerçants gagnent en visibilité et en ventes**,  
- les **clients accèdent rapidement aux produits de proximité**,  
- et la **plateforme génère des revenus durables** grâce à un système publicitaire local performant.

---
