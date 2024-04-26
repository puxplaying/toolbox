# Maintainer: Georg Wagner <puxplaying_at_gmail_dot_com>
# Maintainer: Mark Wagie <mark_at_manjaro_dot_org>
# Contributor: Chrysostomus <forum.manjaro.org/u/Chrysostomus>
# Contributor: konung-yaropolk <https://github.com/konung-yaropolk>

pkgname=bmenu
pkgver=0.24
pkgrel=2
pkgdesc="Bash scripts providing a collection of terminal applications in a simple UI"
arch=('any')
url="https://github.com/puxplaying/toolbox/"
license=('GPL-3.0-or-later')
depends=(
  'bash'
  'btop'
  'cmus'
  'cpupower'
  'curl'
  'dmidecode'
  'expac'
  'fzf'
  'gawk'
  'inxi'
  'lm_sensors'
  'lshw'
  'mhwd'
  'ncdu'
  'pacman-contrib'
  'pacui'
  'powertop'
  'sed'
  'sudo'
  'xorg-xinput'
)
optdepends=(
  'cmatrix: Enter The Matrix'
  'cups: Manage printers'
  'sane: Manage scanners'
  'meld: Diff operations'
  'ranger: File manager operations'
)
provides=('mhwd-tui')
conflicts=('mhwd-tui')
source=("$pkgname-$pkgver.tar.gz::$url/archive/$pkgver.tar.gz")
sha256sums=('dc1c5f0c3ae556e9a47ff26cafad952af43da8c52a362371db8df60bb760cc53')

prepare() {
  cd "toolbox-$pkgver"

  # toolbox script conflicts with Arch extra toolbox package
  mv -f bin/toolbox "bin/$pkgname"
  sed -i "s/Exec=toolbox/Exec=$pkgname/g" toolbox.desktop
}

package () {
  cd "toolbox-$pkgver"
  install -Dm755 bin/* -t "$pkgdir/usr/bin/"
  install -Dm644 toolbox.desktop -t "$pkgdir/usr/share/applications/"
  install -Dm644 toolbox.png -t "$pkgdir/usr/share/pixmaps/"
}
