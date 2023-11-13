# OSN data access

OSN ([Open Storage Network](https://www.openstoragenetwork.org/)) buckets by default are with public Read access, which is convenient for our use.

To set up data access using `rclone`:
1. Follow the steps [here](https://openstoragenetwork.readthedocs.io/en/latest/accessing-datasets.html#rclone) to install `rclone` 
2. Configure access to OSN by generating and editing `rclone.conf` according to [here](https://openstoragenetwork.readthedocs.io/en/latest/accessing-datasets.html#rclone-configuration)
  - example entry:
    ```ini
    [alias]  # how you want to call this in rclone
    type = s3
    provider = Ceph
    access_key_id =  # keep blank for anonymous access
    secret_access_key =  # keep blank for anonymous access
    endpoint = https://sdsc.osn.xsede.org
    no_check_bucket = true
    ```
  - ask @leewujung for specific `bucket_name`
  - once you set it up, test by running `$ rclone lsd alias:/bucket_name` to check that you can see the folders in the bucket
