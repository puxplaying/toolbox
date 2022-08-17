# Maintainer: Chrysostomus @forum.manjaro.org
# Maintainer: Georg Wagner <puxplaying_at_gmail_dot_com>
# Maintainer: Mark Wagie <mark_at_manjaro_dot_org>

pkgname=bmenu
pkgver=0.19
pkgrel=1
pkgdesc="Bash scripts providing a collection of terminal applications in a simple UI"
arch=('any')
url="https://github.com/puxplaying/toolbox/"
license=('GPL3')
depends=('pacui' 'pacman-contrib' 'expac' 'sudo' 'fzf' 'ncdu' 'gawk' 'bash' 'sed'
         'xorg-xinput' 'inxi' 'cpupower' 'ranger' 'curl' 'powertop' 'cmus' 'mhwd'
         'lshw' 'lm_sensors' 'dmidecode')
optdepends=('cmatrix: Needed for ToolBox'
            'meld: Needed for diff operations')
provides=('mhwd-tui')
conflicts=('mhwd-tui')
source=("$pkgname-$pkgver.tar.gz::$url/archive/$pkgver.tar.gz")
sha256sums=('8b4790377ce8af14ecb9e6e3935628ff67ec6e22aacc5c511b3431fa35b83638')

prepare() {
  cd "toolbox-$pkgver"

  # toolbox script conflicts with Arch community toolbox package
  mv -f bin/toolbox "bin/$pkgname"
  sed -i "s/Exec=toolbox/Exec=$pkgname/g" toolbox.desktop
}

package () {
  cd "toolbox-$pkgver"
  install -d "$pkgdir/usr/bin/"
  cp -r bin/* "$pkgdir/usr/bin/"
  chmod a+x $pkgdir/usr/bin/*

  install -Dm644 toolbox.desktop -t "$pkgdir/usr/share/applications/"
  install -Dm644 toolbox.png -t "$pkgdir/usr/share/pixmaps/"
}
