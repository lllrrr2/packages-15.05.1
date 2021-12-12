#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-docx
PKG_VERSION:=0.8.11
PKG_RELEASE:=1

PKG_SOURCE:=python-docx-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/8b/a0/52729ce4aa026f31b74cc877be1d11e4ddeaa361dc7aebec148171644b33/
PKG_MD5SUM:=231baf33ba280d3d751ce50d48872a1e

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-docx-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python3/python3-package.mk

define Package/python3-docx
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:= python-docx is a Python library for creating and updating Microsoft Word (.docx) files.
  URL:=https://github.com/python-openxml/python-docx
  DEPENDS:= \
	  +python3-light \
	  +python3-lxml
endef

define Package/python3-docx/description
  python-docx is a Python library for creating and updating Microsoft Word (.docx) files.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-docx/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-docx))
