# Maintainer: Georg Wagner <puxplaying_at_gmail_dot_com>
# Maintainer: Mark Wagie <mark_at_manjaro_dot_org>
# Contributor: Chrysostomus <forum.manjaro.org/u/Chrysostomus>
# Contributor: konung-yaropolk <https://github.com/konung-yaropolk>

pkgname=bmenu
pkgver=0.25
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
  'dialog'
  'dmidecode'
  'expac'
  'fzf'
  'gawk'
  'inxi'
  'lm_sensors'
  'lshw'
  'ncdu'
  'pacman-contrib'
  'powertop'
  'sed'
  'sudo'
  'wget'
  'xorg-xinput'
)
optdepends=(
  'cmatrix: Enter The Matrix'
  'cups: Manage printers'
  'sane: Manage scanners'
  'meld: Diff operations'
  'mhwd: Manjaro Linux Hardware Detection'
  'pacui: Package Manager UI'
  'p7zip: Fast 7z file compression with password protection'
  'ranger: File manager operations'
  'tar: Fast Tar file compression'
  'zstd: Fast Zstd file comression'
)
source=("$pkgname-$pkgver.tar.gz::$url/archive/$pkgver.tar.gz")
sha256sums=('db97221ef6ec84ac30691a30cfde69742d076edd026adae85103a8a95dbc5fa4')

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
