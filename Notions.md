# 🌐 Guide des Réseaux Informatiques

---

## 📡 1. Introduction aux Réseaux et à l'Internet

**Un réseau informatique** est un système interconnectant des ordinateurs dans une zone limitée (comme une résidence ou un bureau) pour partager des données et des ressources comme des imprimantes.

**L'Internet** est le système mondial de réseaux interconnectés utilisant la suite de protocoles TCP/IP pour communiquer entre réseaux et appareils.

### 📜 Historique

L'origine de l'Internet remonte aux recherches sur le **partage de temps** et la **commutation de paquets** (packet switching) dans les années 1960, menées notamment par :
- 👨‍🔬 **Paul Baran** et **Donald Davies**
- 🏛️ L'agence **DARPA** avec le réseau **ARPANET**

---

## 🏗️ 2. Modèles de Référence : OSI et TCP/IP

Les fonctions réseau sont organisées en **couches d'abstraction** pour assurer l'interopérabilité.

### 📚 Le Modèle OSI (Open Systems Interconnection)
<img src="https://github.com/Schpser/holbertonschool-network/blob/main/Pictures/IOS.png" alt="Modèle OSI" width="300"/>

Développé par l'ISO, il comporte **7 couches** :

<img src="https://github.com/Schpser/holbertonschool-network/blob/main/Pictures/IOS2.png" alt="Modèle OSI" width="300"/>

| Couche | Nom | Fonction | Exemples |
|--------|-----|----------|----------|
| **7️⃣** | **Application** | Services réseau directs pour l'utilisateur | HTTP, FTP, SSH |
| **6️⃣** | **Présentation** | Traduction, chiffrement et compression des données | SSL/TLS, JPEG |
| **5️⃣** | **Session** | Gestion des connexions entre applications | NetBIOS, RPC |
| **4️⃣** | **Transport** | Transmission fiable ou non des segments | TCP, UDP |
| **3️⃣** | **Réseau** | Adressage et routage des paquets | IP, Routeurs |
| **2️⃣** | **Liaison** | Transfert de nœud à nœud, correction d'erreurs | Ethernet, Wi-Fi, Switch |
| **1️⃣** | **Physique** | Transmission des bits bruts sur un support physique | Câbles, Ondes |

> **💡 Astuce Mnémotechnique :** "**P**lease **D**o **N**ot **T**hrow **S**ausage **P**izza **A**way"  
> (Physique → Liaison → Réseau → Transport → Session → Présentation → Application)

### 📦 Exemples Concrets par Couche

| Couche | Matériel/Protocoles | Usage |
|--------|---------------------|-------|
| **2️⃣ Liaison** | Switch, adresse MAC, VLAN | 🔀 Commutation locale |
| **3️⃣ Réseau** | Routeur, adresse IP, routage | 🗺️ Routage inter-réseaux |
| **4️⃣ Transport** | Ports TCP/UDP, numéros de séquence | 📬 Livraison des données |

### 📦 Encapsulation des Données (PDU - Protocol Data Unit)

À chaque couche, les données changent de nom :

```
┌──────────────────────────────────────────┐
│   Application (7-5)  →  📄 Données       │
│   Transport (4)      →  📦 Segment/Datagramme
│   Réseau (3)         →  📫 Paquet        │
│   Liaison (2)        →  📨 Trame         │
│   Physique (1)       →  ⚡ Bits          │
└──────────────────────────────────────────┘
```

### 🌐 Le Modèle TCP/IP

C'est le **standard pratique d'Internet**, structuré en **4 couches** :

| Couche TCP/IP | Équivalent OSI | Fonction |
|---------------|----------------|----------|
| **Application** | 7, 6, 5 | HTTP, FTP, DNS, SSH |
| **Transport** | 4 | TCP, UDP |
| **Internet** | 3 | IP, ICMP, routage |
| **Accès réseau (Link)** | 2, 1 | Ethernet, Wi-Fi |

---

## 🗺️ 3. Types de Réseaux selon l'Échelle

