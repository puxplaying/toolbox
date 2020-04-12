# Maintainer: puxplaying

pkgname=toolbox
pkgver=0.3
pkgrel=1
pkgdesc="Bash script providing a collection of terminal applications in a simple UI"
arch=(any)
url="https://github.com/puxplaying/$pkgname"
license=('GPL3')
depends=('pacui' 'pacman-contrib' 'expac' 'sudo' 'fzf' 'meld' 'ncdu' 'gawk' 'bash' 'links' 'sed' 'xorg-xinput' 'inxi' 'cpupower' 'ranger' 'curl' 'powertop' 'cmus' 'mhwd' 'lshw' 'lm_sensors' 'dmidecode')
makedepends=('git')
conflicts=("bmenu" "mhwd-tui")
optdepends=('cmatrix: Needed for ToolBox')
source=("$url/archive/$pkgver.tar.gz")
md5sums=('SKIP')

package () {
	cd "$srcdir/$pkgname-$pkgver"
	install -dm755 $pkgdir/usr/bin
	cp -r $srcdir/$pkgname-$pkgver/bin $pkgdir/usr
	chmod a+x $pkgdir/usr/bin/*
}
