#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-chardet
PKG_VERSION:=4.0.0
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/chardet/chardet
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=b3d867a7279cd438c34d9a9ba901b23d4e00d8c6
PKG_MD5SUM:=7a94399d5554ce832d48b3f191c323ac

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-chardet-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-chardet
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Universal encoding detector for Python3
  URL:=https://github.com/chardet/chardet
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-chardet/description
  Universal encoding detector for Python3.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-chardet/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-chardet))