<img src="https://github.com/Schpser/holbertonschool-network/blob/main/Pictures/TYPES.jpg" alt="Modèle OSI" width="300"/>

Les réseaux sont classés selon leur **étendue géographique** :

### 🏠 LAN (Local Area Network)

**Réseau local** sur une courte distance (maison, bureau)

| Aspect | Détails |
|--------|---------|
| 📏 **Portée** | Quelques mètres à quelques kilomètres |
| ⚡ **Débit** | 100 Mbps à 10 Gbps |
| 💰 **Coût** | Faible, propriétaire |
| 🔧 **Technologies** | Ethernet (802.3), Wi-Fi (802.11) |
| 📌 **Exemple** | Réseau domestique, réseau d'entreprise sur un site |

### 🌍 WAN (Wide Area Network)

**Réseau étendu** couvrant des régions ou pays. L'**Internet** est le plus grand WAN.

| Aspect | Détails |
|--------|---------|
| 📏 **Portée** | Ville, pays, continent |
| ⚡ **Débit** | Variable (souvent inférieur au LAN) |
| 💰 **Coût** | Élevé, souvent location à un opérateur |
| 🔧 **Technologies** | MPLS, Frame Relay, fibre optique dédiée |
| 📌 **Exemple** | Liaison entre siège social et filiale |

### 📡 Autres Types de Réseaux

| Type | Description | Emoji |
|------|-------------|-------|
| **WLAN** | LAN sans fil (Wireless LAN) | 📶 |
| **MAN** | Metropolitan Area Network - échelle d'une ville | 🏙️ |
| **CAN** | Campus Area Network - campus universitaire | 🎓 |
| **PAN** | Personal Area Network - Bluetooth, appareils personnels | 📱 |
| **SAN** | Storage Area Network - réseau de stockage | 💾 |

---

## 🏷️ 4. Adressage : MAC et IP

Pour que les données atteignent leur destination, chaque appareil doit être **identifié**.

<img src="https://github.com/Schpser/holbertonschool-network/blob/main/Pictures/MAC_IP.jpg" alt="Modèle OSI" width="300"/>

### 🔖 Adresse MAC (Adresse Physique)

L'adresse **Media Access Control** est un identifiant matériel unique gravé sur la carte d'interface réseau (NIC) par le fabricant.

```
┌────────────────────────────────────────┐
│   Adresse MAC : 00:1A:2B:3C:4D:5E     │
│                 └──┬──┘ └────┬─────┘   │
│                   OUI    Identifiant   │
│                (Fabricant)  unique     │
└────────────────────────────────────────┘
```

| Aspect | Détails |
|--------|---------|
| 📏 **Format** | 6 groupes de 2 chiffres hexadécimaux |
| 🏭 **OUI** | Les 3 premiers octets = Identifiant du fabricant |
| 🔄 **Protocole** | ARP permet de traduire une adresse IP en adresse MAC |
| 💡 **Exemple** | `00:1A:2B:3C:4D:5E` |

### 🌐 Adresse IP (Adresse Logique)

Chaque machine sur Internet possède une **adresse IP unique** pour communiquer.

#### 🔢 IPv4

```
┌──────────────────────────────────────┐
│  IPv4 : 192.168.1.10                 │
│         32 bits = 4,3 milliards      │
│         Notation décimale            │
└──────────────────────────────────────┘
```

| Élément | Détails |
|---------|---------|
| 📊 **Format** | 32 bits - 4 octets (0-255.0-255.0-255.0-255) |
| 📈 **Capacité** | ~4,3 milliards d'adresses |
| 📌 **Exemple** | `192.168.1.10` |

#### 🆕 IPv6

```
┌──────────────────────────────────────────────┐
│  IPv6 : 2001:0db8:85a3::8a2e:0370:7334      │
│         128 bits = quasi illimité            │
│         Notation hexadécimale                │
└──────────────────────────────────────────────┘
```

**Pourquoi IPv6 était nécessaire ?**

