# Maintainer: X0rg

_pkgbasename=memtest86
pkgname=$_pkgbasename-efi-beta
pkgver=6.0b3
pkgrel=1
pkgdesc="A free, thorough, stand alone memory test as an EFI application."
arch=('i686' 'x86_64')
url="http://www.memtest86.com"
license=('GPL2')
backup=(etc/$pkgname.conf)
install=$pkgname.install
source=("$_pkgbasename-$pkgver.iso.tar.gz::$url/downloads/beta/$_pkgbasename-iso-$pkgver.tar.gz"
	"memtest86-efi-beta"
	"memtest86-efi-beta.conf")
md5sums=('e6d41031bbce2d7484c8b7f091423fc0'
         '8978a9b49e940513829720d54e8c7b8a'
         '9624ed865fbf59006b0a4b892496d1c2')

prepare() {
	msg2 "Extract ISO..."
	bsdtar -xf "Memtest86-6.0.0.iso"
}

package() {
	msg2 "Move MemTest86 stuff in share directory..."
	[[ "$CARCH" == "i686" ]]   && install -Dvm755 "$srcdir/EFI/BOOT/BOOTIA32.EFI" "$pkgdir/usr/share/$pkgname/bootia32.efi"
	[[ "$CARCH" == "x86_64" ]] && install -Dvm755 "$srcdir/EFI/BOOT/BOOTX64.EFI"  "$pkgdir/usr/share/$pkgname/bootx64.efi"
	install -vm644 "$srcdir/EFI/BOOT/MT86.PNG" "$pkgdir/usr/share/$pkgname/mt86.png"

	msg2 "Install AUR provided script..."
	install -Dvm755 "$srcdir/memtest86-efi-beta"		"$pkgdir/usr/bin/memtest86-efi-beta"
	install -Dvm644 "$srcdir/memtest86-efi-beta.conf"	"$pkgdir/etc/memtest86-efi-beta.conf"
}
