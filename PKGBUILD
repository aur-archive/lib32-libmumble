# Maintainer: Matjaz Mozetic <rationalperseus@gmail.com>
# Contributor: Jan Alexander Steffens (heftig) <jan.steffens@gmail.com>
# Contributor: Sven-Hendrik Haase <sh@lutzhaase.com>
# Contributor: Lauri Niskanen <ape@ape3000.com>
# Contributor: Sebastian.Salich@gmx.de
# Contributor: Doc Angelo

pkgname=lib32-libmumble
pkgver=1.2.9
pkgrel=1
arch=(x86_64)
pkgdesc="A voice chat application similar to TeamSpeak (32-bit overlay library)"
license=(BSD)
depends=("mumble=$pkgver" lib32-libgl)
makedepends=(mesa gcc-multilib)
url="http://mumble.sourceforge.net/"
source=("http://downloads.sourceforge.net/mumble/mumble-$pkgver.tar.gz")
md5sums=('85decb9a1efb13e7558fab6265f81ad8')

build() {
  cd $srcdir/mumble-$pkgver/overlay_gl

  qmake-qt4 overlay_gl.pro QMAKE_CFLAGS+="-m32" QMAKE_LFLAGS+="-m32"
  make
}

package() {
  cd $srcdir/mumble-$pkgver

  # lib stuff
  install -m755 -D ./release/libmumble.so.$pkgver $pkgdir/usr/lib32/libmumble.so.$pkgver
  ln -s libmumble.so.$pkgver $pkgdir/usr/lib32/libmumble.so
  ln -s libmumble.so.$pkgver $pkgdir/usr/lib32/libmumble.so.1
  ln -s libmumble.so.$pkgver $pkgdir/usr/lib32/libmumble.so.1.2
  
  install -d $pkgdir/usr/share/licenses
  ln -s mumble $pkgdir/usr/share/licenses/$pkgname
}
# vim: sw=2:ts=2 et:
