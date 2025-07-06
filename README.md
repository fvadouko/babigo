# Babigo

Babigo est une plateforme de gestion de covoiturage et de mobilité professionnelle, composée d’un backend Laravel (API REST sécurisée) et d’un frontend Flutter (application mobile multiplateforme).

## Structure du projet

```
babigo/
├── backend-babigo/   # Backend API Laravel 11 (PHP)
├── babigo_front/     # Frontend Flutter (Dart)
```

---

## 1. Backend : `backend-babigo`

- **Framework** : Laravel 11
- **Fonctionnalités principales** :
  - Authentification unifiée (passager & entreprise) via API REST (Sanctum multi-guard)
  - Gestion des comptes (inscription, login, reset, suppression, vérification email)
  - Sécurité avancée (middleware custom, soft delete, vérification email, tokens)
  - Endpoints robustes pour intégration Flutter
  - Fichiers clés :
    - `app/Http/Controllers/Api/Front/UnifiedAuthController.php` : point d’entrée unifié pour l’auth
    - `app/Http/Middleware/CompanySanctumGuard.php` : middleware custom pour guard entreprise
    - `routes/api.php` : routes API principales
    - `config/sanctum.php`, `bootstrap/app.php` : configuration multi-guard

### Lancer le backend

```bash
cd backend-babigo
cp .env.example .env # puis configurer la base de données
composer install
php artisan migrate --seed
php artisan serve
```

---

## 2. Frontend : `babigo_front`

- **Framework** : Flutter (Dart)
- **Fonctionnalités principales** :
  - Authentification et gestion de profil (passager & entreprise)
  - Appels API sécurisés (compatibilité multi-guard Laravel)
  - UI dynamique selon le type d’utilisateur
  - Synchronisation avec les évolutions backend
  - Fichiers clés :
    - `lib/core/config.dart` : configuration des endpoints API
    - `lib/features/auth/` : logique d’authentification
    - `lib/features/compte/` : gestion des profils utilisateurs

### Lancer le frontend

```bash
cd babigo_front
flutter pub get
flutter run
```

---

## 3. Tests & Debug

- **Backend** :
  - `php artisan test` ou `phpunit`
  - Fichiers de debug : `routes/token_debug.php`, logs Laravel
- **Frontend** :
  - `flutter test`

---

## 4. Contribution

- Forkez le repo, créez une branche, proposez une PR.
- Respectez la structure des dossiers et la séparation des responsabilités (backend <-> frontend).
- Documentez vos endpoints et vos changements majeurs.

---

## 5. Auteurs & Contact

- Backend : @votre-nom
- Frontend : @votre-nom
- Contact : contact@babigo.com

---

## 6. Licence

Projet sous licence MIT.
