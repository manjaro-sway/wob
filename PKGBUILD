# Maintainer: Martin Franc <me@martinfranc.eu>

pkgname=wob
pkgver=0.21
pkgrel=2
pkgdesc='A lightweight overlay volume/backlight/progress/anything bar for Wayland'
arch=('i686' 'x86_64' 'aarch64')
url='https://github.com/boredland/wob'
license=('ISC')
depends=('wayland')
makedepends=('meson' 'wayland-protocols' 'scdoc')
_commit='562a5414af6a14c2249bf53a1ed336b586ae712c'
source=(
	"${pkgname}-${_commit}.zip::${url}/archive/${_commit}.zip"
)
sha512sums=(
	'SKIP'
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