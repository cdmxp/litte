
# SPDX-License-Identifier: GPL-3.0-only
#
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=redsocks2
PKG_VERSION:=0.71
PKG_RELEASE:=2

PKG_SOURCE_VERSION:=43ba8a3cb1b5f8c44b2a827b924375f1de733370
PKG_SOURCE:=redsocks-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
PKG_SOURCE_URL:=https://codeload.github.com/kenzok8/redsocks/tar.gz/$(PKG_SOURCE_VERSION)?
PKG_HASH:=7431089ba99f0830c5c11ee1203f720ff19e734aa99fbd87334f9f4547d15b3c
PKG_BUILD_DIR:=$(BUILD_DIR)/redsocks-$(PKG_SOURCE_VERSION)

PKG_MAINTAINER:=semigodking <semigodking@gmail.com>
PKG_LICENSE:=Apache-2.0
PKG_LICENSE_FILE:=LICENSE

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

define Package/redsocks2
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=Web Servers/Proxies
  TITLE:=Redirect TCP connection to proxy server
  URL:=https://github.com/kenzok8/redsocks
  DEPENDS:=+libevent2 +libopenssl
endef

define Package/redsocks2/description
  This is a modified version of original redsocks.
  Transparent redirector of any TCP/UDP connection to proxy.
endef

MAKE_VARS += DISABLE_SHADOWSOCKS=true

define Package/redsocks2/install
	$(INSTALL_DIR) $(1)/usr/sbin
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/redsocks2 $(1)/usr/sbin
	$(INSTALL_DIR) $(1)/etc/redsocks2
	$(INSTALL_DATA) ./files/redsocks2.template $(1)/etc/redsocks2/config.template
endef

$(eval $(call BuildPackage,redsocks2))
