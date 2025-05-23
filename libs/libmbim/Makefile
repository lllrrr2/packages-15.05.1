#
# Copyright (C) 2016 Velocloud Inc.
# Copyright (C) 2016 Aleksander Morgado <aleksander@aleksander.es>
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libmbim
PKG_VERSION:=1.26.2
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.xz
PKG_SOURCE_URL:=https://www.freedesktop.org/software/libmbim
PKG_MD5SUM:=8893edbfd16e1198c018277cd2ad487e

PKG_MAINTAINER:=Nicholas Smith <nicholas@nbembedded.com>

PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk

CONFIGURE_ARGS += \
	--disable-static \
	--disable-gtk-doc \
	--disable-gtk-doc-html \
	--disable-gtk-doc-pdf \
	--disable-silent-rules

define Package/libmbim
  SECTION:=libs
  CATEGORY:=Libraries
  DEPENDS:=+glib2
  TITLE:=Helper library and utils to talk to MBIM enabled modems
  URL:=https://www.freedesktop.org/wiki/Software/libmbim
  LICENSE:=LGPL-2.0-or-later
  LICENSE_FILES:=COPYING.LIB
endef

define Package/libmbim/description
  Helper library to talk to MBIM enabled modems.
  Add mbim-utils for extra utilities.
endef

define Package/mbim-utils
  SECTION:=utils
  CATEGORY:=Utilities
  DEPENDS:=+libmbim
  TITLE:=Utilities to talk to MBIM enabled modems
  URL:=https://www.freedesktop.org/wiki/Software/libmbim
  LICENSE:=GPL-2.0-or-later
  LICENSE_FILES:=COPYING
endef

CONFIGURE_ARGS += \
	--without-udev-base-dir

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/include/libmbim-glib \
		$(1)/usr/include/

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libmbim*.so* \
		$(1)/usr/lib/

	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/pkgconfig/mbim-glib.pc \
		$(1)/usr/lib/pkgconfig
endef

define Package/libmbim/install
	$(INSTALL_DIR) $(1)/usr/lib

	$(CP) \
		$(PKG_INSTALL_DIR)/usr/lib/libmbim*.so.* \
		$(1)/usr/lib/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/lib/mbim-proxy $(1)/usr/lib/
endef

define Package/mbim-utils/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mbimcli $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mbim-network $(1)/usr/bin/
endef

$(eval $(call BuildPackage,libmbim))
$(eval $(call BuildPackage,mbim-utils))
