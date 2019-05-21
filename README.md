# rhel8

## Vanilla RHEL8 box, no subs.

    [root@localhost ~]# subscription-manager identity
    This system is not yet registered. Try 'subscription-manager register --help' for more information.
    [root@localhost ~]# cat /etc/redhat-release
    Red Hat Enterprise Linux release 8.0 (Ootpa)
    [root@localhost ~]#

## Register, attach

    [root@localhost ~]# subscription-manager register
    Registering to: subscription.rhsm.redhat.com:443/subscription
    Username: my-rh-username
    Password: my-rh-password
    The system has been registered with ID: XXXXXXXX-YYYY-ZZZZ-AAAA-BBBBBBBBBBBB
    The registered system name is: localhost.localdomain
    [root@localhost ~]# subscription-manager attach
    Installed Product Current Status:
    Product Name: Red Hat Enterprise Linux for x86_64
    Status:       Subscribed

    [root@localhost ~]#

## Review repos

    [root@localhost ~]# subscription-manager repos|grep "^Repo ID"|sort
    Repo ID:   ansible-2.8-for-rhel-8-x86_64-debug-rpms
    Repo ID:   ansible-2.8-for-rhel-8-x86_64-rpms
    Repo ID:   ansible-2.8-for-rhel-8-x86_64-source-rpms
    Repo ID:   cfme-5.11-for-rhel-8-x86_64-debug-rpms
    Repo ID:   cfme-5.11-for-rhel-8-x86_64-rpms
    Repo ID:   cfme-5.11-for-rhel-8-x86_64-source-rpms
    Repo ID:   codeready-builder-for-rhel-8-x86_64-debug-rpms
    Repo ID:   codeready-builder-for-rhel-8-x86_64-rpms
    Repo ID:   codeready-builder-for-rhel-8-x86_64-source-rpms
    Repo ID:   fast-datapath-beta-for-rhel-8-x86_64-debug-rpms
    Repo ID:   fast-datapath-beta-for-rhel-8-x86_64-rpms
    Repo ID:   fast-datapath-beta-for-rhel-8-x86_64-source-rpms
    Repo ID:   ossm-0-for-rhel-8-x86_64-debug-rpms
    Repo ID:   ossm-0-for-rhel-8-x86_64-rpms
    Repo ID:   ossm-0-for-rhel-8-x86_64-source-rpms
    Repo ID:   rhel-8-for-x86_64-appstream-debug-rpms
    Repo ID:   rhel-8-for-x86_64-appstream-rpms
    Repo ID:   rhel-8-for-x86_64-appstream-source-rpms
    Repo ID:   rhel-8-for-x86_64-baseos-debug-rpms
    Repo ID:   rhel-8-for-x86_64-baseos-rpms
    Repo ID:   rhel-8-for-x86_64-baseos-source-rpms
    Repo ID:   rhel-8-for-x86_64-supplementary-debug-rpms
    Repo ID:   rhel-8-for-x86_64-supplementary-rpms
    Repo ID:   rhel-8-for-x86_64-supplementary-source-rpms
    Repo ID:   RHOCP-4.1-for-rhel-8-x86_64-debug-rpms
    Repo ID:   RHOCP-4.1-for-rhel-8-x86_64-rpms
    Repo ID:   RHOCP-4.1-for-rhel-8-x86_64-source-rpms
    Repo ID:   satellite-tools-6.5-for-rhel-8-x86_64-debug-rpms
    Repo ID:   satellite-tools-6.5-for-rhel-8-x86_64-rpms
    Repo ID:   satellite-tools-6.5-for-rhel-8-x86_64-source-rpms
    [root@localhost ~]#

