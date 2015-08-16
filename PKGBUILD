# Maintainer: Jianing YANG <jianingy.yang at gmail dot com>

pkgname='iprange-git'
pkgver=20130427
pkgrel=1
pkgdesc="tools for expanding / compressing ip addresses"
url=('http://github.com/jianingy/iprange')
arch=('x86_64' 'i686')
license=('BSD')
depends=('pcre')
makedepends=('git' 'ocaml' 'ocaml-pcre')

_gitroot="https://github.com/jianingy/iprange.git"
_gitname="iprange"

build() {
  
  cd "$srcdir"

  # Fetch last git revision
  msg "Connecting to GIT server...."
  if [ -d $_gitname ] ; then
    cd $_gitname && git pull origin
    msg "The local files are updated."
  else
    git clone --depth=1 $_gitroot $_gitname
  fi
  msg "GIT checkout done or server timeout"
  
  msg ""
}

build() {
  cd "$srcdir/$_gitname/source" || return 1
  make || return 1
}

package() {
  cd "$srcdir/$_gitname/source" || return 1
  mkdir -p "$pkgdir/usr/bin" "$pkgdir/usr/share/man/man1" || return 1
  install -m755 ipcompress $pkgdir/usr/bin || return 1
  install -m755 ipexpand $pkgdir/usr/bin || return 1
  cp -a doc/ipcompress.man $pkgdir/usr/share/man/man1/ipcompress.1 || return 1
  cp doc/ipexpand.man $pkgdir/usr/share/man/man1/ipexpand.1 || return 1
}
