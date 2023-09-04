#
# Copyright (C) 2015-2023 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python-cryptography-3x
PKG_VERSION:=39.0.2
PKG_RELEASE:=2

PYPI_NAME:=cryptography
PKG_HASH:=bc5b871e977c8ee5a1bbc42fa8d19bcc08baf0c51cbf1586b0e87a2694dde42f

PKG_MAINTAINER:=Andreas Fiedler <andreas.fiedler@gmx.net>
PKG_LICENSE:=Apache-2.0 BSD-3-Clause
PKG_LICENSE_FILES:=LICENSE.APACHE LICENSE.BSD

PKG_BUILD_DEPENDS:=libffi/host python-cffi/host  # cffi>=1.12

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-cryptography3x
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  TITLE:=Cryptographic recipes and primitives
  URL:=https://github.com/pyca/cryptography
  DEPENDS:= \
      +libopenssl \
      +python3-light \
      +python3-email \
      +python3-openssl \
      +python3-urllib \
      +python3-cffi \
      +python3-six
endef

define Package/python3-cryptography3x/description
cryptography 3x.x.x is a package which provides cryptographic recipes and
primitives to Python developers.  Our goal is for it to be your "cryptographic
standard library". It supports Python 3.3+, and PyPy 2.6+.
endef

$(eval $(call Py3Package,python3-cryptography3x))
$(eval $(call BuildPackage,python3-cryptography3x))
$(eval $(call BuildPackage,python3-cryptography3x-src))
