#
# Copyright (C) 2006-2018 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=tiff
PKG_VERSION:=4.0.9
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_SOURCE_URL:=http://download.osgeo.org/libtiff
PKG_MD5SUM:=54bad211279cc93eb4fca31ba9bfdc79

PKG_FIXUP:=autoreconf
PKG_REMOVE_FILES:=autogen.sh aclocal.m4

PKG_LICENSE:=BSD
PKG_LICENSE_FILES:=COPYRIGHT

PKG_INSTALL:=1

PKG_CONFIG_DEPENDS:=CONFIG_PACKAGE_libtiffxx

include $(INCLUDE_DIR)/uclibc++.mk
include $(INCLUDE_DIR)/package.mk

define Package/tiff/Default
  TITLE:=TIFF
  URL:=http://www.remotesensing.org/libtiff/
  MAINTAINER:=Jiri Slachta <jiri@slachta.eu>
endef

define Package/libtiff
$(call Package/tiff/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE+= library
  DEPENDS:=+zlib +libjpeg-turbo
endef

define Package/libtiff-dev
  SECTION:=devel
  CATEGORY:=Development
  SUBMENU:=Libraries
  DEPENDS:=libtiff
  TITLE:=Development files for the libtiff library
endef

define Package/libtiffxx
$(call Package/tiff/Default)
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE+= library(c++ bindings)
  DEPENDS:=+libtiff $(CXX_DEPENDS)
endef

define Package/tiff-utils
$(call Package/tiff/Default)
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE+= utilities
  DEPENDS:=+libtiff
endef

TARGET_CFLAGS += $(FPIC)

define Build/Configure
	$(call Build/Configure/Default, \
		$(if $(CONFIG_PACKAGE_libtiffxx), \
			--enable-cxx, \
			--disable-cxx \
		) \
		--disable-lzma \
		--enable-ccitt \
		--enable-packbits \
		--enable-lzw \
		--enable-thunder \
		--enable-next \
		--enable-logluv \
		--enable-mdi \
		--enable-zlib \
		--enable-jpeg \
		--disable-old-jpeg \
		--disable-jbig \
		--without-x \
	)
endef

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/{lib,include}
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/lib* $(1)/usr/lib/
	$(CP) $(PKG_INSTALL_DIR)/usr/include/* $(1)/usr/include/
endef

define Package/libtiff/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtiff.so.* $(1)/usr/lib/
endef

define Package/libtiff-dev/install
	$(INSTALL_DIR) $(1)/usr/include
	$(CP) $(PKG_INSTALL_DIR)/usr/include/*.h $(1)/usr/include
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtiff.a $(1)/usr/lib/
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/libtiff-4.pc \
	  $(1)/usr/lib/pkgconfig
endef

define Package/libtiffxx/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libtiffxx.so.* $(1)/usr/lib/
endef

define Package/tiff-utils/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/* $(1)/usr/bin/
endef

$(eval $(call BuildPackage,libtiff))
$(eval $(call BuildPackage,libtiff-dev))
$(eval $(call BuildPackage,libtiffxx))
$(eval $(call BuildPackage,tiff-utils))
