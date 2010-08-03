# Contributor: ragnarok2040 at gmail dot com
# ps2sdk-ports-zlib PKGBUILD


pkgname=ps2sdk-ports-zlib
pkgver=1.2.5
pkgrel=1
pkgdesc="Zlib for ps2sdk"
arch=('i686' 'x86_64')
license=('Custom')
url="http://www.ps2dev.org/"
depends=('ps2sdk-git')
makedepends=('cross-ps2-binutils>=2.14'
             'cross-ps2-ee-newlib>=1.10.0'
             'cross-ps2-ee-gcc'
             'cross-ps2-iop-gcc'
             'make' 'gcc' 'patch' 'subversion')
options=('!strip' '!libtool')
source=("http://zlib.net/zlib-$pkgver.tar.gz"
        Makefile)
md5sums=('c735eab2d659a96e5a594c9e8541ad63'
         'cdc97a4220773a2d3af9fe6978a793df')

build() {
  # Setup PKGBUILD ps2dev environment
  source /etc/profile.d/ps2dev.sh

  # Checkout or update source
  cd $srcdir

  msg "Cleaning up sources..."
  rm -rf $srcdir/zlib-build || return 1
  msg "Done."

  # Copy clean sources
  cd $srcdir
  cp -r zlib-$pkgver zlib-build
  cp Makefile zlib-build/

  # Start compiling
  cd zlib-build
  msg "Starting make..."
  make || return 1
  make DESTDIR=$pkgdir install || return 1

  # Install license for zlib
  install -m755 -D $srcdir/zlib-$pkgver/README $pkgdir/usr/share/licenses/$pkgname/README

}
