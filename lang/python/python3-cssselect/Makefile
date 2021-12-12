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

PKG_NAME:=python3-cssselect
PKG_VERSION:=1.1.0
PKG_RELEASE:=1

PKG_SOURCE:=cssselect-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/70/54/37630f6eb2c214cdee2ae56b7287394c8aa2f3bafb8b4eb8c3791aae7a14/
PKG_MD5SUM:=fa57704c1cb66cc8e537b782bd6b227e

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-cssselect-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-cssselect
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Cssselect
  URL:=https://libraries.io/pypi/cssselect
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-cssselect/description
 Cssselect parses CSS3 Selectors and translate them to XPath 1.0 expressions.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-cssselect/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-cssselect))
