# 📱 GUIDE D'INSTALLATION — Boutique Artisanale App
## Suivez ces étapes dans l'ordre (30 minutes maximum)

---

## ÉTAPE 1 — Créer votre projet Firebase (gratuit)

1. Allez sur : https://console.firebase.google.com
2. Cliquez **"Créer un projet"**
3. Nom du projet : **boutique-artisanale**
4. Désactivez Google Analytics (pas nécessaire)
5. Cliquez **"Créer le projet"**

---

## ÉTAPE 2 — Activer l'Authentification

1. Dans le menu gauche → **Authentication**
2. Cliquez **"Commencer"**
3. Onglet **"Sign-in method"**
4. Cliquez sur **Email/Mot de passe** → Activer → Enregistrer

---

## ÉTAPE 3 — Créer la base de données

1. Menu gauche → **Firestore Database**
2. Cliquez **"Créer une base de données"**
3. Choisissez **"Mode production"**
4. Région : **europe-west3 (Frankfurt)**
5. Cliquez **"Activer"**

### Règles de sécurité (copiez-collez) :
Allez dans Firestore → onglet **Règles** → remplacez par :

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId} {
      allow read: if request.auth != null;
      allow write: if request.auth.uid == userId;
    }
    match /planning/{month} {
      allow read, write: if request.auth != null;
    }
    match /chats/{room}/messages/{msg} {
      allow read, write: if request.auth != null;
    }
  }
}
```

Cliquez **"Publier"**

---

## ÉTAPE 4 — Récupérer votre configuration

1. Cliquez l'icône ⚙️ (Paramètres du projet)
2. Descendez jusqu'à **"Vos applications"**
3. Cliquez l'icône **</>** (Web)
4. Nom : **boutique-app** → Enregistrer
5. Copiez le bloc `firebaseConfig` qui ressemble à :

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "boutique-artisanale-xxx.firebaseapp.com",
  projectId: "boutique-artisanale-xxx",
  storageBucket: "boutique-artisanale-xxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abc123"
};
```

---

## ÉTAPE 5 — Mettre votre config dans l'app

1. Ouvrez le fichier **index.html** avec un éditeur de texte (Notepad)
2. Cherchez : `VOTRE_API_KEY`
3. Remplacez TOUT le bloc `firebaseConfig` par celui copié à l'étape 4
4. Sauvegardez le fichier

---

## ÉTAPE 6 — Mettre l'app en ligne (Netlify — GRATUIT)

1. Allez sur : https://netlify.com
2. Cliquez **"Sign up"** → choisissez **"Email"** → créez votre compte
3. Une fois connecté, allez sur **https://app.netlify.com/drop**
4. **Glissez-déposez** votre dossier `boutique-app` sur la page
5. Netlify génère une URL du type : `https://amazing-name-123.netlify.app`

C'est votre lien d'accès ! Partagez-le avec tous vos artisans.

---

## ÉTAPE 7 — Installer sur les smartphones

### Sur Android (Chrome) :
1. Ouvrez Chrome sur votre téléphone
2. Allez sur votre URL Netlify
3. Appuyez sur les ⋮ (3 points en haut à droite)
4. Cliquez **"Ajouter à l'écran d'accueil"**
5. L'icône **BA** apparaît sur votre écran → c'est votre app !

### Sur iPhone (Safari) :
1. Ouvrez Safari (pas Chrome !)
2. Allez sur votre URL Netlify
3. Appuyez sur le bouton **Partager** (carré avec flèche)
4. Appuyez sur **"Sur l'écran d'accueil"**
5. Appuyez **Ajouter**

---

## ÉTAPE 8 — Créer les comptes artisans

Chaque artisan doit :
1. Ouvrir l'app sur son téléphone
2. Cliquer **"Créer un compte"**
3. Remplir son nom, activité, email, mot de passe
4. Choisir sa couleur
5. C'est fait ! Il est visible de tous.

---

## EN CAS DE PROBLÈME

Contactez Valérie : +32 496 84 25 52
Ou envoyez votre question à claude.ai

---

*Application créée avec Firebase (Google) + Netlify — 100% gratuit pour votre usage*
