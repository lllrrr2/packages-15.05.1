#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-jdcal
PKG_VERSION:=1.4.1
PKG_RELEASE:=1

PKG_SOURCE:=jdcal-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/7b/b0/fa20fce23e9c3b55b640e629cb5edf32a85e6af3cf7af599940eb0c753fe/
PKG_MD5SUM:=e05bdb60fa80f25bc60e73e0c6b7c5dc

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-jdcal-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python3/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python3/python3-package.mk

define Package/python3-jdcal
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=jdcal
  URL:=https://github.com/phn/jdcal
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-jdcal/description
  This module contains functions for converting between Julian dates and calendar dates.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-jdcal/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-jdcal))
