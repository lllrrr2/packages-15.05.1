#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-qrcode
PKG_VERSION:=7.3.1
PKG_RELEASE:=1

PKG_SOURCE:=qrcode-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/94/9f/31f33cdf3cf8f98e64c42582fb82f39ca718264df61957f28b0bbb09b134/
PKG_MD5SUM:=124103c685e96ba3b7a1616760f31c11

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-qrcode-$(PKG_VERSION)

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)

define Package/python3-qrcode
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:= Pure python QR Code generator
  URL:=https://github.com/lincolnloop/python-qrcode
  DEPENDS:= \
	  +python3-light \
	  +python3-pillow
endef

define Package/python3-qrcode/description
  A Quick Response code is a two-dimensional pictographic code used for
 its fast readability and comparatively large storage capacity.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-qrcode/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-qrcode))
