# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.
 
# Maintainer: Victor Marzo <samsaga2@gmail.com>
pkgname=openmsx-debugger
pkgver=git
pkgrel=1
epoch=
pkgdesc="OpenMSX debugger"
arch=('i686' 'x86_64')
url="http://openmsx.sourceforge.net/"
license=('GPL')
groups=()
depends=('qt5-base')
makedepends=('git' 'python2')
checkdepends=()
optdepends=('openmsx')
provides=()
conflicts=()
replaces=()
backup=()
options=()
install=
changelog=
source=()
noextract=()
md5sums=()
_gitname="debugger"
_gitroot="git://git.code.sf.net/p/openmsx/debugger"
 
build() {
  cd "$srcdir"
  msg "Connecting to GIT server...."

  if [[ -d "$_gitname" ]]; then
    cd "$_gitname" && git pull origin
    msg "The local files are updated."
  else
    git clone "$_gitroot" "$_gitname"
  fi

  msg "GIT checkout done or server timeout"
  msg "Starting build..."

  rm -rf "$srcdir/$_gitname-build"
  git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
  cd "$srcdir/$_gitname-build"

  #
  # BUILD HERE
  #
  PATH=/usr/lib/qt5/bin:$PATH PYTHON=python2 make
}
 
package() {
  cd "$srcdir/$_gitname-build"
  install -Dm0755 "derived/bin/openmsx-debugger" "${pkgdir}/usr/bin/openmsx-debugger"
}
