# Maintainer: Sung Pae <self@sungpae.com>
# Contributor: D. Can Celasun <dcelasun[at]gmail[dot]com>
# Contributor: Alessio Sergi <asergi at archlinux dot us>
# Contributor: Asa Marco <marcoasa90[at]gmail[.]com>
pkgname=kupfer-nerv
pkgver=
pkgrel=1
pkgdesc="Custom kupfer build"
arch=('x86_64')
url="https://github.com/guns/kupfer"
license=('GPL3')
groups=('nerv')
depends=('desktop-file-utils' 'gnome-doc-utils' 'hicolor-icon-theme' 'pygtk'
         'python2-dbus' 'python2-gobject2' 'python2-keybinder2' 'python2-wnck' 'python2-xdg')
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

  # python2 fix
  sed -i -e 's_#![ ]*.*python$_&2_' {waf,{auxdata/,}wscript,$(find . -name "*.py")}

  # fix man page generation
  sed -i 's_rst2man_&2_Ig' wscript

  export PYTHON="/usr/bin/python2"
  ./waf configure --prefix=/usr \
                  --no-update-mime \
                  --no-update-icon-cache
  ./waf
}

package() {
  cd "$startdir"

 ./waf install -f --destdir="$pkgdir"
}
