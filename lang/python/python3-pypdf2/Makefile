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

PKG_NAME:=python3-pypdf2
PKG_VERSION:=1.26.0
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/mstamy2/PyPDF2
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=18a2627adac13124d4122c8b92aaa863ccfb8c29
PKG_MD5SUM:=1a591f6e5a582b9556986dc542b24782

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-pypdf2-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

define Package/python3-pypdf2
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=pure-python PDF library
  URL:=https://github.com/mstamy2/PyPDF2
  DEPENDS:= \
	  +python3-light
endef

define Package/python3-pypdf2/description
 PyPDF2 is a pure-python PDF library capable of splitting, merging together,
 cropping, and transforming the pages of PDF files. It can also add custom
 data, viewing options, and passwords to PDF files. It can retrieve text 
 and metadata from PDFs as well as merge entire files together.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-pypdf2/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-pypdf2))
