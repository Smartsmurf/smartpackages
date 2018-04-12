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
PKG_SOURCE_DATE:=2018-03-21
PKG_SOURCE_VERSION:=64162b3c167ffe15a0b1476c85c00479bfcffaff
PKG_MAINTAINER:=Angel Dust <smartsmurf@shared-files.de>

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
  URL:=http://gerbera.io/
  DEPENDS:=+libstdcpp +libupnp-1.8 +libcurl +libexpat +libsqlite3 +libmagic +libexif +libuuid +libtag +libduktape 
endef

define Package/gerbera/description
 A free media server.
 Stream your media to devices on your home network.
endef

TARGET_CFLAGS += -ffunction-sections -fdata-sections
TARGET_LDFLAGS += -Wl,--gc-sections

# CMAKE_OPTIONS += -DWITH_JS=0
CMAKE_OPTIONS += -DWITH_SYSTEMD=0

define Package/gerbera/conffiles
/etc/gerbera
endef

define Package/gerbera/install
	$(INSTALL_DIR) $(1)/etc/gerbera
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_DIR) $(1)/usr/share
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/gerbera $(1)/usr/bin/
	$(CP)  $(PKG_INSTALL_DIR)/usr/share/* $(1)/usr/share/
	$(INSTALL_DATA) ./files/config.xml $(1)/etc/gerbera/
	$(INSTALL_BIN) ./files/gerbera.init $(1)/etc/init.d/gerbera
endef

$(eval $(call BuildPackage,gerbera))


