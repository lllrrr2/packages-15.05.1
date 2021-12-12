#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-xlwt
PKG_VERSION:=1.3.0
PKG_RELEASE:=1

PKG_SOURCE:=xlwt-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/06/97/56a6f56ce44578a69343449aa5a0d98eefe04085d69da539f3034e2cd5c1
PKG_MD5SUM:=4b1ca8a3cef3261f4b4dc3f138e383a8

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-xlwt-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-xlwt
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python xlwt
  URL:=https://pypi.org/project/xlwt
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-xlwt/description
 This is a library for developers to use to generate spreadsheet files 
 compatible with Microsoft Excel versions 95 to 2003.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-xlwt/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-xlwt))
