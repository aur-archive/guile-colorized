# Maintainer: Profpatsch <mail[at]profpatsch[dot]de>
pkgname=guile-colorized
pkgver=0.0.7
pkgrel=1
pkgdesc="Colorized REPL for GNU Guile"
url="https://github.com/NalaGinrut/guile-colorized"
arch=('any')
license=('GPL3')
depends=('guile')
install=${pkgname}.install
source=(
    "test.scm"
    "git+https://github.com/NalaGinrut/guile-colorized.git")
md5sums=('9e39e918102f6ded6f5f0bdb96dba2a9'
         'SKIP')

package() {
  cd ${pkgname}
  local load_path="$(guile -c "(display (car %load-path))")"
  target="${pkgdir}/${load_path}/ice-9"
  mkdir -p "${target}"

  local tag_prefix="v"
  git checkout "${tag_prefix}${pkgver}" 2>&1 | head -n1
  [ $? -eq 0 ] \
    && make TARGET="${target}" install \
    || (echo "Version ${tag_prefix}${pkgver} doesn’t exist!" ; exit -1)
}
