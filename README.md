SELinux Generic Monitor Interface to create simple SELinux modules for monitoring applications
==========================================================
https://github.com/Laurent-Gaillard/selinux_generic_monitor

## Introduction

This SELinux interface was created to help people develop simple SELinux modules for
monitoring applications.

The file exposes multiple interface named after their purpose 

When used correctly, this SELinux interface will avoid you a lot of work by calling 
simple interfaces.

## Prerequisites

You will absolutely need to install selinux-policy-devel package to compile SELinux modules.

## How to use this SELinux module

This interface file must be placed into a subdirectory of */usr/share/selinux/devel/include/*
You can either:  
 - put it in the apps subdirectory  
 - create a subdirectory of your own

Once the SELinux interface is in place, you will be able to use the interfaces in your own 
modules and compile them.

## Templates / Interfaces explanation

"*Domain subname*" stands for the name of the monitoring application / purpose, ...

### generic_mon_app_domain
- *type*: **template**
- *description*:  ****This template creates a domain, types, and rules to be used by a monitoring application.**
- *parameters*:
    - **domain subname**

### generic_mon_listening_socket:
- *type*: **interface**
- *description*:  **Authorize to create a listening socket.**
- *parameters*:
    - **domain subname**

### generic_mon_connecting_socket:
- *type*: **interface**
- *description*:  **Authorize to connect to socket.**
- *parameters*: The domain subname to be authorized to connect to socket.
    - **domain subname**

### generic_mon_commom_access
- *type*: **interface**
- *description*:  **Authorize to get some basic infos for monitoring tools (processes, fs info).**
- *parameters*: 
    - **domain subname**
### generic_mon_pid_file_trans
- *type*: **interface**
- *description*:  **Ensure pid files are labelled correctly.**
- *parameters*: 
    - **domain subname**

### generic_mon_sudo_exec   
- *type*: **interface**
- *description*:  **Run commands through sudo.**
- *parameters*:
    - **domain subname**

### generic_mon_kernel_message    
- *type*: **interface**
- *description*:  **Read and send kernel messages.**
- *parameters*:
    - **domain subname**

### generic_mon_manage_tmp_files
- *type*: **interface**
- *description*:  **Manage tmp files and ensure they are labelled correctly.**
- *parameters*:
    - **domain subname**

### generic_mon_dmesg
- *type*: **interface**
- *description*:  **Allow to run dmesg command.**
- *parameters*:
    - **domain subname**

### generic_mon_systat
- *type*: **interface**
- *description*:  **Allow to run systat commands.**
- *parameters*:
    - **domain subname**

### generic_mon_write_devlog
- *type*: **interface**
- *description*:  **Allow to write to devlog sock file.**
- *parameters*:
    - **domain subname**

### generic_mon_service_status
- *type*: **interface**
- *description*:  **Allow to check service / unit status.**
- *parameters*:
    - **domain subname**

### generic_mon_read_dir_auditd_log
- *type*: **interface**
- *description*:  **Allow to read auditd log directories.**
- *parameters*:
    - **domain subname**

### generic_mon_monitoring_metrics
- *type*: **interface**
- *description*:  ** Allow to bind on monitoring port
- *parameters*:
    - **domain subname**
## Customisation with booleans
Be very carefull when turning those booleans to true till it provides great privileges. 
### generic_mon_**<domain_subname>**_allow_net_admin
- *description*:  **Authorize to manage all networking configurations and modifications on self. 
- *default*: **false**

### generic_mon_**<domain_subname>**_allow_execmem
- *description*:  **Authorize to make executable an anonymous mapping or private file mapping that is writable. 
- *default*: **false**

## Disclaimer

The code of the this SELinux policy module is provided AS-IS. People and organisation
willing to use it must be fully aware that they are doing it at their own risks and
expenses.

The Author(s) of this SELinux policy module SHALL NOT be held liable nor accountable, in
 any way, of any malfunction or limitation of said module, nor of the resulting damage, of
 any kind, resulting, directly or indirectly, of the usage of this SELinux policy module.

It is strongly advised to always use the last version of the code, to check for the 
compatibility of the platform where it is about to be deployed, to compile the module on
the target specific Linux distribution and version where it is intended to be used.

Finally, users should check regularly for updates.
