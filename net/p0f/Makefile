# Copyright (C) 2006 OpenWrt.org
#
# This is free software, licensed under the GNU General Public License v2.
# See /LICENSE for more information.
#
# $Id: Makefile 9695 2007-12-09 18:59:01Z nbd $

include $(TOPDIR)/rules.mk

PKG_NAME:=p0f
PKG_VERSION:=3.06b
PKG_RELEASE:=1

PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION).tgz
PKG_SOURCE_URL:=http://lcamtuf.coredump.cx/p0f3/releases/
PKG_MD5SUM:=unknown

include $(INCLUDE_DIR)/package.mk

define Package/p0f
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libpcap
	TITLE:=P0f
	URL:=http://lcamtuf.coredump.cx/p0f3/
endef

define Package/p0f/description
	P0f
endef

CONFIGURE_VARS += \
	CPPFLAGS="$$$$CPPFLAGS -g " \
	LIBS="-nodefaultlibs" \

define Build/Configure
	$(call Build/Configure/Default,)
endef

define Package/p0f/install
	install -d -m0755 $(1)/usr
	install -d -m0755 $(1)/usr/bin
	install -d -m0755 $(1)/etc
	install -d -m0755 $(1)/etc/p0f
	install -m0755 $(PKG_BUILD_DIR)/p0f $(1)/usr/bin
	cp -R $(PKG_BUILD_DIR)/p0f.fp $(1)/etc/p0f
endef

$(eval $(call BuildPackage,p0f))

