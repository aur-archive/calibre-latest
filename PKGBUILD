pkgname=calibre-latest
pkgver=2.12.0
pkgrel=3
pkgdesc="Ebook management application"
arch=('i686' 'x86_64')
url="http://calibre-ebook.com/"
license=('GPL3')
depends=('python2' 'python2-pillow' 'python2-dateutil' 'python2-cssutils'
	  'python2-mechanize' 'podofo' 'libwmf' 'python2-mechanize'
         'imagemagick' 'chmlib' 'python2-lxml' 'libusbx' 'xdg-utils' 'poppler'
         'shared-mime-info' 'python2-dnspython' 'python2-beautifulsoup3'
         'python2-pyqt5' 'python2-psutil' 'icu' 'libmtp' 'python2-pygments'
         'python2-netifaces' 'python2-cssselect' 'python2-apsw' 'python2-dbus'
	 'qt5-webkit' 'python2-chardet' 'python2-beautifulsoup3'
	 'desktop-file-utils' 'qt5-svg' 'python2-html5lib')
provides=('calibre')
conflicts=('calibre')
source=("calibre.tar.xz::http://status.calibre-ebook.com/dist/src")
md5sums=('SKIP')
buildfolder=calibre-$pkgver

build() {
  cd $srcdir/$buildfolder
  sed -i -e "s|(prefix=.*)|(prefix='$pkgdir/usr')|g" setup/install.py
  
  install -d "${pkgdir}/usr/lib/python2.7/site-packages" \
             "${pkgdir}/usr/share/zsh/site-functions"

  LANG='en_US.UTF-8' python2 setup.py install --root="${pkgdir}" \
      --prefix=/usr \
      --staging-bindir="${pkgdir}/usr/bin" \
      --staging-libdir="${pkgdir}/usr/lib" \
      --staging-sharedir="${pkgdir}/usr/share"

  # Compiling bytecode FS#33392
  python2 -m compileall "${pkgdir}/usr/lib/calibre/"

  }