#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-ply
PKG_VERSION:=3.11
PKG_RELEASE:=1

PKG_SOURCE:=ply-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/e5/69/882ee5c9d017149285cab114ebeab373308ef0f874fcdac9beb90e0ac4da/
PKG_MD5SUM:=6465f602e656455affcd7c5734c638f8

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-ply-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-ply
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=lex and yacc for Python
  URL:=http://www.dabeaz.com/ply/
  DEPENDS:=+python3-light
endef

define Package/python3-ply/description
PLY is a 100% Python implementation of the common parsing tools lex
and yacc.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-ply/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-ply))
