include $(TOPDIR)/rules.mk

PKG_NAME:=smartgadgets
PKG_RELEASE:=1

PKG_LICENSE:=BSD-2-Clause

PKG_MAINTAINER:=Andreas Fiedler <andreas.fiedler@gmx.net>

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=@USB_GADGET_SUPPORT +kmod-usb-gadget +kmod-usb-lib-composite
  TITLE:=Init script to create USB gadgets. Configure via usbgadgets config
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/config $(1)/etc/init.d
	$(INSTALL_CONF) ./files/usbgadget.conf $(1)/etc/config/usbgadget
	$(INSTALL_BIN) ./files/usbgadget.init $(1)/etc/init.d/usbgadget
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
