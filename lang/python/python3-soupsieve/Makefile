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

PKG_NAME:=python3-soupsieve
PKG_VERSION:=2.1
PKG_RELEASE:=1

PKG_SOURCE:=soupsieve-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/58/5d/445e21e92345848305eecf473338e9ec7ed8905b99ea78415042060127fc
PKG_MD5SUM:=0194a795d6073b4336e7b95e42e5292f

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-soupsieve-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-soupsieve
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Soup Sieve is a CSS selector library
  URL:=https://github.com/facelessuser/soupsieve
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-soupsieve/description
 Soup Sieve is a CSS selector library designed to be used with Beautiful Soup 4.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-soupsieve/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-soupsieve))
