# Copyright (C) 2010-2021 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=node
PKG_VERSION:=v8
PKG_RELEASE:=

include $(INCLUDE_DIR)/package.mk

define Package/$(PKG_NAME)
  SECTION:=lang
  CATEGORY:=Languages
  SUBMENU:=Node.js-v8
  TITLE:=Node.js is a platform built on Chrome's JavaScript runtime
  URL:=https://nodejs.org/
  DEPENDS:=+libstdcpp +libopenssl +zlib +USE_UCLIBC:libpthread +USE_UCLIBC:librt
endef

define Package/$(PKG_NAME)/description
node8 for ramips and ar71xx
endef

ifeq ($(ARCH),x86_64)
	node_ARCH:=x86_64
	PKG_MD5SUM:=4e294cd6c8af22ff58b099398cefa334
endif

ifeq ($(ARCH),mipsel)
ifdef CONFIG_TARGET_ramips_mt7621
	node_ARCH:=mt7621
	PKG_MD5SUM:=459d13cb3b62798b2d153ca1f7da2efa
else
	node_ARCH:=mt7620
	PKG_MD5SUM:=f19b49e99de2a0d5bfa93dd81282a383
endif
endif

ifeq ($(ARCH),mips)
	node_ARCH:=ar71xx
	PKG_MD5SUM:=0df720e0efadf3c2c49389eb289ea0ab
endif

PKG_SOURCE_URL:=https://raw.githubusercontent.com/syb999/cc-upx/master/node/$(node_ARCH)
PKG_SOURCE:=node

define Build/Prepare
	mv $(DL_DIR)/$(PKG_SOURCE) $(PKG_BUILD_DIR)
endef

define Build/Compile
endef

define Package/$(PKG_NAME)/install
	$(INSTALL_DIR) $(1)/usr/bin/
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/node $(1)/usr/bin/node
endef

$(eval $(call BuildPackage,$(PKG_NAME)))
