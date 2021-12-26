pkgname=wlroots-git
pkgver=1
pkgrel=0
provides="wlroots"
_repo="https://gitlab.freedesktop.org/wlroots/wlroots"
pkgdesc="Modular Wayland compositor library"
url="https://gitlab.freedesktop.org/wlroots/wlroots"
license="MIT"
arch="all !ppc64le !mips64" # blocked by libseat
makedepends="
	eudev-dev
	libcap-dev
	libinput-dev
	libseat-dev
	libxcb-dev
	libxkbcommon-dev
	mesa-dev
	meson
	ninja
	pixman-dev
	wayland-dev
	wayland-protocols
	xcb-util-image-dev
	xcb-util-renderutil-dev
	xcb-util-wm-dev
	xkeyboard-config
	xwayland-dev
	"
subpackages="$pkgname-dbg $pkgname-dev"
source=""

prepare() {
    default_prepare
    cd "${srcdir}"
    git clone --depth=1 "${_repo}" || return 1
}

build() {
    cd "${srcdir}/${pkgname}"
    abuild-meson \
	-Dexamples=false \
	. build
    meson compile ${JOBS:+-j ${JOBS}} -C build
}

package() {
    cd "${srcdir}/${pkgname}"
    DESTDIR="$pkgdir" meson install --no-rebuild -C build
}