| Raison | Détails |
|--------|---------|
| ⚠️ **Épuisement IPv4** | Dernier bloc alloué en 2011 |
| 📈 **Capacité** | 340 undécillions d'adresses |
| 🔐 **Sécurité** | IPsec intégré |
| 🚀 **Performance** | Configuration automatique (SLAAC) |
| 📱 **Mobilité** | Meilleure prise en charge |

**Raccourcis IPv6 :**
- Zéros consécutifs → `::` (une seule fois par adresse)
- Zéros débutants → omis
- Exemple : `2001:0db8:0000:0000:0000:0000:0000:0001` → `2001:db8::1`

### 🏛️ Classes et Adresses Spéciales (IPv4)

| Classe | Plage | Usage |
|--------|-------|-------|
| **A** | 1.0.0.0 - 126.255.255.255 | Très grands réseaux |
| **B** | 128.0.0.0 - 191.255.255.255 | Réseaux moyens |
| **C** | 192.0.0.0 - 223.255.255.255 | Petits réseaux |
| **D** | 224.0.0.0 - 239.255.255.255 | Multicast |
| **E** | 240.0.0.0 - 255.255.255.255 | Expérimental |

#### 🔑 Adresses Spéciales

| Adresse | Usage | Emoji |
|---------|-------|-------|
| `0.0.0.0` | Réseau par défaut | 🌐 |
| `255.255.255.255` | Broadcast (diffusion) | 📢 |
| `127.0.0.1` | Loopback (localhost) | 🔄 |
| `127.0.0.0/8` | Plage complète localhost | 🏠 |

### 🔐 Adresses Publiques vs Privées

```
┌────────────────────────────────────────────┐
│  🌍 Internet (Adresses Publiques)          │
│                    ▲                       │
│                    │                       │
│            [🛡️ NAT Router]                │
│                    │                       │
│  🏠 Réseau Privé (Adresses Privées)       │
│     10.x.x.x                               │
│     172.16.x.x - 172.31.x.x               │
│     192.168.x.x                            │
└────────────────────────────────────────────┘
```

| Type | Caractéristiques |
|------|------------------|
| 🌍 **Publiques** | Uniques mondialement, accessibles sur Internet |
| 🏠 **Privées** | Usage interne, non routées sur Internet |

**Plages d'adresses privées :**
- `10.0.0.0` - `10.255.255.255` (10/8)
- `172.16.0.0` - `172.31.255.255` (172.16/12)
- `192.168.0.0` - `192.168.255.255` (192.168/16)

> **💡 NAT (Network Address Translation) :** Permet aux appareils privés de communiquer avec Internet via l'adresse publique unique du routeur.

### ✂️ Subnetting (Sous-réseaux)

**Division d'un réseau IP en plusieurs réseaux logiques plus petits**

```
Réseau : 192.168.1.0/24
         └──────┬──────┘
         Masque : 255.255.255.0
         
/24 signifie : 24 bits pour le réseau, 8 bits pour les hôtes
```

| Aspect | Détails |
|--------|---------|
| 🎯 **Masque** | Indique quelle partie = réseau vs hôte |
| 📌 **Exemple** | `192.168.1.0/24` = masque `255.255.255.0` |
| ✅ **Utilité** | • Réduire le broadcast domain<br>• Améliorer la sécurité<br>• Optimiser les performances |
| 🧮 **Calcul** | Opérations binaires AND |

---

## 🔄 5. Protocoles Fondamentaux

### 🚚 Protocoles de Transport

#### TCP vs UDP

```
┌─────────────────────────────────────────────┐
│  🤝 TCP : Fiable, lent, vérifie tout       │
│  ⚡ UDP : Rapide, pas de vérification       │
└─────────────────────────────────────────────┘
```

| Critère | 🤝 TCP | ⚡ UDP |
|---------|--------|--------|
| **Connexion** | Orienté connexion (3-way handshake) | Sans connexion |
| **Fiabilité** | ✅ Garantie | ❌ Non garantie |
| **Contrôle de flux** | ✅ Oui (fenêtre glissante) | ❌ Non |
| **Ordonnancement** | ✅ Oui | ❌ Non |
| **Usage typique** | 🌐 Web, 📧 Email, 📁 FTP | 🎥 Streaming, 📞 VoIP, 🎮 Jeux |
| **Surcharge** | Plus élevée | Minimale |
| **Emoji** | 🐢 Fiable mais lent | 🐇 Rapide mais risqué |

