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

PKG_NAME:=python3-six
PKG_VERSION:=1.15.0
PKG_RELEASE:=1

PKG_SOURCE:=six-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/6b/34/415834bfdafca3c5f451532e8a8d9ba89a21c9743a0c59fbd0205c7f9426/
PKG_MD5SUM:=9f90a0eaa0ea7747fda01ca79d21ebcb

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-six-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python3/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-six
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=Python 2 and 3 compatibility library
  URL:=https://six.readthedocs.io/
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-six/description
 Six is a Python 2 and 3 compatibility library. It provides utility
 functions for smoothing over the differences between the Python ve
 rsions with the goal of writing Python code that is compatible on 
 both Python versions.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-six/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-six))
