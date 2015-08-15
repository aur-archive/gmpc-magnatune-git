#Contributor: Mineo <the_mineo@web.de>

pkgname=gmpc-magnatune-git
provides=gmpc-magnatune
conflicts=('gmpc-magnatune')
pkgver=20091025
pkgrel=1
pkgdesc="The magnatune plugin allows you to browse and preview music available on Magnatune."
url="http://gmpc.wikia.com/wiki/GMPC_PLUGIN_MAGNATUNE"
license="GPL"
arch=('i686' 'x86_64')
depends=('gmpc-git') 
makedepends=('git' 'intltool' 'pkgconfig')
options=('!libtool')

_gitroot="git://repo.or.cz/gmpc-magnatune.git"
_gitname="gmpc-magnatune"
build() {
	cd $startdir/src
	msg "Connecting to $_gitroot server..."

	if [ -d $startdir/src/$_gitname ] ; then
		cd $_gitname && git pull origin
		msg "The local files are updated."
	else
		git clone $_gitroot
	fi

	msg "GIT checkout done or server timeout"
	msg "Starting make..."

	cp -r $startdir/src/$_gitname $startdir/src/$_gitname-build
	cd $startdir/src/$_gitname-build

	./autogen.sh --prefix=/usr
	make || return 1
	make DESTDIR=$startdir/pkg install
}

