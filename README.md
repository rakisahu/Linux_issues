# Linux_issues
Issue in Centos 7 &amp; RHEL 7
"Issue: while using yum to update or install any pavkage I come across error, and i resolved the error as below, plesae have a look on the issues and verify all at your end take necessary action.

Issue : on Centos 7
[root@localhost ~]# yum update -y
Loaded plugins: fastestmirror


File contains no section headers.
file: file:///etc/yum.repos.d/devel:kubic:libcontainers:stable:cri-o:.repo, line: 1
'<?xml version="1.0" encoding="UTF-8"?>\n'


Last login: Sat Dec  3 16:14:55 2022 from 192.168.149.1
Hi i am root user
[root@localhost ~]# yum install crio-o
Loaded plugins: fastestmirror


File contains no section headers.
file: file:///etc/yum.repos.d/devel:kubic:libcontainers:stable:cri-o:.repo, line: 1
'<?xml version="1.0" encoding="UTF-8"?>\n'
[root@localhost ~]# yum update -y
Loaded plugins: fastestmirror


File contains no section headers.
file: file:///etc/yum.repos.d/devel:kubic:libcontainers:stable:cri-o:.repo, line: 1
'<?xml version="1.0" encoding="UTF-8"?>\n'
[root@localhost ~]# cd /etc/yum.repos.d
[root@localhost yum.repos.d]# ls
CentOS-Base.repo       CentOS-Media.repo          devel:kubic:libcontainers:stable:cri-o:.repo  epel-testing.repo
CentOS-CR.repo         CentOS-Sources.repo        devel:kubic:libcontainers:stable.repo         hashicorp.repo
CentOS-Debuginfo.repo  CentOS-Vault.repo          docker-ce.repo
CentOS-fasttrack.repo  CentOS-x86_64-kernel.repo  epel.repo
[root@localhost yum.repos.d]# vi  devel:kubic:libcontainers:stable:cri-o:.repo
[root@localhost yum.repos.d]# cat devel\:kubic\:libcontainers\:stable.repo
[devel_kubic_libcontainers_stable]
name=Stable Releases of Upstream github.com/containers packages (CentOS_7)
type=rpm-md
baseurl=https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/CentOS_7/
gpgcheck=1
gpgkey=https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/CentOS_7/repodata/repomd.xml.key
enabled=1
[root@localhost yum.repos.d]# cat devel:kubic:libcontainers:stable:cri-o:.repo
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN"
  "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html xmlns="http://www.w3.org/1999/xhtml" lang="en" xml:lang="en">
