# Contributor: Tomas Meszaros <exo [at] tty [dot] sk>
# Maintainer:  Tomas Meszaros <exo [at] tty [dot] sk>

pkgname=spdf-git
pkgver=1.1
pkgrel=6
pkgdesc="spdf is a simple program which can split pdf file into two"
arch=('i686' 'x86_64')
url="http://github.com/examon/spdf"
license=('GPL')
depends=('python2' 'python2-pypdf')
makedepends=('git')
provides=('spdf')
conflicts=('spdf')

_gitroot="git://github.com/examon/spdf.git"
_gitname="spdf"

build() {
  cd ${srcdir}

  msg "Connecting to GIT server..."
  if [[ -d ${_gitname} ]]; then
    (cd ${_gitname} && git pull origin)
  else
    git clone ${_gitroot} ${_gitname}
  fi
  msg "GIT checkout done or server timeout"
  msg "Starting make..."
}

package() {
  cd ${srcdir}/${_gitname}

  mv spdf.py spdf

  # install it
  mkdir -p "${pkgdir}/usr/bin"
  install -m755 spdf "${pkgdir}/usr/bin"
}