## Upgrade to latest

    [root@localhost ~]# yum -y update
    Updating Subscription Management repositories.
    Last metadata expiration check: 0:04:58 ago on Tue 21 May 2019 05:32:32 PM EDT.
    Dependencies resolved.
    =============================================================================================================================================================================================================================================
     Package                                        Arch                               Version                                                                                Repository                                                    Size
    =============================================================================================================================================================================================================================================
    Installing:
     kernel                                         x86_64                             4.18.0-80.1.2.el8_0                                                                    rhel-8-for-x86_64-baseos-rpms                                406 k
     kernel-modules                                 x86_64                             4.18.0-80.1.2.el8_0                                                                    rhel-8-for-x86_64-baseos-rpms                                 20 M
     kernel-core                                    x86_64                             4.18.0-80.1.2.el8_0                                                                    rhel-8-for-x86_64-baseos-rpms                                 24 M
    Upgrading:
     wget                                           x86_64                             1.19.5-7.el8_0.1                                                                       rhel-8-for-x86_64-appstream-rpms                             734 k
    [...]
      Verifying        : kernel-tools-4.18.0-80.1.2.el8_0.x86_64                                                                                                                                                                         108/111
      Verifying        : kernel-tools-4.18.0-80.el8.x86_64                                                                                                                                                                               109/111
      Verifying        : bpftool-4.18.0-80.1.2.el8_0.x86_64                                                                                                                                                                              110/111
      Verifying        : bpftool-4.18.0-80.el8.x86_64                                                                                                                                                                                    111/111
    Installed products updated.

    Upgraded:
      wget-1.19.5-7.el8_0.1.x86_64                   runc-1.0.0-55.rc5.dev.git2abd837.module+el8.0.0+3049+59fd2bba.x86_64  container-selinux-2:2.94-1.git1e99f1d.module+el8.0.0+2958+4e823551.noarch  bind-license-32:9.11.4-17.P2.el8_0.noarch
      bind-libs-32:9.11.4-17.P2.el8_0.x86_64         python3-bind-32:9.11.4-17.P2.el8_0.noarch                             bind-libs-lite-32:9.11.4-17.P2.el8_0.x86_64                                bind-utils-32:9.11.4-17.P2.el8_0.x86_64
      tzdata-2019a-1.el8.noarch                      sssd-client-2.0.0-43.el8_0.3.x86_64                                   python3-libdnf-0.22.5-5.el8_0.x86_64                                       sssd-common-pac-2.0.0-43.el8_0.3.x86_64
      sssd-ad-2.0.0-43.el8_0.3.x86_64                kmod-libs-25-11.el8_0.2.x86_64                                        p11-kit-0.23.14-5.el8_0.x86_64                                             libsss_idmap-2.0.0-43.el8_0.3.x86_64
      libsss_certmap-2.0.0-43.el8_0.3.x86_64         sssd-ipa-2.0.0-43.el8_0.3.x86_64                                      glibc-langpack-en-2.28-42.el8_0.1.x86_64                                   sssd-proxy-2.0.0-43.el8_0.3.x86_64
      libipa_hbac-2.0.0-43.el8_0.3.x86_64            platform-python-3.6.8-2.el8_0.x86_64                                  python3-libs-3.6.8-2.el8_0.x86_64                                          glibc-devel-2.28-42.el8_0.1.x86_64
      sssd-ldap-2.0.0-43.el8_0.3.x86_64              sssd-common-2.0.0-43.el8_0.3.x86_64                                   glibc-headers-2.28-42.el8_0.1.x86_64                                       glibc-common-2.28-42.el8_0.1.x86_64
      libsss_nss_idmap-2.0.0-43.el8_0.3.x86_64       p11-kit-trust-0.23.14-5.el8_0.x86_64                                  sssd-nfs-idmap-2.0.0-43.el8_0.3.x86_64                                     sssd-krb5-common-2.0.0-43.el8_0.3.x86_64
      python3-hawkey-0.22.5-5.el8_0.x86_64           systemd-pam-239-13.el8_0.3.x86_64                                     sssd-krb5-2.0.0-43.el8_0.3.x86_64                                          systemd-239-13.el8_0.3.x86_64
      libsss_autofs-2.0.0-43.el8_0.3.x86_64          libdnf-0.22.5-5.el8_0.x86_64                                          libnfsidmap-1:2.3.3-14.el8_0.x86_64                                        sssd-kcm-2.0.0-43.el8_0.3.x86_64
      glibc-2.28-42.el8_0.1.x86_64                   systemd-libs-239-13.el8_0.3.x86_64                                    vdo-6.2.0.298-10.el8_0.x86_64                                              kmod-25-11.el8_0.2.x86_64
      sssd-2.0.0-43.el8_0.3.x86_64                   systemd-udev-239-13.el8_0.3.x86_64                                    python3-sssdconfig-2.0.0-43.el8_0.3.noarch                                 libsss_sudo-2.0.0-43.el8_0.3.x86_64
      bind-export-libs-32:9.11.4-17.P2.el8_0.x86_64  kernel-tools-libs-4.18.0-80.1.2.el8_0.x86_64                          microcode_ctl-4:20180807a-2.20190507.1.el8_0.x86_64                        python3-perf-4.18.0-80.1.2.el8_0.x86_64
      kernel-tools-4.18.0-80.1.2.el8_0.x86_64        bpftool-4.18.0-80.1.2.el8_0.x86_64

    Installed:
      kernel-4.18.0-80.1.2.el8_0.x86_64                                         kernel-modules-4.18.0-80.1.2.el8_0.x86_64                                         kernel-core-4.18.0-80.1.2.el8_0.x86_64

    Complete!
    [root@localhost ~]#

