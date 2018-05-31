# Maintainer: aimileus <me at aimileus dot nl>
# Contributor: Afri 5chdn <aur@5chdn.co>
# Contributor: Andy Weidenbaum <archbaum@gmail.com>

pkgname=ethminer
pkgver=0.13.0
pkgrel=2
pkgdesc="Ethereum miner with OpenCL and stratum support (built without CUDA)."
arch=('x86_64')
url="https://github.com/ethereum/cpp-ethereum"
license=('MIT')
depends=(
  'leveldb'
  'libmicrohttpd'
)
makedepends=(
  'cmake'
  'libtool'
  'autoconf'
  'automake'
  'gcc'
)
conflicts=('ethereum')
source=(
  "${pkgname}::git+${url}#commit=38ac899bf30b87ec76f0e940674046bed952b229"
  "patch"
)
sha512sums=(
  'SKIP'
  'SKIP'
)

prepare() {
 cd "${pkgname}"
 patch -Np1 -i "${srcdir}/patch"
}

build () {
    cd "${pkgname}"
    git submodule update --init
    cmake -DCMAKE_INSTALL_PREFIX:PATH=/usr -H. -Bbuild
    cd build/ethminer
    make
}

package() {
  cd "${pkgname}/build/ethminer"
  make DESTDIR=$pkgdir install
}
