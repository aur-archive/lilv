# Maintainer: SpepS <dreamspepser at yahoo dot it>

pkgname=lilv
pkgver=0.14.2
pkgrel=1
pkgdesc="A library to make the use of LV2 plugins as simple as possible for applications."
arch=(i686 x86_64)
url="http://drobilla.net/software/$pkgname/"
license=('custom:ISC')
depends=('python2' 'sratom>=0.2.0' 'jack')
makedepends=('swig')
optdepends=('bash-completion: auto-complete words')
source=("http://download.drobilla.net/$pkgname-$pkgver.tar.bz2")
md5sums=('1aea6761f3e44007c0fb4eb20630655d')

build() {
  cd "$srcdir/$pkgname-$pkgver"

  export PYTHON="/usr/bin/python2"

  # remove ldconfig
  sed -i "/ldconfig/d" wscript

  python2 ./waf configure --prefix=/usr \
                          --mandir=/usr/share/man \
                          --configdir=/etc \
                          --dyn-manifest \
                          --bindings
  python2 ./waf
}

package() {
  cd "$srcdir/$pkgname-$pkgver"

  DESTDIR="$pkgdir" python2 ./waf install

  # license
  install -Dm644 COPYING \
    "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}

# vim:set ts=2 sw=2 et:
