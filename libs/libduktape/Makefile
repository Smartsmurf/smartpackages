#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libduktape
PKG_VERSION:=2.2.0
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/svaarala/duktape
PKG_SOURCE_DATE:=2017-09-23
PKG_SOURCE_VERSION:=a459cf3c9bd1779fc01b435d69302b742675a08f
PKG_MIRROR_HASH:=
PKG_MAINTAINER:=Andreas Fiedler <smartsmurf@shared-files.de>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libduktape
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=Duktape JavaScript library
  URL:=http://duktape.org
  DEPENDS:=+libpthread
  MENU:=1
endef

define Package/libduktape/description
Duktape is an embeddable Javascript engine, with a focus on portability and compact footprint.
endef

define Build/Configure
	cd $(PKG_BUILD_DIR) && python tools/configure.py \
	    --source-directory src-input \
	    --platform linux \
	    --architecture arm32 \
	    --config-metadata config/ \
	    --output-directory /tmp/arm32  

endef

define Build/Compile

	$(MAKE) -C $(PKG_BUILD_DIR) \
		duk libduktape.so.1.0.0

endef

define Build/Install
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_BUILD_DIR)/prep/nondebug/duk*.h $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libduktape.so* $(1)/usr/lib/
#	$(INSTALL_DIR) $(1)/usr/bin
#	$(CP) $(PKG_BUILD_DIR)/duk $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) ./files/libduktape.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libduktape/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_BUILD_DIR)/libduktape.so* $(1)/usr/lib/
#	$(INSTALL_DIR) $(1)/usr/bin
#	$(CP) $(PKG_BUILD_DIR)/duk $(1)/usr/bin/
endef

$(eval $(call BuildPackage,libduktape))

