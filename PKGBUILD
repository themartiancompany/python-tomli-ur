# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_py="python"
_pyver="$( \
  "${_py}" \
    -V | \
    awk \
      '{print $2}')"
_pymajver="${_pyver%.*}"
_pyminver="${_pymajver#*.}"
_pynextver="${_pymajver%.*}.$(( \
  ${_pyminver} + 1))"
_pkg=tomli
pkgname="python-${_pkg}"
pkgver=2.0.1
pkgrel=3
pkgdesc="A lil' TOML parser"
url="https://github.com/hukkin/tomli"
license=(
  'MIT'
)
arch=(
  'any'
)
depends=(
  "${_py}>="${_pymajver}"
  "${_py}<"${_pynextver}"
)
makedepends=(
  "${_py}-build"
  "${_py}-installer"
  "${_py}-flit-core"
)
_http="https://github.com"
_ns="hukkin"
_url="${_http}/${_ns}/${_pkg}"
source=(
  "${_url}/archive/$pkgver/$pkgname-$pkgver.tar.gz"
)
sha512sums=(
  'a467f8d48cdbd7213bd9b6f85fd48ba142ab7c9656c40bb30785e1c4b37a9e29eaed420f183458ad20112baee8413ebbec87755332795c8f02235d1018c3aa5c'
)

build() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      build \
    -wn \
    --skip-dependency-check
}

check() {
  cd \
    "${_pkg}-${pkgver}"
  PYTHONPATH="$PWD"/src \
  "${_py}" \
    -m \
      unittest
}

package() {
  cd \
    "${_pkg}-${pkgver}"
  "${_py}" \
    -m \
      installer \
    --destdir="${pkgdir}" \
    dist/*.whl
  install \
    -Dm644 \
    LICENSE \
    -t \
      "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim:set sw=2 sts=-1 et:
