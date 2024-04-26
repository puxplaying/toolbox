# Maintainer: Chrysostomus <forum.manjaro.org/u/Chrysostomus>
# Maintainer: Georg Wagner <puxplaying_at_gmail_dot_com>
# Maintainer: Mark Wagie <mark_at_manjaro_dot_org>
# Contributor: konung-yaropolk <https://github.com/konung-yaropolk>

pkgname=bmenu
pkgver=0.22
pkgrel=1
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
  'ranger'
  'sed'
  'sudo'
  'xorg-xinput'
)
optdepends=('cmatrix: Needed for ToolBox'
            'meld: Needed for diff operations')
provides=('mhwd-tui')
conflicts=('mhwd-tui')
source=("$pkgname-$pkgver.tar.gz::$url/archive/$pkgver.tar.gz")
sha256sums=('d4d16a09feec754041630c37795b71d9aa9239784815f2c86edc5422bbade8da')

prepare() {
  cd "toolbox-$pkgver"

  # toolbox script conflicts with Arch community toolbox package
  mv -f bin/toolbox "bin/$pkgname"
  sed -i "s/Exec=toolbox/Exec=$pkgname/g" toolbox.desktop
}

package () {
  cd "toolbox-$pkgver"
  install -Dm755 bin/* -t "$pkgdir/usr/bin/"
  install -Dm644 toolbox.desktop -t "$pkgdir/usr/share/applications/"
  install -Dm644 toolbox.png -t "$pkgdir/usr/share/pixmaps/"
}
