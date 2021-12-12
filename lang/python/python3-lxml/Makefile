#
# Copyright (C) 2007-2019 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk
#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-lxml
PKG_VERSION:=4.6.3
PKG_RELEASE:=1

PKG_SOURCE:=lxml-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/e5/21/a2e4517e3d216f0051687eea3d3317557bde68736f038a3b105ac3809247/
PKG_MD5SUM:=017f94473dcec0f9b2e9b03524398fa5

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-lxml-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-lxml
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=lxml is a Pythonic, mature binding for the libxml2 and libxslt libraries
  URL:=https://launchpad.net/lxml
  DEPENDS:= \
	  +python3-light \
	  +libxml2 \
	  +libexslt \
	  +libxslt
endef

define Package/python3-lxml/description
 lxml is a Pythonic, mature binding for the libxml2 and libxslt libraries.
 It provides safe and convenient access to these libraries using the ElementTree API.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-lxml/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-lxml))
