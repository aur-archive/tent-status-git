# Maintainer: Jacob Cook <jacob at jcook dot cc>
_name=tent-status
pkgname=$_name-git
pkgver=20130309
pkgrel=1
pkgdesc="A simple Twitter-like client for a Tent protocol server"
arch=('any')
url="https://github.com/tent/tent-status"
license=('MIT')
groups=()
depends=('pacman' 'ruby' 'postgresql' 'postgresql-libs' 'v8' 'nodejs' 'make' 'libxml2' 'libxslt' 'ruby-bundler')
makedepends=('git')
provides=('tent-status')
conflicts=()
backup=()
options=()
install=
source=('ARCHREADME')
noextract=()
md5sums=(61f16c9e065677f2e020131e8a00269b)
install=tent-status-git.install

_gitroot='git://github.com/tent/tent-status.git'
_gitname=$_name

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
}

package() {
  install -d $pkgdir/var/lib/$_gitname
  install -D -m644 $srcdir/$_gitname/LICENSE.txt "${pkgdir}/usr/share/licenses/${_gitname}-git/LICENSE"
  cp $srcdir/ARCHREADME $pkgdir/var/lib/$_gitname/
  cp -a $srcdir/$_gitname $pkgdir/var/lib/
}

# vim:set ts=2 sw=2 et:
