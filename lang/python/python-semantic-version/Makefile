#
# Copyright (C) 2023 Andreas Fiedler
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-semantic-version
PKG_VERSION:=2.10.0
PKG_RELEASE:=1

PYPI_NAME:=semantic_version
PKG_HASH:=bdabb6d336998cbb378d4b9db3a4b56a1e3235701dc05ea2690d9a997ed5041c

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Andreas Fiedler <andreas.fiedler@gmx.net>

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/host-build.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk

PKG_HOST_ONLY:=1
HOST_BUILD_DEPENDS:=python3/host python-build/host python-installer/host python-wheel/host

define Package/python3-semantic-version
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://pypi.org/project/semantic-version/
  TITLE:=A library implementing the 'SemVer' scheme.
  DEPENDS:=+python3-light
  BUILDONLY:=1
endef

define Package/python3-semantic-version/description
Build a library implementing the 'SemVer' scheme.
Normally this module is required on host side only.
endef

$(eval $(call Py3Package,python3-semantic-version))
$(eval $(call BuildPackage,python3-semantic-version))
$(eval $(call BuildPackage,python3-semantic-version-src))
$(eval $(call HostBuild))
