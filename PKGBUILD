# Maintainer: Martin Franc <me@martinfranc.eu>

pkgname=wob
pkgver=0.12
pkgrel=1
pkgdesc='A lightweight overlay volume/backlight/progress/anything bar for Wayland'
arch=('i686' 'x86_64' 'aarch64')
url='https://github.com/francma/wob'
license=('ISC')
depends=('wayland')
makedepends=('meson' 'wayland-protocols' 'scdoc')
source=(
	"${pkgname}-${pkgver}.tar.gz::https://github.com/francma/wob/releases/download/${pkgver}/wob-${pkgver}.tar.gz"
	"${pkgname}-${pkgver}.tar.gz.sig::https://github.com/francma/wob/releases/download/${pkgver}/wob-${pkgver}.tar.gz.sig"
)
validpgpkeys=('5C6DA024DDE27178073EA103F4B432D5D67990E3')
sha512sums=(
	'a8b0bf5d3b3ade69fa367cef50cb94e3de2fe8fafe99a3f9ab37f7690d89a5bc4adece34df9c79c064f1d0dc203bc2c6785292f725d5c63d6d1e5732c09b38c3'
	'SKIP'
)

prepare() {
	cd "${pkgname}-${pkgver}"
}

build() {
	mkdir -p build
	arch-meson build "${pkgname}-${pkgver}" -D b_ndebug=true
	ninja -C build
}

package() {
	DESTDIR="${pkgdir}" ninja -C build install
	install -Dm644 "${pkgname}-${pkgver}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

check() {
	ninja -C build test
}
