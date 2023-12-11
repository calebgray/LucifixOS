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
RUN eselect repository enable steam-overlay
RUN emaint sync -r brave-overlay steam-overlay

# install software
RUN emerge app-admin/sudo app-arch/file-roller app-arch/p7zip app-arch/rpm app-arch/unrar app-arch/zip app-cdr/cdrtools app-containers/docker app-containers/docker-compose app-editors/vscode app-emulation/open-vm-tools app-portage/gentoolkit dev-dotnet/dotnet-sdk-bin dev-python/pip dev-util/scanmem dev-util/strace dev-vcs/git-lfs games-emulation/retroarch games-util/steam-meta gnome-extra/nm-applet media-gfx/gimp media-gfx/renderdoc media-gfx/viewnior media-sound/alsa-utils media-sound/audacity media-sound/pavucontrol media-video/shotcut media-video/vlc media-video/wireplumber net-im/slack net-im/zoom net-libs/nodejs net-libs/webkit-gtk:4 net-misc/dhcpcd net-misc/networkmanager net-wireless/blueman sys-apps/xdg-desktop-portal-gtk sys-block/io-scheduler-udev-rules sys-boot/os-prober sys-fs/ntfs3g sys-power/tlp www-client/brave-bin www-client/firefox-bin x11-base/xorg-server x11-drivers/nvidia-drivers xfce-base/xfce4-meta xfce-extra/thunar-archive-plugin xfce-extra/xfce4-screenshooter
