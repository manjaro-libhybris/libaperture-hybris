# Maintainer: Bardia Moshiri <fakeshell@bardia.tech>

pkgname=libaperture-hybris
pkgver=0.1.0+git20200908+8+gdf53c57
pkgrel=1
_commit=693622e3fc071fc25ee46f66661266c44277cc02
pkgdesc='A camera library for GTK3'
arch=('any')
url='https://github.com/droidian/libaperture-0'
license=('GPL3')
depends=('vala' 'gtk3' 'gobject-introspection')
makedepends=('git' 'meson')
provides=('libaperture')
conflicts=('libaperture')
source=("libaperture::git+https://github.com/droidian/libaperture-0#commit=${_commit}")
sha256sums=('SKIP')

prepare() {
  cd "$srcdir/libaperture"
  git switch feature/bookworm/droidcamsrc-devel
}

pkgver() {
  cd "$srcdir/libaperture"
  git describe --tags | sed 's/^v//;s/-/+/g;s|upstream/||g;s|droidian/||g;s|bookworm/||g'
}

build() {
  cd "$srcdir/libaperture"
  rm -rf build
  mkdir build
  cd build
  meson --prefix /usr --buildtype release ..
  ninja
}

package() {
  cd "$srcdir/libaperture"
  cd build
  DESTDIR="$pkgdir" ninja install
}
