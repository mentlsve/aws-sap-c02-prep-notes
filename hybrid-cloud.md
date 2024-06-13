# Storage Gateway

Host platform for gateways:
* VMware ESXi
* Microsoft Hyper-V
* Linux KVM
* Amazon EC2
* Hardware Appliance

## S3 File Gateway

* Glacier tiers can not be used, the 4 others can be used
* Client uses NFS or SMB to indirectly access data in the configured S3 Bucket
* S3 File Gateway acts as a cache

## FSx File Gateway

* Although FSx can be mounted directly, FSx File Gateway can improve performance because of caching
  
## Volume Gateway

* Block storage (iSCSI).
* Volumes will be backed up (S3)

## Tape Gateway

* Virtual Tape Library will be backed up (S3)

# Snow Family

* Snowcone 8 or 14TB (use up to 24 terrabytes)
* Snowball Edge (use up to petabytes)
  * Storage Optimized 80TB -210TB
  * Compute Optimized 
* Snowmobile <100 PB

E.g. Transferring 100TB over 1Gbps takes 12 days