<img src="https://github.com/Schpser/holbertonschool-network/blob/main/Pictures/UCP_TCP.jpg" alt="Modèle OSI" width="300"/>

### 🌐 Protocoles de Service

| Protocole | Fonction | Port | Emoji |
|-----------|----------|------|-------|
| **DHCP** | 🏷️ Assigne automatiquement des adresses IP | 67/68 | 🏷️ |
| **DNS** | 📖 Résout les noms de domaine en adresses IP | 53 | 📖 |
| **ICMP** | 🏓 Test de connectivité (Ping) | - | 🏓 |
| **ARP** | 🔍 Traduit IP → MAC | - | 🔍 |
| **HTTP** | 🌐 Transfert de pages web | 80 | 🌐 |
| **HTTPS** | 🔒 HTTP sécurisé (chiffré) | 443 | 🔒 |
| **FTP** | 📁 Transfert de fichiers | 21 | 📁 |
| **SSH** | 🔐 Connexion sécurisée à distance | 22 | 🔐 |
| **SMTP** | 📧 Envoi d'emails | 25 | 📧 |

> **💡 Exemple ICMP :** La commande `ping` mesure le temps de trajet aller-retour (round-trip time) vers un hôte.

---

## 🛠️ 6. Infrastructure et Matériel

### 🔌 Câblage et Connexions

| Type | Détails | Emoji |
|------|---------|-------|
| **Câbles RJ45** | Paires torsadées Cat5/Cat6 | 🔌 |
| **Wi-Fi** | IEEE 802.11 (2.4 GHz, 5 GHz, 6 GHz) | 📶 |
| **Fibre optique** | Très haut débit, longue distance | 💡 |

### 🖥️ Équipements Réseau

```
┌────────────────────────────────────────────┐
│  👤 Client  ──>  [Switch]  ──>  [Router]   │
│                    LAN          WAN        │
│                              ──>  🌍       │
└────────────────────────────────────────────┘
```

| Équipement | Couche OSI | Fonction | Emoji |
|------------|------------|----------|-------|
| **Hub** | 1 (Physique) | Répéteur bête, diffuse à tous | 📡 |
| **Switch** | 2 (Liaison) | Commutation intelligente par MAC | 🔀 |
| **Routeur** | 3 (Réseau) | Routage entre réseaux par IP | 🗺️ |
| **Passerelle** | 7 (Application) | Point de sortie vers Internet | 🚪 |
| **Pare-feu** | 3-7 | Filtre et sécurise le trafic | 🛡️ |

### 🕸️ Topologies Réseau

| Topologie | Description | Emoji |
|-----------|-------------|-------|
| **⭐ Étoile** | Tous connectés à un hub/switch central | ⭐ |
| **🚌 Bus** | Tous sur un câble principal | 🚌 |
| **⭕ Anneau** | Connexion circulaire | ⭕ |
| **🕸️ Maillée** | Connexions multiples entre tous | 🕸️ |

---

## 🔌 7. Ports et Services

Les **ports** (0 à 65535) identifient les services spécifiques sur un appareil.

### 📊 Classification des Ports

```
┌────────────────────────────────────────────┐
│  0 - 1023      : 🔑 Ports Bien Connus      │
│  1024 - 49151  : 📝 Ports Enregistrés      │
│  49152 - 65535 : 🔀 Ports Dynamiques       │
└────────────────────────────────────────────┘
```

### 🔑 Ports Bien Connus (0-1023)

