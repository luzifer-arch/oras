# Maintainer: Knut Ahlers <knut@ahlers.me>
# Contributor: JayceCao <jaycecao520@gmail.com>

pkgname=oras
pkgver=1.2.2 # renovate: depName=oras-project/oras datasource=github-releases
pkgrel=1
pkgdesc='A command line tool that allows you to push and pull files from any OCI registry'
arch=(x86_64)
url='https://github.com/oras-project/oras'
license=(MIT)
makedepends=('go' 'git')
source=("$pkgname-${pkgver}.tgz::https://github.com/oras-project/oras/archive/refs/tags/v${pkgver}.tar.gz")
sha256sums=('09436b3048aab42fdfd5662f71da7d211f9d6e7ce66740cbbd8f3695ae621f6a')

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
