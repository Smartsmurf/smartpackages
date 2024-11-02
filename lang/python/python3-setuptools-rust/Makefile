#
# Copyright (C) 2023 Andreas Fiedler
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-setuptools-rust
PKG_VERSION:=1.7.0
PKG_RELEASE:=1

PYPI_NAME:=setuptools-rust
PKG_HASH:=c7100999948235a38ae7e555fe199aa66c253dc384b125f5d85473bf81eae3a3

PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Andreas Fiedler <andreas.fiedler@gmx.net>

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
#include $(INCLUDE_DIR)/package.mk
#include $(INCLUDE_DIR)/host-build.mk
#include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-host-build.mk
include $(TOPDIR)/feeds/packages/lang/rust/rust-values.mk

PKG_HOST_ONLY:=1
HOST_BUILD_DEPENDS:=python3/host python-build/host python-installer/host python-wheel/host python-semantic-version/host rust/host

define Package/python3-setuptools-rust
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Python
  URL:=https://github.com/PyO3/setuptools-rust
  TITLE:=Setuptools plugin for Rust extensions
  DEPENDS:=+python3-setuptools $(RUST_ARCH_DEPENDS)
  BUILDONLY:=1
endef

define Package/python3-setuptools-rust/description
Compile and distribute Python extensions written in Rust as easily as if they were written in C.
Normally this plugin is required on host side only.
endef

$(eval $(call RustBinHostBuild))
$(eval $(call HostBuild))
$(eval $(call Py3Package,python3-setuptools-rust))
$(eval $(call BuildPackage,python3-setuptools-rust))

