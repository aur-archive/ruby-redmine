# Maintainer: Blaž Tomažič <blaz.tomazic@gmail.com>
# Maintainer: Mikołaj Milej <mikolajmm at the gmail>

pkgname=ruby-redmine
pkgver=1.3.2
pkgrel=2
_realname="redmine"
pkgdesc="Redmine is a flexible project management web application written using Ruby on Rails framework."
arch=('i686' 'x86_64')
url="http://www.redmine.org/"
license=('GPL2')
depends=('ruby1.8' 'ruby1.8-rack-v1.1.0' 'ruby1.8-rake>=0.8.3' 'procps' 'ruby1.8-i18n-v0.4.2')
makedepends=('glibc' 'rubygems1.8')
optdepends=('ruby1.8-rmagick: Enable Gantt export to png image'
            'mysql-ruby1.8: MySQL database backend'
            'ruby1.8-sqlite3: SQLite database backend'
            'subversion>=1.3.0: Subversion repository browsing'
            'git: Git repository browsing'
            'darcs: Darcs repository browsing'
            'bzr: Bazaar repository browsing'
            'mercurial: Mercurial repository browsing')
options=()
install=ruby-redmine.install
_rubyforge=75910
source=("http://rubyforge.org/frs/download.php/$_rubyforge/$_realname-$pkgver.tar.gz"
        "redmine.rc"
        "redmine.service")
md5sums=('49b5dc8a4d06b4db855fdda2e30c2a69'
         'ff866b376f6bfe24d89cc1cccbf3f942'
         '9ea693da2f2e036e122283f0d3fe3b3b')

build() {
  return 0
}

package() {
  cd "$srcdir/$_realname-$pkgver"
  
  #install in /var/lib
  _instdir="$pkgdir/var/lib/$_realname"
  mkdir -p ${_instdir}
  cp -ra . ${_instdir}
  
  #create some needed dir
  mkdir -p "${_instdir}/public/plugin_assets"
  
  #create /etc/rc.d/redmine
  mkdir -p "$pkgdir/etc/rc.d/"
  install -m 755 "$srcdir/redmine.rc" "$pkgdir/etc/rc.d/redmine"
  
  #create systemd service
  mkdir -p "$pkgdir/lib/systemd/system/"
  install -m 644 "$srcdir/redmine.service" "$pkgdir/lib/systemd/system/"
  
  #create redmine user home
  mkdir -p "${_instdir}/redmine/"
}

# vim:set ts=2 sw=2 et:
