pkgname=purple-facebook
license=('GPL')
arch=('x86_64')
pkgver=0.9.5_9ff9acf9fa14
pkgrel=1
pkgdesc="Purple Facebook implements the Facebook Messenger protocol into pidgin, finch, and libpurple"
depends=('json-glib' 'libpurple')
url="https://github.com/dequis/purple-facebook"
pkgfullver=${pkgver/_/-}
pkgfullname="${pkgname}-${pkgfullver}"
source=("${pkgfullname}.tar.gz::https://github.com/dequis/purple-facebook/releases/download/v${pkgfullver}/${pkgfullname}.tar.gz" "ktp-haze-facebook-im.service" "ktp-haze-facebook.provider")
md5sums=('ef5b78a3473182ae5574c4571799186f' '4f559540664cbebf33c817f7b33e81ff' '4ce3aa23e0f5502401359eb0df2606cb')

build() {
  mkdir -p build
  cd build

  ../${pkgfullname}/configure \
    --prefix=/usr
  make
}

package() {
  cd build

  install -D -m644 ${srcdir}/ktp-haze-facebook.provider ${pkgdir}/usr/share/accounts/providers/kde/ktp-haze-facebook.provider
  install -D -m644 ${srcdir}/ktp-haze-facebook-im.service ${pkgdir}/usr/share/accounts/services/kde/ktp-haze-facebook-im.service
  make DESTDIR=${pkgdir} install
}
