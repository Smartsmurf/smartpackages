#
# Copyright (C) 2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
PKG_NAME:=jdk
#PKG_VERSION:=a92720b96ded
#PKG_SOURCE_PROTO:=http
#PKG_SOURCE:=tip.tar.gz
#PKG_SOURCE_URL:=https://hg.openjdk.java.net/aarch32-port/jdk8u/jdk/archive/
#PKG_HASH:=518aba8fe1a4b9e819d0f97299cf776ffcec7e3a461319402c946f945b300b1b

PKG_VERSION:=a1ee9743f4ee
PKG_SOURCE:=a1ee9743f4ee.tar.gz
PKG_SOURCE_URL:=http://hg.openjdk.java.net/jdk/jdk/archive/
PKG_HASH:=dccbabbd17bee087dac38bf4fbcd7e1c06a7547926b7208650aff8262315517d
#PKG_RELEASE:=1.2
#PKG_SOURCE_DATE:=2018-04-29
#PKG_SOURCE_VERSION:=c7f3f301ad357d15720edca63ea6b81865d13e0e
PKG_MAINTAINER:=Andreas Fiedler <smartsmurf@shared-files.de>

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/openjdk/Default

endef

#
define Package/openjdk
  SUBMENU:=Java
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=OpenJDK 8
  URL:=http://openjdk.java.net/
  DEPENDS:=+zlib +libfreetype +libcups +jamvm
endef


define Package/openjdk/description
 OpenJDK 8
endef

define Build/Configure
	cd $(PKG_BUILD_DIR) && chmod 755 configure && \
	PKG_CONFIG="pkg-config" FREETYPE_CFLAGS="-I/usr/include/freetype2 -I/usr/include/libpng16" FREETYPE_LIBS="-L/usr/lib -lfreetype" ./configure \
	    --host=$(REAL_GNU_TARGET_NAME) \
            --target=$(REAL_GNU_TARGET_NAME) \
	    --disable-headful
endef
#            --openjdk-target=$(REAL_GNU_TARGET_NAME) \

#	CC=$(REAL_GNU_TARGET_NAME)-gcc CXX=$(REAL_GNU_TARGET_NAME)-g++ ./configure \
# PKG_CONFIG="pkg-config" 
#	CPPFLAGS="-m32" CC=$(REAL_GNU_TARGET_NAME)-gcc PKG_CONFIG="pkg-config" ./configure \
#	    --host=$(REAL_GNU_TARGET_NAME) \
#            --target=$(REAL_GNU_TARGET_NAME) \
# 	    --without-alsa


# CMAKE_OPTIONS += -DWITH_SYSTEMD=0
# CMAKE_OPTIONS += -DWITH_AVCODEC=1

#define Package/openjdk/conffiles
#/etc/openjdk.conf
#endef

#define Package/openjdk/install
#	$(INSTALL_DIR) $(1)/etc/gerbera
#	$(INSTALL_DIR) $(1)/etc/init.d
#	$(INSTALL_DIR) $(1)/usr/bin
#	$(INSTALL_DIR) $(1)/usr/share
#	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/gerbera $(1)/usr/bin/
#	$(CP)  $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
#	$(INSTALL_DATA) ./files/config.xml $(1)/etc/gerbera/
#	$(INSTALL_BIN) ./files/gerbera.init $(1)/etc/init.d/gerbera
#endef

$(eval $(call BuildPackage,openjdk))


