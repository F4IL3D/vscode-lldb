pkgname=vscode-lldb
pkgver=1.6.10
pkgrel=1
pkgdesc="vscode-lldb"
arch=('x86_64' 'armv7h' 'armv6h' 'aarch64')
url="https://github.com/vadimcn/vscode-lldb"
license=('MIT')
depends=('lldb' 'python')
makedepends=('gcc' 'rust' 'nodejs' 'npm' 'cmake')
source=(git+https://github.com/vadimcn/vscode-lldb)
sha256sums=('SKIP')
install="${pkgname}".install

prepare() {
  cd "${srcdir}"/"${pkgname}"
  git submodule update --init
  mkdir build
}
build() {
  cd "${srcdir}"/"${pkgname}"/build
  cmake .. -DLLDB_PACKAGE=/usr
  cmake --build . --target codelldb
}
package() {
    install -dm755 "${pkgdir}"/opt/vscode-lldb/{adapter,lldb}
    install -m755 "${srcdir}"/"${pkgname}"/build/adapter/{codelldb,*.so,*.py} "${pkgdir}"/opt/vscode-lldb/adapter/
}
