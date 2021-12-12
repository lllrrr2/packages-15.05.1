#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-openpyxl
PKG_VERSION:=3.0.8
PKG_RELEASE:=1

PKG_SOURCE:=openpyxl-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/1f/fd/b8d831d0cc949c454b1f02d26b4cd5bafaf71e959a68f326909291fb2089/
PKG_MD5SUM:=bdd7bb6f834598b24b26733e819c5162

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-openpyxl-$(PKG_VERSION)

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-openpyxl
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:= library to read/write Excel 2010 xlsx/xlsm/xltx/xltm files.
  URL:=https://foss.heptapod.net/openpyxl/openpyxl
  DEPENDS:= \
	  +python3-light \
	  +python3-decimal \
	  +python3-xml \
	  +python3-et_xmlfile
endef

define Package/python3-openpyxl/description
  Topenpyxl is a Python library to read/write Excel 2010 xlsx/xlsm/xltx/xltm files.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-openpyxl/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-openpyxl))
