# Maintainer Haskellfant <moritz.kiefer@purelyfunctional.org
pkgname=zamplugins-git
pkgver=3.3.r15.g01120ff
pkgrel=1
pkgdesc="Collection of LV2/LADSPA/VST audio plugins for high quality processing"
arch=('i686' 'x86_64')
url="https://github.com/zamaudio/zam-plugins"
license=('MIT')
provides=('zamplugins')
depends=('fftw')
makedepends=('git' 'pkg-config' 'libx11' 'libgl' 'liblo' 'jack')
optdepends=()
source=("$pkgname"::'git://github.com/zamaudio/zam-plugins.git')
md5sums=('SKIP')

pkgver() {
  cd "$srcdir/$pkgname"
  git describe --long | sed -r 's/([^-]*-g)/r\1/;s/-/./g'
}

build() {
  cd "$srcdir/$pkgname"
  make
}

package() {
  cd $pkgname
  make DESTDIR="$pkgdir/" PREFIX=/usr install
  install -d "$pkgdir/usr/lib/vst"
  install -Dm755 "$srcdir/$pkgname/bin/"*vst.so "$pkgdir/usr/lib/vst"
}