## Create a RHEL6 container, perform reposync

    [root@localhost ~]# podman pull registry.access.redhat.com/rhel6/rhel
    Trying to pull registry.access.redhat.com/rhel6/rhel...Getting image source signatures
    Copying blob e94c811b9cc4: 87.07 MiB / 87.07 MiB [=========================] 28s
    Copying blob cdefd474e5ab: 1.22 KiB / 1.22 KiB [===========================] 28s
    Copying config c3d7822f2e85: 6.37 KiB / 6.37 KiB [==========================] 0s
    Writing manifest to image destination
    Storing signatures
    c3d7822f2e85d9e4df76c4010e5ba203a5450b5d387f71ff28668181b5d5ab45
    [root@localhost ~]# podman run -it registry.access.redhat.com/rhel6/rhel /bin/bash
    [root@687706d531f2 /]# cat /etc/redhat-release
    Red Hat Enterprise Linux Server release 6.10 (Santiago)
    [root@687706d531f2 /]# yum repolist
    Loaded plugins: ovl, product-id, search-disabled-repos, subscription-manager
    rhel-6-server-rpms                                                                                                                                                                                                    | 3.5 kB     00:00
    rhel-6-server-rpms/primary_db                                                                                                                                                                                         |  59 MB     00:04
    repo id                                                                                                 repo name                                                                                                                      status
    rhel-6-server-rpms                                                                                      Red Hat Enterprise Linux 6 Server (RPMs)                                                                                       20,719
    repolist: 20,719
    [root@687706d531f2 /]# reposync -r rhel-6-server-rpms
    [rhel-6-server-rpms: 1     of 20719 ] Downloading Packages/3/389-ds-base-1.2.8.2-1.el6_1.3.x86_64.rpm
    389-ds-base-1.2.8.2-1.el6_1.3.x86_64.rpm                                                                                                                                                                              | 1.2 MB     00:00
    [rhel-6-server-rpms: 2     of 20719 ] Downloading Packages/3/389-ds-base-1.2.11.15-22.el6_4.x86_64.rpm
    389-ds-base-1.2.11.15-22.el6_4.x86_64.rpm                                                                                                                                                                             | 1.5 MB     00:00
    [rhel-6-server-rpms: 3     of 20719 ] Downloading Packages/3/389-ds-base-1.2.10.2-18.el6_3.x86_64.rpm
    389-ds-base-1.2.10.2-18.el6_3.x86_64.rpm                                                                                                                                                                              | 1.4 MB     00:00
    [rhel-6-server-rpms: 4     of 20719 ] Downloading Packages/3/389-ds-base-1.2.11.15-12.el6_4.x86_64.rpm
    389-ds-base-1.2.11.15-12.el6_4.x86_64.rpm                                                                                                                                                                             | 1.5 MB     00:00
    [rhel-6-server-rpms: 5     of 20719 ] Downloading Packages/3/389-ds-base-1.2.11.15-29.el6.x86_64.rpm
    389-ds-base-1.2.11.15-29.el6.x86_64.rpm                                                                                                                                                                               | 1.5 MB     00:00
    [rhel-6-server-rpms: 6     of 20719 ] Downloading Packages/3/389-ds-base-1.2.10.2-20.el6_3.x86_64.rpm
    389-ds-base-1.2.10.2-20.el6_3.x86_64.rpm                                                                                                                                                                              | 1.4 MB     00:00
    [rhel-6-server-rpms: 7     of 20719 ] Downloading Packages/3/389-ds-base-1.2.9.14-1.el6.x86_64.rpm
    389-ds-base-1.2.9.14-1.el6.x86_64.rpm                                                                                                                                                                                 | 1.4 MB     00:00
    [root@687706d531f2 /]# find rhel-6-server-rpms -name \*rpm -ls
    6536639 1196 -rw-r--r--   1 root     root      1221228 Jun  2  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.8.2-1.el6_1.3.x86_64.rpm
    6578304 1492 -rw-r--r--   1 root     root      1526776 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.11.15-22.el6_4.x86_64.rpm
    6578305 1412 -rw-r--r--   1 root     root      1442240 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.10.2-18.el6_3.x86_64.rpm
    6578306 1492 -rw-r--r--   1 root     root      1524096 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.11.15-12.el6_4.x86_64.rpm
    6578307 1500 -rw-r--r--   1 root     root      1535400 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.11.15-29.el6.x86_64.rpm
    6578308 1412 -rw-r--r--   1 root     root      1442572 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.10.2-20.el6_3.x86_64.rpm
    6578309 1404 -rw-r--r--   1 root     root      1437028 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.9.14-1.el6.x86_64.rpm
    6578310 1500 -rw-r--r--   1 root     root      1535516 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.11.15-32.el6_5.x86_64.rpm
    6578311 1492 -rw-r--r--   1 root     root      1526524 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.11.15-20.el6_4.x86_64.rpm
    6578312 1408 -rw-r--r--   1 root     root      1438452 May 26  2014 rhel-6-server-rpms/Packages/3/389-ds-base-1.2.9.14-1.el6_2.2.x86_64.rpm
    [root@687706d531f2 /]# exit
    [root@localhost ~]#

