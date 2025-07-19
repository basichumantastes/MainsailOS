# MainsailOS Custom - Ender 3 Pro Edition

Cette version personnalisée de MainsailOS est spécialement optimisée pour votre **Ender 3 Pro + BLTouch** sur **Raspberry Pi 3B+**.

## ✨ Caractéristiques de cette version

### 🔧 Configuration Pré-Calibrée
- **BLTouch** configuré avec z_offset: 4.115 (calibré)
- **Extrudeur** avec rotation_distance: 32.575 (calibré)
- **Bed mesh** 5x5 points pré-configuré
- **PID** extrudeur et lit calibrés

### 🎯 Macros Optimisées
- **START_PRINT** avec bed mesh automatique
- **END_PRINT** avec parking et arrêt différé des moteurs
- **PAUSE/RESUME/CANCEL** compatibles Mainsail
- **LOAD_FILAMENT / UNLOAD_FILAMENT** pour changement facile

### 📊 Configuration Matériel
- Board: **Creality 4.2.2** (STM32F103)
- Extrudeur: **Métal Creality**
- Tube Bowden: **Capricorn**
- Buse: **0.4mm laiton**
- Sonde: **BLTouch**

## 🚀 Installation

1. **Flashez l'image** sur votre carte SD (16GB minimum recommandé)
2. **Première connexion** : 
   - SSH: `ssh pi@mainsailos.local` (mot de passe: raspberry)
   - Interface web: `http://mainsailos.local`

3. **Vérifications post-installation** :
   ```bash
   # Vérifier la connexion à l'imprimante
   ls /dev/serial/by-id/
   
   # Si besoin, modifier le serial dans printer.cfg
   nano ~/printer_data/config/printer.cfg
   ```

## ⚙️ Configuration Réseau

### WiFi
Éditez le fichier sur la partition boot de la SD :
```
mainsailos-wpa-supplicant.txt
```

### Ethernet
Connexion automatique par DHCP.

## 🔧 Première Utilisation

1. **Connexion à l'imprimante** - Vérifiez le port série
2. **Home All** - Test des axes
3. **Bed Mesh Calibrate** - Si besoin de recalibrer
4. **PID Tuning** - Si changement de buse/hotend

## 📁 Structure des Fichiers

```
~/printer_data/
├── config/
│   ├── printer.cfg          # Configuration principale calibrée
│   ├── moonraker.conf       # Configuration Moonraker
│   └── printer.cfg.backup   # Sauvegarde
├── gcodes/                  # Fichiers G-code
└── logs/                    # Logs système
```

## 🛠️ Commandes Utiles

```bash
# Redémarrer Klipper
sudo systemctl restart klipper

# Redémarrer Moonraker  
sudo systemctl restart moonraker

# Voir les logs Klipper
tail -f ~/printer_data/logs/klippy.log

# Mise à jour
~/moonraker-env/bin/python ~/moonraker/scripts/update-manager.py
```

## 🎨 Interface Web

Accès via : **http://mainsailos.local** ou **http://[adresse-ip]**

### Fonctionnalités Pré-configurées :
- 📊 Dashboard avec température/vitesse
- 🎥 Webcam (si connectée)
- 📂 Gestionnaire de fichiers G-code
- ⚙️ Configuration en temps réel
- 📈 Graphiques de température
- 🔄 Mise à jour automatique

## 🚨 Résolution de Problèmes

### Problème de connexion série
```bash
# Lister les ports disponibles
ls /dev/ttyUSB* /dev/ttyACM*

# Modifier printer.cfg si nécessaire
# Remplacer la ligne serial: par le bon port
```

### BLTouch ne fonctionne pas
```bash
# Tester le BLTouch
BLTOUCH_DEBUG COMMAND=pin_down
BLTOUCH_DEBUG COMMAND=pin_up
```

### Problème de calibration
```bash
# Re-calibrer le z_offset
PROBE_CALIBRATE
# Puis sauvegarder avec SAVE_CONFIG
```

## 📞 Support

- **Mainsail Discord** : https://discord.gg/mainsail  
- **Documentation** : https://docs-os.mainsail.xyz
- **Klipper Docs** : https://www.klipper3d.org

---

## 🔄 Changelog Personnalisations

### Version Custom v1.0
- ✅ Configuration Ender 3 Pro calibrée
- ✅ Macros optimisées Mainsail
- ✅ BLTouch pré-configuré
- ✅ Bed mesh par défaut
- ✅ Fichier test inclus

---

*Configuration réalisée pour Ender 3 Pro + BLTouch + Raspberry Pi 3B+*  
*Basé sur MainsailOS officiel - Version personnalisée*
