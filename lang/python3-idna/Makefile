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

PKG_NAME:=python3-idna
PKG_VERSION:=2.10
PKG_RELEASE:=1

PKG_SOURCE_URL:=https://github.com/kjd/idna
PKG_SOURCE_PROTO:=git
PKG_SOURCE_VERSION:=e5c11dbcd8dd32bb048b4dbdd344b49d18ecdf45
PKG_MD5SUM:=a802847c76a831674cbad80ce3c6ccea

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-idna-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python3/python3-package.mk

define Package/python3-idna
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=IDNA library
  URL:=https://github.com/kjd/idna
  DEPENDS:= \
	  +python3-light  \
	  +python3-codecs
endef

define Package/python3-idna/description
A library to support the Internationalised Domain Names in Applications
(IDNA) protocol as specified in RFC 5891. This version of the protocol
is often referred to as "IDNA2008" and can produce different results
from the earlier standard from 2003.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-idna/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-idna))
