# Maintainer zanderhavgaard <contact@pzh.dk>

pkgname=opentofu
pkgver=1.6.0
_pkgver="${pkgver//_/-}"
pkgrel=1
pkgdesc='Open source fork of terraform'
arch=('x86_64')
url='https://github.com/opentofu/opentofu'
license=('MPL 2.0')
provides=('tofu')
makedepends=('go')
# source=("$pkgname::git+$url")
source=("https://github.com/opentofu/opentofu/archive/refs/tags/v$_pkgver.tar.gz")
sha512sums=('SKIP')

# TODO: fix
# pkgver() {
# 	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short=7 HEAD)"
# }

build() {
	cd "$pkgname-$_pkgver"
	go build -ldflags "-w -s -X 'github.com/opentofu/opentofu/version.dev=no'" -o bin/ ./cmd/tofu
}

package() {
	cd "${srcdir}/$pkgname-$_pkgver"
	install "bin/tofu" -t "${pkgdir}/usr/bin" -Dm 0755
}
