# Tablette

### Configuration tablette non-Wacom ArchLinux KDE

Résumé rapide de la doc [https://wiki.archlinux.org/title/Wacom\_tablet#Non-Wacom\_tablets ](https://wiki.archlinux.org/title/Wacom\_tablet#Non-Wacom\_tablets)[https://github.com/KDE/wacomtablet#installation](https://github.com/KDE/wacomtablet#installation)

Installation de pilotes et outils nécessaire

`yay -S digimend-kernel-drivers-dkms subutils kcm-wacomtablet`

Éxécuter la commande `lsusb` pour afficher les périphériques usb connectés. trouver la tablette dans la liste `Bus 007 Device 003: ID 172f:0034 Waltop International Corp. Slim Tablet 12.1"`

Modifier ou créer le fichier 50-tablet.conf&#x20;

`nano /etc/X11/xorg.conf.d/50-tablet.conf`

Ajouter dans ce fichier

```
Section "InputClass"
    Identifier "Tablet"
    Driver "wacom"
    MatchDevicePath "/dev/input/event*"
    MatchUSBID "172f:0034"
EndSection
```

Déco, reco la session pour être sûr que tout fonctionne bien

Exécuter la commande `xsetwacom --list devices` pour vérifier que la tablette est bien détecté. La réponse devrait afficher quelque chose comme&#x20;

`WALTOP International Corp. Slim Tablet stylus id: 12 type: STYLUS`&#x20;

Y'a plus qu'à configurer dans les configurations système de Plasma, périphériques > tablette graphiques, voilà voilà :)
