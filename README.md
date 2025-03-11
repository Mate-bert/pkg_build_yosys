# pkg_build_yosys

Ce fichier de Package fonctionne de paire avec le github customisé "Yosys_Ozixe"

yosys_ozixe est une version customisée de Yosys destinée à la synthèse RTL pour tous type de FPGA. Ce framework intègre un nouveau flux de synthèse – notamment via la commande synth_ozixe – qui convertit la logique en cellules LUT4, sans utiliser les primitives FPGA spécifiques (RAM, IO, etc.). Il intègre également la prise en charge d'ABC (ou ABC9) et du plugin GHDL pour une meilleure couverture de la chaîne RTL.

# Installation
Pour installer le package sur MSYS2/mingw-w64 :

## Clonez ce dépôt :

git clone https://github.com/Mate-bert/.git
cd yosys_ozixe

## Mettez à jour les sous-modules (le cas échéant) :

git submodule update --init --recursive

Utilisez le PKGBUILD fourni pour construire le package. Par exemple, depuis MSYS2 :

bash
Copier
makepkg -si
Cela téléchargera également les sources d'ABC et du plugin GHDL, compilera yosys_ozixe avec le flux custom, et installera le package dans votre environnement.
