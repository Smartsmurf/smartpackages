include $(TOPDIR)/rules.mk

PKG_NAME:=metasploit
PKG_VERSION:=6.4.36
PKG_RELEASE:=1

PKG_BUILD_DIR:=$(BUILD_DIR)/metasploit-framework-$(PKG_VERSION)
PKG_SOURCE:=$(PKG_NAME).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/rapid7/metasploit-framework/tar.gz/$(PKG_VERSION)?
PKG_HASH:=5249bf094994ab4fa69d325fff30676b804af71aa7e5834c9e469454dcc32a80

PKG_LICENSE:=BSD-3-Clause

PKG_BUILD_DEPENDS:=ruby/host

include $(INCLUDE_DIR)/package.mk

#define Package/qrtr-lib
#	SECTION:=libs
#	CATEGORY:=Libraries
#	TITLE:=Userspace reference for net/qrtr in the Linux kernel
#	URL:=https://github.com/andersson/qrtr
#endef

define Package/metasploit
	SECTION:=base
	CATEGORY:=Network
	DEPENDS:=+ruby +ruby-json +ruby-bundler +ruby-dev +libpcap +libpqxx +zlib +libsqlite3
	TITLE:=The worlds most used penetration testing framework
	URL:=https://github.com/rapid7/metasploit-framework/
endef

define Package/$(PKG_NAME)/description
  The Metasploit Framework is a tool for developing and executing exploit code against a remote target machine.
  Knowledge is power, especially when it's shared. A collaboration between the open source community and Rapid7,
  Metasploit helps security teams do more than just verify vulnerabilities, manage security assessments,
  and improve security awareness; it empowers and arms defenders to always stay one step (or two) ahead of the game.
endef

define Build/Prepare
	$(call Build/Prepare/Default)
endef

define Build/Compile
	cd $(PKG_BUILD_DIR) && \
		gem install bundler && \
		bundle config set --local path 'vendor/bundle' && \
		bundle install -v
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/lib/metasploit-framework
	$(CP) $(PKG_BUILD_DIR)/* $(1)/usr/lib/metasploit-framework
endef

#define Build/InstallDev
#	$(INSTALL_DIR) $(1)/usr/include
#	$(CP) $(PKG_INSTALL_DIR)/usr/include/libqrtr.h $(1)/usr/include/
#	$(INSTALL_DIR) $(1)/usr/lib
#	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
#endef

#define Package/qrtr-lib/install
#	$(INSTALL_DIR) $(1)/usr/lib
#	$(CP) $(PKG_INSTALL_DIR)/usr/lib/* $(1)/usr/lib/
#endef

#define Package/qrtr/install
#	$(INSTALL_DIR) $(1)/usr/bin
#	$(CP) $(PKG_INSTALL_DIR)/usr/bin/qrtr-* $(1)/usr/bin/
#endef

#$(eval $(call BuildPackage,qrtr-lib))
$(eval $(call BuildPackage,$(PKG_NAME)))
