# Contributor: Jonas Heinrich <onny@project-insanity.org>
# Contributor: jtts
# Maintainer: Jonas Heinrich <onny@project-insanity.org>

pkgname=wine-mono
pkgver=0.0.8
pkgrel=8
pkgdesc="Wine addon providing Mono, inteded as a replacement for the .NET runtime and class libraries in Wine"
arch=('i686' 'x86_64')
url="https://github.com/madewokherd/wine-mono"
license=('custom')
depends=('wine')
makedepends=(mingw32-gcc mono bc)
options=(!buildflags)
source=("http://downloads.sourceforge.net/project/wine/Wine%20Mono/${pkgver}/${pkgname}-${pkgver}.tar.gz"
	'printf.diff'
	'2nd-printf-fix.diff'
	'http://gist.github.com/raw/4513866/aa52b87e59e02485ebb1a3d6e07ee2f2bb88cf0e/wnie-mono-automake-1.13.diff')
sha512sums=('82467baff691ba65f372a3695ab95290293a6c90c2d75254f305424a53e2b8349768ec103ff9a4611aecd5dd8237d0e5d64b825019f0abe37ab800702fc10e5c'
	    '92162b3ce5fabff836b8a8de527ab87dbbf8c1c01e12e4eb394d948ac0799548b8704337a20bee92c4c1d658788a2026882868e83dda65d1df3ec0cd6c5601f1'
            'c439d8afe1fc55b7ef902a550e33635554cd062777ab6b964da734faaf950538057561e736ccbe95cf8611b16d5708998af2ea259f3a2fd97d1fcc7b172bfbdc'
	    '9f241d4668d1373742ee663ea6abade808468218fc0e7c23a1f72ad8371b1ea1a9dca3da6090ad47729a34ced44eb0d66d7b03cc7360362c34665f0df70fbce6')

build() {
  cd "$srcdir/${pkgname}-${pkgver}"
  patch -p1 < ../printf.diff
  patch -p1 < ../2nd-printf-fix.diff
  patch -p1 < ../wnie-mono-automake-1.13.diff
  source build-winemono.sh -m i486-mingw32 -M i486-mingw32
}

package () {
  cd "$srcdir/${pkgname}-${pkgver}"
  install -Dm644 COPYING ${pkgdir}/usr/share/licenses/wine-mono/LICENSE
  install -Dm664 winemono.msi "$pkgdir/usr/share/wine/mono/${pkgname}-${pkgver}.msi"
}
