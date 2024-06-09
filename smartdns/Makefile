include $(TOPDIR)/rules.mk

PKG_NAME:=smartdns
PKG_VERSION:=1.2024.06
PKG_RELEASE:=1

PKG_SOURCE_PROTO:=git
PKG_SOURCE_URL=https://github.com/pymumu/smartdns.git
PKG_SOURCE_VERSION:=07c13827bb523519a638214ed7ad76180f71a40a
PKG_MIRROR_HASH:=c9eb770919cd614ccd8931f7f609d5ffb55c8969cd5f78364525c8c710ef0434

PKG_MAINTAINER:=silvercrown07 <44765224+silvercrown07@users.noreply.github.com>
PKG_LICENSE:=GPL-3.0-or-later
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_PARALLEL:=1

include $(INCLUDE_DIR)/package.mk

MAKE_VARS += VER=$(PKG_VERSION)
MAKE_PATH:=src

define Package/smartdns
  SECTION:=net
  CATEGORY:=Network
  TITLE:=smartdns server
  DEPENDS:=+libpthread +libopenssl
  URL:=https://www.github.com/pymumu/smartdns/
endef

define Package/smartdns/description
SmartDNS is a local DNS server which accepts DNS query requests from local network clients,
gets DNS query results from multiple upstream DNS servers concurrently, and returns the fastest IP to clients.
Unlike dnsmasq's all-servers, smartdns returns the fastest IP, and encrypt DNS queries with DoT or DoH.
endef

define Package/smartdns/conffiles
/etc/smartdns/smartdns.conf
endef

define Package/smartdns/install
	$(INSTALL_DIR) $(1)/usr/sbin $(1)/etc/init.d $(1)/etc/smartdns
	$(INSTALL_BIN) $(PKG_BUILD_DIR)/src/smartdns $(1)/usr/sbin/smartdns
	$(INSTALL_BIN) files/etc/init.d/smartdns $(1)/etc/init.d/smartdns
	$(INSTALL_CONF) files/etc/smartdns/smartdns.conf $(1)/etc/smartdns/smartdns.conf
endef

$(eval $(call BuildPackage,smartdns))
