#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libupnp
PKG_VERSION:=1.8.3
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mrjimenez/pupnp
#PKG_SOURCE_DATE:=2018-03-19
#PKG_SOURCE_VERSION:=82a29482acedacb1d6b26742724d4fd3a49e48b8
PKG_SOURCE_DATE:=2017-11-14
PKG_SOURCE_VERSION:=cea5496e27f5122369c897d82304ca9e8fa49ba7
PKG_MAINTAINER:=Andreas Fiedler <smartsmurf@shared-files.de>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk


define Package/libupnp-1.8
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=UPnP SDK library
  URL:=http://pupnp.sourceforge.net/
  DEPENDS:=+libpthread
  MENU:=1
endef

define Package/libupnp-1.8/description
The portable SDK for UPnP Devices (libupnp) provides developers with an API and
open source code for building control points, devices, and bridges that are
compliant with Version 1.0 of the  Universal Plug and Play Device Architecture
Specification.
endef

CONFIGURE_ARGS += \
	--enable-reuseaddr \
	--enable-ipv6 \

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/upnp $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{ixml,upnp}.{a,so*,la} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libupnp.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libupnp-1.8/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{ixml,upnp}.so.* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libupnp-1.8))

