#
# Copyright (C) 2006-2015 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=mutt
PKG_VERSION:=2.1.5
PKG_RELEASE:=$(AUTORELEASE)

PKG_SOURCE_URL:=https://bitbucket.org/mutt/mutt/downloads/ \
		http://ftp.mutt.org/pub/mutt/
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz
PKG_MD5SUM:=7e63bbbe65a4aae8d0ab76f71be88c7b

PKG_MAINTAINER:=Phil Eichinger <phil@zankapfel.net>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=GPL
PKG_CPE_ID:=cpe:/a:mutt:mutt

PKG_FIXUP:=autoreconf
PKG_INSTALL:=1
PKG_BUILD_PARALLEL:=1
PKG_CONFIG_DEPENDS:= \
	CONFIG_MUTT_POP \
	CONFIG_MUTT_IMAP \
	CONFIG_MUTT_SMTP \
	CONFIG_MUTT_HCACHE \
	CONFIG_MUTT_SASL \
	CONFIG_MUTT_GNUTLS \
	CONFIG_MUTT_OPENSSL

include $(INCLUDE_DIR)/package.mk

define Package/mutt
  SECTION:=mail
  CATEGORY:=Mail
  DEPENDS:=+MUTT_HCACHE:libgdbm +MUTT_GNUTLS:libgnutls +MUTT_OPENSSL:libopenssl +libncursesw +MUTT_SASL:libsasl2 +terminfo +zlib
  TITLE:=Console mail client
  URL:=http://www.mutt.org/
  MENU:=1
endef

define Package/mutt/description
	Mutt is a small but very powerful text-based mail client for Unix
	operating systems.
endef

ifdef CONFIG_USE_UCLIBC
  TARGET_CFLAGS += -std=gnu99
endif

CONFIGURE_ARGS += \
	--includedir=$(PKG_BUILD_DIR)/. \
	--oldincludedir=$(PKG_BUILD_DIR)/. \
	$(if $(CONFIG_MUTT_POP),--enable-pop) \
	$(if $(CONFIG_MUTT_IMAP),--enable-imap) \
	$(if $(CONFIG_MUTT_SMTP),--enable-smtp) \
	$(if $(CONFIG_MUTT_HCACHE),--enable-hcache) \
	$(if $(CONFIG_MUTT_SASL),--with-sasl) \
	--with-mailpath=/var/mail \
	$(if $(CONFIG_MUTT_GNUTLS),--with-gnutls) \
	$(if $(CONFIG_MUTT_OPENSSL),--with-ssl) \
	--without-idn \
	--disable-doc

define Package/mutt/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mutt $(1)/usr/bin/
endef

define Package/mutt/config
  source "$(SOURCE)/Config.in"
endef

$(eval $(call BuildPackage,mutt))
