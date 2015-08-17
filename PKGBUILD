# $Id: PKGBUILD 213377 2014-05-22 01:59:19Z dan $
# Maintainer: Chris Warrick <aur@chriswarrick.com>
# Contributor: Dan McGee <dan@archlinux.org>
# Contributor: Sebastien Binet <binet@lblbox>

pkgname=python26-pip
pkgver=6.0.3
pkgrel=1
pkgdesc="An easy_install replacement for installing pypi python packages"
url="https://pip.pypa.io/"
arch=('any')
license=('MIT')
depends=('python26' 'python26-setuptools')
source=(http://pypi.python.org/packages/source/p/pip/pip-${pkgver}.tar.gz)
md5sums=('1ca6788e57a176abbdf6d99d69f54ae0')

package() {
  conflicts=('python-pyinstall')
  replaces=('python-pyinstall')

  cd "$srcdir/pip-$pkgver"
  python2.6 setup.py build
  python2.6 setup.py install --prefix=/usr --root="$pkgdir"

  mv "$pkgdir/usr/bin/pip" "$pkgdir/usr/bin/pip2.6"
  rm "$pkgdir/usr/bin/pip2"
  sed -i "s|#!/usr/bin/env python$|#!/usr/bin/env python2.6|" \
    ${pkgdir}/usr/lib/python2.6/site-packages/pip/__init__.py

  install -D -m644 LICENSE.txt "$pkgdir/usr/share/licenses/$pkgname/LICENSE"
}