<head>
<title>Resource is no longer available!</title>
<link rev="made" href="mailto:webmaster@opensuse.org" />
<style type="text/css"><!--/*--><![CDATA[/*><!--*/
    body { color: #000000; background-color: #FFFFFF; }
    a:link { color: #0000CC; }
    p, address {margin-left: 3em;}
    span {font-size: smaller;}
/*]]>*/--></style>
</head>

<body>
<h1>Resource is no longer available!</h1>
<p>


    The requested URL is no longer available on this server and there is no
    forwarding address.



    If you followed a link from a foreign page, please contact the
    author of this page.



</p>
<p>
If you think this is a server error, please contact
the <a href="mailto:webmaster@opensuse.org">webmaster</a>.

</p>

<h2>Error 404</h2>
<address>
  <a href="/">download.opensuse.org</a><br />
  <span>Apache</span>
</address>
</body>
</html>

[root@localhost yum.repos.d]# mv devel:kubic:libcontainers:stable:cri-o:.repo /tmp
[root@localhost yum.repos.d]# ls
CentOS-Base.repo       CentOS-fasttrack.repo  CentOS-Vault.repo                      docker-ce.repo     hashicorp.repo
CentOS-CR.repo         CentOS-Media.repo      CentOS-x86_64-kernel.repo              epel.repo
CentOS-Debuginfo.repo  CentOS-Sources.repo    devel:kubic:libcontainers:stable.repo  epel-testing.repo
[root@localhost yum.repos.d]# yum update -y
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
epel/x86_64/metalink                                                                                              | 3.7 kB  00:00:00
 * base: centos.excellmedia.net
 * epel: repo.extreme-ix.org
 * extras: centos.excellmedia.net
 * updates: centos.excellmedia.net
base                                                                                                              | 3.6 kB  00:00:00
devel_kubic_libcontainers_stable                                                                                  | 1.7 kB  00:00:00
docker-ce-stable                                                                                                  | 3.5 kB  00:00:00
epel                                                                                                              | 4.7 kB  00:00:00
extras                                                                                                            | 2.9 kB  00:00:00
hashicorp                                                                                                         | 1.4 kB  00:00:00
updates                                                                                                           | 2.9 kB  00:00:00
(1/5): devel_kubic_libcontainers_stable/primary                                                                   | 6.3 kB  00:00:10
(2/5): hashicorp/7/x86_64/primary                                                                                 | 136 kB  00:00:10
(3/5): epel/x86_64/updateinfo                                                                                     | 1.0 MB  00:00:17
(4/5): updates/7/x86_64/primary_db                                                                                |  18 MB  00:00:25
(5/5): epel/x86_64/primary_db                                                                                     | 7.0 MB  00:00:45
devel_kubic_libcontainers_stable                                                                                                   19/19
hashicorp                                                                                                                        979/979
Resolving Dependencies
--> Running transaction check
---> Package fuse-overlayfs.x86_64 0:0.7.2-6.el7_8 will be updated
---> Package fuse-overlayfs.x86_64 0:1.5.0-1.el7.5.2 will be an update
--> Processing Dependency: fuse3 for package: fuse-overlayfs-1.5.0-1.el7.5.2.x86_64
---> Package kpartx.x86_64 0:0.4.9-135.el7_9 will be updated
---> Package kpartx.x86_64 0:0.4.9-136.el7_9 will be an update
---> Package krb5-devel.x86_64 0:1.15.1-54.el7_9 will be updated
---> Package krb5-devel.x86_64 0:1.15.1-55.el7_9 will be an update
---> Package krb5-libs.x86_64 0:1.15.1-54.el7_9 will be updated
---> Package krb5-libs.x86_64 0:1.15.1-55.el7_9 will be an update
---> Package libkadm5.x86_64 0:1.15.1-54.el7_9 will be updated
---> Package libkadm5.x86_64 0:1.15.1-55.el7_9 will be an update
---> Package terraform.x86_64 0:1.3.5-1 will be updated
---> Package terraform.x86_64 0:1.3.6-1 will be an update
---> Package tzdata.noarch 0:2022e-1.el7 will be updated
---> Package tzdata.noarch 0:2022f-1.el7 will be an update
--> Running transaction check
---> Package fuse3.x86_64 0:3.6.1-4.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=========================================================================================================================================
 Package                      Arch                 Version                          Repository                                      Size
=========================================================================================================================================
Updating:
 fuse-overlayfs               x86_64               1.5.0-1.el7.5.2                  devel_kubic_libcontainers_stable                68 k
 kpartx                       x86_64               0.4.9-136.el7_9                  updates                                         81 k
 krb5-devel                   x86_64               1.15.1-55.el7_9                  updates                                        273 k
 krb5-libs                    x86_64               1.15.1-55.el7_9                  updates                                        810 k
 libkadm5                     x86_64               1.15.1-55.el7_9                  updates                                        180 k
 terraform                    x86_64               1.3.6-1                          hashicorp                                       13 M
 tzdata                       noarch               2022f-1.el7                      updates                                        491 k
Installing for dependencies:
 fuse3                        x86_64               3.6.1-4.el7                      extras                                          47 k

Transaction Summary
=========================================================================================================================================
Install             ( 1 Dependent package)
Upgrade  7 Packages

Total download size: 15 M
Downloading packages:
Delta RPMs disabled because /usr/bin/applydeltarpm not installed.
(1/8): fuse3-3.6.1-4.el7.x86_64.rpm                                                                               |  47 kB  00:00:11
(2/8): kpartx-0.4.9-136.el7_9.x86_64.rpm                                                                          |  81 kB  00:00:12
(3/8): krb5-devel-1.15.1-55.el7_9.x86_64.rpm                                                                      | 273 kB  00:00:12
warning: /var/cache/yum/x86_64/7/devel_kubic_libcontainers_stable/packages/fuse-overlayfs-1.5.0-1.el7.5.2.x86_64.rpm: Header V3 RSA/SHA256 Signature, key ID 75060aa4: NOKEY
Public key for fuse-overlayfs-1.5.0-1.el7.5.2.x86_64.rpm is not installed
(4/8): fuse-overlayfs-1.5.0-1.el7.5.2.x86_64.rpm                                                                  |  68 kB  00:00:15
(5/8): libkadm5-1.15.1-55.el7_9.x86_64.rpm                                                                        | 180 kB  00:00:03
(6/8): tzdata-2022f-1.el7.noarch.rpm                                                                              | 491 kB  00:00:02
(7/8): krb5-libs-1.15.1-55.el7_9.x86_64.rpm                                                                       | 810 kB  00:00:13
(8/8): terraform-1.3.6-1.x86_64.rpm                                                                               |  13 MB  00:00:13
-----------------------------------------------------------------------------------------------------------------------------------------
Total                                                                                                    550 kB/s |  15 MB  00:00:27
Retrieving key from https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/CentOS_7/repodata/repomd.xml.key
Importing GPG key 0x75060AA4:
 Userid     : "devel:kubic OBS Project <devel:kubic@build.opensuse.org>"
 Fingerprint: 2472 d6d0 d2f6 6af8 7aba 8da3 4d64 3903 7506 0aa4
 From       : https://download.opensuse.org/repositories/devel:/kubic:/libcontainers:/stable/CentOS_7/repodata/repomd.xml.key
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Updating   : krb5-libs-1.15.1-55.el7_9.x86_64                                                                                     1/15
  Updating   : libkadm5-1.15.1-55.el7_9.x86_64                                                                                      2/15
  Installing : fuse3-3.6.1-4.el7.x86_64                                                                                             3/15
  Updating   : fuse-overlayfs-1.5.0-1.el7.5.2.x86_64                                                                                4/15
  Updating   : krb5-devel-1.15.1-55.el7_9.x86_64                                                                                    5/15
  Updating   : terraform-1.3.6-1.x86_64                                                                                             6/15
  Updating   : tzdata-2022f-1.el7.noarch                                                                                            7/15
  Updating   : kpartx-0.4.9-136.el7_9.x86_64                                                                                        8/15
  Cleanup    : krb5-devel-1.15.1-54.el7_9.x86_64                                                                                    9/15
  Cleanup    : terraform-1.3.5-1.x86_64                                                                                            10/15
  Cleanup    : tzdata-2022e-1.el7.noarch                                                                                           11/15
  Cleanup    : libkadm5-1.15.1-54.el7_9.x86_64                                                                                     12/15
  Cleanup    : krb5-libs-1.15.1-54.el7_9.x86_64                                                                                    13/15
  Cleanup    : fuse-overlayfs-0.7.2-6.el7_8.x86_64                                                                                 14/15
  Cleanup    : kpartx-0.4.9-135.el7_9.x86_64                                                                                       15/15
  Verifying  : kpartx-0.4.9-136.el7_9.x86_64                                                                                        1/15
  Verifying  : fuse3-3.6.1-4.el7.x86_64                                                                                             2/15
  Verifying  : libkadm5-1.15.1-55.el7_9.x86_64                                                                                      3/15
  Verifying  : krb5-libs-1.15.1-55.el7_9.x86_64                                                                                     4/15
  Verifying  : krb5-devel-1.15.1-55.el7_9.x86_64                                                                                    5/15
  Verifying  : fuse-overlayfs-1.5.0-1.el7.5.2.x86_64                                                                                6/15
  Verifying  : tzdata-2022f-1.el7.noarch                                                                                            7/15
  Verifying  : terraform-1.3.6-1.x86_64                                                                                             8/15
  Verifying  : tzdata-2022e-1.el7.noarch                                                                                            9/15
  Verifying  : fuse-overlayfs-0.7.2-6.el7_8.x86_64                                                                                 10/15
  Verifying  : libkadm5-1.15.1-54.el7_9.x86_64                                                                                     11/15
  Verifying  : kpartx-0.4.9-135.el7_9.x86_64                                                                                       12/15
  Verifying  : krb5-devel-1.15.1-54.el7_9.x86_64                                                                                   13/15
  Verifying  : krb5-libs-1.15.1-54.el7_9.x86_64                                                                                    14/15
  Verifying  : terraform-1.3.5-1.x86_64                                                                                            15/15

Dependency Installed:
  fuse3.x86_64 0:3.6.1-4.el7

Updated:
  fuse-overlayfs.x86_64 0:1.5.0-1.el7.5.2         kpartx.x86_64 0:0.4.9-136.el7_9           krb5-devel.x86_64 0:1.15.1-55.el7_9
  krb5-libs.x86_64 0:1.15.1-55.el7_9              libkadm5.x86_64 0:1.15.1-55.el7_9         terraform.x86_64 0:1.3.6-1
  tzdata.noarch 0:2022f-1.el7

Complete!
[root@localhost yum.repos.d]# yum install tree
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.excellmedia.net
 * epel: repo.extreme-ix.org
 * extras: centos.excellmedia.net
 * updates: centos.excellmedia.net
Package tree-1.6.0-10.el7.x86_64 already installed and latest version
Nothing to do
[root@localhost yum.repos.d]# yum install mariadb
Loaded plugins: fastestmirror
Loading mirror speeds from cached hostfile
 * base: centos.excellmedia.net
 * epel: repo.extreme-ix.org
 * extras: centos.excellmedia.net
 * updates: centos.excellmedia.net
Resolving Dependencies
--> Running transaction check
---> Package mariadb.x86_64 1:5.5.68-1.el7 will be installed
--> Finished Dependency Resolution

Dependencies Resolved

=========================================================================================================================================
 Package                        Arch                          Version                                  Repository                   Size
=========================================================================================================================================
Installing:
 mariadb                        x86_64                        1:5.5.68-1.el7                           base                        8.8 M

Transaction Summary
=========================================================================================================================================
Install  1 Package

Total download size: 8.8 M
Installed size: 49 M
Is this ok [y/d/N]: y
Downloading packages:
mariadb-5.5.68-1.el7.x86_64.rpm                                                                                   | 8.8 MB  00:00:04
Running transaction check
Running transaction test
Transaction test succeeded
Running transaction
  Installing : 1:mariadb-5.5.68-1.el7.x86_64                                                                                         1/1
  Verifying  : 1:mariadb-5.5.68-1.el7.x86_64                                                                                         1/1

Installed:
  mariadb.x86_64 1:5.5.68-1.el7

Complete!
[root@localhost yum.repos.d]# "


  [1]: https://i.stack.imgur.com/XCDqO.jpg
