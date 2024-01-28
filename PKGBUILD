# SPDX-License-Identifier: AGPL-3.0
#
# Maintainer: Felix Yan <felixonmars@archlinux.org>
# Maintainer: Truocolo <truocolo@aol.com>
# Maintainer: Pellegrino Prevete (tallero) <pellegrinoprevete@gmail.com>

_pkg="tomli"
pkgname="python-${_pkg}"
pkgver=2.0.1
pkgrel=3
pkgdesc="A lil' TOML parser"
url="https://github.com/hukkin/tomli"
license=('MIT')
arch=('any')
depends=('python')
makedepends=('python-build' 'python-installer' 'python-flit-core')
source=("https://github.com/hukkin/tomli/archive/$pkgver/$pkgname-$pkgver.tar.gz")
sha512sums=('a467f8d48cdbd7213bd9b6f85fd48ba142ab7c9656c40bb30785e1c4b37a9e29eaed420f183458ad20112baee8413ebbec87755332795c8f02235d1018c3aa5c')

build() {
  cd tomli-$pkgver
  python -m build -wn --skip-dependency-check
}

check() {
  cd tomli-$pkgver
  PYTHONPATH="$PWD"/src python -m unittest
}

package() {
  cd tomli-$pkgver
  python \
    -m \
      installer \
    --destdir="$pkgdir" \
    dist/*.whl

  install \
    -Dm644 \
    LICENSE \
    -t \
      "${pkgdir}/usr/share/licenses/${pkgname}"
}

# vim:set sw=2 sts=-1 et:
