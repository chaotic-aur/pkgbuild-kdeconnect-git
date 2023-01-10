# Merged with official ABS kdeconnect PKGBUILD by João, 2021/02/18 (all respective contributors apply herein)
# Maintainer: João Figueiredo <jf.mundox@gmail.com>
# Contributor: Rihards Skuja <rhssk at posteo dot eu>
# Contributor: Vojtech Kral <vojtech_kral^hk>
# Contributor: Antonio Rojas <arojas@archlinux.org>
# Contributor: Kuba Serafinowski <zizzfizzix(at)gmail(dot)com>

pkgname=kdeconnect-git
pkgver=21.03.70_r3133.gdd999334
pkgrel=1
pkgdesc='Adds communication between KDE and your smartphone'
url='https://community.kde.org/KDEConnect'
arch=($CARCH)
license=(GPL)
groups=(kde-applications-git kde-network-git)
depends=(kcmutils-git kwayland-git libfakekey qqc2-desktop-style-git qca-git kpeoplevcard-git pulseaudio-qt kirigami-git hicolor-icon-theme wayland-protocols-git plasma-wayland-protocols-git kpackage-git kwindowsystem-git kirigami2-git kirigami-addons-git kpeople-git modemmanager-qt-git)
makedepends=(git extra-cmake-modules-git kdoctools-git)
conflicts=(${pkgname%-git})
provides=(${pkgname%-git})
optdepends=('sshfs: remote filesystem browser' 'python-nautilus: Nautilus integration' 'qt5-tools: for some runcommand plugin actions')
source=("git+https://github.com/KDE/${pkgname%-git}-kde.git")
sha256sums=('SKIP')

pkgver() {
    cd ${pkgname%-git}-kde
      _major_ver="$(grep -m1 'set *(RELEASE_SERVICE_VERSION_MAJOR' CMakeLists.txt | cut -d '"' -f2)"
        _minor_ver="$(grep -m1 'set *(RELEASE_SERVICE_VERSION_MINOR' CMakeLists.txt | cut -d '"' -f2)"
          _micro_ver="$(grep -m1 'set *(RELEASE_SERVICE_VERSION_MICRO' CMakeLists.txt | cut -d '"' -f2)"
            echo "${_major_ver}.${_minor_ver}.${_micro_ver}_r$(git rev-list --count HEAD).g$(git rev-parse --short HEAD)"
}

build() {
    cmake -B build -S ${pkgname%-git}-kde \
        -DBUILD_TESTING=OFF \
            -DCMAKE_INSTALL_LIBEXECDIR=lib
              cmake --build build
}

package() {
    DESTDIR="$pkgdir" cmake --install build
}
