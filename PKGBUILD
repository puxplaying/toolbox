# Maintainer: Chrysostomus @forum.manjaro.org
# Maintainer: Georg Wagner <puxplaying_at_gmail_dot_com>
# Maintainer: Mark Wagie <mark_at_manjaro_dot_org>

pkgname=bmenu
pkgver=0.21
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
sha256sums=('570a8d0ac3cf141594f38facda469e19b63f0c72712d8d50922af93357d74185')

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
