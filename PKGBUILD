# Maintainer: Michael Kogan <michael dot kogan at gmx dot net>
# Contributor: Jan de Groot <jgc@archlinux.org>

pkgname=libgnomecanvas
pkgver=2.30.3
pkgrel=4
pkgdesc="The GNOME Canvas library"
arch=('x86_64' 'arm' 'armv6h' 'armv7h' 'aarch64')
license=('LGPL')
depends=('libglade' 'libart-lgpl')
makedepends=('pkg-config' 'intltool' 'python')
url="http://www.gnome.org"
source=(https://download.gnome.org/sources/${pkgname}/2.30/${pkgname}-${pkgver}.tar.bz2
		config.guess
        config.sub)
sha256sums=('859b78e08489fce4d5c15c676fec1cd79782f115f516e8ad8bed6abcb8dedd40'
			'7d1e3c79b86de601c3a0457855ab854dffd15163f53c91edac54a7be2e9c931b'
			'0c6489c65150773a2a94eebaa794b079e74a403b50b48d5adb69fc6cd14f4810')

prepare() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  cp -vf ${srcdir}/config.guess	${srcdir}/${pkgname}-${pkgver}/
  cp -vf ${srcdir}/config.sub	${srcdir}/${pkgname}-${pkgver}/
}

build() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  ./configure --prefix=/usr --disable-static \
      --enable-glade

  sed -i -e 's/ -shared / -Wl,-O1,--as-needed\0/g' libtool

  make
}

package() {
  cd "${srcdir}/${pkgname}-${pkgver}"
  make DESTDIR="${pkgdir}" install
}
