# Contributor: Thomas Kinnen <thomas.kinnen@gmail.com>
pkgname=pyenet-svn
provides="pyenet"
conflicts="pyenet"
pkgdesc="pyenet is a python wrapper for the ENet library"
url="http://code.google.com/p/pyenet"
pkgver=24
pkgrel=1
arch=('i686' 'x86_64')
license=('BSD' 'MIT')
depends=('python2' 'cython2')
makedepends=('subversion')
_svntrunk="http://pyenet.googlecode.com/svn/trunk/"
_svnmod="pyenet"
_enetpackage="enet-1.3.6"
source=(http://enet.bespin.org/download/${_enetpackage}.tar.gz)
md5sums=('215faae73d7e1f0d6dc48676884d07c7')

build() {
	cd $srcdir

	if [ -d ./$_svnmod ]; then
		cd $_svnmod
		svn up
	else
		svn co $_svntrunk $_svnmod
	fi

	mkdir -p pyenet/enet/
	mv -T $_enetpackage pyenet/enet/
	cd $srcdir/$_svnmod

	python2 setup.py build
	python2 setup.py install --home=$pkgdir/usr --optimize=1 || return 1
	mkdir -p $pkgdir/usr/lib/python2.7/site-packages/
	mv $pkgdir/usr/lib/python/* $pkgdir/usr/lib/python2.7/site-packages/
	rm -r $pkgdir/usr/lib/python
}

