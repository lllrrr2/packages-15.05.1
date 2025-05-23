#
# Copyright (C) 2016 Velocloud Inc.
# Copyright (C) 2016 Aleksander Morgado <aleksander@aleksander.es>
#
# This is free software, licensed under the GNU General Public License v2.
#

include $(TOPDIR)/rules.mk

PKG_NAME:=modemmanager
PKG_SOURCE_VERSION:=1.18.8
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://gitlab.freedesktop.org/mobile-broadband/ModemManager.git
PKG_MD5SUM:=4ab84643d1a3cff27edef32a277c54fd

PKG_MAINTAINER:=Nicholas Smith <nicholas@nbembedded.com>
PKG_LICENSE:=GPL-2.0-or-later
PKG_LICENSE_FILES:=COPYING

PKG_BUILD_DEPENDS:=glib2/host libxslt/host

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/nls.mk
include $(INCLUDE_DIR)/meson.mk

TARGET_CFLAGS += -ffunction-sections -fdata-sections -fno-merge-all-constants -fmerge-constants
TARGET_LDFLAGS += -Wl,--gc-sections

define Package/modemmanager/config
  source "$(SOURCE)/Config.in"
endef

define Package/modemmanager
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Control utility for any kind of mobile broadband modem
  URL:=https://www.freedesktop.org/wiki/Software/ModemManager
  DEPENDS:= \
	$(INTL_DEPENDS) \
	+glib2 \
	+dbus \
	+ppp \
	+MODEMMANAGER_WITH_MBIM:libmbim \
	+MODEMMANAGER_WITH_QMI:libqmi
endef

define Package/modemmanager/description
  ModemManager is a D-Bus-activated service which allows controlling mobile
  broadband modems. Add kernel modules for your modems as needed.
  Select Utilities/usb-modeswitch if needed.
endef

MESON_ARGS += \
	-Dudev=false \
	-Dudevdir=/lib/udev \
	-Dsystemdsystemunitdir=no \
	-Dsystemd_suspend_resume=false \
	-Dsystemd_journal=false \
	-Dpolkit=no \
	-Dintrospection=false \
	-Dman=false \
	-Dbash_completion=false \
	-Db_lto=true \
	-Dmbim=$(if $(CONFIG_MODEMMANAGER_WITH_MBIM),true,false) \
	-Dqmi=$(if $(CONFIG_MODEMMANAGER_WITH_QMI),true,false) \
	-Dqrtr=false \
	-Dat_command_via_dbus=$(if $(CONFIG_MODEMMANAGER_WITH_AT_COMMAND_VIA_DBUS),true,false)

define Build/InstallDev
	$(INSTALL_DIR) $(1)/usr/include/ModemManager
	$(CP) $(PKG_INSTALL_DIR)/usr/include/ModemManager/*.h $(1)/usr/include/ModemManager
	$(INSTALL_DIR) $(1)/usr/include/libmm-glib
	$(CP) $(PKG_INSTALL_DIR)/usr/include/libmm-glib/*.h $(1)/usr/include/libmm-glib
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libmm-glib.so* $(1)/usr/lib
	$(INSTALL_DIR) $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/ModemManager.pc $(1)/usr/lib/pkgconfig
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/pkgconfig/mm-glib.pc $(1)/usr/lib/pkgconfig
endef

define Package/modemmanager/install
	$(INSTALL_DIR) $(1)/lib/udev/rules.d
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/lib/udev/rules.d/*.rules $(1)/lib/udev/rules.d

	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/sbin/ModemManager $(1)/usr/sbin
	$(INSTALL_BIN) ./files/usr/sbin/ModemManager-wrapper $(1)/usr/sbin

	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/mmcli $(1)/usr/bin

	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libmm-glib.so.* $(1)/usr/lib

	$(INSTALL_DIR) $(1)/usr/lib/ModemManager
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/ModemManager/libmm-shared-*.so* $(1)/usr/lib/ModemManager
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/ModemManager/libmm-plugin-*.so* $(1)/usr/lib/ModemManager

	$(INSTALL_DIR) $(1)/usr/lib/ModemManager/connection.d
	$(INSTALL_BIN) ./files/10-report-down $(1)/usr/lib/ModemManager/connection.d

	$(INSTALL_DIR) $(1)/etc/dbus-1/system.d
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/etc/dbus-1/system.d/org.freedesktop.ModemManager1.conf $(1)/etc/dbus-1/system.d

	$(INSTALL_DIR) $(1)/usr/share/dbus-1/system-services
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/dbus-1/system-services/org.freedesktop.ModemManager1.service $(1)/usr/share/dbus-1/system-services

	$(INSTALL_DIR) $(1)/usr/share/ModemManager
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/ModemManager/*.conf $(1)/usr/share/ModemManager
	$(INSTALL_DATA) ./files/modemmanager.common $(1)/usr/share/ModemManager

	$(INSTALL_DIR) $(1)/usr/share/ModemManager/fcc-unlock.available.d
	$(INSTALL_DATA) $(PKG_INSTALL_DIR)/usr/share/ModemManager/fcc-unlock.available.d/* $(1)/usr/share/ModemManager/fcc-unlock.available.d

	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/modemmanager.init $(1)/etc/init.d/modemmanager

	$(INSTALL_DIR) $(1)/etc/hotplug.d/usb
	$(INSTALL_DATA) ./files/25-modemmanager-usb $(1)/etc/hotplug.d/usb

	$(INSTALL_DIR) $(1)/etc/hotplug.d/net
	$(INSTALL_DATA) ./files/25-modemmanager-net $(1)/etc/hotplug.d/net

	$(INSTALL_DIR) $(1)/etc/hotplug.d/tty
	$(INSTALL_DATA) ./files/25-modemmanager-tty $(1)/etc/hotplug.d/tty

	$(INSTALL_DIR) $(1)/etc/hotplug.d/wwan
	$(INSTALL_DATA) ./files/25-modemmanager-wwan $(1)/etc/hotplug.d/wwan

	$(INSTALL_DIR) $(1)/lib/netifd/proto
	$(INSTALL_BIN) ./files/modemmanager.proto $(1)/lib/netifd/proto/modemmanager.sh
endef

$(eval $(call BuildPackage,modemmanager))
