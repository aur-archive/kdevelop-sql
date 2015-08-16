
pkgname=kdevelop-sql
_name=kdev-sql
pkgver=1.3.80
pkgrel=2
pkgdesc="It allows you to execute SQL queries from within Kate/KDevelop"
arch=(i686 x86_64)
url="http://nikosams.blogspot.it/2012/10/execute-sql-kdevelop-plugin.html"
license=('GPL2')
depends=('kdelibs>=4' 'sqlite2' 'qt4' 'kdevelop>=4')
makedepends=('automoc4' 'cmake')
source=("http://master.kde.org/unstable/kdevelop/kdev-sql/1.3.80/src/${_name}-${pkgver}.tar.bz2")
md5sums=('f0058f9fa0190f8a2a2e43137c3dd96c')
_buildir=$srcdir/${_name}-${pkgver}/build

build() {
cd $srcdir/${_name}-${pkgver}

if [ -d "$_buildir" ]; then
		msg 'Cleaning previous build...'
		rm -rf "$_buildir"
	fi
#run cmake manually to set the correct CMAKE_INSTALL_PREFIX
mkdir build
cd build
cmake DCMAKE_INSTALL_PREFIX=`kde4-config --prefix` ..

make || return 1

cd $srcdir/${_name}-${pkgver}/build
make DESTDIR=$pkgdir install/strip || return 1
#install -D -m644 $srcdir/kfritz/$pkgname.desktop $pkgdir/usr/share/applications/$pkgname.desktop
}
