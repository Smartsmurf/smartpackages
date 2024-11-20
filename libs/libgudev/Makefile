#
# Copyright (C) 2020-2021 HandsomeMod Project
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.

include $(TOPDIR)/rules.mk

PKG_NAME:=libgudev
PKG_VERSION:=238
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://download-fallback.gnome.org/sources/libgudev/$(PKG_VERSION)/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_HASH:=61266ab1afc9d73dbc60a8b2af73e99d2fdff47d99544d085760e4fa667b5dd1
PKG_BUILD_DEPENDS:=glib2/host

PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/meson.mk

define Package/libgudev
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+glib2 +eudev
  TITLE:=GObject-based wrapper library for libudev
  URL:=https://wiki.gnome.org/Projects/libgudev
endef

TARGET_LDFLAGS+= -ludev 
TARGET_CFLAGS+=-I$(STAGING_DIR)/usr/include
LDFLAGS+=-L$(STAGING_DIR)/usr/lib/ -ludev 


MESON_ARGS += \
	-Dtests=disabled \
	-Dintrospection=disabled \
	-Dvapi=disabled \
	-Dgtk_doc=false


define Build/InstallDev
	$(INSTALL_DIR) \
	  $(1)/usr/include \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/include/* \
	  $(1)/usr/include/

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/{pkgconfig,*.so*} \
	  $(1)/usr/lib/
endef

define Package/libgudev/install
	$(INSTALL_DIR) \
	  $(1)/usr/lib

	$(CP) \
	  $(PKG_INSTALL_DIR)/usr/lib/*.so* \
	  $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libgudev))
