# Contributor: vaca

pkgbase=mythplugins-git
pkgname=('mythplugins-git')
true && pkgname=('mythplugins-mytharchive-git'
         'mythplugins-mythbrowser-git'
         'mythplugins-mythgallery-git'
         'mythplugins-mythgame-git'
         'mythplugins-mythmusic-git'
         'mythplugins-mythnews-git'
         'mythplugins-mythzoneminder-git'
	 'mythplugins-mythweather-git'
	 'mythplugins-mythnetvision-git')
pkgver=20130302
pkgrel=1
pkgdesc="mythplugins 0.26-fixes"
arch=('i686' 'x86_64')
url="http://www.mythtv.org"
license=('GPL')
makedepends=("mythtv-git" 'cdrkit' 'dvdauthor' 'dvd+rw-tools' 'ffmpeg'
             'python-imaging' 'libexif' 'perl-date-manip' 'zlib' 'cdparanoia'
             'flac' 'libcdaudio' 'libvisual' 'libvorbis' 'sdl' 'taglib'
             'python2-oauth' 'python-pycurl' 'mplayer' 'perl-date-manip'
             'perl-libwww' 'perl-soap-lite' 'perl-xml-sax' 'perl-xml-simple'
             'perl-xml-xpath' 'perl-image-size' 'perl-datetime-format-iso8601' 'perl-module-implementation' 'git')
#options=('force')
source=('mtd.rc')

md5sums=('476c12ba074794ad7f4ae092bdf949d6')


_gitname="mythplugins"
_gitroot="git://github.com/MythTV/mythtv.git"

build() {
    msg "Connecting to GIT server...."

if [ -d $_gitname/.git ]; then
    cd $_gitname
    git pull && git pull origin
    msg "The local files are updated."
else
    git clone -b fixes/0.26 "$_gitroot" "$_gitname"
    #git clone "$_gitroot" "$_gitname"
fi

msg "GIT checkout done or server timeout"
msg "Starting make..."

rm -rf "$srcdir/$_gitname-build"
git clone "$srcdir/$_gitname" "$srcdir/$_gitname-build"
cd "$srcdir/$_gitname-build/$_gitname"

find . -name '*.py' -type f | xargs sed -i 's@^#!.*python$@#!/usr/bin/python2@'

  ./configure --prefix=/usr \
              --enable-all \
              --python=python2 \
	      --qmake=qmake4
	      
  #qmake mythplugins.pro
  make
}

package_mythplugins-mytharchive-git() {
  pkgdesc="Create DVDs or archive recorded shows in MythTV"
  depends=("mythtv-git" 'cdrkit' 'dvdauthor' 'dvd+rw-tools' 'ffmpeg'
           'python-imaging')

  replaces=('mythplugins-mytharchive')
  conflicts=('mythplugins-mytharchive')
  cd "${srcdir}/$_gitname-build/$_gitname/mytharchive"
  make INSTALL_ROOT="${pkgdir}" install
}

package_mythplugins-mythbrowser-git() {
  pkgdesc="Mini web browser for MythTV"
  depends=("mythtv-git")
  replaces=('mythplugins-mythbrowser')
  conflicts=('mythplugins-mythbrowser')
  cd "${srcdir}/$_gitname-build/$_gitname/mythbrowser"
  make INSTALL_ROOT="${pkgdir}" install
}


package_mythplugins-mythgallery-git() {
  pkgdesc="Image gallery plugin for MythTV"
  depends=("mythtv-git" 'libexif')
  replaces=('mythplugins-mythgallery')
  conflicts=('mythplugins-mythgallery')
  cd "${srcdir}/$_gitname-build/$_gitname/mythgallery"
  make INSTALL_ROOT="${pkgdir}" install
}

package_mythplugins-mythgame-git() {
  pkgdesc="Game emulator module for MythTV"
  depends=("mythtv-git")
  replaces=('mythplugins-mythgame')
  conflicts=('mythplugins-mythgame')
  cd "${srcdir}/$_gitname-build/$_gitname/mythgame"
  make INSTALL_ROOT="${pkgdir}" install
}


package_mythplugins-mythmusic-git() {
  pkgdesc="Music playing plugin for MythTV"
  depends=("mythtv-git" 'cdparanoia' 'flac' 'libcdaudio' 'libvisual'
           'libvorbis' 'sdl' 'taglib')
  replaces=('mythplugins-mythmusic')
  conflicts=('mythplugins-mythmusic')
  cd "${srcdir}/$_gitname-build/$_gitname/mythmusic"
  make INSTALL_ROOT="${pkgdir}" install
}

package_mythplugins-mythnetvision-git() {
  pkgdesc="MythNetvision plugin for MythTV"
  depends=("mythtv-git" 'python2-oauth' 'python-pycurl')
  replaces=('mythplugins-mythnetvision')
  conflicts=('mythplugins-mythnetvision')
  cd "${srcdir}/$_gitname-build/$_gitname/mythnetvision"
  make INSTALL_ROOT="$pkgdir" install
}

package_mythplugins-mythnews-git() {
  pkgdesc="News checking plugin for MythTV"
  depends=("mythtv-git")
  replaces=('mythplugins-mythnews')
  conflicts=('mythplugins-mythnews')
  cd "${srcdir}/$_gitname-build/$_gitname/mythnews"
  make INSTALL_ROOT="${pkgdir}" install
}


package_mythplugins-mythweather-git() {
  pkgdesc="Weather checking plugin for MythTV"
  depends=("mythtv-git" 'perl-date-manip' 'perl-libwww' 'perl-soap-lite'
           'perl-xml-sax' 'perl-xml-simple' 'perl-xml-xpath' 'perl-image-size'
           'perl-datetime-format-iso8601')
  replaces=('mythplugins-mythweather')
  conflicts=('mythplugins-mythweather')
  cd "${srcdir}/$_gitname-build/$_gitname/mythweather"
  make INSTALL_ROOT="$pkgdir" install
}


package_mythplugins-mythzoneminder-git() {
  pkgdesc="View CCTV footage from zoneminder in MythTV"
  depends=("mythtv-git")
  replaces=('mythzoneminder')
  conflicts=('mythzoneminder')
  install='mythplugins-mythzoneminder.install'
  cd "${srcdir}/$_gitname-build/$_gitname/mythzoneminder"
  make INSTALL_ROOT="${pkgdir}" install
}
