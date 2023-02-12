#
# Copyright (C) 2020 Project OpenWrt
# This is free software, licensed under the GNU General Public License v3.
# See /LICENSE.txt for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=filebrowser
PKG_VERSION:=2.10.0
PKG_RELEASE:=1

include $(INCLUDE_DIR)/package.mk

define Package/filebrowser
  SECTION:=utils
  CATEGORY:=Utilities
  TITLE:=Web File Browser which can be used as a middleware or standalone app.
  URL:=https://github.com/filebrowser/filebrowser
  DEPENDS:=@(TARGET_kirkwood||TARGET_armvirt||TARGET_ar71xx||TARGET_ramips||TARGET_x86_64||TARGET_x86) +libpthread
endef

define Package/filebrowser/description
  filebrowser provides a file managing interface within a specified directory
  and it can be used to upload, delete, preview, rename and edit your files.
  It allows the creation of multiple users and each user can have its own directory.
  It can be used as a standalone app or as a middleware.
endef

ifeq ($(ARCH),x86_64)
	filebrowser_ARCH:=x86_64
	PKG_MD5SUM:=c2c659d19f8117dede16b608cd1e227f
endif

ifeq ($(ARCH),i386)
	caddy_ARCH:=i386
	PKG_MD5SUM:=d2c4f83301b7dd45e03401fc974eaa70
endif

ifeq ($(ARCH),mipsel)
ifdef CONFIG_TARGET_ramips_mt7621
	filebrowser_ARCH:=mt7621
	PKG_MD5SUM:=7aa1c06d619a8e29eb227f769a0cd345
else
	filebrowser_ARCH:=mt7620
	PKG_MD5SUM:=668574b3f27d326160e1fca91347a3c9
endif
endif

ifeq ($(ARCH),mips)
	filebrowser_ARCH:=ar71xx
	PKG_MD5SUM:=0a56964b5ddf7353ef061821b85ad897
endif

ifeq ($(ARCH),arm)
ifdef CONFIG_TARGET_kirkwood
	filebrowser_ARCH:=kirkwood
	PKG_MD5SUM:=864f19ac1c35ff5d93aa826a53b8c286
else ifdef CONFIG_TARGET_armvirt
	filebrowser_ARCH:=kirkwood
	PKG_MD5SUM:=864f19ac1c35ff5d93aa826a53b8c286
endif
endif

PKG_SOURCE_URL:=https://raw.githubusercontent.com/syb999/cc-upx/master/filebrowser/$(filebrowser_ARCH)
PKG_SOURCE:=filebrowser

define Build/Prepare
	mv $(DL_DIR)/$(PKG_SOURCE) $(PKG_BUILD_DIR)
endef

define Build/Compile
endef

define Package/filebrowser/install
	$(INSTALL_DIR) $(1)/etc/config/ $(1)/etc/init.d/ $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/filebrowser $(1)/usr/bin
	$(INSTALL_CONF) ./files/filebrowser.config $(1)/etc/config/filebrowser
	$(INSTALL_BIN) ./files/filebrowser.init $(1)/etc/init.d/filebrowser
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
