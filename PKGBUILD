# Mantainer: itigr <skipper.071 @ gmail.com>

pkgname=firefox-nightly-l10n-ru
pkgdesc='mozilla.org web browser, nightly build'
url='http://www.mozilla.org/projects/firefox'
pkgver=23.0a1
arch=('i686' 'x86_64')
license=('MPL' 'GPL' 'LGPL')
source=('firefox-nightly.desktop' 'firefox-nightly-safe.desktop' 
'firefox-nightly-l10n-ru.install')
install=${pkgname}.install
depends=('alsa-lib' 'libxt' 'libnotify' 'mime-types' 'nss' 'sqlite' 'gtk2' 
 'desktop-file-utils' 'dbus-glib')
conflicts=('firefox-nightly' 'firefox-nightly-russian' 'firefox-nightly-ru')
package() {
  FX_SRC="firefox-${pkgver}.ru.linux-${CARCH}.tar.bz2"
  FX_SRC_URI="http://ftp.mozilla.org/pub/mozilla.org/firefox/nightly/latest-mozilla-central-l10n/${FX_SRC}"

  msg "Загрузка..."
  wget -N ${FX_SRC_URI}
  msg "Распаковка..."
  bsdtar -x -f ${FX_SRC}
  msg "Создание пакета..."

#   uncomment this line to remove these
#   rm -rf firefox/{extensions,plugins,searchplugins}

  mkdir -p "${pkgdir}"/{usr/{bin,share/{applications,pixmaps}},opt}
  cp -r firefox "${pkgdir}/opt/firefox-${pkgver}"

  ln -s /opt/firefox-${pkgver}/firefox "${pkgdir}/usr/bin/firefox-nightly"
  install -m644 "${srcdir}"/{firefox-nightly.desktop,firefox-nightly-safe.desktop} "${pkgdir}/usr/share/applications/"
}

pkgrel=3

md5sums=('17822c5862de6aac78f9bfd9d2661127'
         'f3a853a58909b75bb9ab3969c0102b66'
         '04793335a2ba7d17d1bd92085461e77e')
