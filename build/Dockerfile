FROM gentoo/stage3:systemd AS gentoo

# optimized defaults
COPY root /

# bootstrap portage
RUN mkdir /var/db/repos/gentoo
RUN emerge --sync
RUN eselect news read --quiet all && eselect news purge

# install satan's kernel
RUN emerge sys-kernel/linux-firmware
RUN emerge sys-kernel/gentoo-kernel-bin:6.6.6

# install overlays
RUN emerge app-eselect/eselect-repository dev-vcs/git
RUN eselect repository add brave-overlay git https://gitlab.com/jason.oliveira/brave-overlay.git
RUN emaint sync -r brave-overlay
RUN eselect repository enable steam-overlay
RUN emaint sync -r steam-overlay

# install software
RUN emerge app-admin/sudo
RUN emerge app-arch/file-roller
RUN emerge app-arch/p7zip
RUN emerge app-arch/rpm
RUN emerge app-arch/unrar
RUN emerge app-arch/zip
RUN emerge app-cdr/cdrtools
RUN emerge app-containers/docker
RUN emerge app-containers/docker-compose
RUN emerge app-editors/vscode
RUN emerge app-emulation/open-vm-tools
RUN emerge app-portage/gentoolkit
RUN emerge dev-dotnet/dotnet-sdk-bin
RUN emerge dev-python/pip
RUN emerge dev-util/scanmem
RUN emerge dev-util/strace
RUN emerge dev-vcs/git-lfs
RUN emerge games-emulation/retroarch
RUN emerge games-util/steam-meta
RUN emerge gnome-extra/nm-applet
RUN emerge media-gfx/gimp
RUN emerge media-gfx/renderdoc
RUN emerge media-gfx/viewnior
RUN emerge media-sound/alsa-utils
RUN emerge media-sound/audacity
RUN emerge media-sound/pavucontrol
RUN emerge media-video/shotcut
RUN emerge media-video/vlc
RUN emerge media-video/wireplumber
RUN emerge net-im/slack
RUN emerge net-im/zoom
RUN emerge net-libs/nodejs
RUN emerge net-libs/webkit-gtk:4
RUN emerge net-misc/dhcpcd
RUN emerge net-misc/networkmanager
RUN emerge net-wireless/blueman
RUN emerge sys-apps/xdg-desktop-portal-gtk
RUN emerge sys-block/io-scheduler-udev-rules
RUN emerge sys-boot/os-prober
RUN emerge sys-fs/ntfs3g
RUN emerge sys-power/tlp
RUN emerge www-client/brave-bin
RUN emerge www-client/firefox-bin
RUN emerge x11-base/xorg-server
RUN emerge x11-drivers/nvidia-drivers
RUN emerge xfce-base/xfce4-meta
RUN emerge xfce-extra/thunar-archive-plugin
RUN emerge xfce-extra/xfce4-screenshooter
