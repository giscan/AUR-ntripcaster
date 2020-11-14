# Maintainer: Sylvain Poulain <sylvain.poulain@giscan.com>

pkgname=ntripcaster
pkgver=0.1.5
pkgrel=1
pkgdesc='IGS Ntrip (Networked Transport of RTCM via Internet Protocol) Caster'
arch=('i686' 'x86_64')
url='https://github.com/giscan/ntripcaster/'
license=('GPL')

source=($pkgname-$pkgver.tar.gz::"https://github.com/giscan/ntripcaster/archive/$pkgver.tar.gz"
        $pkgname.service)
md5sums=('5fe6c0fb9f875e5be4a3f8e112d6ba2e'
        '82d37d17d27fd54f6b25cc204a0eb9cf')


build() {
  cd $pkgname-$pkgver

  ./configure --prefix=/opt/ntripcaster
  make

}

package() {
  cd $pkgname-$pkgver
  make DESTDIR="${pkgdir}" install
  
  echo "#!/bin/bash
  cd /opt/ntripcaster/logs
  ../bin/ntripcaster" > $srcdir/$pkgname
  install -Dm755 $srcdir/$pkgname $pkgdir/usr/bin/$pkgname

  install -Dm644 $srcdir/$pkgname.service $pkgdir/usr/lib/systemd/system/$pkgname.service

}
