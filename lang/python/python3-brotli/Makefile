#
# Copyright (C) 2019-2020 CZ.NIC, z. s. p. o. (https://www.nic.cz/)
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-brotli
PKG_VERSION:=1.0.9
PKG_RELEASE:=1

PYPI_NAME:=Brotli
PYPI_SOURCE_EXT:=zip
PKG_HASH:=4d1b810aa0ed773f81dceda2cc7b403d01057458730e309856356d4ef4188438

PKG_MAINTAINER:=Andreas Fiedler <andreas.fiedler@gmx.net>
PKG_LICENSE:=BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-brotli
    SECTION:=lang
    CATEGORY:=Languages
    SUBMENU:=Python
    TITLE:=Brotli lossless compression algorithm
    URL:=https://babel.pocoo.org/en/latest/
    DEPENDS:= \
        +libstdcpp \
        +python3-light
endef

$(eval $(call Py3Package,python3-brotli))
$(eval $(call BuildPackage,python3-brotli))
$(eval $(call BuildPackage,python3-brotli-src))
