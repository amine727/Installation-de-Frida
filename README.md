# 📱 LAB 10 — Installation et utilisation de Frida (Android)

## 🎯 Objectif du lab

Ce lab a pour objectif de :

* Installer et configurer **Frida**
* Déployer **frida-server** sur un émulateur Android
* Vérifier la connexion entre le PC et l’émulateur
* Injecter un script JavaScript dans une application Android (DIVA)
* Comprendre les bases de l’instrumentation dynamique

---

## 🛠️ Environnement utilisé

* OS : Windows 10
* Frida : 17.9.1
* ADB : 36.0.0
* Émulateur : Android x86_64 (API 28)
* Application cible : **DIVA**

---

## 📥 Étape 1 — Vérification des outils

```bash
frida --version
adb version
adb devices
```

### 📸 Résultat

<img width="952" height="563" alt="2" src="https://github.com/user-attachments/assets/21185084-29ea-4392-aec4-e96ba5693ce3" />

---

## 📱 Étape 2 — Vérification de l’architecture

```bash
adb shell getprop ro.product.cpu.abi
```

### 📸 Résultat

<img width="1357" height="335" alt="3" src="https://github.com/user-attachments/assets/6fe90d04-6395-4b79-baf1-50c7f5492ffa" />

👉 Architecture détectée : **x86_64**

---

## ⚙️ Étape 3 — Déploiement de frida-server

### Copier le fichier :

```bash
adb push frida-server /data/local/tmp/
```

### Donner les permissions :

```bash
adb shell
cd /data/local/tmp
chmod 755 frida-server
```

---

## 🚀 Étape 4 — Lancer frida-server

```bash
./frida-server &
```

---

## 🔌 Étape 5 — Connexion avec Frida

### Vérifier les processus :

```bash
frida-ps -U
```

---

## 🧪 Étape 6 — Injection dans l’application DIVA

### Commande utilisée :

```bash
frida -U -p 6598 -l test.js
```

### 📸 Résultat

<img width="1144" height="398" alt="4" src="https://github.com/user-attachments/assets/64571a38-e216-46ba-9096-0715be04c0bc" />

👉 Résultat :

```
[+] Frida connecté à DIVA
```

---

## 📜 Exemple de script utilisé

```javascript
Java.perform(function() {
    console.log("[+] Frida fonctionne !");
});
```

---

## 🔍 Analyse

Grâce à Frida, nous avons pu :

* Injecter du code JavaScript dans une application Android
* Accéder à l’API Java via `Java.perform`
* Observer le comportement dynamique de l’application
* Vérifier la communication entre le PC et l’émulateur

---


---

## 🧠 Conclusion

Ce lab permet de comprendre les bases de :

* L’instrumentation dynamique Android
* L’utilisation de Frida pour la sécurité mobile
* L’analyse des applications vulnérables

Frida est un outil puissant permettant :

* l’analyse en temps réel
* l’interception de données sensibles
* le reverse engineering dynamique

---

