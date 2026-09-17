WORKING WITH EBS

NAME: DEEPIKA R

REG NO: 212224100009

Aim
To create and configure an Amazon Elastic Block Store (EBS) volume, attach and mount it to an Amazon EC2 instance, create a snapshot backup, and restore the snapshot to a new EBS volume.

Algorithm / Steps
Create a new Amazon EBS volume with a size of 1 GiB.
Select the same Availability Zone as the EC2 instance.
Attach the EBS volume to the EC2 instance using /dev/sdb.
Connect to the EC2 instance using AWS Systems Manager Session Manager.
Check the available storage using df -h.
Create an ext3 file system on the EBS volume.
Create the /mnt/data-store directory.
Mount the EBS volume to /mnt/data-store.
Configure /etc/fstab for automatic mounting.
Verify that the EBS volume is successfully mounted.
Create file.txt inside the mounted EBS volume.
Verify the contents of the created file.
Create an EBS snapshot named My Snapshot.
Delete file.txt from the original EBS volume.
Create a new EBS volume from the snapshot.
Attach the restored volume to the EC2 instance using /dev/sdc.
Create the /mnt/data-store2 directory.
Mount the restored volume to /mnt/data-store2.
Verify that file.txt has been successfully restored.
Program
1. Check Available Storage
```
df -h
```
2. Create an ext3 File System
```
sudo mkfs -t ext3 /dev/sdb
```
3. Create a Mount Directory
```
sudo mkdir /mnt/data-store
```
4. Mount the EBS Volume
```
sudo mount /dev/sdb /mnt/data-store
```
5. Configure Automatic Mounting
```
echo "/dev/sdb   /mnt/data-store ext3 defaults,noatime 1 2" | sudo tee -a /etc/fstab
```
6. View the File System Configuration
```
cat /etc/fstab
```
7. Verify the Mounted Volume
```
df -h
```
8. Create a File in the EBS Volume
```
sudo sh -c "echo some text has been written > /mnt/data-store/file.txt"
```
9. Read the File
```
cat /mnt/data-store/file.txt
```
10. Delete the File
```
sudo rm /mnt/data-store/file.txt
```
11. Verify File Deletion
```
ls /mnt/data-store/
```
12. Create a Mount Directory for the Restored Volume
```
sudo mkdir /mnt/data-store2
```
13. Mount the Restored EBS Volume
```
sudo mount /dev/sdc /mnt/data-store2
```
14. Verify Snapshot Restoration
```
ls /mnt/data-store2/
```
Expected output:
```
file.txt
```
Outputs
<img width="1600" height="768" alt="image" src="https://github.com/user-attachments/assets/ed6966b1-210e-4c06-84e4-1101ae23205a" />
<img width="1600" height="764" alt="image" src="https://github.com/user-attachments/assets/48395ab0-d354-407b-a5c9-9aeae5752da2" />
<img width="1875" height="595" alt="image" src="https://github.com/user-attachments/assets/c1d8b4dc-2734-444d-b070-334e6f526cc6" />
<img width="1871" height="707" alt="image" src="https://github.com/user-attachments/assets/85ad042f-f9e1-484c-9e88-4a5ce58c274f" />
<img width="1917" height="606" alt="image" src="https://github.com/user-attachments/assets/bf3a1a6b-8fbd-42d5-9b72-544c6d04240a" />
<img width="1600" height="760" alt="image" src="https://github.com/user-attachments/assets/e22fc9ef-85f6-4fe4-9a74-8e04eafbdbf8" />
<img width="1918" height="930" alt="image" src="https://github.com/user-attachments/assets/82bb3121-8e6f-4f48-b3eb-08175fd480f4" />
<img width="1548" height="546" alt="image" src="https://github.com/user-attachments/assets/785e7eb0-f2a8-45b6-ad9b-a42587132873" />

Result

Thus, an Amazon EBS volume was successfully created and attached to an Amazon EC2 instance. The volume was formatted with an ext3 file system, mounted, and used for storing data. An EBS snapshot was successfully created as a backup, and a new EBS volume was restored from the snapshot. The previously deleted file.txt was successfully recovered, demonstrating the backup and restore functionality of Amazon EBS.

