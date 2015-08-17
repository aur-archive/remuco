# Contributor: Andrea Scarpino <andrea@archlinux.org>
# Contributor: Marcelo Cavalcante - kalib <kaliblsack@gmail.com>
# Contributor: Sebastian Wicki <gandro@gmx.net>
# Maintrainer: Robin K Joy <726f62696e@gmail.com>

pkgname=remuco
pkgver=0.9.6
pkgrel=4
pkgdesc="A duplex remote control system for Linux media players and mobile devices equipped with Bluetooth or WiFi"
arch=('any')
url="https://code.google.com/p/remuco/"
license=('GPL3')
depends=('pygobject' 'pyxdg' 'dbus-glib' 'dbus-python' 'python2-pybluez' 
'python2-imaging')
optdepends=('python-mpd: needed for the remuco-mpd adapter')
source=("http://remuco.googlecode.com/files/$pkgname-$pkgver.tar.gz")
sha1sums=('29af307133609b6756f13ea120a0032410b6fbbb')

build() {
  cd $srcdir/$pkgname-$pkgver

  sed -i 's|LIB_DIR = "lib64"|LIB_DIR = "lib"|' setup.py

  sed -i 's|python|python2|' base/scripts/remuco-report

  # fix shebangs
  cd adapter/
  sed -i 's|#!/usr/bin/python|#!/usr/bin/python2|' tvtime/remuco-tvtime \
    gmusicbrowser/remuco-gmusicbrowser \
    fooplay/remuco-fooplay \
    xmms2/remuco-xmms2 \
    mpd/remuco-mpd \
    amarok14/remuco-amarok14 \
    okular/remuco-okular \
    mplayer/remuco-mplayer \
    vlc/remuco-vlc \
    amarok/remuco-amarok \
    audacious/remuco-audacious \
    quodlibet/remuco-quodlibet \
    songbird/remuco-songbird
  sed -i 's|#!/usr/bin/env python|#!/usr/bin/env python2|' banshee/remuco-banshee
  cd ../

  sed -i 's|#!/usr/bin/python|#!/usr/bin/python2|' client/midp/design/themes/themes.py

  python2 setup.py build
}

package() {
  cd $srcdir/$pkgname-$pkgver

  python2 setup.py install --root=${pkgdir} --optimize=1
}
