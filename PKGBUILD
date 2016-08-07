# Maintainer: Denis Kasak <dkasak AT termina DOT org DOT uk>

pkgname=termite-dkasak-git
pkgver=20170709
pkgrel=1
pkgdesc="A simple VTE-based terminal"
arch=('i686' 'x86_64')
url="https://github.com/dkasak/termite/"
license=('LGPL')
depends=('vte3-ng')
makedepends=('git')
provides=('termite')
conflicts=('termite' 'termite-git')
backup=('etc/xdg/termite/config')
source=("termite-src::git://github.com/dkasak/termite#branch=custom")
md5sums=(SKIP)

pkgver() {
  cd termite-src
  git log -1 --format="%cd" --date=short | sed 's/-//g'
}

build() {
  cd "$srcdir/termite-src"
  git submodule update --init
  make
}

package() {
  cd "$srcdir/termite-src"
  make PREFIX=/usr DESTDIR="$pkgdir" install
  rm -rf "$pkgdir/usr/share/terminfo"
  install -Dm644 config "$pkgdir/etc/xdg/termite/config"
}

