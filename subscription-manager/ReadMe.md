<!DOCTYPE html>
<html>
<head>
  <title>RHEL Subscription Manager Guide</title>
</head>
<body>
  <h1>RHEL Subscription Manager</h1>

  <p>This document explains how to register a Red Hat Enterprise Linux system with the Subscription Manager, attach subscriptions, and manage repositories.</p>

  <h2>1. Check Subscription Status</h2>
  <pre>
[root@localhost ~]# subscription-manager status 
+-------------------------------------------+ 
   System Status Details 
+-------------------------------------------+ 
Overall Status: Unknown 
System Purpose Status: Unknown
  </pre>

  <h2>2. Register System</h2>
  <pre>
[root@localhost ~]# subscription-manager register 
Registering to: subscription.rhsm.redhat.com:443/subscription 
Username: madhavisawant 
Password: ************ 
The system has been registered with ID: df29c0cf-b18e-40a9-b99f-34cf0708e02a 
The registered system name is: localhost.localdomain
  </pre>

  <h2>3. Attach Subscription</h2>
  <pre>
[root@localhost ~]# subscription-manager attach --auto 
Installed Product Current Status: 
Product Name: Red Hat Enterprise Linux Server 
Status:       Subscribed
  </pre>

  <h2>4. Verify Subscription Status</h2>
  <pre>
[root@localhost ~]# subscription-manager status 
+-------------------------------------------+ 
   System Status Details 
+-------------------------------------------+ 
Overall Status: Current 
System Purpose Status: Not Specified
  </pre>

  <h2>5. List Subscriptions</h2>
  <pre>
[root@localhost yum.repos.d]# subscription-manager list 
+-------------------------------------------+ 
    Installed Product Status 
+-------------------------------------------+ 
Product Name:   Red Hat Enterprise Linux Server 
Product ID:     69 
Version:        7.9 
Arch:           x86_64 
Status:         Subscribed 
Starts:         11/24/2021 
Ends:           11/24/2022
  </pre>

  <h2>6. Repository Configuration</h2>
  <p>All repositories are stored at <code>/etc/yum.repos.d/</code>.</p>
  <pre>
[root@localhost yum.repos.d]# ls 
epel.repo          redhat.repo       remi-glpi93.repo   remi-php54.repo  remi-php72.repo  remi-php80.repo  remi-safe.repo 
epel-testing.repo  remi-glpi91.repo  remi-glpi94.repo   remi-php70.repo  remi-php73.repo  remi-php81.repo 
mariadb.repo       remi-glpi92.repo  remi-modular.repo  remi-php71.repo  remi-php74.repo  remi.repo
  </pre>

  <h3>Example redhat.repo entry</h3>
  <pre>
[rhel-7-server-ose-4.11-debug-rpms] 
metadata_expire = 86400 
baseurl = https://cdn.redhat.com/content/dist/rhel/server/7/7Server/$basearch/ose/4.11/debug 
enabled = 0 
gpgkey = file:///etc/pki/rpm-gpg/RPM-GPG-KEY-redhat-release 
gpgcheck = 1
  </pre>

  <h2>7. Display Enabled Repositories</h2>
  <pre>
[root@localhost yum.repos.d]# yum repolist 
repo id                     repo name                                                  status 
epel/x86_64                 Extra Packages for Enterprise Linux 7 - x86_64             13,746 
mariadb                     MariaDB                                                        83 
remi-php74                  Remi's PHP 7.4 RPM repository                                436 
rhel-7-server-rpms/x86_64   Red Hat Enterprise Linux 7 Server (RPMs)                  32,908 
repolist: 75,365
  </pre>

  <h2>8. Important Configurations</h2>
  <h3>Disable Proxy if Not Needed</h3>
  <p>Check <code>/etc/rhsm/rhsm.conf</code> to ensure proxy is not configured if unnecessary.</p>

  <h3>YUM Configuration</h3>
  <pre>
# /etc/yum.conf
[main] 
cachedir=/var/cache/yum/$basearch/$releasever 
keepcache=0 
debuglevel=2 
logfile=/var/log/yum.log 
exactarch=1 
obsoletes=1 
gpgcheck=1 
plugins=1 
installonly_limit=3
  </pre>

  <hr>
  <p><b>Note:</b> Always refresh subscriptions after making changes using <code>subscription-manager refresh</code>.</p>
</body>
</html>
