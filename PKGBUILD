# Maintainer: Stefan Zipproth <s.zipproth@ditana.org>

pkgname=ditana-ramdisk
pkgver=1.005
pkgrel=1
pkgdesc="Ditana RAM disk service"
arch=(any)
url="https://ditana.org"
license=('AGPL-3.0-or-later AND LGPL-2.1-or-later AND CC0-1.0 AND GPL-2.0-or-later AND MIT-0')
conflicts=()
install=ditana-ramdisk.install
depends=(systemd)
makedepends=()
source=(
    'ditana-ramdisk.service'
    'ramdisk.sh'
    '90-ditana-ramdisk.conf'
    'ditana-ramdisk.sh'
)
sha256sums=(
    'SKIP'
    'SKIP'
    'SKIP'
    'SKIP'
)

package() {
    # Install the systemd user service to launch the RAM disk script located at /usr/share/ditana/ramdisk.sh
    install -D -m644 $srcdir/ditana-ramdisk.service $pkgdir/etc/systemd/user/ditana-ramdisk.service

    # Install the main RAM disk script that creates and manages the RAM disk directory
    install -D -m755 $srcdir/ramdisk.sh $pkgdir/usr/share/ditana/ramdisk.sh

    # Install the environment configuration for systemd context to ensure the RAMDISK variable is available
    install -D -m644 $srcdir/90-ditana-ramdisk.conf $pkgdir/etc/environment.d/90-ditana-ramdisk.conf

    # Install the profile script to export the RAMDISK variable for user shell sessions
    install -D -m644 $srcdir/ditana-ramdisk.sh $pkgdir/etc/profile.d/ditana-ramdisk.sh
}
