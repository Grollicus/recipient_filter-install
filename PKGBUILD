# This is an example PKGBUILD file. Use this as a start to creating your own,
# and remove these comments. For more information, see 'man PKGBUILD'.
# NOTE: Please fill out the license field for your package! If it is unknown,
# then please put 'unknown'.

# Maintainer: Grollicus <youremail@domain.com>
pkgname=recipient_filter
pkgver=0.2.1
pkgrel=1
pkgdesc="Validate incoming email usernames against a Secret"
arch=('i686' 'x86_64')
url="https://github.com/Grollicus/recipientfilter"
license=('GPL3')
groups=()
depends=('rust')
makedepends=('cargo')
provides=()
conflicts=()
replaces=()
backup=('etc/recipient_filter.toml')
options=()
install=
source=("https://github.com/Grollicus/recipientfilter/archive/v$pkgver.tar.gz")
noextract=()
sha256sums=('84c9e6c98b7f61c60a1f5461e48e4bb8f743c5baa5bb09597e27433c40a9f993')

build() {
	cd "$srcdir/recipientfilter-${pkgver}/${pkgname}/"
	cargo build --release
}

clean() {
    cd "$srcdir/recipientfilter-${pkgver}/${pkgname}/"
	cargo clean
}

package() {
	cd "$srcdir/recipientfilter-${pkgver}/${pkgname}/"
    install -Dm755 "target/release/recipient_filter" "$pkgdir/usr/bin/recipient_filter"

    install -Dm644 "recipient_filter.service" "$pkgdir/usr/lib/systemd/system/recipient_filter.service"
    install -Dm644 "recipient_filter.default.toml" "$pkgdir/etc/recipient_filter.toml"
}
