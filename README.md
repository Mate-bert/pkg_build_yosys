# pkg_build_yosys

Ce fichier de Package fonctionne de paire avec le github customisé "Yosys_Ozixe"

yosys_ozixe est une version customisée de Yosys destinée à la synthèse RTL pour tous type de FPGA. Ce framework intègre un nouveau flux de synthèse – notamment via la commande synth_ozixe – qui convertit la logique en cellules LUT4, sans utiliser les primitives FPGA spécifiques (RAM, IO, etc.).

# Installation
Pour installer le package sur MSYS2/mingw-w64 :

## Clonez ce dépôt :

git clone https://github.com/Mate-bert/pkg_build_yosys.git

## Utilisez le PKGBUILD fourni pour construire le package. Par exemple, depuis MSYS2 :

makepkg -fsi

