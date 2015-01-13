#
# libwebsockets makefile for openwrt
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libwebsockets
PKG_VERSION:=1
PKG_RELEASE=$(PKG_SOURCE_VERSION)

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=git://git.libwebsockets.org/libwebsockets
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=master
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz
CMAKE_INSTALL:=1

include $(INCLUDE_DIR)/package.mk
include $(INCLUDE_DIR)/cmake.mk

CMAKE_OPTIONS += -DLWS_OPENSSL_CLIENT_CERTS=/etc/ssl/certs
CMAKE_OPTIONS += -DLWS_OPENSSL_SUPPORT=ON
CMAKE_OPTIONS += -DLWS_WITH_SSL=ON
CMAKE_OPTIONS += -DLWS_WITHOUT_TESTAPPS=ON

define Package/libwebsockets
  SECTION:=libs
  CATEGORY:=Libraries
  TITLE:=libwebsockets
  DEPENDS:=+zlib +libopenssl
endef

define Package/libwebsockets/description
  This package contains libwebsocket libraries
endef

TARGET_CFLAGS += -I$(STAGING_DIR)/usr/include

define Package/libwebsockets/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwebsockets.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libwebsockets))
