# Maintainer: Me 
pkgname="connect-iq"
pkgver=2.4.2
pkgrel=1
epoch=
pkgdesc="Connect IQ SDK"
arch=('i686' 'x86_64')
url="https://developer.garmin.com/connect-iq/sdk/"
license=('Connect IQ License Agreement')
groups=()
depends=('wine' 'java-runtime')
makedepends=()
checkdepends=()
optdepends=()
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=("https://developer.garmin.com/downloads/connect-iq/sdks/connectiq-sdk-win-$pkgver.zip")
noextract=("connectiq-sdk-win-$pkgver.zip")
md5sums=("a5144b79506bbd78fa45451458d40594")
validpgpkeys=()
prepare() {
	echo 'prepare'
	mkdir -p $srcdir/opt/$pkgname
	unzip connectiq-sdk-win-$pkgver.zip  -d $srcdir/opt/$pkgname/
}
build() {
	echo 'build'
	cd $srcdir/opt/$pkgname/bin
	echo -e '#!/bin/bash\n\nwine $(dirname "$0")/shell.exe "$@"' > shell
	echo -e '#!/bin/bash\n\nwine $(dirname "$0")/simulator.exe "$@"' > simulator
	chmod a+x monkeyc monkeydo monkeygraph connectiq connectiqpkg simulator shell
	sed -i 's/\r//g' monkeygraph monkeyc monkeydo connectiq connectiqpkg simulator shell

}

check() {
	echo 'check'
}

package() {
	echo 'package'
	cp -r $srcdir/opt $pkgdir/
}
