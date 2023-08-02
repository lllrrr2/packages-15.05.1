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
PKG_VERSION:=2.2.1
PKG_RELEASE:=1

PYPI_NAME:=soupsieve
PKG_MD5SUM:=73ff6ce22ba973fe2d47197834e0f728

include $(TOPDIR)/feeds/packages/lang/python/pypi.mk
include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

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

$(eval $(call Py3Package,python3-soupsieve))
$(eval $(call BuildPackage,python3-soupsieve))
$(eval $(call BuildPackage,python3-soupsieve-src))
