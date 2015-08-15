# Maintainer: speps <speps at aur dot archlinux dot org>

pkgname=dataquay
pkgver=0.9
pkgrel=2
pkgdesc="A library that provides a friendly C++ interface to an RDF datastore using Qt4 classes and containers."
arch=(i686 x86_64)
url="http://breakfastquay.com/dataquay/"
license=('custom:BSD')
depends=('qt4')
makedepends=('redland')
source=("http://code.breakfastquay.com/attachments/download/30/$pkgname-$pkgver.tar.bz2")
md5sums=('e0015bd5c7f7ed23b8cc924abc656849')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  # disable tests (needs running X server)
  sed -i "s/ \?sub_tests.*//" $pkgname.pro

  qmake-qt4 PREFIX=/usr $pkgname.pro
  make
}

package() {
  cd "$srcdir/$pkgname-$pkgver"
  make INSTALL_ROOT="$pkgdir/" install

  # missing pkgconfig file
  install -Dm644 deploy/$pkgname.pc \
    "$pkgdir/usr/lib/pkgconfig"

  # license
  install -Dm644 COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