| Port | Service | Protocole | Description |
|------|---------|-----------|-------------|
| **20/21** | FTP | TCP | 📁 Transfert de fichiers |
| **22** | SSH | TCP | 🔐 Shell sécurisé |
| **23** | Telnet | TCP | 💻 Terminal non sécurisé |
| **25** | SMTP | TCP | 📧 Envoi d'emails |
| **53** | DNS | TCP/UDP | 📖 Résolution de noms |
| **67/68** | DHCP | UDP | 🏷️ Attribution d'IP |
| **80** | HTTP | TCP | 🌐 Web non sécurisé |
| **110** | POP3 | TCP | 📬 Réception d'emails |
| **143** | IMAP | TCP | 📮 Emails sur serveur |
| **443** | HTTPS | TCP | 🔒 Web sécurisé |
| **3306** | MySQL | TCP | 🗄️ Base de données |
| **3389** | RDP | TCP | 🖥️ Bureau à distance |

### 📝 Ports Enregistrés (1024-49151)

Applications spécifiques enregistrées auprès de l'IANA

### 🔀 Ports Dynamiques (49152-65535)

Utilisés temporairement pour les connexions client (éphémères)

---

## 🔒 8. Sécurité et Gouvernance

### 🏛️ Gouvernance d'Internet

| Organisme | Rôle | Emoji |
|-----------|------|-------|
| **ICANN** | Gère les espaces d'adresses IP et noms de domaine | 🌐 |
| **IETF** | Standardise les protocoles via les RFC | 📜 |
| **IANA** | Assigne les numéros de protocoles et ports | 🔢 |
| **W3C** | Standards du Web | 🕸️ |

### ⚠️ Menaces Réseau

| Menace | Description | Emoji |
|--------|-------------|-------|
| **Malware** | Virus, vers, ransomwares | 🦠 |
| **DDoS** | Attaque par déni de service | 💥 |
| **Phishing** | Hameçonnage par email | 🎣 |
| **MITM** | Interception de communication | 👂 |
| **Spoofing** | Usurpation d'identité | 🎭 |

### 🛡️ Mesures de Protection

| Protection | Fonction | Emoji |
|------------|----------|-------|
| **Pare-feu (Firewall)** | Filtre le trafic entrant/sortant | 🛡️ |
| **Filtrage MAC** | Limite l'accès aux adresses autorisées | 🔐 |
| **VPN** | Tunnel chiffré pour connexions sécurisées | 🔒 |
| **TLS/SSL** | Chiffrement des données en transit | 🔐 |
| **IDS/IPS** | Détection/Prévention d'intrusions | 🚨 |
| **Segmentation** | Isolation des réseaux critiques | ✂️ |

> **💡 Confidentialité :** Les protocoles comme **TLS** chiffrent les données pour empêcher la surveillance et l'interception.

---

## 🏠 9. Localhost et Boucle Locale

### 🔄 127.0.0.1 - Plus qu'une Simple Adresse

```
┌────────────────────────────────────────────┐
│  localhost = 127.0.0.1                     │
│  Interface virtuelle pour se connecter     │
│  à sa propre machine                       │
└────────────────────────────────────────────┘
```

| Aspect | Détails |
|--------|---------|
| 📍 **Plage** | `127.0.0.0` à `127.255.255.255` |
| 🎯 **Usage** | Test d'applications réseau sans réseau physique |
| 🔒 **Isolation** | Trafic ne quitte jamais la machine |
| 📌 **Nom** | `localhost` (résolu par `/etc/hosts`) |

**Cas d'usage :**
- 🧪 Test de serveurs web locaux
- 🔧 Développement d'applications
- 🔍 Débogage de services réseau
- 🛡️ Services accessibles uniquement localement

---

## 🧪 10. Commandes Réseau Utiles

### 🔍 Diagnostic et Test

| Commande | Fonction | Exemple |
|----------|----------|---------|
| `ping` | 🏓 Teste la connectivité | `ping 8.8.8.8` |
| `traceroute` | 🗺️ Trace le chemin des paquets | `traceroute google.com` |
| `netstat` | 📊 Affiche les connexions réseau | `netstat -tunlp` |
| `ss` | 🔍 Socket statistics (remplace netstat) | `ss -tunlp` |
| `ifconfig` | 🔧 Configuration des interfaces | `ifconfig eth0` |
| `ip` | 🛠️ Configuration réseau moderne | `ip addr show` |
| `nslookup` | 📖 Requête DNS | `nslookup google.com` |
| `dig` | 🔬 Analyse DNS détaillée | `dig google.com` |
| `arp` | 🔍 Table ARP (IP → MAC) | `arp -a` |
| `route` | 🗺️ Table de routage | `route -n` |
| `curl` | 🌐 Requêtes HTTP | `curl https://api.example.com` |
| `wget` | ⬇️ Téléchargement de fichiers | `wget https://example.com/file.zip` |

### 📜 Script Bash : Afficher les Ports en Écoute

```bash
#!/usr/bin/env bash
# Script that displays listening ports with PID and program name

# Using netstat with options:
# -t : TCP ports
# -u : UDP ports
# -l : Only listening ports
# -n : Display numerical addresses
# -p : Show PID and program name
netstat -tunlp
```

**Explication des options :**
- `-t` : Ports TCP
- `-u` : Ports UDP
- `-n` : Affichage numérique
- `-l` : Seulement les ports en écoute
- `-p` : Affiche PID et nom du programme

### 🏓 Script Bash : Ping une Adresse IP

```bash
#!/usr/bin/env bash
# Script that pings an IP address 5 times

# Check if argument is provided
if [ $# -eq 0 ]; then
    echo "Usage: $0 {IP_ADDRESS}"
    exit 1
fi

# Ping the IP address 5 times
ping -c 5 "$1"
```

**Usage :**
```bash
./ping_script.sh 8.8.8.8
./ping_script.sh google.com
```

---

## 📚 11. Résumé Visuel - Architecture Réseau Complète

```
┌─────────────────────────────────────────────────────────────────┐
│                    🌐 Internet (WAN)                             │
│                           ▲                                      │
│                           │                                      │
│                   [🛡️ Firewall/Router]                          │
│                    NAT : 203.0.113.5                            │
│                           │                                      │
├───────────────────────────┼──────────────────────────────────────┤
│                   🏠 LAN (192.168.1.0/24)                       │
│                           │                                      │
│                    [🔀 Switch]                                   │
│                           │                                      │
│          ┌────────────────┼────────────────┐                    │
│          │                │                │                    │
│     [💻 PC1]         [📱 Phone]      [🖨️ Printer]              │
│   192.168.1.10     192.168.1.20    192.168.1.30               │
│   MAC: AA:BB:...   MAC: CC:DD:...  MAC: EE:FF:...             │
│                                                                  │
└──────────────────────────────────────────────────────────────────┘

Couches OSI appliquées :
┌──────────────────────────────────────────┐
│ 7 - Application  │ HTTP/HTTPS, DNS, SSH  │
│ 6 - Présentation │ TLS/SSL               │
│ 5 - Session      │ Établissement         │
│ 4 - Transport    │ TCP/UDP + Ports       │
│ 3 - Réseau       │ IP + Routage          │
│ 2 - Liaison      │ Ethernet + MAC        │
│ 1 - Physique     │ Câbles/Wi-Fi          │
└──────────────────────────────────────────┘
```

---

## 🎯 12. Cas Pratiques et Scénarios

### 🌐 Scénario 1 : Navigation Web

```
1️⃣ Utilisateur tape "google.com" dans le navigateur
        ↓
2️⃣ Requête DNS → Résolution → 142.250.185.46
        ↓
3️⃣ Connexion TCP (3-way handshake) sur port 443
        ↓
4️⃣ Requête HTTPS (HTTP + TLS)
        ↓
5️⃣ Réponse du serveur
        ↓
6️⃣ Affichage de la page
```

### 📧 Scénario 2 : Envoi d'un Email

```
1️⃣ Client email → SMTP (port 25/587)
        ↓
2️⃣ Serveur SMTP expéditeur
        ↓
3️⃣ DNS MX record lookup
        ↓
4️⃣ Serveur SMTP destinataire
        ↓
5️⃣ Stockage (IMAP/POP3)
        ↓
6️⃣ Réception par destinataire
```

