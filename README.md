# 📈 Uptime & Reaction Time API

Une API simple pour surveiller la disponibilité et le temps de réaction de n'importe quel site web.
Ajoutez vos liens, consultez l'historique des temps de réponse, et visualisez tout ça en un clin d'œil !

---

## ✨ Fonctionnalités

* ➕ Ajout d'un site à surveiller (avec mot de passe/secret)
* 📊 Récupération de l'historique des temps de réaction (ms)
* 🟢 Vérification automatique de l'uptime toutes les 3 heures (nous réfléchissons à un éventuel plan VIP voir premium qui permettrait de reduire ce délai)
* 🗃️ Sauvegarde et rotation automatique de la base de données
* 📈 Intégration HTML prête à l'emploi avec graphique (Chart.js)

---

## 🌐 Lien de l’API

> Par défaut : 
```js
http://88.151.197.191:2025/uptime
```

---

## 🚀 Exemples d’appel

### ➕ Ajouter un site à surveiller

```js
fetch('http://' + '88.151.197.191:2025' + '/uptime/add', {
  method: 'POST',
  headers: { 'Content-Type': 'application/json' },
  body: JSON.stringify({
    link: 'https://monsite.fr', // Pensez au http.s devant !
    password: 'monSecret'
  })
})
.then(res => res.json())
.then(data => {
  console.log(data);
});
```

---

### 📊 Récupérer les stats d'un site (GET)
*Attention: A utiliser à titre indicatif uniquement, la connection de notre serveur a un impact direct sur le temps de reaction affiché.
```js
fetch('http://' + '88.151.197.191:2025' + '/uptime/stats?link=https://monsite.fr&password=monSecret')
  .then(res => res.json())
  .then(data => {
    // data.data = [{ time, status }, ...]
    console.log(data.data);
  });
```

---

## 🔧 Paramètres acceptés

### `/uptime/add` – POST JSON

| Champ      | Type   | Description                        | Obligatoire |
| ---------- | ------ | ---------------------------------- | ----------- |
| `link`     | string | Lien du site à surveiller          | Oui         |
| `password` | string | Mot de passe/secret associé        | Oui         |

### `/uptime/stats` – GET Query

| Paramètre  | Type   | Description                        | Obligatoire |
| ---------- | ------ | ---------------------------------- | ----------- |
| `link`  | string | Lien du site à surveiller          | Oui         |
| `password` | string | Mot de passe/secret associé        | Oui         |

---

## 🌐 Exemple d’intégration HTML

Un exemple complet est disponible dans [`uptimeStats.html`](./uptimeStats.html), incluant :

* Ajout d'un site à surveiller
* Affichage d'un graphique interactif du temps de réaction (Chart.js)

---

## 🧠 À propos

API développée pour être **simple** et **sans dépendances**.

---

## 💬 Contact

Tu veux proposer une amélioration ? Discuter de l’intégration dans un projet plus vaste ?

* [@console.log(" *x1 ")](https://discord.com/users/1066067393123733595)
* [@! ℳ𝓪𝔁𝟑𝟐](https://discord.com/users/1163887501895815168)

---

## Vu total de nos API
<img src='https://komarev.com/ghpvc/?username=console-log-Max32-API&style=for-the-badge'>

---

> 🛠️ Maintenu par des devs **passionnés & bénévoles**. Soyez compréhensif 🙏

> Chatgpt nous as permis d'économiser du temps en rédigeant à notre place le fichier d'exemple (html) et le readme. Je pense que je n'apprends rien à personne en précisant que cet outil magique a encore besoin d'une supervision humaine.