## Create a RHEL7 container, perform reposync

    [root@localhost ~]# podman pull registry.access.redhat.com/rhel7/rhel
    Trying to pull registry.access.redhat.com/rhel7/rhel...Getting image source signatures
    Copying blob d69140bdce18: 72.34 MiB / 72.34 MiB [=========================] 13s
    Copying blob a82dd37af30d: 1.23 KiB / 1.23 KiB [===========================] 13s
    Copying config 5044f6040ea5: 6.31 KiB / 6.31 KiB [==========================] 0s
    Writing manifest to image destination
    Storing signatures
    5044f6040ea5535b508dcade2cbee564dae54907ed47ee6002c8cd6e39c60c3c
    [root@localhost ~]# podman run -it registry.access.redhat.com/rhel7/rhel /bin/bash
    [root@ce44637e76f3 /]# cat /etc/redhat-release
    Red Hat Enterprise Linux Server release 7.6 (Maipo)
    [root@ce44637e76f3 /]# yum repolist
    Loaded plugins: ovl, product-id, search-disabled-repos, subscription-manager
    rhel-7-server-rpms                                                                                                                                                                                                    | 3.5 kB  00:00:00
    (1/3): rhel-7-server-rpms/7Server/x86_64/group                                                                                                                                                                        | 774 kB  00:00:00
    (2/3): rhel-7-server-rpms/7Server/x86_64/updateinfo                                                                                                                                                                   | 3.1 MB  00:00:00
    (3/3): rhel-7-server-rpms/7Server/x86_64/primary_db                                                                                                                                                                   |  56 MB  00:00:05
    repo id                                                                                                         repo name                                                                                                              status
    rhel-7-server-rpms/7Server/x86_64                                                                               Red Hat Enterprise Linux 7 Server (RPMs)                                                                               24192
    repolist: 24192
    [root@ce44637e76f3 /]# reposync -r rhel-7-server-rpms
    Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
    warning: /rhel-7-server-rpms/Packages/3/389-ds-base-1.3.1.6-25.el7.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID fd431d51: NOKEY                                                                      ]  0.0 B/s |    0 B  --:--:-- ETA
    Public key for 389-ds-base-1.3.1.6-25.el7.x86_64.rpm is not installed
    (1/24192): 389-ds-base-1.3.1.6-25.el7.x86_64.rpm                                                                                                                                                                      | 1.5 MB  00:00:00
    (2/24192): 389-ds-base-1.3.1.6-26.el7_0.x86_64.rpm                                                                                                                                                                    | 1.5 MB  00:00:00
    (3/24192): 389-ds-base-1.3.3.1-13.el7.x86_64.rpm                                                                                                                                                                      | 1.6 MB  00:00:00
    (4/24192): 389-ds-base-1.3.3.1-15.el7_1.x86_64.rpm                                                                                                                                                                    | 1.6 MB  00:00:00
    (5/24192): 389-ds-base-1.3.3.1-16.el7_1.x86_64.rpm                                                                                                                                                                    | 1.6 MB  00:00:00
    (6/24192): 389-ds-base-1.3.3.1-20.el7_1.x86_64.rpm                                                                                                                                                                    | 1.6 MB  00:00:00
    (7/24192): 389-ds-base-1.3.3.1-23.el7_1.x86_64.rpm                                                                                                                                                                    | 1.6 MB  00:00:00
    (8/24192): 389-ds-base-1.3.4.0-19.el7.x86_64.rpm                                                                                                                                                                      | 1.7 MB  00:00:00
    (9/24192): 389-ds-base-1.3.4.0-21.el7_2.x86_64.rpm                                                                                                                                                                    | 1.7 MB  00:00:00
    (10/24192): 389-ds-base-1.3.4.0-26.el7_2.x86_64.rpm                                                                                                                                                                   | 1.7 MB  00:00:00
    (11/24192): 389-ds-base-1.3.4.0-29.el7_2.x86_64.rpm                                                                                                                                                                   | 1.7 MB  00:00:00
    (12/24192): 389-ds-base-1.3.4.0-30.el7_2.x86_64.rpm                                                                                                                                                                   | 1.7 MB  00:00:00
    (13/24192): 389-ds-base-1.3.4.0-32.el7_2.x86_64.rpm                                                                                                                                                                   | 1.7 MB  00:00:00
    (14/24192): 389-ds-base-1.3.4.0-33.el7_2.x86_64.rpm                                                                                                                                                                   | 1.7 MB  00:00:00
    (15/24192): 389-ds-base-1.3.5.10-11.el7.x86_64.rpm                                                                                                                                                                    | 1.7 MB  00:00:00
    (16/24192): 389-ds-base-1.3.5.10-12.el7_3.x86_64.rpm                                                                                                                                                                  | 1.7 MB  00:00:00
    (17/24192): 389-ds-base-1.3.5.10-15.el7_3.x86_64.rpm                                                                                                                                                                  | 1.7 MB  00:00:00
    (18/24192): 389-ds-base-1.3.5.10-18.el7_3.x86_64.rpm                                                                                                                                                                  | 1.7 MB  00:00:00
    (19/24192): 389-ds-base-1.3.5.10-20.el7_3.x86_64.rpm                                                                                                                                                                  | 1.7 MB  00:00:00
    (20/24192): 389-ds-base-1.3.5.10-21.el7_3.x86_64.rpm                                                                                                                                                                  | 1.7 MB  00:00:00
    ^C
    [root@ce44637e76f3 /]# find rhel-7-server-rpms -name \*rpm -ls
    4320920 1580 -rw-r--r--   1 root     root      1615920 Apr 16  2014 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.1.6-25.el7.x86_64.rpm
    4320921 1580 -rw-r--r--   1 root     root      1616100 Aug  7  2014 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.1.6-26.el7_0.x86_64.rpm
    4320922 1676 -rw-r--r--   1 root     root      1712608 Feb  4  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.3.1-13.el7.x86_64.rpm
    4320923 1676 -rw-r--r--   1 root     root      1714428 Mar  5  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.3.1-15.el7_1.x86_64.rpm
    4320924 1676 -rw-r--r--   1 root     root      1714796 Apr 28  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.3.1-16.el7_1.x86_64.rpm
    4320925 1676 -rw-r--r--   1 root     root      1715748 Aug  5  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.3.1-20.el7_1.x86_64.rpm
    4320926 1680 -rw-r--r--   1 root     root      1719784 Nov  3  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.3.1-23.el7_1.x86_64.rpm
    4320927 1708 -rw-r--r--   1 root     root      1746448 Nov  4  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-19.el7.x86_64.rpm
    4320928 1708 -rw-r--r--   1 root     root      1747300 Dec  8  2015 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-21.el7_2.x86_64.rpm
    4320929 1708 -rw-r--r--   1 root     root      1748476 Feb 16  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-26.el7_2.x86_64.rpm
    4320930 1712 -rw-r--r--   1 root     root      1749000 Mar 17  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-29.el7_2.x86_64.rpm
    4320931 1712 -rw-r--r--   1 root     root      1749184 May 12  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-30.el7_2.x86_64.rpm
    4320932 1712 -rw-r--r--   1 root     root      1749132 Jun 13  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-32.el7_2.x86_64.rpm
    4320933 1712 -rw-r--r--   1 root     root      1750332 Jul 26  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.4.0-33.el7_2.x86_64.rpm
    4320934 1732 -rw-r--r--   1 root     root      1772872 Oct  6  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.5.10-11.el7.x86_64.rpm
    4320935 1736 -rw-r--r--   1 root     root      1773652 Nov 14  2016 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.5.10-12.el7_3.x86_64.rpm
    4320936 1736 -rw-r--r--   1 root     root      1774740 Jan  9  2017 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.5.10-15.el7_3.x86_64.rpm
    4320937 1736 -rw-r--r--   1 root     root      1776920 Feb 20  2017 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.5.10-18.el7_3.x86_64.rpm
    4320938 1736 -rw-r--r--   1 root     root      1777448 Apr 10  2017 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.5.10-20.el7_3.x86_64.rpm
    4320939 1740 -rw-r--r--   1 root     root      1777872 Apr 25  2017 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.5.10-21.el7_3.x86_64.rpm
    4320940    0 -rw-r--r--   1 root     root            0 May 21 21:44 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.6.1-16.el7.x86_64.rpm
    4320941    0 -rw-r--r--   1 root     root            0 May 21 21:44 rhel-7-server-rpms/Packages/3/389-ds-base-1.3.6.1-19.el7_4.x86_64.rpm
    [root@ce44637e76f3 /]# exit
    exit
    [root@localhost ~]#