### 🏓 Scénario 3 : Test de Connectivité

```bash
# 1. Tester la connectivité de base
ping 8.8.8.8

# 2. Tester la résolution DNS
ping google.com

# 3. Tracer le chemin
traceroute google.com

# 4. Vérifier les ports ouverts
netstat -tunlp

# 5. Tester un port spécifique
telnet google.com 80
```

---

## 💡 13. Bonnes Pratiques et Astuces

### ✅ Sécurité Réseau

| Pratique | Description | Emoji |
|----------|-------------|-------|
| **Firewall actif** | Toujours activer le pare-feu | 🛡️ |
| **Mots de passe forts** | Complexité + 12 caractères minimum | 🔐 |
| **Mises à jour** | Patcher régulièrement tous les systèmes | 🔄 |
| **Segmentation** | Séparer les réseaux critiques | ✂️ |
| **Chiffrement** | HTTPS, VPN, SSH obligatoires | 🔒 |
| **Monitoring** | Surveiller le trafic anormal | 👁️ |
| **Backup** | Sauvegardes régulières et testées | 💾 |

### 🚀 Performance Réseau

| Astuce | Bénéfice |
|--------|----------|
| **Câble > Wi-Fi** | Latence plus faible, débit stable |
| **Canaux Wi-Fi** | Éviter les interférences |
| **QoS** | Prioriser le trafic critique |
| **DNS rapides** | Cloudflare (1.1.1.1), Google (8.8.8.8) |
| **MTU optimal** | Éviter la fragmentation |

---

## 🔧 14. Dépannage Réseau (Troubleshooting)

### 🩺 Méthodologie de Diagnostic

```
┌─────────────────────────────────────────┐
│  1️⃣  Couche Physique                    │
│     ↓  Câbles branchés ? LED actives ?  │
│  2️⃣  Couche Liaison                     │
│     ↓  Adresse MAC valide ? Switch OK ? │
│  3️⃣  Couche Réseau                      │
│     ↓  Adresse IP ? Ping gateway ?      │
│  4️⃣  Couche Transport                   │
│     ↓  Ports ouverts ? Firewall OK ?    │
│  5️⃣  Couches supérieures                │
│     ↓  DNS ? Application configurée ?   │
└─────────────────────────────────────────┘
```

### 🛠️ Checklist de Dépannage

| Problème | Tests à Effectuer |
|----------|-------------------|
| **Pas de connexion** | • Vérifier câbles/Wi-Fi<br>• `ping 127.0.0.1` (localhost)<br>• `ping [gateway]`<br>• Vérifier IP : `ip addr` |
| **Lenteur réseau** | • `ping` pour latence<br>• `iperf` pour débit<br>• Vérifier utilisation : `iftop` |
| **Site inaccessible** | • `nslookup [site]` (DNS)<br>• `ping [IP du site]`<br>• `traceroute [site]`<br>• Vérifier firewall |
| **Service ne répond pas** | • `netstat -tunlp` (port écoute ?)<br>• `telnet localhost [port]`<br>• Vérifier logs service |

### 🔍 Commandes de Diagnostic Avancées

```bash
# Vérifier la configuration réseau
ip addr show
ip route show

# Tester la résolution DNS
dig google.com
nslookup google.com 8.8.8.8

# Analyser les paquets
tcpdump -i eth0
wireshark  # Interface graphique

# Tester la bande passante
iperf -s  # Serveur
iperf -c [IP]  # Client

# Surveiller le trafic en temps réel
iftop
nethogs
```

---

## 📖 15. Glossaire des Termes Réseau

