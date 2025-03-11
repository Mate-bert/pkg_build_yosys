
_realname=yosys_ozixe
pkgbase=mingw-w64-${_realname}
pkgname="pkg_ozixe"
pkgver=0.38
pkgrel=1
pkgdesc="A framework for RTL synthesis tools with ozixe synthesis added (mingw-w64)"
arch=('any')
mingw_arch=('mingw64' 'ucrt64')
url="https://yosyshq.net/yosys"
msys2_repository_url="https://github.com/Mate-bert/yosys_ozixe"
msys2_references=(
  'archlinux: yosys'
)
license=('spdx:ISC')
groups=("${MINGW_PACKAGE_PREFIX}-eda")
depends=(
  "${MINGW_PACKAGE_PREFIX}-gcc-libs"
  "${MINGW_PACKAGE_PREFIX}-ghdl"
  "${MINGW_PACKAGE_PREFIX}-libwinpthread-git"
  "${MINGW_PACKAGE_PREFIX}-python"
  "${MINGW_PACKAGE_PREFIX}-readline"
  "${MINGW_PACKAGE_PREFIX}-tcl"
  "${MINGW_PACKAGE_PREFIX}-zlib"
)
checkdepends=("${MINGW_PACKAGE_PREFIX}-iverilog")
makedepends=(
  "${MINGW_PACKAGE_PREFIX}-cc"
)
_ghdl_plugin_commit="0c4740a4f8f1e615cc587b3cd3849fa23a623862"

source=(
  "git+https://github.com/Mate-bert/yosys_ozixe.git#branch=main"
  "abc-${pkgver}.tar.gz::https://github.com/YosysHQ/yosys/releases/download/${_realname}-${pkgver}/abc.tar.gz"
  "https://github.com/ghdl/ghdl-yosys-plugin/archive/${_ghdl_plugin_commit}/ghdl-yosys-plugin-${_ghdl_plugin_commit}.tar.gz"
)


sha256sums=('SKIP'
            'a453ead5c6ee63a87588be63669bfc919cfe9a9b9b3a76d438fc11d90a6a9666'
            '1c05d579f0799f027ede97adbc1283ad325ef8019614f9a3bca194997535176a')

prepare() {
  cd "${srcdir}/yosys_ozixe"
  git submodule update --init --recursive
  cp -r "${srcdir}/ghdl-yosys-plugin-${_ghdl_plugin_commit}/src" frontends/ghdl
  cp -r "${srcdir}/YosysHQ-abc-896e5e7" abc
}



build() {
  [[ -d build-${MSYSTEM} ]] && rm -rf build-${MSYSTEM}
  cp -r "${srcdir}/yosys_ozixe" "build-${MSYSTEM}" && cd "build-${MSYSTEM}"
  make config-msys2-64

  make \
    PRETTY=0 \
    ENABLE_GHDL=1 \
    GHDL_PREFIX=${MINGW_PREFIX}
}

check() {
  cd build-${MSYSTEM}
  make test || true
}

package() {
  cd build-${MSYSTEM}
  make DESTDIR="${pkgdir}" install

  # Ajuste le chemin vers le fichier COPYING en fonction du nom du dossier extrait
  install -Dm644 "${srcdir}/yosys_ozixe/COPYING" "${pkgdir}${MINGW_PREFIX}/share/licenses/yosys_ozixe/LICENSE"
}
