NFS Mount
=========

Manage NFS mounts.


Role Variables
--------------

- `nfs_mount_opts`: Default NFS mount options
- `nfs_version`: Default NFS version to use (4)
- `nfs_share_mounts`: List of dictionaries of NFS shares:
   - path: mount-point
   - location: nfs server path
   - opts: mount options (optional)
   - dump: fs to dump (optional)
   - passno: fs checks on reboot (optional)


Example Playbook
----------------

    - hosts: localhost
      vars:
        nfs_version: 3 # to force nfs version to 3.
      roles:
      - role: nfs-mount
        nfs_share_mounts:
        - path: /mnt/remote
          location: nfs.example.org:/data
        - path: /mnt/readonly
          location: nfs.example.org:/read-only
          opts: "{{ nfs_mount_opts }},ro"
        - path: /mnt/ex_passno
          location: nfs.example.org:/ex_passno
          passno: 0
        - path: /mnt/ex_dump
          location: nfs.example.org:/ex_dump
          dump: 0


Author Information
------------------

ome-devel@lists.openmicroscopy.org.uk
