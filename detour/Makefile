include $(TOPDIR)/rules.mk

PKG_NAME:=detour
PKG_VERSION:=1.2024.04
PKG_RELEASE:=1

PKG_SOURCE:=exmcUbTW.tar.gz
PKG_SOURCE_URL:=https://a.uguu.se
PKG_HASH:=8613599f24c9bd3e3d405cb401ad56898b053c9b11599b76cc8b24d18a3f6a51

PKG_MAINTAINER:=silvercrown07 <44765224+silvercrown07@users.noreply.github.com>
PKG_LICENSE:=MIT
PKG_LICENSE_FILES:=LICENSE

PKG_BUILD_DEPENDS:=golang/host
PKG_BUILD_PARALLEL:=1
PKG_BUILD_FLAGS:=no-mips16

GO_PKG:=dohkie/detour
GO_PKG_BUILD_PKG:=$(GO_PKG)

include $(INCLUDE_DIR)/package.mk
include /builder/feeds/packages/lang/golang/golang-package.mk

define Package/detour
  SECTION:=net
  CATEGORY:=Network
  SUBMENU:=IP Addresses and Names
  TITLE:=Naive DNS forwarder
  URL:=https://github.com/silvercrown07/feeds/detour
  DEPENDS:=$(GO_ARCH_DEPENDS)
endef

define Package/detour/description
  Naive DNS forwarder written in Go.
endef

define Package/detour/install
	$(call GoPackage/Package/Install/Bin,$(PKG_INSTALL_DIR))

	$(INSTALL_DIR) $(1)/usr/bin $(1)/etc/init.d $(1)/etc/detour
	$(INSTALL_BIN) $(PKG_INSTALL_DIR)/usr/bin/detour  $(1)/usr/bin/detour
	$(INSTALL_BIN) files/etc/init.d/detour $(1)/etc/init.d/detour
endef

$(eval $(call GoBinPackage,detour))
$(eval $(call BuildPackage,detour))
