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
PKG_VERSION:=4.6.2
PKG_RELEASE:=1

PKG_SOURCE:=lxml-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/db/f7/43fecb94d66959c1e23aa53d6161231dca0e93ec500224cf31b3c4073e37/
PKG_MD5SUM:=2e39c6e17d61f61e5be68fd328ba6a51

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-lxml-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python3/python3-package.mk

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
