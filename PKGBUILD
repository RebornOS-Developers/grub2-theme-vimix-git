# Maintainer: Felix Golatofski <contact@xdfr.de>
# Contributor: mads256h <mads256h(at)gmail(dot)com>
# Contributor: Alireza Ayinmehr <alireza.darksun@gmail.com>
# Contributor: wenLiangcan <boxeed at gmail dot com>
# Contributor: se7enday(87635645#qq.com)

pkgname=grub2-theme-vimix-git
pkgver=2020.11.04.r11.g8f531d2
pkgrel=1.2
pkgdesc="Grub2 theme Vimix"
url='https://github.com/vinceliuice/grub2-themes/'
arch=('any')
license=('GPLv3')
depends=('grub')
makedepends=('git' 'sed')
install=${pkgname}.install
source=("${pkgname}"::"git+https://github.com/vinceliuice/grub2-themes.git"
        "theme.txt"
        "unifont-regular-16.pf2")
conflicts=('grub2-theme-vimix')
md5sums=('SKIP'
         'a2d93f98bd9c3e606a11aa8f1abda467'
         '7b830bf22b77415ba51a93ad24397472')
_theme="Vimix"

pkgver() {
    cd "${srcdir}/${pkgname}"
    git describe --long --tags | sed 's/\([^-]*-g\)/r\1/;s/-/./g'
}

package() {
    cd "${srcdir}/${pkgname}/common"
    for file in *; do
        install -Dm644 "${file}" "${pkgdir}/boot/grub/themes/${_theme}/${file}"
    done

    cd "${srcdir}/${pkgname}"
    install -Dm644 "backgrounds/1080p/background-${_theme,,}.jpg" "${pkgdir}/boot/grub/themes/${_theme}/background.jpg"

    install -dm644 "assets/assets-white/icons" "${pkgdir}/boot/grub/themes/${_theme}/icons"

    cd "${srcdir}/${pkgname}/assets/assets-white/select-1080p"
    for file in *.png; do
        install -m644 "${file}" "${pkgdir}/boot/grub/themes/${_theme}/${file}"
    done
    mkdir -p ${pkgdir}/boot/grub/themes/${_theme}
    install -Dm644 ${srcdir}/theme.txt ${pkgdir}/boot/grub/themes/${_theme}
    install -Dm644 ${srcdir}/unifont-regular-16.pf2 ${pkgdir}/boot/grub/themes/${_theme}
}

