#
# Copyright (C) 2007-2016 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=python3-cffi
PKG_VERSION:=1.13.2
PKG_RELEASE:=1

PKG_SOURCE:=cffi-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=https://files.pythonhosted.org/packages/2d/bf/960e5a422db3ac1a5e612cb35ca436c3fc985ed4b7ed13a1b4879006f450/
PKG_MD5SUM:=652203cf99faa254efff7fab23c2f3a2

PKG_BUILD_DIR:=$(BUILD_DIR)/python3-cffi-$(PKG_VERSION)

PKG_BUILD_DEPENDS:=libffi/host

include $(INCLUDE_DIR)/package.mk
include $(TOPDIR)/feeds/packages/lang/python/python3-package.mk

PKG_UNPACK:=$(HOST_TAR) -C $(PKG_BUILD_DIR) --strip-components=1 -xzf $(DL_DIR)/$(PKG_SOURCE)


define Package/python3-cffi
  SUBMENU:=Python
  SECTION:=lang
  CATEGORY:=Languages
  TITLE:=C Foreign Function Interface
  URL:=https://cffi.readthedocs.org/
  DEPENDS:= \
      +libffi \
      +python3-light \
      +python3-pycparser
endef

define Package/python3-cffi/description
Foreign Function Interface for Python calling C code.
endef

define Build/Compile
	$(call Build/Compile/Py3Mod,., \
		install --prefix="/usr" --root="$(PKG_INSTALL_DIR)", \
	)
endef

define Package/python3-cffi/install
	$(INSTALL_DIR) $(1)$(PYTHON3_PKG_DIR)
	$(CP) \
	    $(PKG_INSTALL_DIR)$(PYTHON3_PKG_DIR)/* \
	    $(1)$(PYTHON3_PKG_DIR)
endef

$(eval $(call BuildPackage,python3-cffi))
