#
# libwebsockets makefile for openwrt
#

include $(TOPDIR)/rules.mk

PKG_NAME:=libwebsockets
PKG_VERSION:=master
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
CMAKE_OPTIONS += -DLWS_WITHOUT_TESTAPPS=$(if $(CONFIG_PACKAGE_libwebsockets-examples),"OFF","ON")

# for cyassl, define these in addition to LWS_OPENSSL_SUPPORT and
# edit package/libs/cyassl/Makefile to include --enable-opensslextra
# CMAKE_OPTIONS += -DLWS_USE_CYASSL=ON
# CMAKE_OPTIONS += -DLWS_CYASSL_LIB=$(STAGING_DIR)/usr/lib/libcyassl.so
# CMAKE_OPTIONS += -DLWS_CYASSL_INCLUDE_DIRS=$(STAGING_DIR)/usr/include

# other options worth noting
# CMAKE_OPTIONS += -DLWS_WITHOUT_EXTENSIONS=ON
# CMAKE_OPTIONS += -DLWS_WITHOUT_DAEMONIZE=ON
# CMAKE_OPTIONS += -DLWS_WITHOUT_SERVER=ON
# CMAKE_OPTIONS += -DLWS_WITHOUT_DEBUG=ON


define Package/libwebsockets/Default
	SECTION:=libs
	CATEGORY:=Libraries
	TITLE:=libwebsockets
	DEPENDS:=+zlib +libopenssl
endef

define Package/libwebsockets
	$(call Package/libwebsockets/Default)
	TITLE+= (libraries)
endef

define Package/libwebsockets/description
	libwebsockets
	This package contains libwebsocket libraries
endef

define Package/libwebsockets/install
	$(INSTALL_DIR) $(1)/usr/lib
	$(CP) $(PKG_INSTALL_DIR)/usr/lib/libwebsockets.so* $(1)/usr/lib/
endef

$(eval $(call BuildPackage,libwebsockets))