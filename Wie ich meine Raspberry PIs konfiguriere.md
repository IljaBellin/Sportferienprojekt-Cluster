Wie ich meine Raspberry PIs konfiguriert habe
---
## Ubuntu Server installieren
Ich habe auf jede SD Karte der PIs Ubuntu Server mit dem [Raspberry PI Imager](https://www.raspberrypi.com/software/) gebrannt.

Zudem habe ich bei den erweiterten Einstellungen SSH mit der Passwort-Option ausgewählt.

Danach habe ich mich mit dem Befehl
`ssh <username>@<hostname>` per SSH mit den PIs verbunden.

##MicroK8s installieren

Auf jedem PI muss man das CMD line File ändern.
`sudo nano /boot/firmware/cmdline.txt`

Am Anfang der Zeile fügt man diese Parameter ein.
`cgroup_enable=memory cgroup_memory=1`

Danach führt man einen Reboot durch.
`sudo reboot`

Danach installiert man den MicroK8s snap.
`sudo snap install microk8s --classic`

Danach kann man Nodes mit
`sudo microk8s.add-node`
hinzufügen. Dabei kommt ein Befehl als Ausgabe den man beim PI mit dem man joinen will eingeben muss.

Mit `microk8s.kubectl get node` sieht man alle verbundenen PIs.

Mit `sudo microk8s.leave` kann man mit einem Node den Cluster wieder verlassen.
