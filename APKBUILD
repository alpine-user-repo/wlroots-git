pkgname=wlroots-git
pkgver=0
pkgrel=0
provides="wlroots"
_pkgname="wlroots"
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
source="https://gitlab.freedesktop.org/wlroots/wlroots/-/archive/master/wlroots-master.zip"

build() {
    cd "${srcdir}/wlroots-master"
    abuild-meson \
	-Dexamples=false \
	. build
    meson compile ${JOBS:+-j ${JOBS}} -C build
}

package() {
    cd "${srcdir}/wlroots-master"
    DESTDIR="$pkgdir" meson install --no-rebuild -C build
}
sha512sums="
ff3bf2d221dc7437b0051349c65f847501a7349628fb65ba32596f1598c49b8779e73dd2e57a63e51a10edbcc1c585eab99dfb3d80bee55111763dd7da0c9aa5  wlroots-master.zip
"
