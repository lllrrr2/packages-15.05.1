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

PKG_NAME:=python3-beautifulsoup4
PKG_VERSION:=4.9.3
PKG_RELEASE:=1

PKG_SOURCE:=beautifulsoup4-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/6b/c3/d31704ae558dcca862e4ee8e8388f357af6c9d9acb0cad4ba0fbbd350d9a
PKG_MD5SUM:=57fd468ae3eb055f6871106e8f7813e2

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-beautifulsoup4-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-beautifulsoup4
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=library that makes it easy to scrape information from web pages. 
  URL:=https://www.crummy.com/software/BeautifulSoup/
  DEPENDS:= \
	  +python3-light \
	  +python3-soupsieve
endef

define Package/python3-beautifulsoup4/description
Beautiful Soup is a library that makes it easy to scrape information from web pages. 
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-beautifulsoup4/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-beautifulsoup4))
