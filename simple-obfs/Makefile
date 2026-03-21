# SPDX-License-Identifier: GPL-3.0-or-later
#
# Copyright (C) 2017-2019 Jian Chang <aa65535@live.com>
# Copyright (C) 2021 ImmortalWrt.org

include $(TOPDIR)/rules.mk

PKG_NAME:=simple-obfs
PKG_VERSION:=0.0.10-git20260321
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/kenzok8/simple-obfs.git
PKG_SOURCE_DATE:=2026-03-21
PKG_SOURCE_VERSION:=d5cb2d53062dc22708b1d78b3430fe2fb3e2b38a
PKG_MIRROR_HASH:=341a60b89a51e82ca239033e4fa9aac536c680324f3b51e3dc0d01c83455b052

PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE
PKG_MAINTAINER:=Jian Chang <aa65535@live.com>

PKG_BUILD_DEPENDS:=libev
PKG_FIXUP:=autoreconf
PKG_BUILD_PARALLEL:=1
PKG_INSTALL:=1

include $(INCLUDE_DIR)/package.mk

define Package/simple-obfs/template
  SECTION:=net
  CATEGORY:=Network
  TITLE:=A simple obfuscating tool
  URL:=https://github.com/kenzok8/simple-obfs
  DEPENDS:=+libpthread +libev
endef

define Package/simple-obfs-client
  $(call Package/simple-obfs/template)
  TITLE+= (client)
  PROVIDES:=simple-obfs
endef

define Package/simple-obfs-server
  $(call Package/simple-obfs/template)
  TITLE+= (server)
endef

define Package/simple-obfs/description
  Simple-obfs is a simple obfusacting tool, designed as plugin server of shadowsocks.
endef

Package/simple-obfs-client/description = $(Package/simple-obfs/description)
Package/simple-obfs-server/description = $(Package/simple-obfs/description)

CONFIGURE_ARGS += \
	--disable-ssp \
	--disable-documentation \
	--disable-assert

define Package/simple-obfs-client/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/obfs-local $(1)/usr/bin/
endef

define Package/simple-obfs-server/install
	$(INSTALL_DIR) $(1)/usr/bin
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/obfs-server $(1)/usr/bin/
endef

$(eval $(call BuildPackage,simple-obfs-client))
$(eval $(call BuildPackage,simple-obfs-server))
