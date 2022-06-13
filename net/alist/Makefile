#
# Copyright (C) 2015-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v3.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=alist
PKG_VERSION:=2.5.1
PKG_WEB_VERSION:=2.5.0
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/Xhofe/alist/tar.gz/v$(PKG_VERSION)?
PKG_MD5SUM:=599463ad9758b85b78ec82174ab2b767

PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILE:=LICENSE
PKG_MAINTAINER:=sbwml <admin@cooluc.com>

define Download/$(PKG_NAME)-web
  FILE:=$(PKG_NAME)-web-$(PKG_WEB_VERSION).tar.gz
  URL_FILE:=dist.tar.gz
  URL:=https://github.com/alist-org/alist-web/releases/download/$(PKG_WEB_VERSION)/
  MD5SUM:=19e6710e7d9f970b068d6039c9dc2db8
endef

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_USE_MIPS16:=0

GO_PKG:=github.com/Xhofe/alist
ALIST_PKG:=github.com/Xhofe/alist/conf
GO_PKG_LDFLAGS:=-w -s
GO_PKG_LDFLAGS_X:=$(ALIST_PKG).GitTag=v$(PKG_VERSION)-$(ARCH)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/golang/golang-package.mk

define Package/$(PKG_NAME)/Default
	SECTION:=net
	CATEGORY:=Network
	SUBMENU:=Web Servers/Proxies
	TITLE:=Alist - Main program
	URL:=https://alist-doc.nn.ci/
endef

define Package/$(PKG_NAME)/description
  A file list program that supports multiple storage
endef

define Package/$(PKG_NAME)
	$(call Package/alist/Default)
	DEPENDS:=$(GO_ARCH_DEPENDS) +libpthread
endef

define Package/$(PKG_NAME)/conffiles
/etc/alist/
/etc/config/alist
endef

define Package/$(PKG_NAME)/postinst
#!/bin/sh
if [ -z "$${IPKG_INSTROOT}" ]; then
	[ -f /etc/uci-defaults/alist ] && /etc/uci-defaults/alist && rm -f /etc/uci-defaults/alist
fi
endef

define Build/Prepare
	$(call Build/Prepare/Default)
endef

define Build/Compile
	( \
		pushd $(PKG_BUILD_DIR) ; \
			tar -zxvf $(DL_DIR)/$(PKG_NAME)-web-$(PKG_WEB_VERSION).tar.gz -C ./ ; \
			cp -ax dist/* ./public/ ; \
			cp -ax $(CURDIR)/files/assets/* ./public/assets/ ; \
			rm -rf dist/ ; \
		popd ; \
		$(call GoPackage/Build/Compile) ; \
	)
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/etc/alist $(1)/etc/config $(1)/etc/init.d $(1)/etc/uci-defaults
	$(call GoPackage/Package/Install/Bin,$(1))
	$(INSTALL_CONF) ./files/alist.config $(1)/etc/config/alist
	$(INSTALL_BIN) ./files/alist.init $(1)/etc/init.d/alist
	$(INSTALL_BIN) ./files/alist.uci-default $(1)/etc/uci-defaults/alist
	$(INSTALL_CONF) ./files/data.db $(1)/etc/alist/data.db
endef

$(eval $(call Download,$(PKG_NAME)-web))
$(eval $(call GoBinPackage,$(PKG_NAME)))
$(eval $(call BuildPackage,$(PKG_NAME)))
