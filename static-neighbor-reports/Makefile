#
# Copyright (C) 2020 OpenWrt.org
#
include $(TOPDIR)/rules.mk

PKG_NAME:=static-neighbor-reports
PKG_VERSION:=1
PKG_RELEASE:=1

PKG_MAINTAINER:=David Bauer <mail@david-bauer.net
PKG_LICENSE:=GPL-2.0

include $(INCLUDE_DIR)/package.mk

Build/Compile=

define Package/static-neighbor-reports/Default
endef

define Package/static-neighbor-reports
  SECTION:=net
  CATEGORY:=Network
  TITLE:=Configure static 802.11k neighbor reports
  PKGARCH:=all
  DEPENDS:=+libuci-lua +lua +libubus-lua
endef

define Package/static-neighbor-reports/install
	$(INSTALL_DIR) $(1)/etc/config
	$(INSTALL_CONF) ./files/static-neighbor-report.conf $(1)/etc/config/static-neighbor-report
	$(INSTALL_DIR) $(1)/etc/hotplug.d/net
	$(INSTALL_DATA) ./files/reload-neighbor-reports.hotplug $(1)/etc/hotplug.d/net/reload-neighbor-reports
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/static-neighbor-reports.init $(1)/etc/init.d/static-neighbor-reports
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) ./files/reload-neighbor-reports.lua $(1)/usr/bin/reload-neighbor-reports
endef

define Package/static-neighbor-reports/conffiles
/etc/config/static-neighbor-reports
endef

define Package/static-neighbor-reports/description
  Allows to configure static neighbor reports for hostapd interfaces.

  These neighbor reports are avilable to clients using IEEE 802.11k.
endef

$(eval $(call BuildPackage,static-neighbor-reports))
