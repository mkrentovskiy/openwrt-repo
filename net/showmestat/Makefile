include $(TOPDIR)/rules.mk

PKG_NAME:=showmestat
PKG_VERSION:=0.1
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL:=https://github.com/mkrentovskiy/showmestat.git
PKG_SOURCE_SUBDIR:=$(PKG_NAME)-$(PKG_VERSION)
PKG_SOURCE_VERSION:=master
PKG_SOURCE:=$(PKG_NAME)-$(PKG_VERSION)-$(PKG_SOURCE_VERSION).tar.gz

include $(INCLUDE_DIR)/package.mk

define Package/showmestat
	SECTION:=net
	CATEGORY:=Network
	DEPENDS:=+libwebsockets
	TITLE:=ShowMeStat
endef

define Package/showmestat/description
	DPI statistics demonstration tool.
endef

define Build/Compile
	$(MAKE) -C $(PKG_BUILD_DIR) DESTDIR="$(PKG_INSTALL_DIR)"
endef

define Package/showmwstat/install
    install -d -m0755 $(1)/usr
    install -d -m0755 $(1)/usr/bin
    install -d -m0755 $(1)/usr/share
    install -d -m0755 $(1)/usr/share/showmestat
    install -m0755 $(PKG_BUILD_DIR)/showmestat $(1)/usr/bin
    cp -R $(PKG_BUILD_DIR)/wwwroot $(1)/usr/share/showmestat
endef

$(eval $(call BuildPackage, showmestat))

