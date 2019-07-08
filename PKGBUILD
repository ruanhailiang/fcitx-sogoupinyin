# Maintainer: Bian Jiaping <ssbianjp [AT] gmail.com>
# Contributor: Jove Yu <yushijun110 [AT] gmail.com>
# Contributor: csslayer <wengxt [AT] gmail.com>
# Contributor: Felix Yan <felixonmars [AT] gmail.com>

pkgname=fcitx-sogoupinyin
pkgver=2.3.0.0109
pkgrel=6
pkgdesc="Sogou Pinyin for Linux"
arch=('x86_64')
url="https://pinyin.sogou.com/linux/"
license=('custom')
depends=('fcitx' 'fcitx-qt5' 'fcitx-gtk2' 'fcitx-gtk3' 'opencc' 'libidn11' 'lsb-release' 'xorg-xprop' 'qt5-webkit')


source=('sogou-autostart')
#source_i686=("http://cdn2.ime.sogou.com/dl/index/${_i686_time}/sogoupinyin_${pkgver}_i386.deb")
source_x86_64=("data.tar.xz :: file://data.tar.xz")

md5sums=('ff599d805084f49b95ba99fe640bc170')
md5sums_x86_64=('fc72ece988596af940a10f36680aaefd')
#md5sums_i686=('475d07b3a99c2e23daca68c7d900388f')

package(){
    cd ${srcdir}
    mv "$srcdir"/* "$pkgdir"
	 rm "$pkgdir"/data.tar.xz
    #tar -xJvf data.tar.xz -C "${pkgdir}"
    
    mv "$pkgdir"/usr/lib/*-linux-gnu/fcitx "$pkgdir"/usr/lib/
    rmdir "$pkgdir"/usr/lib/*-linux-gnu

    # Avoid warning "No such key 'Gtk/IMModule' in schema 'org.gnome.settings-daemon.plugins.xsettings'"
    sed -i "s#Gtk/IMModule=fcitx#overrides={'Gtk/IMModule':<'fcitx'>}#" "$pkgdir"/usr/share/glib-2.0/schemas/50_sogoupinyin.gschema.override

    rm -r "$pkgdir"/usr/share/keyrings
    rm -r "$pkgdir"/etc/X11

    # install -m755 sogou-autostart "$pkgdir"/usr/bin

    # Do not modify $pkgdir/etc/xdg/autostart/fcitx-ui-sogou-qimpanel.desktop, as it is
    # a symlink to absolute path "/usr/share/applications/fcitx-ui-sogou-qimpanel.desktop"
    # sed -i 's/sogou-qimpanel\ %U/sogou-autostart/g' "$pkgdir"/usr/share/applications/fcitx-ui-sogou-qimpanel.desktop
}