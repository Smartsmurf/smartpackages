#
# Copyright (C) 2006-2014 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=taglib
PKG_VERSION:=1.11.1
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://taglib.org/releases
PKG_HASH:=b6d1a5a610aae6ff39d93de5efd0fdc787aa9e9dc1e7026fa4c961b26563526b
PKG_MAINTAINER:=Andreas Fiedler <smartsmurf@shared-files.de>

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DBUILD_SHARED_LIBS=ON

define Package/libtag
  SECTION:=libs
  CATEGORY:=Libraries
  URL:=http://http://taglib.org/
  TITLE:=TagLib Audio Meta-Data Library
  DEPENDS:=+libstdcpp +zlib
  MENU:=1
endef

define Package/libtag/description
TagLib is a library for reading and editing the meta-data of several popular audio formats. Currently it supports both ID3v1 and ID3v2 for MP3 files, Ogg Vorbis comments and ID3 tags and Vorbis comments in FLAC, MPC, Speex, WavPack, TrueAudio, WAV, AIFF, MP4 and ASF files.
endef


define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/taglib $(1)/usr/include/
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtag.so* $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/taglib*.pc $(1)/usr/lib/pkgconfig/
endef

define Package/libtag/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtag.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libtag))

