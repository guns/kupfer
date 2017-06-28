# Maintainer: Sung Pae <self@sungpae.com>
# Contributor: D. Can Celasun <dcelasun[at]gmail[dot]com>
# Contributor: Alessio Sergi <asergi at archlinux dot us>
# Contributor: Asa Marco <marcoasa90[at]gmail[.]com>
pkgname=kupfer-nerv
pkgver=0
pkgrel=1
pkgdesc="Custom kupfer build"
arch=('x86_64')
url="https://github.com/guns/kupfer"
license=('GPL3')
groups=('nerv')
depends=('libkeybinder3' 'libwnck3' 'python-cairo' 'python-dbus' 'python-gobject' 'python-xdg')
makedepends=('intltool' 'python2-docutils')
optdepends=('gnome-python-desktop: full GNOME integration'
            'python2-gdata: Google services support'
            'python2-gnomekeyring: GNOME keyring support'
            'python2-setproctitle: set process name'
            'python2-wnck: tracks running applications')
provides=('kupfer')
conflict=('kupfer')
replaces=('kupfer-guns')
install=kupfer.install

pkgver() {
    printf %s "$(git describe --long --tags | tr - .)"
}

build() {
  cd "$startdir"

  ./waf configure --prefix=/usr \
                  --no-update-mime \
                  --no-update-icon-cache
  ./waf
}

package() {
  cd "$startdir"

 ./waf install -f --destdir="$pkgdir"
}
