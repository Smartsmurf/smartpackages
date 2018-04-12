#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libupnp-1.8
PKG_VERSION:=1
PKG_RELEASE:=1

#PKG_SOURCE:=release-$(PKG_VERSION).tar.gz
#PKG_SOURCE_URL:=https://github.com/mrjimenez/pupnp/archive
#PKG_HASH:=b3142b39601243b50532eec90f4a27dba85eb86f58d4b849ac94edeb29d9b22a
PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mrjimenez/pupnp
PKG_SOURCE_DATE:=2017-05-23
PKG_SOURCE_VERSION:=b8a81b0324a9e08add5066c5fe39ed70e6ef31a6
PKG_MIRROR_HASH:=34ad1f5c7d2eab90b795f2a512102891428216e3d439d918a8992846550e9697
PKG_MAINTAINER:=Ted Hess <thess@kitschensync.net>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/libupnp-1.8/Default
  SECTION:=libs
  CATEGORY:=Libraries
  URL:=http://pupnp.sourceforge.net/
endef

define Package/libupnp-1.8
  $(call Package/libupnp-1.8/Default)
  DEPENDS:=+libpthread
  TITLE:=UPnP SDK library
  MENU:=1
endef

define Package/libupnp-1.8/description
The portable SDK for UPnP Devices (libupnp) provides developers with an API and
open source code for building control points, devices, and bridges that are
compliant with Version 1.0 of the  Universal Plug and Play Device Architecture
Specification.
endef

define Package/libupnp-1.8-sample
  $(call Package/libupnp-1.8/Default)
  DEPENDS:=libupnp-1.8
  TITLE:=UPnP sample applications
endef

define Package/libupnp-1.8-sample/description
TVcontrolpoint & tvdevice sample applications run inside /etc/upnp-tvdevice/
endef

CONFIGURE_ARGS += \
	--enable-reuseaddr \


define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/upnp-1.8 $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{ixml-1.8,upnp-1.8}.{a,so*,la} $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libupnp-1.8.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libupnp-1.8/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib{ixml-1.8,upnp-1.8}.so.* $(1)/usr/lib/
endef

define Package/libupnp-1.8-sample/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/upnp/sample/.libs/* $(1)/usr/bin
	$(INSTALL_DIR) $(1)/etc/upnp-tvdevice/web
	$(INSTALL_DATA) $(PKG_BUILD_DIR)/upnp/sample/web/* $(1)/etc/upnp-tvdevice
endef

$(eval $(call BuildPackage,libupnp-1.8))
$(eval $(call BuildPackage,libupnp-1.8-sample))
