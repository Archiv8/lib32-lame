#!/bin/bash

# Created from the original package by Daniel Bermond < gmail-com: danielbermond >, Johannes Dewender  arch at JonnyJD dot net and josephgbr <rafael.f.f1@gmail.com>

# Disable various shellcheck rules that produce false positives in this file.
# Repository rules should be added to the .shellcheckrc file located in the
# repository root directory, see https://github.com/koalaman/shellcheck/wiki
# and https://archiv8.github.io for further information.
# shellcheck disable=SC2034,SC2154
# [Query]: Is package still being maintained.  Last release was 3.100, 2017-10-13.  Latest commit was 2021-06-19.
# [ToDo]: Add files: User documentation
# [ToDo]: Add files: Tooling
# [FixMe]: Namcap warnings and errors

# Maintainer: Ross Clark <https://github.com/Archiv8/lib32-lame/discussions>
# Contributor: Ross Clark <https://github.com/Archiv8/lib32-lame/discussions>

_relname=lame

pkgname=lib32-"$_relname"
pkgver=3.100
pkgrel=4
pkgdesc='A high quality MPEG Audio Layer III (MP3) encoder (32 bit)'
arch=('x86_64')
url='http://lame.sourceforge.net/'
depends=('lib32-ncurses' "$_relname")
makedepends=('nasm')
license=('LGPL')
source=("https://downloads.sourceforge.net/sourceforge/lame/${_relname}-${pkgver}.tar.gz")
sha512sums=('ddfe36cab873794038ae2c1210557ad34857a4b6bdc515785d1da9e175b1da1e')

build() {
    cd "${_relname}-${pkgver}"

    export CC='gcc -m32'
    export CXX='g++ -m32'
    export PKG_CONFIG_PATH='/usr/lib32/pkgconfig'

    ./configure \
        --prefix='/usr' \
        --libdir='/usr/lib32' \
        --enable-shared='yes' \
        --enable-nasm

    make
}

package() {
    cd "${_relname}-${pkgver}"

    make DESTDIR="$pkgdir" install

    rm -r "$pkgdir"/usr/{bin,include,share}
}
