# Maintainer: not_anonymous <nmlibertarian@gmail.com>
# Contributor: Bob Finch <w9ya@qrparci.net>

pkgname=tlf-git
_pkgname=tlf
_author=Tlf
pkgver=1.4.1.r343.g678adbcd
#.r1.g3535aa1
pkgrel=1
pkgdesc="Ham Radio networked logging and contest program - CLI"
arch=('i686' 'x86_64')
url="https://tlf.github.io/"
license=('GPL')
depends=('hamlib' 'xmlrpc-c' 'hamradio-menus')
makedepends=('autoconf' 'automake' 'pkg-config')
optdepends=('cwdaemon: transmitting cw'
	    'winkeydaemon: transmitting cw'
	    'cty: country files'
	    'joe: editing qsos'
	    'xplanet: mapped qso display'
	    'sox: audio signal handling'
	    'fldigi: digital modes/modem & gui/display')
provides=('tlf')
conflicts=('tlf')
source=("$_pkgname::git+https://github.com/$_author/$_pkgname.git#branch=master")

pkgver() {
	cd $_pkgname
	git describe --long --tags | sed 's/^tlf-//;s/\([^-]*-g\)/r\1/;s/-/./g'
}

build() {
	cd $srcdir/$_pkgname

	autoreconf --install

	CFLAGS=-Wno-error ./configure --prefix=/usr --enable-hamlib\
	 --enable-fldigi-xmlrpc --enable-python-plugin

	make || return 1
}

package() {
	cd $srcdir/$_pkgname

	make prefix=$pkgdir/usr datadir=$pkgdir/usr/share install
}
md5sums=('SKIP')
sha256sums=('SKIP')
