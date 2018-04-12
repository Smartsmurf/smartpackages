#
# Copyright (C) 2013 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=gerbera
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/gerbera/gerbera
PKG_SOURCE_DATE:=2017-09-29
PKG_SOURCE_VERSION:=2b2a13d2476f59e4dab88d2e2464ed2a6d081b23
PKG_MIRROR_HASH:=34ad1f5c7d2eab90b795f2a512102891428216e3d439d918a8992846550e9697
PKG_MAINTAINER:=Angel Dust <jo@mein.io>

PKG_LICENSE:=GPL-2.0
PKG_LICENSE_FILES:=COPYING

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

define Package/gerbera/Default
endef

define Package/gerbera
  SECTION:=multimedia
  CATEGORY:=Multimedia
  TITLE:=A lightweight media server
  URL:=http://gerbera.io
  DEPENDS:=+libupnp-1.8 +libjs +libcurl +libexpat +libsqlite3 +libduktape +libmagic +libexif
endef

define Package/gerbera/description
 A free media server.
 Stream your media to devices on your home network.
endef

TARGET_CFLAGS += -ffunction-sections -fdata-sections
TARGET_LDFLAGS += -Wl,--gc-sections

CMAKE_OPTIONS += -DWITH_JS=0
CMAKE_OPTIONS += -DWITH_TAGLIB=0
CMAKE_OPTIONS += -DWITH_SYSTEMD=0

define Package/gerbera/conffiles
/etc/config/gerbera
endef

define Package/gerbera/install
	$(INSTALL_DIR) $(1)/etc/gerbera
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/share
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/gerbera $(1)/usr/bin/
	$(CP)  $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
	$(INSTALL_DATA)  ./files/config.xml $(1)/etc/gerbera/
	$(INSTALL_BIN) ./files/gerbera.init $(1)/etc/init.d/gerbera
endef

$(eval $(call BuildPackage,gerbera))
