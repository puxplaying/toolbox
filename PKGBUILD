# Maintainer: puxplaying

_pkgname=toolbox
pkgname=$_pkgname-git
pkgver=0.6
pkgrel=1
pkgdesc="Bash scripts providing a collection of terminal applications in a simple UI"
arch=(any)
url="https://github.com/puxplaying/$_pkgname"
license=('GPL3')
depends=('pacui' 'pacman-contrib' 'expac' 'sudo' 'fzf' 'meld' 'ncdu' 'gawk' 'bash' 'elinks' 'sed' 'xorg-xinput' 'inxi' 'cpupower' 'ranger' 'curl' 'powertop' 'cmus' 'mhwd' 'lshw' 'lm_sensors' 'dmidecode')
makedepends=('git')
conflicts=("bmenu" "mhwd-tui")
optdepends=('cmatrix: Needed for ToolBox')
source=("$url/archive/$pkgver.tar.gz")
md5sums=('SKIP')

package () {
	cd "$srcdir/$_pkgname-$pkgver"
	install -dm755 $pkgdir/usr/bin
	cp -r $srcdir/$_pkgname-$pkgver/bin $pkgdir/usr
	chmod a+x $pkgdir/usr/bin/*
}
