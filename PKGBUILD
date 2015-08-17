# Maintainer:  Gustavo Alvarez <sl1pkn07@gmail.com>

_plug=example_plugins
pkgname=vapoursynth-${_plug}-git
pkgver=20131221.94d8a3e
pkgrel=1
pkgdesc="Plugin for Vapoursynth: ${_plug} (GIT Version)"
arch=('i686' 'x86_64')
url="http://forum.doom9.org/showthread.php?t=166147"
license=('GPL')
depends=('vapoursynth')
provides=("vapoursynth-${_plug}")
conflicts=("vapoursynth-${_plug}" "vapoursynth-plugin-${_plug}")
source=("${_plug}::git+https://github.com/sekrit-twc/VSExamples.git"
        'Makefile')
md5sums=('SKIP'
         '574a3b873c04120734de7336b3c588fb')
_gitname="${_plug}"

pkgver() {
  cd "${_gitname}"
  echo "$(git log -1 --format="%cd" --date=short | tr -d '-').$(git log -1 --format="%h")"
}

prepare() {
  cd "${_gitname}"
  cp -R ../Makefile .
}

build() {
  cd "${_gitname}"
  make
}

package(){
  cd "${_gitname}"
  install -Dm755 vsmatrix.so "${pkgdir}/usr/lib/vapoursynth/vsmatrix.so"
  install -Dm755 vsrandom.so "${pkgdir}/usr/lib/vapoursynth/vsrand.so"
  install -Dm644 matrix_conversions.txt "${pkgdir}/usr/share/doc/vapoursynth/plugins/${pkgname}/matrix_conversions.txt"
}
