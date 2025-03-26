## podman 5.4.1

### Fedora 41 x86_64

#### SELinux security context
> [!CAUTION]
> ```shell
> docker run -it --rm -v $(pwd):/emba localhost/ubuk:v1
> ```
> ```
> Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.
> root@db0761beaa99:/# ls emba/
> ls: cannot open directory 'emba/': Permission denied
> ```
> 😨
> 

> [!NOTE]
> 
> ```shell
> ls -Z      
> ```
> ```
> system_u:object_r:container_file_t:s0:c667,c807 bin     system_u:object_r:container_file_t:s0:c667,c807 mnt
> system_u:object_r:container_file_t:s0:c667,c807 boot    system_u:object_r:container_file_t:s0:c667,c807 opt
> system_u:object_r:container_file_t:s0:c667,c807 dev                         system_u:object_r:proc_t:s0 proc
>            unconfined_u:object_r:user_home_t:s0 emba    system_u:object_r:container_file_t:s0:c667,c807 root
> system_u:object_r:container_file_t:s0:c667,c807 etc     system_u:object_r:container_file_t:s0:c667,c807 run
> system_u:object_r:container_file_t:s0:c667,c807 home    system_u:object_r:container_file_t:s0:c667,c807 sbin
> system_u:object_r:container_file_t:s0:c667,c807 lib     system_u:object_r:container_file_t:s0:c667,c807 srv
> system_u:object_r:container_file_t:s0:c667,c807 lib32                      system_u:object_r:sysfs_t:s0 sys
> system_u:object_r:container_file_t:s0:c667,c807 lib64   system_u:object_r:container_file_t:s0:c667,c807 tmp
> system_u:object_r:container_file_t:s0:c667,c807 libx32  system_u:object_r:container_file_t:s0:c667,c807 usr
> system_u:object_r:container_file_t:s0:c667,c807 media   system_u:object_r:container_file_t:s0:c667,c807 var
> ```
>
> 
> ```shell
> chcon -R --reference=/var emba
> ```
> ```
> chcon: cannot read directory 'emba': Permission denied
> ```
>
> 
> ```shell
> chcon --reference=/var emba
> ```
> ```
> chcon: failed to change context of 'emba' to 'system_u:object_r:container_file_t:s0:c667,c807': Permission denied
> ```
>
> 🤷
> 

> [!TIP]
> Fix:
> 
> add `:z` to it just like `cp -Z` or `mv -Z`:
> ```shell
> docker run -it --rm -v $(pwd):/emba:z localhost/ubuk:v1
> ```
> ```
> Emulate Docker CLI using podman. Create /etc/containers/nodocker to quiet msg.
> root@bf84131a18ab:/# ls emba/
> CODE_OF_CONDUCT.md  CONTRIBUTORS.md  LICENSE    SECURITY.md       config              emba     installer     licenses  scan-profiles
> CONTRIBUTING.md     Dockerfile       README.md  check_project.sh  docker-compose.yml  helpers  installer.sh  modules
> ```
>
> (it's needed only for the first time.)
> 
> ✅
> 
