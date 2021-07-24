# Maintainer: Martin Franc <me@martinfranc.eu>

pkgname=wob
pkgver=0.20
pkgrel=2
pkgdesc='A lightweight overlay volume/backlight/progress/anything bar for Wayland'
arch=('i686' 'x86_64' 'aarch64')
url='https://github.com/francma/wob'
license=('ISC')
depends=('wayland')
makedepends=('meson' 'wayland-protocols' 'scdoc')
_commit='002b84b4ce654b0e38e8d1b2512b779345896e42'
source=(
	"${pkgname}-${_commit}.zip::${url}/archive/${_commit}.zip"
)
sha512sums=(
	'314e696cf9886fb447504503cc42a258e71624ccb9a8fe3a4261efaecb50571583e648bea56aad4a9ca46cde56a698144187937123a268cb1c93086639c08025'
)

prepare() {
	cd "${pkgname}-${_commit}"
}

build() {
	mkdir -p build
	arch-meson build "${pkgname}-${_commit}" -D b_ndebug=true
	ninja -C build
}

package() {
	DESTDIR="${pkgdir}" ninja -C build install
	install -Dm644 "${pkgname}-${_commit}/LICENSE" "${pkgdir}/usr/share/licenses/${pkgname}/LICENSE"
}

check() {
	ninja -C build test
}
