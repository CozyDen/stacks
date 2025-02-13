## Storage floor-plan
- 1x 18tb media drive, no shits given if it fails, seperated for good reason
- 3x 8tb RaidZ, one drive can fail without losing data, would mean only half (16Tb) is usable
  - Entirely dedicated to MinIO + NextCloud
    - MinIO may need to be on k8s, same for next-cloud
    - Optionally, running both on the NAS host and keeping it isolated
    - A seperate MinIO or NextCloud instance could be ran on k8s to allow for better control & public access
      - Or some type of reverse proxy, something like that
    - https://github.com/mikeroyal/Self-Hosting-Guide?tab=readme-ov-file
- 2x bare metal nvmes on the PvE host OR via iSCSI
  - One passthroughed to a CT for k8s
    - https://github.com/democratic-csi/democratic-csi ZFS provisioner for volumes
    - A snapshot controller for taking snapshots and sending them to the redundancy pool via s3
  - One passthroughed to a CT for any linux-based game servers
    - Backups probabily orchestrated manually, could just be orchestrated via s3
    - Highly game server dependent, sadly
- AS5404T, 4 bay NAS + 4 m.2
  - M.2 can be used as a caching layer or a way to move/add to the general network storage via iSCSI


https://store.ui.com/us/en/category/all-switching/products/usw-pro-max-16
https://store.ui.com/us/en/category/switching-utility/products/usw-flex-2-5g-5