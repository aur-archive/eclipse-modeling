# $Id$
# Maintainer: David Roheim <david dot roheim at gmail dot com>

[ $CARCH = "x86_64" ] && _arch=-x86_64
_eclipse_name=luna
_eclipse_release=SR1
_eclipse_timestamp=20140606-1215

pkgname=eclipse-modeling
pkgver=4.4.1
pkgrel=1
pkgdesc="Eclipse Modeling Tools"
arch=('i686' 'x86_64')
url="http://www.eclipse.org"
license=('EPL')
depends=('java-environment>=6' 'gtk2' 'xulrunner' 'webkitgtk2')
provides=('eclipse')
conflicts=('eclipse' 'eclipse-jee' 'eclipse-cpp' 'eclipse-java' 'eclipse-rcp' 'eclipse-testing')
options=(!strip)
install=${pkgname}.install
source=("http://www.eclipse.org/downloads/download.php?r=1&file=/technology/epp/downloads/release/${_eclipse_name}/${_eclipse_release}/${pkgname}-${_eclipse_name}-${_eclipse_release}-linux-gtk${_arch}.tar.gz"
        "eclipse.sh"
        "eclipse.desktop"
        "eclipse.ini.patch"
        "eclipse.svg"
)

changelog=${pkgname}.changelog

sha256sums=('ef3f82488c756689bdb4cacf86e1d61f18d8ba27c29173072dbce6481ee9b69b'
            '4cca2873697a3af39a96449021d7fdc2fc2b01abc9f7883946081f6be7a5ed48'
            '4eb2189c96fcfa340886b049b34dc3636d7b2bfa865140dc72edb61455d900c3'
            '4a86578ebbe8adddf731b6bef31c05277ea792cb22d733b6a5c0a25f65546caf'
            '6fe3ab198af244f9c8c2463b6837855506e811f61e5fd8ac7c9d5fe348830a14')

[ "$CARCH" = "i686" ] && sha256sums[0]='017d6fed3451e6746a625c811191763f8b67766ded1321c6936c366ad1ea9a63'

build() {
	cd $srcdir

	patch -p1 < eclipse.ini.patch
}

package() {
	local _icon_path=/usr/share/eclipse/plugins/org.eclipse.platform_${pkgver}.v${_eclipse_timestamp}

	install -m755 -d $pkgdir/usr/{bin,share/applications}
	install -m755 -d $pkgdir/usr/share/icons/hicolor/{16x16,32x32,48x48,256x256,scalable}/apps

	cd $srcdir

	mv eclipse $pkgdir/usr/share
	install -D -m 755 eclipse.sh $pkgdir/usr/bin/eclipse
	install -D -m 644 eclipse.desktop $pkgdir/usr/share/applications
	install -D -m 644 eclipse.svg $pkgdir/usr/share/icons/hicolor/scalable/apps/eclipse.svg
	ln -s ${_icon_path}/eclipse16.png ${pkgdir}/usr/share/icons/hicolor/16x16/apps/eclipse.png
	ln -s ${_icon_path}/eclipse32.png ${pkgdir}/usr/share/icons/hicolor/32x32/apps/eclipse.png
	ln -s ${_icon_path}/eclipse48.png ${pkgdir}/usr/share/icons/hicolor/48x48/apps/eclipse.png
	ln -s ${_icon_path}/eclipse256.png ${pkgdir}/usr/share/icons/hicolor/256x256/apps/eclipse.png
}
