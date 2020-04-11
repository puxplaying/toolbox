# Maintainer: puxplaying

pkgname=toolbox
pkgver=0.2
pkgrel=1
pkgdesc="Bash script providing a collection of terminal applications in a simple UI"
arch=(any)
url="https://github.com/puxplaying/$pkgname"
license=('GPL3')
depends=('pacui' 'pacman-contrib' 'expac' 'sudo' 'fzf' 'meld' 'ncdu' 'gawk' 'bash' 'pacui' 'links' 'sed' 'mhwd-tui' 'xorg-xinput' 'inxi' 'cpupower' 'ranger' 'curl' 'powertop')
makedepends=('git')
conflicts=("bmenu")
optdepends=('cmatrix: Needed for ToolBox')
source=("$url/archive/$pkgver.tar.gz")
md5sums=('SKIP')

package () {
	cd "$srcdir"
	install -dm755 $pkgdir/usr/bin
	cp -r $srcdir/$pkgname/bin $pkgdir/usr
	chmod a+x $pkgdir/usr/bin/*
}
