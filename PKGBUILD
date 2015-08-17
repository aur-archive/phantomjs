# Maintainer: grimsock <lord.grimsock at gmail dot com>
# Contributor: Dieter Plaetinck <dieter@plaetinck.be>
# Contributor: Vladimir Chizhov <jagoterr@gmail.com>
# Contributor: Henry Tang <henryykt@gmail.com>

pkgname=phantomjs
pkgver=1.9.1
pkgrel=1
pkgdesc="Headless WebKit with JavaScript API"
url="http://www.phantomjs.org/"
license=("BSD")
arch=('i686' 'x86_64')
depends=('gstreamer0.10-base')
makedepends=('unzip')
source=("http://phantomjs.googlecode.com/files/${pkgname}-${pkgver}-source.zip")
noextract=("${pkgname}-${pkgver}-source.zip")
md5sums=('93a0043d4ff8cd83e23e9d261c93830d')

build() {
  # workaround for https://code.google.com/p/libarchive/issues/detail?id=271
  # cd $srcdir/$pkgname-$pkgver
  unzip ${pkgname}-${pkgver}-source.zip
  cd $pkgname-$pkgver
  # workaround for http://code.google.com/p/phantomjs/issues/detail?id=635
  sed -i 's/QMAKE_LFLAGS+=-fuse-ld=gold/#QMAKE_LFLAGS+=-fuse-ld=gold/' src/qt/src/3rdparty/webkit/Source/common.pri
 ./build.sh
}

package() {
  mkdir -p "$pkgdir/usr/bin/"
  install -D -m755 "$srcdir/$pkgname-$pkgver/bin/phantomjs" "$pkgdir/usr/bin/"
}

