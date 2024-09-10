# Maintainer: Knut Ahlers <knut@ahlers.me>
# Contributor: JayceCao <jaycecao520@gmail.com>

pkgname=oras
pkgver=1.2.0
pkgrel=1
pkgdesc='A command line tool that allows you to push and pull files from any OCI registry'
arch=(x86_64)
url='https://github.com/oras-project/oras'
license=(MIT)
makedepends=('go' 'git')
source=("$pkgname-${pkgver}.tgz::https://github.com/oras-project/oras/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('1f3fc661c90cfb48b4b0e6ef4817b86b28c784186ab0da1a778809938899f574')

build() {
  # Flags to trim path from binary
  export GOFLAGS="-gcflags=all=-trimpath=${PWD} -asmflags=all=-trimpath=${PWD} -ldflags=-extldflags=-zrelro -ldflags=-extldflags=-znow"
  export VERSION=$pkgver

  cd "$pkgname-${pkgver}"
  make build-linux-amd64
}

package() {
  install -Dm 755 "$srcdir/$pkgname-${pkgver}/bin/linux/amd64/$pkgname" "$pkgdir/usr/bin/$pkgname"
}