| Terme | Définition | Emoji |
|-------|------------|-------|
| **Backbone** | Infrastructure principale d'un réseau | 🦴 |
| **Bandwidth** | Capacité de transmission (débit) | 📊 |
| **Broadcast** | Diffusion à tous les appareils du réseau | 📢 |
| **CIDR** | Classless Inter-Domain Routing | 📐 |
| **DMZ** | Zone démilitarisée entre LAN et Internet | 🛡️ |
| **Gateway** | Passerelle vers un autre réseau | 🚪 |
| **Hop** | Saut entre deux routeurs | 🦘 |
| **Latency** | Délai de transmission (ping) | ⏱️ |
| **MTU** | Maximum Transmission Unit | 📦 |
| **Packet Loss** | Perte de paquets | 📉 |
| **QoS** | Quality of Service - Priorisation | ⭐ |
| **RTT** | Round-Trip Time (aller-retour) | 🔄 |
| **Throughput** | Débit réel (vs théorique) | 🚀 |
| **VLAN** | Virtual LAN - Segmentation logique | 🔀 |

---

## 📚 16. Ressources Complémentaires

### 📖 Documentation et Standards

- 🌐 [RFC (Request for Comments) - IETF](https://www.ietf.org/rfc/)
- 📘 [TCP/IP Illustrated - Stevens](https://en.wikipedia.org/wiki/TCP/IP_Illustrated)
- 🎓 [Cisco Networking Academy](https://www.netacad.com/)

### 🛠️ Outils en Ligne

| Outil | Usage | Lien |
|-------|-------|------|
| **IPCalc** | Calculateur de sous-réseaux | 🔢 |
| **Speedtest** | Test de débit | ⚡ |
| **Ping.eu** | Outils de diagnostic | 🏓 |
| **Whois** | Information sur domaines | 🔍 |

### 📺 Visualisation

- 🗺️ [Submarine Cable Map](https://www.submarinecablemap.com/) - Câbles sous-marins
- 🌐 [Internet Map](https://internet-map.net/) - Visualisation d'Internet
- 📊 [BGP Looking Glass](https://www.bgplookingglass.com/) - Routage BGP

---

## 🎓 17. Exercices Pratiques

### 🧪 Exercice 1 : Configuration de Base

```bash
# 1. Vérifier votre adresse IP
ip addr show

# 2. Identifier votre passerelle par défaut
ip route show

# 3. Tester la connectivité locale
ping -c 4 [votre_gateway]

# 4. Tester la connectivité Internet
ping -c 4 8.8.8.8

# 5. Tester la résolution DNS
ping -c 4 google.com
```

### 🧪 Exercice 2 : Analyse de Ports

```bash
# Lister tous les ports en écoute
sudo netstat -tunlp

# Identifier le service sur port 80
sudo lsof -i :80

# Vérifier les connexions établies
ss -t state established
```

### 🧪 Exercice 3 : Calcul de Sous-réseau

**Question :** Combien d'hôtes dans 192.168.1.0/26 ?

**Réponse :**
- /26 = 26 bits réseau, 6 bits hôtes
- 2^6 = 64 adresses
- 64 - 2 (réseau + broadcast) = **62 hôtes utilisables**

**Plages :**
- 192.168.1.0 - 192.168.1.63 (première sous-réseau)
- 192.168.1.64 - 192.168.1.127 (deuxième sous-réseau)
- etc.

---

## 🚀 Conclusion

Félicitations ! 🎉 Vous avez maintenant une compréhension solide des **concepts fondamentaux des réseaux informatiques**.

### 📝 Points Clés à Retenir

✅ Les **7 couches OSI** organisent les fonctions réseau  
✅ **TCP** = fiable, **UDP** = rapide  
✅ **IPv4** (32 bits) vs **IPv6** (128 bits)  
✅ **Adresses privées** vs **publiques** + NAT  
✅ **Ports** identifient les services (0-65535)  
✅ **Sécurité** : Firewall, chiffrement, segmentation  
✅ **Diagnostic** : ping, traceroute, netstat  

### 🎯 Prochaines Étapes

1. **Pratiquer** les commandes réseau régulièrement
2. **Configurer** un réseau domestique complet
3. **Explorer** les protocoles de routage (OSPF, BGP)
4. **Approfondir** la sécurité réseau (VPN, IDS/IPS)
5. **Étudier** les architectures cloud (AWS, Azure)

---

**Bon apprentissage des réseaux ! 🌐🚀**