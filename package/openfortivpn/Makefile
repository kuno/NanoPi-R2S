#
# Copyright (C) 2016 Ralf Schlatterbeck Open Source Consulting
# This Software is under the GNU General Public License, Version 3.
# See LICENSE of original package
#

include $(TOPDIR)/rules.mk

PKG_NAME:=openfortivpn
PKG_VERSION:=1.6.0
PKG_RELEASE:=1.0
PKG_MAINTAINER:=Ralf Schlatterbeck <rsc@runtux.com>
PKG_LICENSE:=GPL-3.0
PKG_LICENSE_FILES:=LICENSE

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git@github.com:adrienverge/openfortivpn.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=cde9d6
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tar.gz

PKG_FIXUP:=autoreconf
PKG_BUILD_DIR:=$(BUILD_DIR)/$(PKG_NAME)-$(PKG_VERSION)
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/openfortivpn
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=VPN
  TITLE:=A VPN for Fortinet Servers
  URL:=https://github.com/adrienverge/openfortivpn
  DEPENDS:=+kmod-tun +libopenssl +ppp
endef

CONFIGURE_ARGS+= \
    --prefix=/usr --sysconfdir=/etc

define Package/openfortivpn/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(CP) $(PKG_INSTALL_DIR)/usr/bin/openfortivpn $(1)/usr/bin/
	$(INSTALL_DIR) $(1)/etc/openfortivpn
	$(INSTALL_CONF) $(PKG_INSTALL_DIR)/etc/openfortivpn/config $(1)/etc/openfortivpn/config
	$(INSTALL_DIR) $(1)/etc/init.d
	$(INSTALL_BIN) ./files/openfortivpn.init $(1)/etc/init.d/openfortivpn
endef

define Package/openfortivpn/conffiles
/etc/config/openfortivpn
endef

$(eval $(call BuildPackage,openfortivpn)